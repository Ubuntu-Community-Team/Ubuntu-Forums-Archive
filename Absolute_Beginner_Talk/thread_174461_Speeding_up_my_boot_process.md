---
title: "Speeding up my boot process"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by Clay85 on 2006-05-11
I'd like to fiddle around with my boot-up options to disable things I"m not using. I tried following the directions [here]("http://www.ubuntuforums.org/showthread.php?t=89491&highlight=faster+bootuphere") 

But when I type sudo apt-get install sysv-rc-conf in my terminal I get this

```
enzo@reboot:~$ sudo apt-get install sysv-rc-conf
Reading package lists... Done
Building dependency tree... Done
Package sysv-rc-conf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sysv-rc-conf has no installation candidate

```

I'm not really sure what I'm supposed to be doing, so I know I'm doing it incorrectly. If this isn't enough information just prod me a little, I can try to tell you more about what I'm doing.

---

### Post by xXx 0wn3d xXx on 2006-05-11
[QUOTE=Clay85]I'd like to fiddle around with my boot-up options to disable things I"m not using. I tried following the directions [here]("http://httphttp://www.ubuntuforums.org/showthread.php?t=89491&highlight=faster+bootuphere://www.ubuntuforums.org/showthread.php?t=89491&highlight=faster+bootuphere") 

But when I type sudo apt-get install sysv-rc-conf in my terminal I get this

```
enzo@reboot:~$ sudo apt-get install sysv-rc-conf
Reading package lists... Done
Building dependency tree... Done
Package sysv-rc-conf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sysv-rc-conf has no installation candidate

```

I'm not really sure what I'm supposed to be doing, so I know I'm doing it incorrectly. If this isn't enough information just prod me a little, I can try to tell you more about what I'm doing.[/QUOTE]
That link sends me to the national weather center but make sure that you have the multiverse and universe repositories enabled.

---

### Post by Clay85 on 2006-05-11
Sorry. I fixed the link (I think). I'm not used to this copy and paste thing yet.

Well that brings up two and a half questions.
1 & 1.5: What are the multiverse and universe? (this sounds like a Sci-Fi show)
2: What are repositories? (Is that a euphemism?)

---

### Post by confused57 on 2006-05-11
Here's how to enable extra repositories:

[http://help.ubuntu.com/starterguide/C/ch02.html](http://help.ubuntu.com/starterguide/C/ch02.html)

You may be able to use BUM to change startup options:

[http://www.ubuntuforums.org/showthread.php?t=174345](http://www.ubuntuforums.org/showthread.php?t=174345)

---

### Post by Clay85 on 2006-05-11
Well I'm making a little more progress...

I went [here]("http://doc.gwos.org/index.php/Reduce_boot")

And changed a whole bunch of my files! I hope this works... o.O

---

### Post by Clay85 on 2006-05-11
Well... now it takes about a minute longer to boot up.

---

### Post by skippy81 on 2006-05-11
A bit unrelated but something worth checking:-

Open a terminal and type:

> sudo hdparm /dev/hda1

you may have to change hda1 if you have multiple hard disks.  

If using_dma is set to 0 then your boot up time will be about 5 times longer than it set to 1.  If this is the case then maybe now would be a good time to try dapper out, it has a newer kernel and is more likely to recognise your southbridge.  

The difference with dma enabled is massive, when I upgraded my breezy kernel i got great results with DMA on.

---

### Post by Clay85 on 2006-05-12
Haha. o.O I don't think I understood most of what you said, but my dma is on. 
using_dma    =  1 (on)
Whatever that means.

I think I give up on this boot thing for a bit. It seems much too complicated. I can't even install anything, yet. I mess something up... I get an error everytime I try to install anything. X.X

---

### Post by nalmeth on 2006-05-12
don't know the solution, but maybe this might find it.
If you're looking for a package and know some of it's name, type:
apt-cache search sysv-rc-conf

---

