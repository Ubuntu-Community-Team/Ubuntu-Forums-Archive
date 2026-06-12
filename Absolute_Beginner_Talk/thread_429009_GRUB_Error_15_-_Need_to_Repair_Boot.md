---
title: "GRUB Error 15 - Need to Repair Boot"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by novus721 on 2007-04-30
:confused: Hi all

So I formatted my second hard drive, but for some reason (because the pins are in it as master?) it had the boot point for my kernel stored there - and when I formatted it, it deleted.

now, fdisk -l gives me this

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24133   193848291   83  Linux
/dev/sdb2           24134       24321     1510110    5  Extended
/dev/sdb5           24134       24321     1510078+  82  Linux swap / Solaris

Disk /dev/sdc: 256 MB, 256900608 bytes
16 heads, 32 sectors/track, 979 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         979      250574+   6  FAT16

...I am trying to boot from my 200gig which is labeled as the boot but whenever I go to load it I get an Error 15

I tried to change the kernel path to root=/dev/sdb1 and then boot, it but it was to no avail. Is there anyway I can repair the boot command? I really would prefer not to have to reformat my whole drive, as I do have information on there that I cannot loose - any help would be greatly appreciated, thank you!!

---

### Post by confused57 on 2007-04-30
You could try reinstalling grub, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Can you post the output of your /boot/grub/menu.lst?

---

### Post by psusi on 2007-04-30
If hdb is the disk you have installed to and sda is just storage, then yes, you should switch them so that the storage drive is slave and the boot drive needs to be master.  Then from a livecd you need to reinstall grub:

sudo grub
root (hd0,0)
setup (hd0)

---

### Post by novus721 on 2007-04-30
Thanks for the replies...


I have done as you have both suggested, the 200g is now my master, but the only difference now is that whenever it goes to load i get...

GRUB Loading stage 1.5
GRUB loading, please wait...
Error 17

any ideas?

---

### Post by novus721 on 2007-04-30
whoops forgot to add this too

to output to that line was...

root@ubuntu:~# /boot/grub/menu.lst
bash: /boot/grub/menu.lst: No such file or directory

---

### Post by confused57 on 2007-04-30
> **novus721 said:**
> Thanks for the replies...


I have done as you have both suggested, the 200g is now my master, but the only difference now is that whenever it goes to load i get...

GRUB Loading stage 1.5
GRUB loading, please wait...
Error 17

any ideas?

If you get a grub menu at boot, highlight your Ubuntu entry, press "e", then change root from (hdx,y) to (hd0,y), then press "b" to boot.

If you're not getting a grub menu, you'll need to mount your partition & examine your menu.lst.
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sdb1 /media/ubuntu
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```

---

### Post by novus721 on 2007-04-30
No grub menu was to be found, so I did the latter, replacing the sdb1 with sda1 because after  I changed my slave/master disks fdisk showed that my 200 was now sda, if I should change that back please let me know...

and to be honest I don't know exactly what I am looking for within that gedit, so here is the output if you don't mind looking through it: 

[http://rafb.net/p/rWsouY68.html](http://rafb.net/p/rWsouY68.html)

thank you so much!

---

### Post by confused57 on 2007-04-30
> **novus721 said:**
> No grub menu was to be found, so I did the latter, replacing the sdb1 with sda1 because after  I changed my slave/master disks fdisk showed that my 200 was now sda, if I should change that back please let me know...

and to be honest I don't know exactly what I am looking for within that gedit, so here is the output if you don't mind looking through it: 

[http://rafb.net/p/rWsouY68.html](http://rafb.net/p/rWsouY68.html)

thank you so much!

Since Feisty uses UUID's, it shouldn't matter whether your disk is shown as sda or sdb.  Here's the line I'm referring to in your /boot/grub/menu.lst:
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd[COLOR="Red"]1[/COLOR],0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f3a4bb1d-a830-4400-9136-372e2c00361f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```

change the root to (hd0,0):
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd[COLOR="Red"]0[/COLOR],0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f3a4bb1d-a830-4400-9136-372e2c00361f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```

Hopefully, this will give you a grub menu at boot.  You should be able to mount your partition using the live cd, edit your menu.lst, quit & save:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Added:  If you have access to another computer & a spare cd-rw disk, I'd recommend downloading & burning a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's a small download(5-7 Mb) & it should be able to boot your Ubuntu.

---

### Post by novus721 on 2007-04-30
I made the change, saved it, and then rebooted, and still got the error 17 and no menu

also, when i came back with the live cd to open the menu.lst and double check it i found to my surprise it is now completely blank - i have a feeling that is not a good thing

---

### Post by novus721 on 2007-04-30
Ignore that I mounted the wrong thing, but the hd0,0 is still there

---

### Post by confused57 on 2007-04-30
> **novus721 said:**
> I made the change, saved it, and then rebooted, and still got the error 17 and no menu

also, when i came back with the live cd to open the menu.lst and double check it i found to my surprise it is now completely blank - i have a feeling that is not a good thing
Did you try mounting it as sda1, instead of sdb1?:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```

Also, see the link I gave you in my last reply for mounting your /boot/grub/menu.lst with the live cd.

---

### Post by novus721 on 2007-04-30
Would there be any benefit of changing my

```
/boot/vmlinuz-2.6.20-15-generic root=UUID=f3a4bb1d-a830-4400-9136-372e2c00361f ro quiet splash
```

to 

```
/boot/vmlinuz-2.6.20-15-generic root=/dev/sda1
```

sorry to triple post, just throwing it out there because I dont want to damage this beyond compare,thanks

---

### Post by novus721 on 2007-04-30
and yes I realized what I did and changed it and was able to view the menu, thank you though

---

### Post by novus721 on 2007-04-30
> Also, see the link I gave you in my last reply for mounting your /boot/grub/menu.lst with the live cd.

I thought it was just a further explanation of the cmd lines you previously provided, am I missing something? Sorry, finals are kind of frying my brain here, heh - I'll look over it again though, thank you again

---

### Post by confused57 on 2007-04-30
> **novus721 said:**
> Would there be any benefit of changing my

```
/boot/vmlinuz-2.6.20-15-generic root=UUID=f3a4bb1d-a830-4400-9136-372e2c00361f ro quiet splash
```

to 

```
/boot/vmlinuz-2.6.20-15-generic root=/dev/sda1
```

sorry to triple post, just throwing it out there because I dont want to damage this beyond compare,thanks
I'm not sure why you're not getting a grub menu at boot.  You could use the live cd to see if the root partition UUID agrees with your kernel entry:
```
sudo vol_id -u /dev/sda1
```

When you reinstalled grub, what did this return?:
```
sudo grub
find /boot/grub/stage1
```
maybe wouldn't hurt to try reinstalling grub to the mbr of sda (hd0)

Another thing that may or may not make a difference is to change your device.map, mount your partition using the live cd, then:
```
gksudo gedit /media/ubuntu/boot/grub/device.map
```
then change your device.map to:
```
(hd0) /dev/sda
```

I don't know if running a filesystem check on your root partition would help or not:
```
sudo e2fsck -f /dev/sda1
```

I believe your best bet would be to obtain a copy of the Super Grub Disk...I'm mainly throwing out ideas that you might try, but the SGD should work.

Added:  You're probably using Cable Select, but make sure jumper settings are correct(master, if not cable select), since you switched the positiion of the hard drive...is your bios detecting the hard drive correctly?

---

### Post by confused57 on 2007-05-01
> **novus721 said:**
> :confused: Hi all

So I formatted my second hard drive, but for some reason (because the pins are in it as master?) it had the boot point for my kernel stored there - and when I formatted it, it deleted.

now, fdisk -l gives me this

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161   83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24133   193848291   83  Linux
/dev/sdb2           24134       24321     1510110    5  Extended
/dev/sdb5           24134       24321     1510078+  82  Linux swap / Solaris

Disk /dev/sdc: 256 MB, 256900608 bytes
16 heads, 32 sectors/track, 979 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         979      250574+   6  FAT16

...I am trying to boot from my 200gig which is labeled as the boot but whenever I go to load it I get an Error 15

I tried to change the kernel path to root=/dev/sdb1 and then boot, it but it was to no avail. Is there anyway I can repair the boot command? I really would prefer not to have to reformat my whole drive, as I do have information on there that I cannot loose - any help would be greatly appreciated, thank you!!

I've reread your first post and I believe what we should have done from the beginning was to reinstall grub to the mbr of your original sda drive listed above, using the live cd:
```
sudo grub
find /boot/grub/stage1
```
should have returned  "root (hd1,0)"
you would have needed to then enter:
```
root (hd1,0)
setup (hd0)
quit
```

then you "should" have been able to boot Ubuntu, by booting first to your original sda drive...I know this is 20/20 hindsight, but I believe that would have worked.  Sorry to run you in circles, but if all else fails, then you could set up system back up the way it was and try this.  You'd need to change the root back to (hd1,0) in your /boot/grub/menu.lst.

---

### Post by novus721 on 2007-05-01
ISSUE HAS (kind of) BEEN RESOLVED

...what I ended up doing on the advice of a friend was to physically unplug my slave drive and reinstall GRUB

```
sudo grub

> root (hd0,0)

> setup (hd0)

> quit
```

I then was able to get back into my master without any problem at all, and I plugged my slave in and I was still able to get into my master, I am now going to deal with the issue of getting my slave to work seamlessly as well, but in the interest of passing my courses I am going to need some shut-eye in the meantime - thank you especially @ confused, helped a lot:)

---

### Post by confused57 on 2007-05-01
> **novus721 said:**
> ISSUE HAS (kind of) BEEN RESOLVED

...what I ended up doing on the advice of a friend was to physically unplug my slave drive and reinstall GRUB

```
sudo grub

> root (hd0,0)

> setup (hd0)

> quit
```

I then was able to get back into my master without any problem at all, and I plugged my slave in and I was still able to get into my master, I am now going to deal with the issue of getting my slave to work seamlessly as well, but in the interest of passing my courses I am going to need some shut-eye in the meantime - thank you especially @ confused, helped a lot:)

Good deal, I thought maybe reinstalling grub might work...you'll also need to change the #groot line in your /boot/grub/menu.lst:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)
you'll need to change it from (hd1,0) to (hd0,0), if you don't a kernel update will change all your root entries back to (hd1,0).

Here's how to mount your slave drive partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu](http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu)

---

