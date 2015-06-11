# hash-to-object
easliy convert any hash to object accessed with dot notation
```ruby
require 'ostruct'

def convert_to_ostruct_recursive(obj)
  if obj.is_a? Hash
    obj.each {|key, val| obj[key] = convert_to_ostruct_recursive(val) }
    OpenStruct.new(obj)
  elsif obj.is_a? Array
    obj.map { |o| convert_to_ostruct_recursive(o) }
  else
    obj
  end
end
```
