---
title: "[SOLVED] Help! Wireless not working on Sony VAIO + and failing file system check"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-10-07
Hello,
So.... I ahev set up a dual boot of Linux and Windows for my dad. He has an fat32 shared partition, a recovery partition, an NTCSF Windows partition, an ext3 ubuntu file system partition, etc.

So, TWO things are going wrong and I have ONE question about tweaking something

Going wrong #1: Cannot recognize wireless card... or something, I am a bit confused on this one, here is some pictures: (His wired hardware is bad, so he can only connect wireless...shucks)
[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-NetworkSettings.png[/IMG]
[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-Devices-NetworkTools.png[/IMG]

So... don't know bout that one, if some one could help, it would be appreciated :) I can help you out by supplying more info I am sure, just ask :)

Going wrong #2: Ok, this I REALLY do not get. when ubuntu boots up it checks the filesystem... fdisk something or other. Anyway, it fails the check and send you to a terminal asking you to repair it manuelly. or ctrl D will boot you into Ubuntu. Then it says "making swapfile" (or something of the likes) and that "[FAILED]". did I not get swap set up correctly? Here is a picture of my partitions so you can have an idea about the stuff I'm pullin'
[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-Computer-FileBrowser.png[/IMG]

Oky doky, I sure hope some one can help me and my pops out. I know its been done before :D 

Wishful tweaking # 1:
Want to get rid of the percussion sound when it hits the login in screen. not good for when you are getting on the computer for an early morning online meeting. wakes up the mama :-/. I've tried editing sound preferences and sound control (ALSA mixer) and nada. any ideas?

allrigt, thanks ahead of time,

Static Void

---

### Post by Crenfinkle on 2007-10-07
as for the swap and filesystem problems, I have no idea. For the wireless, could you post the output of** lspci** from the terminal? We're looking for the lines which say "Network Controller" or something like that. Wireless is hit or miss with ubuntu and Linux and general, but you will definitely be able to get it working eventually. 

For the percussion on login, why not just turn your volume all the way down before you shut down the PC? This works for me on both of my ubuntu machines, because I'm deathly paranoid of ear-shattering primal drums when I boot up the computer

---

### Post by octotom on 2007-10-07
When I installed Ubuntu I was afraid that my wireless card wouldn't work, but Ubuntu has a program called Restricted Drivers Manager.  In this program as long as the check is next to my wireless card, Ubuntu, it seems, forces it to work even though it doesn't know what it is.  Maybe that will help?

Tom

---

### Post by Crenfinkle on 2007-10-07
That may work, unless ubuntu thinks the wireless card can use a non-restricted driver. With my wireless card, ubuntu wanted to use a free driver that wouldn't work. I had to use ndiswrapper to "wrap" the windows driver for the card in the linux kernel.

---

### Post by staticvoid on 2007-10-08
Hi, thank you both :)
I got ndiswrapper and extracted it and typed in make... I forgot to make install though *blush* is there anything I need to do after that? I do not have the comp right now, I'll put up specific output for both the wireless and the fdisk failing swap file system check bad output thingy ;). 
I should have waited and been more specific.

Anyway, why does it think eth0 and wlan0 are *both *wired? Will this be fixed perhaps after I use the wrapper? Oky doky, I'll be posting again soon to get this fixed :D

Static Void

---

### Post by staticvoid on 2007-10-08
ok! :D
Here is some more info: when it boots it goes,

checking file systems fsck 1.40-WIP (November something)"
......
(i did not catch the next part)

If the device is valid and it really contains ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate super block 
e2fsck -b 8193 <device>

fsck died with exit status 8    [fail]
File System Check failed

oh, and this is strange:

The program apt-get is currently not installed. you could try running apt-get install apt
root@ubuntu:~#

Then I have to press ctrl + D to get ubuntu to boot very annoying.  OK, so thats problem #1 :)

PROBLEM # 2: No wireless. Here is my output for lspci 
Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

ok, any ideas? Doesn't look normal... not intel of broadcom. hmmm...

Oh, and NVIDIA, how do I get that set up?


I'd appreciate your help.

sv

edit: I make instaled the wrapper thing and Now I am wonder what do I do next?

---

### Post by Paulmd on 2007-10-08
As to the failing filesysrem checks:
 
Check the hard disk with the diagnostic tool provided by the drive manufacturor. Seatools from seagate will do if you don't know who made your hard drive.

If the hard drive is bad, you have much worse problems than the wireless. It is possible that the 2 are related, so this is the first priority.

If it is bad you should make a backup immediately of anything you want to keep (basicly the contents of the home directory) . And then get a new hard drive.

---

### Post by staticvoid on 2007-11-06
ok, thank you. Its an old computer and should probably get a harddrive check :)

---

