---
title: "Problems with Ubuntu"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by streno on 2007-12-27
Hey guys;) This is my first post, so forgive me for my mistakes.

I wanted something new, so before few days I installed Ubuntu to try it out, all my life was big win XP fan. I had some problems with partitions, because wanted to keep Win XP too, so I installed linux to all my HDD (80gb). The installation process was good enough tho.

But as the title says, I have some huge problems with Ubuntu latest version. I have pretty fast pc (Dual Core (1.7 GHz), 1gb RAM, 80gb, ATI radeon 1100 and etc), but linux is laggy for me. I will try to explain all my problems and I hope someone could help me.

First of all, when I turn my pc and linux should boot up.
Loading GRUB and etc.. But after all that stuff I just get black screen.. Something like loading but nothing happens. Yesterday waited like 10mins with that black screen but nothing happened. When I reboot pc.. Once again (Loading GRUB) and linux loads with no errors. It's like for me -> Linux start normally -> Black screen -> starts normally -> black screen. So, one time it works noramally other time it doesn't. Maybe someone knows what the f*** is this?

Other huge problem I get when I work with linux. Like listening to music, web browsing, skyping and etc. Sometimes it just collapse. I can't do a thing. Even move a mouse or to turn on the root terminal to check what processes takes so much CPU or why it collapses. Once I opened like ten mozzila tabs and it collapsed. All the time it happens I can't do a thing, I just have to reboot pc and once again, it doesn't load normally, I have to reboot it once again to load it up normally. Sometimes when I leave pc for some time screen goes black, same as in Windows screensaver, after that when I move mouse it moves for few seconds and after that it collapse. Maybe someone knows why do I have that?

Another problems is.. Some times Linux don't understand that I have mouse, it just loads up and mouse doesn't work. Mouse doesn't even show any light, that red one. It's good that I have mouse pad in laptop so I can't reboot Linux and just hope it will understand that I have mouse and I will be able to use after load up.

I would like to use Linux for longer period but it seems that we don't get along with it. And after I tried Linux I don't want to get to Windows. I hope someone will help me with my problems because it starts to annoy me.

Thanks!

---

### Post by jas0 on 2007-12-27
First of all, welcome to the UbuntuForums mate!

I want you to know that what you're experiencing is definitely not normal for Ubuntu. To me it really sounds like a flaky hardware component. From your post, it is not really clear whether you have Ubuntu installed on its own drive (the 80GB drive you mentioned). If that's the case, it would not be a surprise to me if the drive was failing. The intermittent boot problems and sudden freezes definitely account for this possibility.

So first of all, try to list as much of your hardware configuration (especially hard drive stuff) as possible. Also, paste the output of your menu.lst file (in /boot/grub/menu.lst), device.map file (in /boot/grub/device.map) and of the following command:
 ```
sudo fdisk -l
```

---

