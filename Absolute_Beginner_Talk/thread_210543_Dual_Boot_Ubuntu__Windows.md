---
title: "Dual Boot Ubuntu / Windows?"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by kaje on 2006-07-07
The other day I decided to format my hd and partition it to allow me to install Ubuntu and Windows for the option of dual booting. After setting up my partitions, I installed Ubuntu first. I was anxious to give it a try and expected to wait a few weeks before finally reinstalling WinXP.

After 24 hours, I had experienced several problems (that I have yet found fixes for [here]("http://ubuntuforums.org/showpost.php?p=1217134&postcount=88"), [here]("http://ubuntuforums.org/showthread.php?t=209383"), and [here]("http://ubuntuforums.org/showthread.php?t=209682")).

With discomfort settling in that I had no idea what I was doing 90% of the time and having to read step by step howtos and readmes for command line commands to simply install applications, I wanted to get windows back on my computer ASAP.

Now that I have Windows installed on my NTFS partition(hda1), and Ubuntu on my ext3 partition(hda2), my PC boots directly into Windows.

I guess I was somewhat expecting a screen to popup every reboot to ask me what partition I wanted to boot into, or F8 giving me the menu to choose Ubuntu, but I was wrong.

Now I'm stuck with no way of booting into Ubuntu and every walkthrough I have found refers to using GRUB to dual boot with Windows installed prior to Ubuntu. Would anyone be able to point me to a walkthrough that talks me through dual booting with Ubuntu installed first? Thanks!

---

### Post by scxtt on 2006-07-07
windows overwrites your /MBR [no questions asked] ... look for a how-to to reinstall grub so you can select XP/Ubuntu - they're all over the place ... i think all you really need is your LiveCD and to issue a command like grub-install ...

---

### Post by CarpKing on 2006-07-07
If you don't mind reinstalling, put Windows on there first and then install Ubuntu (follow one of the dual boot guides floating around).  Windows will do what Windows wants to do, so it is best to let it do its thing and then slip Ubuntu in while it's not looking.

---

### Post by ChiendeRue on 2006-07-07
[http://adrian15.raulete.net/grub/tiki-pagehistory.php?page=HomePage&source=0](http://adrian15.raulete.net/grub/tiki-pagehistory.php?page=HomePage&source=0)

Super Grub Disk is a tool that lets you restore grub or reinstall grub or recover on the MBR very easily and recover your Linux boot election menu.

It did not work for me because I caused far greater damage to begin with.
But it sure sounds like the solution for you.

Cheers,

CDR

---

### Post by kaje on 2006-07-07
Thanks for the replies, guys.

I found this [walkthrough]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-5dbdd6b5302831ed4335bd0b7387ffcad2543857")

and I now get the dual boot screen asking me which I want to boot up to, but when I choose the Ubuntu option I get an error that says this:



```
Booting ‘Ubuntu, 2.6.10’

root (hd0,1)
Filesystem type is ext2fs, parition type 0x83
initrd /boot/initrd.img-2.6.10-5-386

Error 19: Linux kernel must be loaded before initrd
```

---

### Post by kaje on 2006-07-07
> **ChiendeRue said:**
> [http://adrian15.raulete.net/grub/tiki-pagehistory.php?page=HomePage&source=0](http://adrian15.raulete.net/grub/tiki-pagehistory.php?page=HomePage&source=0)

Super Grub Disk is a tool that let's you restore grub or reinstall grub or recover on the MBR very easily and recover your Linux boot election menu.

It did not work for me because I caused far greater damage to begin with.
But it sure sounds like the solution for you.

Cheers,

CDR


That sounds easy enough. I think i'll try the easy route real quick. Thanks!

---

### Post by scxtt on 2006-07-07
what's your dapper entry in /boot/grub/menu.lst look like? -- it should look like this:
```
title           Dapper Drake, kernel 2.6.15-23-386 (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot
```> **kaje said:**
> Thanks for the replies, guys.

I found this [walkthrough]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-5dbdd6b5302831ed4335bd0b7387ffcad2543857")

and I now get the dual boot screen asking me which I want to boot up to, but when I choose the Ubuntu option I get an error that says this:



```
Booting &#8216;Ubuntu, 2.6.10&#8217;

root (hd0,1)
Filesystem type is ext2fs, parition type 0x83
initrd /boot/initrd.img-2.6.10-5-386

Error 19: Linux kernel must be loaded before initrd
```

---

### Post by kaje on 2006-07-07
Doh...tried the Super GRUB Disk Automatic install and get a bunch of Previous Try, failed messages, then a bunch of Error 21: Selected disk does not exist all the way to Booting '73' then at the end it says


```
N O =============== SUCCESS :( :(
```




hmmmm

---

### Post by kaje on 2006-07-07
> **scxtt said:**
> what's your dapper entry in /boot/grub/menu.lst look like? -- it should look like this:
```
title           Dapper Drake, kernel 2.6.15-23-386 (recovery mode) (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sdb1 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot
```

OK..looks like I have the kernel version wrong.

Let me correct that and see if I have better luck.

---

### Post by scxtt on 2006-07-07
we might not have the save kernel version installed ... so if i can see your /boot/grub/menu.lst and the results of
[indent]ls -l /boot[/indent]we should be able to figure it out ...

---

### Post by kaje on 2006-07-07
> **scxtt said:**
> we might not have the save kernel version installed ... so if i can see your /boot/grub/menu.lst and the results of
[indent]ls -l /boot[/indent]we should be able to figure it out ...


Yes I can see that.


I see a listing for

initrd.img -> boot/initrd.img-2.6.15
initrd.img.old -> boot/initrd.img-2.6.15-23-386

and

vmlinuz -> boot/vmlinux-2.6.15-25-386
vmlinuz.old -> boot/vmlinux-2.6.15-23-386

I'm guessing I should be using 2.6.15 for initrd and 2.6.15-25-386 for vmlinuz?

---

### Post by kaje on 2006-07-07
> **kaje said:**
> Yes I can see that.


I see a listing for

initrd.img -> boot/initrd.img-2.6.15
initrd.img.old -> boot/initrd.img-2.6.15-23-386

and

vmlinuz -> boot/vmlinux-2.6.15-25-386
vmlinuz.old -> boot/vmlinux-2.6.15-23-386

I'm guessing I should be using 2.6.15 for initrd and 2.6.15-25-386 for vmlinuz?

Made the changes using 2.6.15 and 2.6.15-25-386 and still get the Error 19: Linux kernel must be loaded before initrd.

---

### Post by kaje on 2006-07-07
Whoops..I'm getting ahead of myself.


Forgot to switch the kernel and initrd commands around. That walkthrough needs to fix that in it's example...

I have a question. What does "root=/dev/sdb1 ro single" do? Is that required or something I will want to do?

---

### Post by scxtt on 2006-07-07
the "root" is which drive it should use, "ro" is read-only, "single" is single-user mode ...

btw, the example i used above is for "recovery mode" -- you'll probably want to use this mode:```
title           Dapper Drake, kernel 2.6.15-23-386 (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot
```i fixed it above too ...

---

### Post by krazyd on 2006-07-07
You don't even need grub. In fact, I prefer using the Windows boot loader.

I used a little program called bootpart, which can be run from windows to edit the boot loader of windows to add partitions to it. See attached, documentation and examples are included. :D

See here for more info: [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)

---

### Post by kaje on 2006-07-07
> **scxtt said:**
> the "root" is which drive it should use, "ro" is read-only, "single" is single-user mode ...

btw, the example i used above is for "recovery mode" -- you'll probably want to use this mode:```
title           Dapper Drake, kernel 2.6.15-23-386 (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sdb1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot
```i fixed it above too ...


Well, I got the boot loader to begin loading ubuntu up now.


Now I'm getting stuck at:

Mounting root file system...
Waiting for root file system...

I'm guessing it has to do with the root=/dev/sdb1 on there. I'm not familiar enough with linux yet, but how do I find out what dev root is under? I know that I installed / on hda2.

---

### Post by scxtt on 2006-07-07
yeah, that's where my ubuntu is (sdb1) - you should definately change it to hda2 if that's where you installed ubuntu ...

---

### Post by kaje on 2006-07-07
> **scxtt said:**
> yeah, that's where my ubuntu is (sdb1) - you should definately change it to hda2 if that's where you installed ubuntu ...


What does sdb stand for then? I thought all hard drive partitions were hd(drive number)(partition number)

---

### Post by jordanmthomas on 2006-07-07
hd is for IDE drives
and sd is for SATA, SCIS, usb external hard drives

a means first disk, and b would mean second disk
the number is the partition number

so, /dev/hda3 would be the first IDE drive -- on the third partition.

---

### Post by kaje on 2006-07-07
> **jordanmthomas said:**
> hd is for IDE drives
and sd is for SATA, SCIS, usb external hard drives

a means first disk, and b would mean second disk
the number is the partition number

so, /dev/hda3 would be the first IDE drive -- on the third partition.


Ah...ok thanks

---

### Post by kaje on 2006-07-07
Well scxtt I got Linux up and running!


Appreciate the help very much! :-D Thanks!

---

### Post by scxtt on 2006-07-07
Congratulations :D -- and you're very welcome ...

---

