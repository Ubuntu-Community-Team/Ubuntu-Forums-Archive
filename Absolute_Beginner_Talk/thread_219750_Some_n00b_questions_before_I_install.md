---
title: "Some n00b questions before I install"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by jdmcadam on 2006-07-20
First off I'd like to say I'm really impressed by the level of support from the Linux community, I think its amazing. I'm a long time PC user, dating back to DOS, Win 3.1 all the way up to XP, so I'm not really a total newb, but this is the first time I've ever dealt with Linux and I have a few questions. I received an Ubuntu live CD from a friend, and it looks perfect, but before I do a full an install and remove windows from my life (finally!) I need to know a couple of things...

1) I have an nVidia GeForce 6600 LE and an acer 1440x900 monitor which doesn't seem to be a supported resolution. I tried the 1280x800 resolution but the fonts are grainy and edges are unsharp. Is there any way to get this resolution supported?

2) I need, NEED, to have the following programs: Flash 8, Photoshop (7 or higher) and Illustrator (10 or higher). I've checked out Gimp, but I really must have Photoshop for work. Is there a way to have my cake and eat it too?

3) I couldn't seem to get XGL working. This isn't a huge deal, but if I can get it working that'd be awesome, 'cause it looks really cool. I copy and pasted the command line stuff from a forum but got an error (and being a n00b I forgot to write down where I got the error). Is this because I was only working off the Live CD and didn't do a full install, or is there something greater at work.

Thank you in advance for anyone who takes the time to help me through this. I'm sorry if any of this is covered in another thread, but the fourm's size is a bit daunting and I was unable to comb through all the threads looking for an answer. Please feel free to redirect me to a thread that might answer any of these questions.

---

### Post by aysiu on 2006-07-20
If you need NEED those applications, get Crossover Office or run Windows using VMWare.

---

### Post by nalmeth on 2006-07-20
When you install, you can install [Nvidia's Proprietary Driver]("http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation"), which should solve problems 1 and 3.

Since flash 8 for linux was skipped by macromedia ](*,) you'll have to install Internet Explorer or Firefox (I'd go with firefox ;) ) in wine, and use that browser when you specifically need it.

I realize we beat the dead horse alot around here, but have you tried [gimpSHOP]("http://www.gimpshop.net/")? It's designed to feel more like photoshop.

If you're absolutely, irreversibly needing Photoshop, you will have to pick up [CrossOver Office]("http://www.codeweavers.com/") to run Photoshop 7

---

### Post by Klaidas on 2006-07-20
First, welcome. ;)
I would suggest you to dual boot, that is, have both Windows and Linux on your computer.
As far as I know, neither flash8, neither photoshop is availible for linux.
As for XGL, it's still alpha software, and you were using LiveCD, so it's not a surprise to have problems with it :)
For resolution, you should be able to manually adjust it by editing some files.

Again, I think you should be dual booting, so you could use both linux and windows

---

### Post by Klemik on 2006-07-20
Maybe you should leave your Windows partition and go with dual boot ?
About the resolution... after instaling nvidia drivers (I have ati, so I wont help you here, but there are tons of tuts on the forums about nvidia drivers), you should get that resolution; if not you can manually add it to xorg.conf or try to hit Ctrl+Alt+KEYPAD_PLUS.

---

### Post by ThrobbingBrain66 on 2006-07-20
EDIT: What everyone else said. lol

---

### Post by cstudent on 2006-07-20
> **Klaidas said:**
> 
Again, I think you should be dual booting, so you could use both linux and windows

I second that. Making the switch cold turkey isn't easy. There will a lot of new stuff to learn.

---

### Post by andrewabc on 2006-07-20
I would dual boot. I installed ubuntu (linux for the first time) a month ago, I like it, but I still need windows for some proprietary sofware that won't run on linux (and there are no alternatives possible).

You already payed for windows, might as well use it when needed ;)

---

### Post by jdmcadam on 2006-07-20
Wow.
Thanks for the amazing responses from everyone, you guys rock. I think I will go with the dual boot option, but I've never partitioned a hard drive before. I'm sure I can handle it no probelm, but how much space should I give to each partition? Should I look into getting a second harddrive to just run my OSes off of, and store all my other files on the second HD? Any other adivce for this? Anyone know where I put my windows CD?

---

### Post by aysiu on 2006-07-20
Read this:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by Blondie on 2006-07-20
> **jdmcadam said:**
> Wow.
Thanks for the amazing responses from everyone, you guys rock. I think I will go with the dual boot option, but I've never partitioned a hard drive before. I'm sure I can handle it no probelm, but how much space should I give to each partition? Should I look into getting a second harddrive to just run my OSes off of, and store all my other files on the second HD? Any other adivce for this? Anyone know where I put my windows CD?

Some people keep Ubuntu on one hard drive and Windows on a separate hard drive but there's really no problem in running both off a single partitioned hard drive. It's easy to do. I wouldn't get an extra hard drive *unless* you feel that you need more space.

Personally I have two hard drives but I run them as one integrated whole using Ubuntu's built in RAID 0 hard disk striping and don't have Windows on my system at all, only Ubuntu. The options are very flexible.

---

