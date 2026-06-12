---
title: "Help getting Ubuntu 6.06 LTS working"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by carl123 on 2006-08-04
Im trying to get a dual boot with windows xp and ubuntu working but I'm having great difficulties as this is my first experience with linux. I've searched the net but every single article I've found seems to be outdated or I get stuck at some point in the instructions.

I'd prefer to maintain the windows MBR and have it recognize the linux install not the other way around. I refer you to this thread [How to dual boot Ubuntu and Windows XP without changing the Windows MBR ]("http://www.ubuntuforums.org/showthread.php?t=56563")

The problem there is that ubuntu 6.06 never gives the option to install the boot loader to a specific location.

Any other ideas on how to dual boot without changing the Windows MBR would be great.

I also tried making a grub boot floppy and booting ubuntu with it. Like this

grub> root (hd0, 1)
grub> kernel /vmlinuz root=/dev/sda2 
grub> boot

But linux panicked
VFS: cannot open root device "sda2" or unknown-block (0,0)
Please append a correct "root=" boot option

8-[

---

### Post by confused57 on 2006-08-04
The Desktop Live CD installer doesn't give the option of where to install grub, automatically installs to the mbr...the alternate CD allows you to select where to install grub(e.g. floppy).
You can make a grub floppy:

[http://www.ubuntuforums.org/showthread.php?t=224345&highlight=floppy](http://www.ubuntuforums.org/showthread.php?t=224345&highlight=floppy)

---

### Post by Drakkor on 2006-08-04
Not positive,but I think the "alternate" CD,which is a text-based install allows you to put grub where you like.
Edit: Beat me confused ! lol :-P

---

### Post by moma on 2006-08-04
Press [COLOR="Red"]TAB-key[/COLOR] on the GRUB-prompt and it will tell you all possible options.  Eg. you press TAB-key after the vmlinuz word and GRUB will auto-complete the file name.

Also add disk prefix (hd0,1) and /boot/ before the kernel name. Like this
[COLOR="Sienna"]kernel (hd0,1)/boot/vmlinuz-2.6.15-18-386  root=/dev/sda2  ro [/COLOR]

Notice: It's completly OK to overwrite the BMR with Linux' boot loader. Just do it.
Ubuntu installer will find your Windows and sets up a dual-boot menu.

---

### Post by Drakkor on 2006-08-04
"Notice: It's completly OK to overwrite the BMR with Linux' boot loader. Just do it."
Unless he doesn't have the original OS install disk,to re-install the original mbr if need be.

---

### Post by carl123 on 2006-08-04
Thanks for all your replys. I gonna start trying those things. right now
I'd prefer to keep the windows MBR. But if it turns out to be too much hassle ill prolly just end up over writing it with grub. I do have the windows install disk but i wouldn't be surprised if i ran into some trouble trying to replace the mbr sometime down the track

---

### Post by Drakkor on 2006-08-04
Actually it's really easy to re-write your master boot record,just put in the XP disk, wait till it loads and you get to the repair option,and at the prompt type fixmbr  which will write a new mbr in seconds than you're done !
Good Luck ! :D

---

### Post by carl123 on 2006-08-04
well that didnt work at all. None of those commands worked. Actually the first one did. Then the second said it couldn't mount my floppy or couldn't find it. I dont even know what those commands do.

Do I need a /boot partition? Coz i dont have one

---

### Post by Drakkor on 2006-08-04
Can you explain your setup? Are you using one hard drive or 2 ?

---

### Post by carl123 on 2006-08-04
2 hard drives.

1 IDE just storage
1 SATA with windows xp and ubuntu on seperate partitions

I think ill have to leave it for tonight. My brain is way too tired to be doing this stuff right now.

---

### Post by confused57 on 2006-08-04
I know you won't be back for awhile, but thought I'd give you some suggestions, links, & options.  First of all, defragment your Windows a couple of times, 2nd time should go much faster.  Since you have the Windows install cd, you shouldn't have any problems repairing the mbr if something goes wrong, which it shouldn't.

Here's a link for installing with the Live CD:
[http://psychocats.net/ubuntu/windowstoubuntu.html](http://psychocats.net/ubuntu/windowstoubuntu.html)

link for installing with the alternate cd:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
The 2nd link has some excellent tutorials for grub, gag, xserver,etc.
As mentioned the alternate CD will give you an option of where to install grub, if you want to install to floppy:
[http://www.ubuntuforums.org/showthread.php?t=188819](http://www.ubuntuforums.org/showthread.php?t=188819)

This will give you some options & howto's to consider.

---

### Post by carl123 on 2006-08-04
I basically just want to know how I can use grub on a floppy to boot into ubuntu so i dont have to keep using the live cd.

---

### Post by carl123 on 2006-08-05
I dunno if anyones reading this thread anymore but here goes anyway.

Man I'm getting really p'd. I've successfully over written the windows MBR with grub. ( which wasn't easy coz there is no way of doing it inside ubuntu that I know of so i had to do it with a grub floppy.) So now I get grub when I boot up the machine. I can boot into windows fine. But i still cant boot into the Ubuntu partition. It tells me it cant mount the partition. I've got a feeling it might be becasue ext3 is not supported by grub.

When i use the root command like this:

root (hd0,1)
It recocnises it as a ext2

Shouldn't this say ext3 or is this normal?

Any ideas on how to get the dam partition to mount?

---

### Post by confused57 on 2006-08-05
First thing you might do is boot up with the Live CD, open a terminal(Applications---Accessories---Terminal), then enter:

```
sudo fdisk -l
```
The -l is a small "L".  I'm not sure if you need sudo with the Live CD.

This will show what your partition table is on your hda.  Did you do an installation of Ubuntu onto another partition(hda2)?  If you did, the installer should have automatically added grub to your Windows mbr.
When you mention "mounting" the partition, I assume you're referring to booting the partition with Ubuntu on it.
The best solution would probably be to reinstall Ubuntu onto a partition after Windows(hda2?) and grub should automatically be reinstalled to your Windows mbr.  Before doing anything, post the output of the above command, that should make it easier for anyone who might have suggestions to help you.

---

### Post by carl123 on 2006-08-05
Its all good now.

It decided to work. I think installing the boot loader may have done something. I have grub as my boot loader now and I can boot into windows and ubuntu successfully. Yay.

Ubuntu is annoying in that there is no option to install the bootloader AT ALL if your creating the partitions manually.

Thanks for all your help

---

