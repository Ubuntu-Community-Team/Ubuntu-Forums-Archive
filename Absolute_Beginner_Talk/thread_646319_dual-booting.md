---
title: "dual-booting?"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Tanhauser on 2007-12-21
Okay, here's what I need help with. You'll all probably think I'm a complete idiot, but whatever.

About a month ago, I reformatted my hard drive and installed Ubuntu 7.10. I've enjoyed it a lot, had a good time trying to iron out all the kinks and things. A few days ago I bought a video-game, Unreal Tournament 3. I haven't played games in quite a while. 

Now when I installed Ubuntu on my computer, I created a partition of maybe 60 gigs for Ubuntu and 20 gigabytes (I know it's tiny) as an empty partition because I knew I was going to try installing Windows on a partition at some point in the future.

Today, I just installed Windows. I selected the unused partition to install to, and everything went smoothly, but now I can't seem to get back to Ubuntu. Is it gone forever? Do I need to reinstall it or something? I had thought that when I restarted my computer, there would be some kind of prompt that would ask me what operating system to boot with. No such luck, it just automatically starts up in Windows. When I go to My Computer in Windows, the only hard drive is labeled "Drive E" and it's only 20 gigabytes in size. So my other partition is around somewhere, but I don't know if it's accessible at all. I haven't been able to get to it so far. 

Thank you all in advance.

---

### Post by Rocket2DMn on 2007-12-21
This is a common problem, this is probably what you're looking for
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Typically, it is easiest to install windows first, then ubuntu (for future note)

---

### Post by ubutufan on 2007-12-21
No need to panic, provided you HAVE made the installation of windows in a parttion other than ubuntu.

On a brief what has happened is that windows took over the MBR (Master Boot record) and they don't know how to take you to ubuntu. You need to fix it. That is fix windows to do it.

There is a very nice site at
[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

Miller talks about a "rescue disk". Just download-burn and use GPARTED instead. You will have the ability to use a command prompt and a parttion editor on the same graphical screen

The process is simple and safe provided YOU READ FROM START TO END. Print the document and READ IT. use a pen to take notes of partitions.
In the unlikely event that you are not sure, ask

---

### Post by Tanhauser on 2007-12-21
Thank you very much!

Guess I'll have to download and burn another CD then :S

Oh well.

---

