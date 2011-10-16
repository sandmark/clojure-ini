# clj-ini

A small library for reading [`.ini`](http://en.wikipedia.org/wiki/INI_file) files into Clojure maps.

## Usage

`(read-ini source & opts)` where `source` can be anything accepted by
[`io/reader`](http://clojure.github.com/clojure/clojure.java.io-api.html#clojure.java.io/reader). Valid options are

- `:keywordize?` (default `false`): Turn segments and property-keys
    into keywords
- `:trim?` (default `true`): trim segments, keys and values
- `:allow-comments-anywhere?` (default `true`): Comments can appear
  anywhere, and not only at the beginning of a line
- `:comment-char` (default `\;`)

## Example

`conf.ini`:

    ; last modified 1 April 2001 by John Doe
    name=John Doe
    organization=Acme Widgets Inc.
 
    [database]
    ; use IP address in case network name resolution is not working
    server=192.0.2.62     
    port=143
    file = payroll.dat

REPL session:

    > (use 'clj-ini.core)
    > (read-ini "conf.ini" :keywordize? true)
    {:database {:file "payroll.dat"
                :port "143"
                :server "192.0.2.62"}
     :organization "Acme Widgets Inc." 
     :name "John Doe"}

## License

Copyright (C) 2011 Jonas Enlund

Distributed under the Eclipse Public License, the same as Clojure.