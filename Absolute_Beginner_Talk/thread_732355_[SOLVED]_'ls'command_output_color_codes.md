---
title: "[SOLVED] 'ls'command output color codes"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by bilijoe on 2008-03-22
When I execute the 'ls' command (in a terminal window), the entries in the output listing are color coded.  Can anyone tell me what the various colors mean, or where to find the color key?

---

### Post by Rocket2DMn on 2008-03-22
A brief google search brings this: [http://www.cyberciti.biz/tips/where-is-color-of-ls-command-defined.html](http://www.cyberciti.biz/tips/where-is-color-of-ls-command-defined.html)

> Executable files: Green
* Normal file : Normal
* Directory: Blue
* Symbolic link : Cyan
* Pipe: Yellow
* Socket: Magenta
* Block device driver: Bold yellow foreground, with black background
* Character device driver: Bold yellow foreground, with black background
* Orphaned syminks : Blinking Bold white with red background
* Missing links ( - and the files they point to) : Blinking Bold white with red background
* Archives or compressed : Red (.tar, .gz, .zip, .rpm)
* Image files : Magenta (.jpg, gif, bmp, png, tif)
That info seems to hold true in Ubuntu, the other stuff from that page is a little weird though.

---

### Post by scottro on 2008-03-22
I think it's fairly standard, including the BSDs.  

It's usually documented somewhere though I wouldn't criticize anyone who couldn't find it--for example, in Fedora, if you go to man or info DIRCOLORS which would be a logical place to have it listed, they tell you run something which basically outputs /etc/DIRCOLORS.  If you look through there, in one section, they give numeric color codes--well below that, they give combos like 32;34 (I think--blue on green or green on blue and explain what it means.  

FreeBSD covers some of them, although not in what I'd call a clear manner, in its ls man page, which makes more sense.

---

