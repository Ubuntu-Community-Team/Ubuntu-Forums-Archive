---
title: "[SOLVED] Help with this BASH script"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Xavieran on 2008-01-07
I am writing a little script for my sister to play her flashgames...
```
#/bin/bash
quit=0
mplayer out.avi
while [  $quit -lt 2 ]; do
     location=`zenity --title="Select a game to play..." --file-selection`
     flashplayer $location
     bing=`zenity --question --text "Continue?" --title "Continue?"`
     if [  $bing -lt 1 ]; then let quit=2;fi
done

```

This *should* quit when you choose cancel in the zenity question...
However it gives me this```
autorun.sh: line 8: [: -lt: unary operator expected
```


I fixed it!

Apparently some syntax thing was going funny...

---

### Post by snickers295 on 2008-01-07
No matter what programming it is, i think syntax errors are the most common because there caused by human error.

---

