---
title: "Fstab/Swapfile Damage"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by WaffleLove on 2007-10-23
I dont know how to explain this, so I'll get to the point. I some how ruined fstab. So I figured deleting what was inside would be smart, nope, but thanks to the disk manager utility posted in another thread, I was able to remount my main partition  and it showing up in my fstab now.

However my swap file is not showing up at all in fstab, gnome partition lets me turn it on, swapon command will not. I've searched the forums and have tried a lot of the commands, but I am absolutly green when it comes to linux. Heres what I got atm.

Sudo fdisk -l
[PHP]Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000df62b

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11905    95626881   83  Linux
/dev/hda2           11906       12161     2056320   82  Linux swap / Solaris[/PHP]



My fstab file
[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

/dev/hda1	/media/hda1_	ext3	defaults	0	2

[/PHP]

I'd like to point out that I've tried fsck, and after I installed disk manager and was able to use it to mount my hda1 partition again. i got an fsck error 8 type message after and reboot but ctrl-d it and everything seems fine, then again I am learning in an fun way right now.

Any input on this would help a lot. thank you.

---

### Post by bodhi.zazen on 2007-10-23
Add this line to /etc/fstab :

> /dev/hda2   none  swap  sw  0  0

Where is your root partition in fstab ?

/dev/hda1  / ext3    defaults,errors=remount-ro 0       1

Are you sure that fstab file is on the hard drive and not the live CD ?

You can edit with :

```
gksu gedit /media/hda1_/etc/fstab
```

or some such ?

---

### Post by WaffleLove on 2007-10-23
How would I get this information? 
Sorry, I'm very new to terminal.

also I take it add the line to the bottom of what already in my fstab?
I used gksudo edit /etc/fstab to bring up fstab orginaly

---

### Post by bodhi.zazen on 2007-10-23
Ah, yes /etc/fstab is teh fstab file on the live CD.

Your hard drive is likely mounted in /media

Enter this command to see :

```
mount
```

then:

```
gksu gedit /media/xxx/etc/fstab
```

where xxx = your mount point (from the mount command)

Yes, then add in the swap line I gave you :twisted:

Save the changes, reboot 

You should be able to see your swap :

```
free
```

And turn it on with :

```
sudo swapon /dev/hda2
```

---

### Post by WaffleLove on 2007-10-23
Thank you. I'll give it an try, and post results. I forgot to mention, I'm currently not using the CD I running from an install if that makes any difference. My swap I think is on atm, I used partition edit (sorry repository/add/remove had it labeled gnome partitioner when I installed it)

---

### Post by WaffleLove on 2007-10-23
I just rebooted, and got the same error message from Fsck. I think I may need to reload ubuntu again, anyway I can correct that?
However, the swap file IS being fully detected now thank you :D
I'll work on this when I get home from work some more.
THANK YOU!
Before I forget, I wanted to resize my swap to something smaller this is how it all began, tips on how to do so to prevent this from happening again?

---

