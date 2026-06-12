---
title: "Repairing Grub or Repairing OS X?"
date: 2009-11-14
forum: Apple Hardware Users
---

### Post by Nohtanhoj on 2009-11-14
I've been using Ubuntu on my mobile machine (Windows based) for a while, and have been really liking it for "work" stuff, so I decided to bite the bullet and install it on my iMac. Right off the bat, I made a huge mistake. I didn't read the Ubuntu FAQ that explicitly states Ubuntu cannot be installed on an external drive, so I tried to put it on an external 1TB My Book drive that I have plugged in. My second error was forgetting to specify the partition that GRUB was to be installed to. Default option is installing to the internal drive, which is where I have OS X installed.

When I tried to boot, my Mac gave me a white screen and a flashing folder, which I assume meant something along the lines of "no bootloader." I was able to boot from my OS X install CD and copy my entire internal drive to a second external drive that I have, so I wouldn't lose any data. On the ensuing reboot, holding down the Option key seems to allow me to boot from the external drive! This isn't what I was anticipating, so I've been running off the external drive while I look for a solution to repair my internal drive's boot situation.

Does solving this problem constitute repairing Grub or repairing the OS X bootloader? I'm not quite sure which "side" of the problem is the one I should be aiming for. I would be content on repairing either, as long as it lets me boot into OS X on my internal drive.

Thanks for any help you might be able to give.

---

### Post by tom4everitt on 2009-11-15
Installing grub to hard drive never caused any problem for me, so I don't actually think thats the issue. It would always let me boot osx normally. 


Rather I think the following is the issue:

When you do changes to your partition table in linux, it will cause osx:s partition table to be out of sync with the actual partitioning. This is because osx uses a (newer and) different partitioning system. 

So when you try booting, efi will not understand the partitioning, and will therefore not be able to boot osx nor linux. (Macs are always booted by efi.)

So what you usually do before you install linux on your mac is to install refit, which can boot both osx and linux. refit also have a partitioning tool that can sync your partitions again. 


So what you need to do is to get refit on a cd:

[http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)

boot from it and use the refit partition tool to sync your partition tables.

boot osx and install refit

now you should e able to boot both osx and linux

---

### Post by Nohtanhoj on 2009-11-15
So you're saying that I should do the rEFIt before or after I install Linux (I know I've already installed it, but this is for future reference).

---

### Post by tom4everitt on 2009-11-16
Always before. 

If it's already installed you don't have to bother with a rEFIt CD, cause then you will have access to the refit partition tool at every boot. If you've installed it but see no refit menu at startup, you need to run

```

sudo /efi/refit/enable.sh

```

in OSX to activate (bless) it.

---

### Post by Nohtanhoj on 2009-11-16
Thank you. So far it's looking good, but I haven't actually got around to doing the dirty work yet. I'll update this probably later tonight.

---

### Post by tom4everitt on 2009-11-16
Okay, good luck :)

Let me know how it goes

---

### Post by Nohtanhoj on 2009-11-16
Ehhhh..... I didn't get it to work, but I'm pretty sure that's my own fault and not that of Linux. I selected the bootloader on the wrong partition(I think), so I'm gonna back up, format, restore to a single partition (BootCamp requires only one partition), and try again on Thursday or something.

Right now just isn't a great time for me to work on this, as I've got a huge assignment due for my Data Structures and Algorithms course on Wednesday... I'll keep this thread updated with what I've done.

---

### Post by tom4everitt on 2009-11-17
Okay, but can you boot os x now? There are ways to reinstall the boot loader without reinstalling everything, but sometimes the easiest option is actually to start over and get things right from the beginning. 


So going back to only osx and then follow some guide, such as

[https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

might be a pretty good idea.

---

### Post by Nohtanhoj on 2009-11-17
OS X still boots fine from rEFIt, but I'm having one error with syncing my partition table.

This thread describes my symptoms exactly.

[http://ubuntuforums.org/showthread.php?t=1297229&highlight=GPT+partition+type+unknown+found](http://ubuntuforums.org/showthread.php?t=1297229&highlight=GPT+partition+type+unknown+found)

I'm gonna give that stuff a try either tonight or tomorrow.

---

