---
title: "Trouble with Grub"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Foolishgrunt on 2007-01-21
So it was about 2 weeks into my Ubuntu experience (I've been running a Edgy/Windows XP dual boot on my laptop). Then one morning, without warning, my computer decided to screw me over. I went to start my computer, and Grub started loading like usual. But on the intial loading screen, before it even got to the boot screen, I got an "Error 17" message. I tried it a couple more times, and got the same result. It was late, so I decided to mess with it in the morning.

The next day, Grub began loading. It took a long time (about 15 seconds) to even get past the initial loading screen, but it finally did. Once I got there, everything was perfect. I tried starting both Ubuntu and Windows, and nothing was seemed wrong. I didn't understand it, but I figured that whatever was wrong, it had fixed itself.

The next day, Grub decided to throw another curve at me. It stalled at the intial loading screen again, and then gave me an "Error 16" message. I did a little fishing around online (on my other computer) and found a couple people suggest to other users that they use the Windows XP disk to fix the master boot record. So I did the same. And now Windows works perfectly.

Only problem is that now it bypasses the Grub screen entirely. Since then, I haven't been able to load Ubuntu. And being the incompetant bungler that I am, I can't figure out how to bring it back. Help, please?

(I gave the whole story leading up to this point just in case it *might* provide a slight insight as to what caused Grub to fart on me. If you have any ideas, could you please tell me?)

---

### Post by scbonney on 2007-01-21
oops

---

### Post by x64Jimbo on 2007-01-21
Try this:
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by Juan Largo on 2007-01-22
For a multi-boot system, I try to use the Windows boot loader NTLDR instead of GRUB.  This is the least obtrusive way to do it.  You have to copy the boot sector of the Linux root partition to a file and copy that file to the active partition where Windows lives.  Then all you have to do is add a line to boot.ini and you're done.

---

### Post by x64Jimbo on 2007-01-24
> **Juan Largo said:**
> For a multi-boot system, I try to use the Windows boot loader NTLDR instead of GRUB.  This is the least obtrusive way to do it.  You have to copy the boot sector of the Linux root partition to a file and copy that file to the active partition where Windows lives.  Then all you have to do is add a line to boot.ini and you're done.
That sounds much more obtrusive than just having a bootloader that is designed to handle both Windows and Linux. Why hack the NTLDR when GRUB is prettier, more customizable, and is actually designed for the task?

---

### Post by housam on 2007-01-24
Try to use the super grub disk , it may help to fix it.
[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

---

### Post by x64Jimbo on 2007-01-24
The link I posted has all the instructions necessary to reinstall GRUB from your existing Ubuntu LiveCD - you don't need to download some separate GRUB disk.

---

### Post by K.Mandla on 2007-01-24
> **Foolishgrunt said:**
> And being the incompetant bungler that I am, I can't figure out how to bring it back. Help, please?
If you have an alternate (install) CD, the "Rescue a broken system" option will allow you to reinstall Grub rather painlessly. You just have to know which partition is your root file system, and it will do what it can to get Ubuntu going again.

---

### Post by geek_Man on 2007-01-24
I would recommend Super GRUB Disk, it can do a lot of cool stuff. Even if you don't get GRUB fixed, you can still boot into Ubuntu.

---

### Post by dannyboy79 on 2007-01-26
I dont' want to hijack this thread but why would I start a new thread for the same problem????? 
So here's my issue. I have had Ubuntu installed since March of 2006. Everything's been great. Lately my machine seems to just lock up (locked mouse, locked keyboard, display is frozen as whatever was last on the screen. Example: nautilus, a terminal session etc etc), the only way to get it to do anything is to either his the reset button on my comp or hit the power button, wait a sec, then turn it back on. Well one day, it just sat there at the Boot to cd screen. (i have my bios set to boot to cd all the time) normally this doesn't matter as if there's no cd in the drive it just continues onto to Grub. Well, for some reason Grrub never starts??? Yes I have checked my bios to make sure the correct hdd is the first boot device, and yes I have made the boot order so that the hdd boots first and just have forgotten about leaving bios to boot to cd first. All the hard drives show up in bios just fine. When i boot to Live CD, the partition is there and is intact! I have a /boot partition that is hdc1 then I have a /root partition that is hdc2, hdc3 is swap, hdc4 is /home. I have reviewed the menu.lst file and everything looks fine. I have even tried to follow a tutorial on how to reinstall grub using Knoppix but i get an error stating the grub-install doesn't exist despite me finding it inside /KNOPPIX/sbin/. The steps I followed were to umount hdc1 if it was mounting auto by Knoppix, then I am to remount it using the -o dev option. then I am to run sudo chroot /mnt/hdc1 grub-install /dev/hdc. as I said, I get an error stating that grub-install doesn't exist??? so I have even tried sudo chroot /mnt/hdc1 /KNOPPIX/sbin/grub-install /dev/hdc and that still says that doesn't exist? Then I tried just sudo grub-install /dev/hdc but it states something about not being able to find /boot? Is this all because I have grub installed on a different partition than /root? Can anyone help please.

---

### Post by geek_Man on 2007-01-26
Dannyboy, your problem MIGHT have something to with your /etc/fstab file. Maybe...

---

### Post by dannyboy79 on 2007-01-26
i seriously doubt it, if grub were loading and then not being able to find where /boot or / was then I could agree with this but that fact that nothing appears after the initial bios info, then I would say that grub isn't being started. your fstab is only used for mounting paritions, where to moun them, whether users can mount and umount them, whether they are checked by fsck etc etc. BUT I will look at this after work just in case. thanks for your feedback.

---

### Post by geek_Man on 2007-01-26
What was the thing about Knoppix? I thought that was another distro.

EDIT: Have you installed Knoppix? I have to say I'm a little confused.

---

### Post by dannyboy79 on 2007-01-26
knoppix is another Distro. Yes, you are correct. I am using that instead of Ubuntu Live CD because is has Part Image on it in case I want to create a image of my partition and move my server to a new hard drive. You have 167 beans, can I ask how long have you been on Linux? Only curious. I know that bean count is no measure of experience, hence why I am asking you your level of experience. I ask this due to you not understanding why I am using Knoppix. Knoppix is a VERY common live cd used for fixing things in OS installs due to it having more software in it's live cd than Ubuntu. Then again, Ubuntu live cd is only 700MB where as Knoppix is burned onto a DVD5.

---

### Post by geek_Man on 2007-01-26
I've been using Ubuntu for a couple months, around since October. I'm a Windows convert and as you might know, the folks at Microsoft like to pretend that Linux doesn't exist. I was confused about you using Knoppix 'cause I thought you said you were using Ubuntu. That's all.

---

### Post by dannyboy79 on 2007-01-27
i am using ubuntu! i have ubuntu 6.06 installed. only using the knoppix live cd to try to fix grub

---

### Post by geek_Man on 2007-01-27
Do you have the Ubuntu CD?

---

### Post by geek_Man on 2007-01-27
Have you tried running grub instead of grub-install?

---

### Post by dannyboy79 on 2007-01-29
yes, to both of your questions. i have even played around with that super grub disk, restored grub to the mbr as well as the /boot partition I made and still nothing. the computer goes thru the bios as normal, then all of a sudden nothing. it just sits there doing nothing where as before grub would start?????? i don't know if I fired my mbr or what? i can mount the partition and see everything in it and the menu.lst is fine, the vmlinuz is on the root partition and everything looks intact as I said. I am really getting pissed off here. i ever started another thread a no one wants to help me?? I can boot into ubuntu fine by using the super grub disk and just telling it to boot the mbr. so the only thing I can thinik of is that the bios doesn't know what mbr to boot. so I made sure the correct hard drive is the one being booted and it is? I don't know what else to do? I suppose I can just always boot to a grub floppy first or even the super grub disk but that's gonna take longer is only a temp fix!

---

### Post by geek_Man on 2007-01-29
It's not that people don't want to help (they do), it's that they don't have any answers therefore making it useless to post anything. I've had a similar experience and my thread still isn't answered yet.

---

### Post by geek_Man on 2007-01-29
What's your groot set as in your menu.lst?

---

### Post by dannyboy79 on 2007-01-29
i wouldn't think this is the probnlem only because grub isn't even starting at all, if the #groot line was wrong, wouldn't I at least get a grub line that gave me an error??? it's like the bios isn't telling my /boot partition to start, or to "run" grub, which is there.

well I am not at home but I thought it said, 
#groot=(hd0,0)
which I think I just realized might be what's wrong since my default grub root device should be (hd1,1) because I made a /boot partition when I first installed ubuntu. and the /boot partition is on the ide channel 1 not ide channel 0. so I have a dvd-rw drive as master on ide channel 0, this is hda, then a (250gb total) fat32 parition and a ntfs partiiton on slave on ide channel 0, these are hdb1 & hdb2, then I have my ide linux hard drive (20gb total) on ide channel 1, which has 4 partitions, 1 is /boot, 1 is /, 1 is swap, and 1 is /home, these are all hdc. then I have a (300gb total) ext3 drive as a slave on the ide channel 1, that's hdd1, then I have a (400gb total) ext3 drive that sda1, and another (500gb total)  ext3 drive that sdb1. I know I have lots of drives. I don't have windows anywhere on any of these drives!
 
i specifically created a /boot partition on purpose so that if it ever got screwed up I could fix without screwing up my linux install. well I am having a hell of a time fixing it!!! It is 50mb in size, my /boot parition that is.

but I know that my entries further down have the correct partition. my root partition is number 2 on the second ide channel, which is hdc2.

---

