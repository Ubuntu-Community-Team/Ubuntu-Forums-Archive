---
title: "wine"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by crazydiver on 2007-08-23
Hello does anybody know if Wine can open other files besides exe. and can somebody tell me how?

---

### Post by Terl on 2007-08-23
Best place to check is:  [WineHQ]("http://www.winehq.org/site/documentation")

What are you trying to load?

---

### Post by crazydiver on 2007-08-23
bin. and cue. 

thanks for the link!

---

### Post by Terl on 2007-08-23
Those are image formats.  I know iso format can load like a drive (I am not certain how to do it...searching will help you there) but I am not sure about bin and cue and Linux.

---

### Post by caricc on 2007-08-23
try here:
[HTML]http://ubuntuforums.org/showthread.php?t=497332&highlight=.msi[/HTML]

---

### Post by rexy on 2007-08-23
to access data on bin files you have to convert them to iso using bin2iso or bchunk and mount the iso that is produced using

sudo mount -o loop image.iso /media/mountpoint

if the bin file contains a vcd mplayer can also play it directly.

---

### Post by Terl on 2007-08-23
I found this:  [http://ubuntuforums.org/showthread.php?t=354222&highlight=bin+cue]("http://ubuntuforums.org/showthread.php?t=354222&highlight=bin+cue")

EDIT:  Rexy got it :)

---

### Post by crazydiver on 2007-08-23
Thanks a lot! It helps!

---

