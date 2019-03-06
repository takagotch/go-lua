### go-lua
---
https://github.com/Shopify/go-lua

```go
package main

import "github.com/Shopify/go-lua"

func main() {
  l := lua.NewState()
  lua.OpenLibraries(l)
  if err := lua.DoFile(l, "hello.lua"); err != nil {
    panic(err)
  }
}

function fib(n)
  if n == 0 then
    return 0
  elseif n == 1 then
    return 1
  end
  return fib(n-1) + fib(n-2)
end


function fibt(n0, n1, c)
  if c == 0 then
    return n0
  else if c == 1 then
    return n1
  end
  return fibt(n1, n0+n1, c-1)
end

function fib(n)
  fibt(0, 1, n)
end


function fib(n)
  if n == 0 then
    return 0
  else if n == 1 then
    return 1
  end
  local n0, n1 = 0, 1
  for i = n, 2, -1 do
    local tmp = n0 + n1
    n0 = n1
    n1 = tmp
  end
  return n1
end
```

```
go get github.com/Shopify/go-lua
git submodule updte --init
go build
go test -cover

time lua fibr.lua

time glua fibr.lua
time glua fibr.lua
time go-lua fibr.lua

time lua fib.lua
time glua fibt.lua
time go-lua fibt.lua
```

```
```


