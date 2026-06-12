---
title: "hard drive help"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by thor908 on 2006-12-26
I installed a new Maxtor 300gb hard rive and Haven't the slightest idea how to make it recognizable... right now when i boot i see my original hard drive but not the new one, where i plan to install Ubuntu when i get it working... 
is there something i need to install to make it work? it came with maxblast 4 but it has been no help.

---

### Post by taurus on 2006-12-26
You need to mount the new harddrive before you can use it...

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by kidders on 2006-12-26
Hi there,

There shouldn't be much to it. You should see your drive mentioned in your dmesg ... someplace near the top, probably. Once you've found it's /dev name, your can partition & format it whatever way you want.

---

### Post by thor908 on 2006-12-26
Is there a way to mount from windows? I'm more familiar with that than i am with Ubuntu.
is it a driver thing or is a mounting hard drives in windows for n00bs?

---

### Post by thor908 on 2006-12-26
Is there a way to mount from windows? I'm more familiar with that than i am with Ubuntu.
is it a driver thing or is a mounting hard drives in windows for n00bs?

---

### Post by jive_turkey on 2006-12-26
Do you have Ubuntu installed at all, or are you just asking how to format a drive so that you can install ubuntu on to a new hard drive? Please expand on your question.

---

### Post by smoker on 2006-12-26
if you are talking about copying all the data from your old drive, including operating systems, windows, ubuntu, on to your new drive to make that a replacement, then the maxblast should copy everything, including partitions over, you may have to resize the partitions later to suit the extra space you have.

---

### Post by Bartender on 2006-12-26
Are you saying maxblast couldn't see the drive?

Is this PATA or SATA?  If it's PATA this could easily be a very simple jumper setting.  What about going into BIOS at startup?  If BIOS isn't picking up the drive either you've got a very basic problem that's not going to be solved with Ubuntu.

Can you please take the side case off and make sure that it's actually spinning up?  Put a finger on it and/or an ear up to it to check.

---

### Post by thor908 on 2006-12-26
> **jive_turkey said:**
> Do you have Ubuntu installed at all, or are you just asking how to format a drive so that you can install Ubuntu on to a new hard drive? Please expand on your question.

i have Ubuntu on an external hard drive.. but i want to put it on my new internal hard drive, but my computer doesn't seem to recognize it at all... in XP there is no icon for the new drive in my computer. What i want to do is install Ubuntu on the new hard drive. I'm gonna assume that i need to format it first, but to do that don't i need to be able to access it, which i can't seem to do now.

---

### Post by jive_turkey on 2006-12-26
In windows go:
Start Menu -> (right click) My Computer -> (left click) Manage

In the Computer Management Window, click disk management. All the hard drives connected to the computer will show up there. If they don't, boot into the bios and make sure that it is recognized there. If both of those things don't work, I would start looking at physical solutions (i.e. is the jumper set correctly on the hard drive and is the hard drive seated correctly).

---

### Post by smoker on 2006-12-26
is it a sata drive? xp usually needs to have sata/raid drivers installed before it will recognize a sata. also, sometimes you have to enable sata in the bios setup before the sata is detected.

---

### Post by thor908 on 2006-12-26
Indeed, i just enabled the thing in the bios but now i have a new problem. When i enable the drive in the bios when i boot i get a grub error. I can't usually boot my computer without the external hard drive with ubuntu on it, if i try to boot without i get "error 5". a friend has suggested that i have installed grub to my main hard drive and not the external drive where ubuntu is actually installed. So it would seem that i need to remedy this problem before i can start working on the new hard drive.

So, if i have in fact installed grub to my original internal hard drive how do i remove it?

---

### Post by thor908 on 2006-12-26
could i remove grub from my main hard drive using a live cd?

---

### Post by smoker on 2006-12-26
hi, thor,

have a look at this thread:
[http://www.ubuntuforums.org/showthread.php?t=325789](http://www.ubuntuforums.org/showthread.php?t=325789)

---

### Post by thor908 on 2006-12-26
Thanks very much...I just finished trying to use it. I cant find midnight commander. if some one could show me a screenie of where it is and give me some hints for finding grub on my hard drive so that i can delete it that would be swell. 

Is midnight commander the thing to use? i read its description and it looks like it would be what I'm looking for.

also some one i know has suggested that i simple use a windows boot loader by running FDISK /MBR. will this allow me to boot with grub getting in my way?

to clarify my problem is that ubuntu is installed on my external hard drive but even when it is not plugged in i still see grub... and cannot boot to windows, all i get is "error 5". Does this mean that grub is not on my external hard drive but on my main internal hard drive. all of this is preventing me from being able to activate my new internal hard drive where i will ultimately install ubuntu.

---

### Post by smoker on 2006-12-26
not sure what you mean about 'midnight commander' meant you have a look at the post by bulldog on that thread quoted below:

"When you get to the desktop open a terminal and enter.
Code:

sudo grub

This will get you a grub> prompt
Code:

find /boot/grub/stage1

This will return a location which you have to use in the next command.
Code:

root (hd?,?)

Next enter the command to install grub to the mbr
Code:

setup (hd0)

Exit the grub shell
Code:

quit

Now Grub will be installed to the mbr.
__________________
using fisk /mbr will remove traces of grub from the windows boot sector, but will disable any chance of loading ubuntu. if you are going to do a fresh install of ubuntu anyway, this will not matter as it will reinstall grub to suit.

you can also use your windows disk and go to the recovery console, and use the commands fixboot and also fixmbr.

---

### Post by Frank Golden on 2006-12-26
> **thor908 said:**
> Thanks very much...I just finished trying to use it. I cant find midnight commander. if some one could show me a screenie of where it is and give me some hints for finding grub on my hard drive so that i can delete it that would be swell. 

Is midnight commander the thing to use? i read its description and it looks like it would be what I'm looking for.

also some one i know has suggested that i simple use a windows boot loader by running FDISK /MBR. will this allow me to boot with grub getting in my way?

to clarify my problem is that ubuntu is installed on my external hard drive but even when it is not plugged in i still see grub... and cannot boot to windows, all i get is "error 5". Does this mean that grub is not on my external hard drive but on my main internal hard drive. all of this is preventing me from being able to activate my new internal hard drive where i will ultimately install ubuntu.
Grub stage 1 was installed to the MBR section of your internal drive. Stage 1 points to the location of stage 2 which is on your external HDD, specifically at /boot/grub on your Ubuntu install. There is where you will find your menu.lst config file. This is the file that grub uses to boot stuff. You can restore the Windows MBR by booting to a XP install cd and choosing repair after the installer boots. When you get to a prompt type fixmbr. Follow the prompts. When done no more Grub stage 1. You will then be able to boot windows.
You should have been able to "activate" your drive in XP by right clicking My Computer
and choosing manage>disk manager. Your drive should have been listed there but not active. All new drives need to be activated. From this tool right click area to the left of your drive entry and choose the activate option. 

BTW, Grub will still be there at /boot/grub in the form of menu.lst on your external drive but without stage 1 you can't boot Ubuntu.
You can however use the info in these tutorials to restore grub stage 1 to the MBR of your external drive and map Ubuntu to boot directly.
This assumes your computer can boot from external USB HDD's.

[http://users.bigpond.net.au/hermanzone/p6.htm](http://users.bigpond.net.au/hermanzone/p6.htm)

and

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by thor908 on 2006-12-26
my windows disk is just the disk that has my operating system on it right?

how do i get to the recovery console?

---

### Post by Drifter on 2006-12-26
Please people when someone asks for help stop using one liners and explain just what to do.  Most people that ask questions are not or may not be as knowlegable as u.

---

### Post by Frank Golden on 2006-12-26
> **thor908 said:**
> my windows disk is just the disk that has my operating system on it right?

how do i get to the recovery console?
That is correct. If you have a windows install disk and not some kind of recovery disk
you should be in business.

Insert disk and boot to it. When the installer finishes booting look for repair option.
Choose repair . You will be asked for the installation you want to repair choose the number
of your XP install (1)?. It may ask for your password. When the prompt appears type fixmbr and follow prompts.

---

### Post by thor908 on 2006-12-26
what are the chances of me finding out what my administration password is? Is there a place to find it?

---

### Post by kidders on 2006-12-26
> **thor908 said:**
> what are the chances of me finding out what my administration password is? Is there a place to find it?

Zero, I'm afraid. (Well, technically not, but let's just say it's not terribly easy.)

The handiest thing to do would be to create a new one. Ubuntu sets you up with an initial account that has the ability to run things as the root user, so (assuming you didn't change that), you can rewrite anyone's password, using "sudo" and the "passwd" utility.

---

### Post by smoker on 2006-12-26
most times there is no administrator password set for using the recovery console in windows, if this is what you mean. try just pressing enter when prompted for a password, and hopefully the console will load.

if you do need a passwork, post back

---

### Post by Frank Golden on 2006-12-27
> **smoker said:**
> most times there is no administrator password set for using the recovery console in windows, if this is what you mean. try just pressing enter when prompted for a password, and hopefully the console will load.

if you do need a passwork, post back
Thanks Smoker, you beat me to it. I had forgotten that bit about the password. If you had setup a admin password then that would be it. If you have not then just ignore and press enter.

This thread is causing some confusion as we are talking about both XP and Ubuntu here.
The above two posts illustrate that.
For the sake of clarity we should specify what OS we are refering to.

---

