---
title: "File Spliter *.avi"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by BGMD on 2007-02-03
Here is the thing i have movie and its been split with [FileSpliter]("http://www.softpedia.com/get/System/File-Management/File-Spliter.shtml") to 27 parts.

Thing is I need to merge these files to get *.avi and I don't know how or is it even possible in linux :)

When u split file with this program u get movie.000 movie.001 movie.002 etc. files and movie.bat file to merge it to *.avi.

This is example of bat file..
```
Copy /b "movie.000"+"movie.001"+"movie.002" "movie.avi"


```

Any ideas or solutions?

---

### Post by neilp85 on 2007-02-11
This is actually relatively simple to accomplish using mencoder (assuming the files weren't modified when split). The following commands should accomplish what you want.
```
sudo apt-get install mencoder
mencoder -forceidx -oac copy -ovc copy -o movie.avi movie.0??
```

---

