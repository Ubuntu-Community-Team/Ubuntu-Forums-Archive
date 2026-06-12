---
title: "A few newbie Q's"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by Aybara on 2006-01-15
Hi guys.

Installed Ubuntu on my Inspiron 6000 yesterday, and so far everything works like a charm! Now I have to start the tedious work of finding out how accomplish my windows tasks in linux. I'll probably find many answers myself, bu I thought maybe I could get a head start here :-)

I use linux at work ( Fedora Core 4 ) so I'm not a complete newbie, but I wanna do other things than programming at home...

I have to get used to the linux-folders. Where do you guys put folders for downloads, music/video/photo-collections and such? Is there a place where I can find out what "roles" var, srv, sbin, proc ++ have?

A command for viewing hard-disk usage?

I browsed quickly thru the topic of which linux-apps to use instead of given windows-apps, and I think it covered most of what I need. There are a few apps I don't like getting rid of, however, so I was wondering if there is a way to run any of them under linux ( wine/crossover office ? ). The apps are: Adobe Photoshop Album, Media Player Classic ( maybe I'll get used to VLC or mplayer ), Total Commander Powerpack and Winamp. (I have an iPod and use winamp with the ml_ipod plugin to sync to my iPod)

I have an ATI Mobility Radeon X300. Is there any other drivers for this than the ones that came with the Ubuntu install? I think I see some lagging when I switch between application windows.

I have an external 300GB HD that is NTFS. Is the NTFS write support in Linux reliable yet? I have read about some problems here... If not, I guess it is a problem to convert my HD from NTFS to EXT3 without losing my data?

Overall I am very excited about Ubuntu. Worked out of the box and looks great! I just can't wait to start bothering you guys with all my petite problems ;-)

---

### Post by pertti on 2006-01-15
[QUOTE=Aybara]I have to get used to the linux-folders. Where do you guys put folders for downloads, music/video/photo-collections and such? Is there a place where I can find out what "roles" var, srv, sbin, proc ++ have?[/QUOTE]

I put my music/photos etc in my home folder (/home/myuser/), which is fine since I'm the only one using this computer (but I guess you can change the permissions of this folders to allow others to browse them). I also use a Fat partition (I still have windows installed) for a lot of music and movies, with no particular organization, but I plan to get rid of it.

[QUOTE=Aybara]A command for viewing hard-disk usage?[/QUOTE]

```
df -h
```

[QUOTE=Aybara]I browsed quickly thru the topic of which linux-apps to use instead of given windows-apps, and I think it covered most of what I need. There are a few apps I don't like getting rid of, however, so I was wondering if there is a way to run any of them under linux ( wine/crossover office ? ). The apps are: Adobe Photoshop Album, Media Player Classic ( maybe I'll get used to VLC or mplayer ), Total Commander Powerpack and Winamp. (I have an iPod and use winamp with the ml_ipod plugin to sync to my iPod)[/QUOTE]

I haven't used Adobe Photoshop Album, but I think F-Spot is the equivalent. Gthumb also has some cataloging abilities. For music I use Rhythmbox, but I'm not sure if works with iPods. I think Banshee does, and I heard of GtkPod, but I don't have an iPod, so I can't help you here.

[QUOTE=Aybara]I have an ATI Mobility Radeon X300. Is there any other drivers for this than the ones that came with the Ubuntu install? I think I see some lagging when I switch between application windows.[/QUOTE]

ATI support on Linux sucks a bit (unless you have a Radeon 9200). I have a 9600 Pro, using ATI's drivers, but I don't rembember how much better it performs.

[QUOTE=Aybara]I have an external 300GB HD that is NTFS. Is the NTFS write support in Linux reliable yet? I have read about some problems here... If not, I guess it is a problem to convert my HD from NTFS to EXT3 without losing my data?[/QUOTE]

As far as I recall is not safe, if even possible, to write on an NTFS partition. There are drivers for Windows for reading/writing on ext2 and ext3 (with no journaling) partitions. I plan to reduce my windows' NTFS partition to a few gigabytes, and create a "middleground" ext partition used by both, but being a lazy guy, I guess I'll just backup everything up and start form scratch ;).

---

