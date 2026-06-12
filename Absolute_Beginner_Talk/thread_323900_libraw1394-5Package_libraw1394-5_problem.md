---
title: "libraw1394-5:

Package libraw1394-5 problem"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-12-22
I am getting an error when trying to convert some movies for my ipod.  

ipodvidenc autobotspike.avi
What would you like to name the output file (sans extension)?
autobot
autobot will be located in /home/caippers. Is this acceptable? [y/n]
y
ffmpeg: error while loading shared libraries: libraw1394.so.5: cannot open shared object file: No such file or directory

So I try and load the following library from synaptic and get this error.


libraw1394-5:

Package libraw1394-5 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list


Now what.

---

### Post by Delvien on 2007-02-18
I am having a problem with this as well.


```
dm@dm-laptop:~/Desktop$ ffmpeg -vcodec xvid -b 300 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 96 -i output.avi -s 320x240 -aspect 4:3 ipod_output.mp4
ffmpeg: error while loading shared libraries: libraw1394.so.5: cannot open shared object file: No such file or directory
```

---

