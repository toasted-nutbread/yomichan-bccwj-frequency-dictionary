# About

This repository contains the source code of a script which is used to generate a frequency dictionary for use with [Yomichan](https://github.com/FooSoft/yomichan).
It uses the data from Balanced Corpus of Contemporary Written Japanese (BCCWJ), supporting both short and long unit words.
The generated dictionary file does not contain part-of-speech information, as Yomichan does not currently support this.

## Links

* https://pj.ninjal.ac.jp/corpus_center/bccwj/en/
* https://pj.ninjal.ac.jp/corpus_center/bccwj/en/freq-list.html
* https://link.springer.com/article/10.1007/s10579-013-9261-0

## Usage

### Prerequisites

This script uses a component from [Yomichan](https://github.com/FooSoft/yomichan)'s implementation,
specifically the `JapaneseUtil` class from [japanese-util.js](https://github.com/FooSoft/yomichan/blob/227cbbc7cd6e524654cb7eb49dc2f2eb898fc83c/ext/js/language/sandbox/japanese-util.js).

This file must be manually copied into the same directory as main.js in order for the script to work.

### Running

A node script is used to generate the dictionary data:

```sh
node main.js path/to/bccwj-data.tsv ./output [long-unit-words] [min-frequency]
```

* `[long-unit-words]` _(optional)_ - `true` if using the long unit words (LUW) list; `false` otherwise.
* `[min-frequency]` _(optional)_ - Integer representing the minimum number of occurrences. Default is `0`.

The data can then be added to a .zip archive using any software.
The example below uses the 7z command line executable to generate the archive:

```sh
7z a -tzip -mx=9 -mm=Deflate -mtc=off -mcu=on BCCWJ-SUW.zip ./output/*.json
```
