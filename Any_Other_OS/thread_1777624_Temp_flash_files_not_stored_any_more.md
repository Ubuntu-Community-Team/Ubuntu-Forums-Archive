---
title: "Temp flash files not stored any more"
date: 2011-06-08
forum: Any Other OS
---

### Post by myolbug on 2011-06-08
I used to be able to watch a flash file online, then it woudl store a copy in the tmp file, I then could do what I wished with it.  No longer.  
What happened?  

I am running Mint 9 with whatever updates there are.

---

### Post by wolfen69 on 2011-06-08
That changed a while ago. It stinks it no longer works that way, but there are other alternatives. I use the Video Downloadhelper add-on for firefox. Works great. And then they are downloaded to /home.

---

### Post by Perfect Storm on 2011-06-08
Moved to Other OS/Distro Talk.

---

### Post by jwcalla on 2011-06-08
There are work-arounds... I used this info here:

[http://www.webupd8.org/2011/02/play-youtube-videos-without-flash-from.html](http://www.webupd8.org/2011/02/play-youtube-videos-without-flash-from.html)

To make this script here:

```
#!/bin/bash

lsof -p `ps x | awk '/libflashplayer.so\ /{print $1}'` -n | perl -lne '@F = split(/ +/, $_, 9); print "/proc/$F[1]/fd/${\($F[3] =~ /(^\d+)/)[0]}" if $F[4] eq "REG" && $F[8] =~ /\(deleted\)$/' | xargs ls -la | grep tmp | awk '{print $8}' | xargs ls -Lla
```But it only works when a YouTube, etc. video is in the browser... once you close the tab it's gone.  Don't forget to let it download completely before copying it over.  ;)

I like that Firefox add-on idea though.

---

