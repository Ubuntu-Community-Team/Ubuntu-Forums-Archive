---
title: "[SOLVED] Dual boot not working"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by dinostabOMG on 2007-10-22
I installed Feisty and recently upgraded to Gutsy - but I think this problem arose before the upgrade, though I'm not sure why.

I use Ubuntu for basically everything, but there are one or two crucial things I need to do in Windows. However, Windows disappeared from the grub boot menu. I did some research, and got this output from sudo fdisk -l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c9ce0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12158    97659103+  83  Linux
/dev/sda2   *       12159       12407     2000092+  82  Linux swap / Solaris
/dev/sda3           12408       19456    56621092+   7  HPFS/NTFS

```

I installed Ubuntu before Windows on my single, partitioned hard drive. I added this code to menu.lst, assuming that /dev/sda3 translates to hd(0,2), and based on what I saw other people doing.

```
title		Windows XP Professional
root		(hd0,2)
makeactive
chainloader+1
```

It didn't work, so I changed root to (hd0,1). Both of these just cause the screen to turn black for a fraction of a second and then the menu page is still there. What am I missing? I looked in various howtos but I don't understand the concepts well enough, apparently, to apply them to my specific case.

Thanks so much if you can help!

---

### Post by Pumalite on 2007-10-22
I wonder what is a boot flag doing in your /swap partition.

---

### Post by dinostabOMG on 2007-10-22
Hm, I don't know what that means. Could you elaborate? Is part of my current problem?

---

### Post by Pumalite on 2007-10-22
I don't know if it is part of your problem, but I'd use Gparted Live CD, boot from it and change that flag to sda1. Also is always better to install Windows first.

---

### Post by alienexplorers on 2007-10-22
Pumalite,
How do you use gparted CD to change boot partition.  I had a simular problem and ended up reloading everything to fix the problem while dual booting.  It was showing my boot flag under the swap too.

---

### Post by Pumalite on 2007-10-22
The GUI presents you with all kinds of menus. Flags is among them

---

### Post by dinostabOMG on 2007-10-22
I've since heard that it's better to install windows first, but I'm kind of stuck at this point. Regardless, my guess is that the change needs to happen in my menu.lst file, I just don't know what it is.

No ideas anyone?

---

### Post by Sef on 2007-10-22
1) Windows needs to be on the first partition.

2) Windows needs to be set as the boot partition.

---

### Post by tehsimple on 2007-10-22
Ok, so I had WinXP and i installed Ubuntu 7.04.  I went to boot to WinXP after the installation so I can play CS:S, but it didn't show the Windows boot option.  all of the information is still there because in Ubuntu I can access the sda1 and see all of my files.  Is there a way to boot to Windows? or do i have to do a clean install?  (I've been looking for the thread but I'm having a bit of trouble finding it :()

---

### Post by Pumalite on 2007-10-22
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by AlCarmon on 2007-10-22
dinostabOMG,
maybe it would be easier to reinstall grub from the liveCD and let grub do the work:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Al

---

### Post by videocheez on 2007-10-22
> **dinostabOMG said:**
> I've since heard that it's better to install windows first, but I'm kind of stuck at this point. Regardless, my guess is that the change needs to happen in my menu.lst file, I just don't know what it is.

No ideas anyone?
This is my biggest fear upgradng to Gutsy.  It took me forever. Not really just a couple of days to get the dual boot working properly and i too modified the menu.lst file so to get dual boot set up correct.  Are you saying that the upgrade will not automatically modify the menu.lst file to dual boot windows and gutsy?  I have been asking about this here for a few days and everyone has said, " don't worry, it's gonna be great." but i don't think any of them actually had modified their menu.lst file for dual boot.  anyways, sorry to highjack the thread.  See below how i modified mt menu.lst when dual booting with windows xp and feisty.  I don't know what it means but it works.:)

```

title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

---

### Post by Pumalite on 2007-10-22
You guys missed this:

[http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007)

---

### Post by dinostabOMG on 2007-10-27
Thanks for the suggestions, everyone. This is still not working for me... videocheez, I tried your suggestion and I get a message saying "Hard drive does not exist!"

The thing is that I already have a windows install on the third partition (after the Ubuntu and swap partitions) and have been able to boot from it in the past; the thing is just that it disappeared from the menu on bootup and I just need to figure out what the proper parameters are to get it back. It seems really unlikely to me that I would need to uninstall and reinstall both OSes just to have Windows in the first partition, and anyway, this would lose me a lot of things I've set up in both.

Most guides refer to the paritions as being dev/hda0,1, etc. For me they are sda, does this have something to do with it?

---

### Post by Duck2006 on 2007-10-27
You can try this.

title           Windows
root            (hd0,2)
map             (hd0,0) (hd0,1)
map             (hd0,1) (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by Duck2006 on 2007-10-27
> **Duck2006 said:**
> You can try this.

title           Windows
root            (hd0,2)
map             (hd0,0) (hd0,1)
map             (hd0,1) (hd0,0)
savedefault
makeactive
chainloader     +1

Sorry sould be this


title Windows
root (hd0,2)
map (hd0,0) (hd0,2)
map (hd0,2) (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by dinostabOMG on 2007-10-27
Everyone, I got it working. It was actually one of the first things I tried, although I don't know why it shouldn't have worked before. One difference is that I took it out of the automatic update section, as I discovered along this magical journey that that will cause the entry to get deleted next time I update the kernel.

Here is my entry:


```

title Windows XP Professional
root (hd0,2)
savedefault
makeactive
chainloader +1

```

Ducky, it's close to what you suggested, but I didn't need to use the map commands. What are they for? Should I stick them in anyway?

One last question, I might like to add an entry for Windows Safe Mode, in case it ever comes up. Can you get grub to do this or do I just have to press F8 as Windows starts?

Thanks for the contributions everyone.


edit: On closer inspection I realise that this is essentially what I posted in the first post of this thread, except I didn't have savedefault at that time. I thought that this would make XP the default OS at boot, whereas I'm much happier to have Ubuntu for that. Could this have been the fatal difference?

---

### Post by Duck2006 on 2007-10-27
The map commands are for swaping drives or partitionsor both, in general if windoze is on the master drive it is not needed.

---

### Post by videocheez on 2007-10-27
Congrats. I know it feels good to have success with this complicated stuff.

---

### Post by meierfra on 2007-10-27
> edit: On closer inspection I realise that this is essentially what I posted in the first post of this thread, except I didn't have savedefault at that time. I thought that this would make XP the default OS at boot, whereas I'm much happier to have Ubuntu for that. Could this have been the fatal difference?


No,  the fatal mistake was:

chainloader+1

versus

chainloader +1


One missing "space" caused all your problem.

---

### Post by dinostabOMG on 2007-10-27
> **meierfra said:**
> 

One missing "space" caused all your problem.

Argh. So, can I take out makedefault then? What does chainloader +1 do, exactly? What does makedefault do?

At this point my interest is academic, but it might be helpful in the future for people searching this thread.

---

### Post by meierfra on 2007-10-27
Yes you can remove the "savedefault"  
If you change "default 0" in menu.lst  to "default saved" then any time an item with "savedefault" is booted it will be the default  at the next boot.
But with "default 0" the first item on the menu is the default and the "savedefault" statements are ignored.

root (hd0,2)  
chainloader +1

tells grub to  turn control over to a  boot loader located at sector 1 of partition 3 (=2+1) of harddrive 1 (=0+1)

---

