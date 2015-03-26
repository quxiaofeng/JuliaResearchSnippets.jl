# JuliaResearchSnippets.jl

#### 收集整理将 Julia 使用在科研中的各种尝试

[![Build Status](https://travis-ci.org/quxiaofeng/JuliaResearchSnippets.jl.svg)](https://travis-ci.org/quxiaofeng/JuliaResearchSnippets.jl)

## `test/dataframe_transparent_rw_test.jl`

写入、读取带有 Array 元素的 DataFrame 数据。测试了五种方法，只有一种成功。

### 需要读写的数据格式

```julia
dataSet = DataFrame()
dataSet[:Labels]  = ["Person One", "Person Two", "Person 3"]
dataSet[:Feature]  = {rand(0:255,5,5), zeros(5,5), ones(5,5)}
```

### 要求

+ 简单直接的存储和读取
+ 直接解析结构化的数据
+ 数据完整准确可测试

### 失败尝试

+ `MAT.jl` 写入时出错
+ `JSON.jl` 读取时 Array 读进来还是 String
+ `DataFrame` 读取时 Array 读进来还是 String
+ `Pandas` 读取时 Array 读进来还是 String

### 成功方法

+ `serialize`/`deserialize` 成功。 但数据存储为二进制格式，优点是数据量小，缺点是无法人工查看。

