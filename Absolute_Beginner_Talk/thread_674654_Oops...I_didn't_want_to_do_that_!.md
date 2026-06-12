---
title: "Oops...I didn't want to do that !"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Chris2169 on 2008-01-21
Well more I didn't want that outcome....

Whilst trying to improve I slow boot (see previous posts!) 

I added vga=790 to the kernel line of menu.lst

and set x and y correctly in usplash.conf


Now ubuntu won't boot,  I've tried recovery mode and this is a slightly abridged version of the last 3 lines before it hangs;

VFS:Cannot open root device
Please append a correct "root="
Kernel panic - not synching unable to mount root fs

I got into this position yesterday and had to completely reinstall, but I've made loads of progress since then and would hate to have to do that if there is another option ?

Thanks

Chris

---

### Post by bodhi.zazen on 2008-01-21
Boot a live CD

mount your partition in say /media/ubuntu

post the contents of /media/ubuntu/boot/grub/menu.lst

---

### Post by Chris2169 on 2008-01-21
OK For reasons I won't bore you with now I won't have access to a live CD for another 3-4 hours, is there anything I can do from the command line to get it booted or is it best to wait till then ?  Frustratingly when it is booted unbuntu can see all the windows files for the dual boot but XP seems unwilling to recognise that there is another OS on the HDD !!!!

Thanks

---

### Post by frup on 2008-01-21
XP can't read any file systems other than fat32 or NTFS I believe. There is an ext3 driver for windows which will give you some access but I believe it is very slow.

---

### Post by bodhi.zazen on 2008-01-21
> **Chris2169 said:**
> OK For reasons I won't bore you with now I won't have access to a live CD for another 3-4 hours, is there anything I can do from the command line to get it booted or is it best to wait till then ?  Frustratingly when it is booted unbuntu can see all the windows files for the dual boot but XP seems unwilling to recognise that there is another OS on the HDD !!!!

Thanks

Yes, you should be able to manually boot.

At the grub prompt, hit "e" to edit the boot stanzas. Remove any reference to splash or vga=xxx

Alternately, hit "c" for a grub prompt.

Then manually, one at at time, go through :

root=(hdx,y)

kernel=/boot/vmlinux.xxx root=sdax ro

initrd=/boot/initrd.xxx

boot

 BUT you need to know the partition and kernel you are booting. You can use tab completion, ie start with vmlinuz<TAB>

---

### Post by Chris2169 on 2008-01-22
Thank you again for your time and patience.

OK I've got into the boot stanzas and edited out vga and splash (and I'm quite pleased with myself for being able to do that, even under instruction ! )

I then key b for boot and get the following;

RAMDISK: ran out of compressed data
invalid compressed format (er=1)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

thanks

---

### Post by bodhi.zazen on 2008-01-22
Nice !

is there any way you can post the stanzas you used ? That would be the only way we can check to see if you made a "simple" error. Otherwise we will need to wait until you get your hands on that live CD.

---

### Post by Chris2169 on 2008-01-22
Yes I can post them in about 1 1/2 - 2 hours.  I'll have access to a live CD by then but I'll post them anyway as I have a feeling that just undoing my changes may not be enough.  I think as your suggesting I may have inadvertantely changed something else which is now causing the problem !

---

### Post by Chris2169 on 2008-01-22
As I suspected, I have got the live cd, accesed the files and unchanged my changes.  However this has made no difference so here are the stanzas;

root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=956feddc-36f1-41fc-36f1-41f4-9e1f-bb49de250c1b ro
initrd /boot/vmlinuz-2.6.22-14-generic
quiet

I still get the same error mesage as the previous post;

RAMDISK: ran out of compressed data
invalid compressed format (er=1)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

Eagerly awaiting some advice !!!!!

---

### Post by bodhi.zazen on 2008-01-22
is the uuid correct ?

you can check with :

```
blkid
```

---

### Post by Chris2169 on 2008-01-22
Yep the UUID is correct;

I"ve now realised that the way I copied it down was incorrect because it was spread over 2 pages it is;

'956feddc-36fl-41f4-9elf-bb49de250clb'


Do I feel a re-instalation coming on ?

Thanks

---

### Post by philinux on 2008-01-22
No need for that, unless bhodi says so.


You could reinstall grub from the live cd.

---

### Post by Chris2169 on 2008-01-22
That sounds considerably less painful !  Could you point me in the right direction as to how to do that ?

Thanks

---

### Post by philinux on 2008-01-22
Here ya go. 2 for the price of one.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/](http://odzangba.wordpress.com/2007/03/10/how-to-restore-grub-using-the-ubuntu-live-cd/)

---

### Post by Chris2169 on 2008-01-22
Thank you,

I've done that, and it has worked, the new boot stanzas are there.  But I'm still getting the same error message.  This is in effect ans experimental install so I may well just re-do it.  The problem is that still doesn't fix the slow boot problem.......

Thanks

---

### Post by philinux on 2008-01-22
Ok read this.

[http://www.byteclub.net/blog/xavier/?p=137](http://www.byteclub.net/blog/xavier/?p=137)

I doubt if you have a /boot partition though

---

### Post by philinux on 2008-01-22
Also found this.

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/31126](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/31126)

If it were me I'd use the live cd to move home to its own partition and reinstall.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Unless you've no data to keep then just reinstall.

One last thing you could try running fsck from the live cd.

---

### Post by Chris2169 on 2008-01-22
Not Data, just settings where I'm gradually setting up all the things I use/want on Ubuntu....my 'working' is still going on in xp until I'm satisfied I can do everything I want in Linux.  The next step is to have a'play' with wine for those 'difficult to replace' apps !

I am just going to check in case I do have a /boot partition, Many thanks for your help

---

### Post by xtigma on 2008-01-22
Hello there.

Before everything else. System Specs:
ASUS P4B266 
pentium 4 1.8GHz 
798 MB DDR RAM 
nvidia GeForce 2 MX400 64MB
partitions: -- sda1=40GB
XP @ hd0,0 (20 GB)
Ubuntu 7.10 /root @ hd0,1 (18GB) 
                   /swap @ hd0,2 (1596MB) 
                   /home hd0,3   (500MB)

I was having a problem kind of like this. I have a 15" monitor that only supports 1024x768 @ 54Hz max.
So I wanted to see Ubuntu's splash instead the "OUT OF RANGE" message from my monitor.

Have changed menu.lst so I can see the boot splash of Ubuntu (7.10).

vga value is set to 791 mode (1024x768 ) ... I had followed the steps of [ _[COLOR="DarkRed"]Fix Slow boot/faulty splash screen[/COLOR]_](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen) guide.

so menu.lst is as follows:```
 kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=20fd9912-6383-4860-9cd8-88a11909d715 ro quiet splash vga=791
```

then edited usplash.conf (1024 on X and 768 on Y coordinate)```
sudo gedit /etc/usplash.conf
```

but i remember copying this line:```
 sudo update-initramfs -u -k `uname -r`
```

and resulting in a strange chain of code like repeating:```
 sudo update-initramfs -u -k `uname -r` sudo update-initramfs -u -k `uname -r`...
```

I was too lazy to read the code and done as guide said: REBOOT

So I was able to see the splash as my system turned off. But after re-start the same kernel panic message had appeared.

So I am telling this for other people that had a similar problem. Both, slow boot and faulty splash makes the same error appear... mmmm... 

I'm now trying the fixes you suggest. I will keep you posted. :)

---

### Post by xtigma on 2008-01-23
Hello Again.

I am posting my status:

Death.

I have detected my error: After doing all the steps on  Fix Slow boot/faulty splash screen guide. I was so eager to reboot and try my new config that I didn't wait to initramfs be completely compile.

So I manage to enter Ubuntu with my liveCD. Mounted /root as I it said on this thread. proc too was mounted. edited menu.lst to default, erasing "vga=791" on the line of "kernel" 
then edited usplash.conf to default (1280x1024) 
compiled again initramfs.
then I noticed my mistake. So I wait until it was compiled. 
Rebooted my machine and still having the same error message. that sounds like I really messed up some other files on my OS. 
So I could only do one thing: reinstall and lear a good lesson of patience. AND NEVER MESS WITH CRITICAL CONFIGS.:lolflag:

I have detected an error on that guide that is mantained by Ubuntu Community (I think). Can Anyone add a line like: Careful! Wait until initramfs is compiled...

 I didn't see a warning on that guide...
Cheers!! :KS

---

### Post by bodhi.zazen on 2008-01-23
@xtigma : it looks like that is a wiki page, in which case you can register with the site and edit it yourself

That is the advantage of wiki, user maintained.

The page maintainer will review and edit you changes if necessary.

---

### Post by xtigma on 2008-01-25
*bodhi.zazen*:

thanks! I thought that wiki was only for consulting... 

now I will  see if I can edit this myself....

---

