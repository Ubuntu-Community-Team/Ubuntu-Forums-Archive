---
title: "A different Grub Problem"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2007-08-21
I have built a new computer and have loaded feisty 7.04 onto the new SATA drive. After a day of fun I got my IDE drive out of the old computer and installed it as well. It also has 7.04 loaded but I wanted to load another version on it.

The problem is that when I power up I get the mother board post for 30+ seconds, followed by a blank screen with a cursor in the top left corner for 30+ seconds, then a "Grub loading, stage 1.5." for 35+ seconds, then "Grub loading,  please wait....." message that lasts 20 seconds, Then "press Esc" for 2 seconds at which time a menue, nothing like Grub flies by and the the SATA HD boots up.

With only one HD connected the boot is very quick.

Almost 2 minutes and no Grub menu.
What could have gone wrong?

---

### Post by MQMike on 2007-08-21
Just some thoughts –
You are mixing SATA with IDE.  That often can and does cause issues with configuring GRUB, but solvable.
Also, maybe it’s something with the IDE controller, or how the Linux kernel deals with that controller.

Had you instead installed a new, second SATA drive (instead of IDE), I would expect you to have no problems.
These things seem to pop up when mixing IDEs and SATAs.

---

### Post by gn2 on 2007-08-21
Is it possible for you to disable the IDE drive as a boot device in the BIOS or put it after the SATA drive in the boot order?

That might help.

---

### Post by kindafunnylookin on 2007-08-21
Thank you both, I'm trying to get the IDE after the SATA as a slave.

---

### Post by kindafunnylookin on 2007-08-21
That did no good at all. SATA is the only drive that Grub sees, I wonder if LILO is the same? I have no idea of how to change the GRUB for LILO now either.

---

### Post by gn2 on 2007-08-22
You could re-install Grub from a live CD using these instructions: [http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

Have a good read of the Hermanzone link in my sig for lots of relevant info.

---

### Post by MQMike on 2007-08-22
I agree with gn2.  Read Herman's bigpond link, try re-installing GRUB, and notice his mention of editing /boot/grub/device.map.  Also take note of how to use the geometry command to find out where and what's on your HDDs.

---

### Post by kindafunnylookin on 2007-08-22
This sounds like the most hopeful solution possibilities yet, thanks again to you both, I'm off to work but will give it a shot tonight. I will at least be able to work without that doubtful cloud over my head.

---

### Post by kindafunnylookin on 2007-08-23
OK!!
Now GRUB is working.

The response to: ```
find /boot/grub/stage1
```was:
```
hd0,0
hd1,0
```so I setup hd0,0 which is the SATA drive.

On reboot Grub was right there like it should be - but - Grub still does not see the IDE HD.

Any ideas?

If I cannot get Grub to list it is there a way that I can mount it from the SATA and copy stuff to a removable drive?

---

### Post by Duck2006 on 2007-08-23
What does the output of

sudo fdisk-l

show

---

### Post by MQMike on 2007-08-23
So you did

grub> root (hd0,0)
setup (hd0)
quit
$ exit

and re-booted to test it, right so far?  That is, you did use setup (hd0), right?

Now, it sounds like you need to edit the menu.lst on the (hd0,0) (/boot/grub/menu.lst)
drive to include a boot entry for the Ubuntu located on the second drive (the IDE drive).

Try this:

Get into the Ubuntu on (hd0,0).
Access /boot/grub/menu.lst.
Edit it * as root * to include a boot entry for the Ubuntu on (hd1,0), like:

title My Ubuntu on the IDE hard drive
root (hd1,0)
configfile  /boot/grub/menu.lst

That’s it.  File-Save, File-Exit.  Close out all windows.  Re-boot to test it.

If it works, then you might want to edit the menu.lst located on (hd1,0) so the default is your Ubuntu and the timeout is short, but not zero, like
timeout = 2     # or timeout = 3, your choice
(So you must get into your Ubuntu on (hd1,0), access and edit as root the file /boot/grub/menu.lst to change the default OS and the timeout, the File-Save, File-Quit.)


(Clarify:  You DO have Ubuntu on both HDs, right?  It does appear so, since your find command returned the second drive (hd1,0) as well as the first drive (hd0,0))

---

### Post by kindafunnylookin on 2007-08-23
```
peter@ububtu7:~$ sudo fdisk -l
Password:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29644   238115398+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       19269   154778211   83  Linux
/dev/hdc2           19270       19457     1510110    5  Extended
/dev/hdc5           19270       19457     1510078+  82  Linux swap / Solaris
peter@ububtu7:~$ 
peter@ububtu7:~$ 
```

---

### Post by MQMike on 2007-08-23
One more thing, let’s be sure about . . .

Your BIOS is set to boot first from the CD then second from the SATA drive, right?
(I think so, but let’s be clear.)

BTW, GRUB sees your drives the same as BIOS sees them, and the find statement did return (hd1,0), so it looks like BIOS sees the IDE drive (which I’m assuming is (hd1,0).

(Ok I just saw your output, too.)

---

### Post by MQMike on 2007-08-23
We posted almost in passing.

So try what I suggested above.

Remember, too, that at a GRUB prompt, grub>, you can test what's on your drives using the geometry command:
geometry (hd0)
press Enter
and 
geometry (hd1)
press Enter

But it does look like you got (hd0) and (hd1) coming up (from the find statement you did above).

---

### Post by logos34 on 2007-08-23
> **kindafunnylookin said:**
> OK!!
Now GRUB is working.

The response to: ```
find /boot/grub/stage1
```was:
```
hd0,0
hd1,0
```so I setup hd0,0 which is the SATA drive.

On reboot Grub was right there like it should be - but - Grub still does not see the IDE HD.

Any ideas?

If I cannot get Grub to list it is there a way that I can mount it from the SATA and copy stuff to a removable drive?

The grub menu screen is showing the menu.lst on the sata drive -- in /dev/sda1/boot/grub. Since the IDE drive was not connected when you installed to the sata, it was not detected.  So you have to add an entry for ubuntu on the IDE to the menu.lst on the sata, which is where grub is pointing.  Like this:

> title		Ubuntu, kernel 2.6.20-16-generic [Feisty - IDE drive]
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/hdc1 ro splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

add the ide drive to  /boot/grub/device.map:

> (hd1) /dev/hdc

---

### Post by MQMike on 2007-08-23
For now, just make this your IDE Ubuntu boot entry on the menu.lst of the SATA Ubuntu:

title My Ubuntu on the IDE hard drive
root (hd1,0)
configfile /boot/grub/menu.lst

---

### Post by kindafunnylookin on 2007-08-23
I got a little carried away and messed up again and now this is what I have for a menu.lst on the SATA. It still boots fine but the IDE will not respond.
```
title        Ubuntu, kernel 2.6.20-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=59705f2a-e24e-4303-aa6d-2d484d52e041 ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title           Old Ubuntu on IDE, kernel 2.6.20-16-generic
root        (hd1,0)        
kernel        /boot/vmlinuz-2.6.20-16generic root=UUID=9eb318d9-ddd0-480f-b58e-e1b23f4c3fbf ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```I think I did something wrong in my IDE menu.lst. I'm going back not to figure out how I messed up there.

---

### Post by MQMike on 2007-08-23
First, please try just the configfile form that I gave.  (Later you can, if you wish, boot it directly with kernel & initrid.)

Second, make sure your SATA Ubuntu entries appear in the menu.lst between the two lines
*** Begin Automagic Kernels List
. . . .
*** End Automagic Kernels List


And then put your IDE Ubuntu after the line
*** End Automagic Kernels List

---

### Post by MQMike on 2007-08-23
Instead of:

title           Old Ubuntu on IDE, kernel 2.6.20-16-generic
root        (hd1,0)        
kernel        /boot/vmlinuz-2.6.20-16generic root=UUID=9eb318d9-ddd0-480f-b58e-e1b23f4c3fbf ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

Try just 3 lines:


title My Ubuntu on the IDE hard drive
root (hd1,0)
configfile /boot/grub/menu.lst

---

### Post by MQMike on 2007-08-23
While you are working, some ramblings . . .

If your IDE is going to boot, it will boot with configfile (or another one is symlink).
One advantage to configfile is that it will always work, and you never have to update it when you get a kernel update to the IDe Ubuntu kernel.  All that configfile does is call up your menu.lst from the IDE Ubuntu file /boot/grub/menu.lst.  Downside:  you do get 2 menus in succession (but as I said above, you can reduce the timeout on the second one to just 2 seconds, just in case you wish to interrupt it by pressing “c” key to get a GRUB prompt).

---

### Post by kindafunnylookin on 2007-08-23
Just set the IDE back to where it was. Now following your advice. Will post results in a few minutes.

---

### Post by MQMike on 2007-08-23
And I think you found this out, but you have to edit menu.lst as root and then save the changes (File-Save, File-Quit).  Sometimes those steps are missed.

---

### Post by kindafunnylookin on 2007-08-23
I could have saved myself a couple of hours if I had followed your instructions to the letter.
Everything is working as it should now and I'm extremely grateful. You are very kind to stick with it when someone does not follow your advice as given.

All the best- Peter

---

### Post by MQMike on 2007-08-23
Congratulations on sticking with it! -- best way to learn, through trying different things along the way.
--Mike

PS --

If you do prefer to boot IDE Ubuntu using its kernel & initrd statements, you may do so.
Just get the correct boot stanza entry directly from the IDE Ubuntu /boot/grub/menu.lst itself (copy/paste, or copy to thumb drive, or whatever logistics it takes).
If you do that, as I said, whenever IDE Ubuntu gets a kernel update, you must manually update the kernel/initrd lines of IDE Ubuntu in the SATA Ubuntu menu.lst.  And so on.

Best of Luck.

---

### Post by logos34 on 2007-08-23
> **kindafunnylookin said:**
> I got a little carried away and messed up again and now this is what I have for a menu.lst on the SATA. It still boots fine but the IDE will not respond.

...

I think I did something wrong in my IDE menu.lst. I'm going back not to figure out how I messed up there.

It was a typo -- you just left out a dash:

> title           Old Ubuntu on IDE, kernel 2.6.20-16-generic
root        (hd1,0)        
kernel        /boot/vmlinuz-2.6.20-**[COLOR="Red"]16generic[/COLOR]** root=UUID=9eb318d9-ddd0-480f-b58e-e1b23f4c3fbf ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

MQMike's way is better.  It works, so leave it that way, then no kernel update issues.

---

### Post by MQMike on 2007-08-23
Nice detective work logos34.

Another note is apropos, and everyone should do it:
Now’s a good time (when you don’t need it!) to download and burn SGD to a LiveCD:

Super Grub Disk, new site:  [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
Super Grub Download List:   [http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

---

### Post by kindafunnylookin on 2007-08-23
> **logos34 said:**
> It was a typo -- you just left out a dash:



MQMike's way is better.  It works, so leave it that way, then no kernel update issues.
I am way to tired to be typing as root.
Thanks for letting me know.

---

