---
title: "Would Like to Install Windows XP"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Pido on 2008-02-04
Recently I installed Ubuntu 7.10 on my once Windows XP running computer, now I allocated the entire 160g drive to Ubuntu but was wondering if somehow I could take maybe 60g of that and making it free space so I can run a Windows XP install CD and install it there?

Also would I need to reinstall GRUB after so I could pick which OS to boot into.

Thanks for any and all help.

---

### Post by jordanmthomas on 2008-02-04
Yes, it is possible.  It is a little more involved than installing Ubuntu after installing XP, though.

Step 1:  Boot off your Ubuntu CD and use gparted to make some room for Windows (just leave the new space unformatted)
It's probably best to make sure you keep your swap in an extended partition like it already is and leave it next to your Ubuntu partition to save you the trouble of editing your /etc/fstab later.
Step 2:  Install Windows into this new space.
Step 3:  After windows is installed and working, boot off your Ubuntu CD again and reinstall grub.
```
sudo grub

```
Then, assuming you have Ubuntu installed on your first partition of your master hard drive:
```
root (hd0,0)
setup (hd0)
quit

``` 
```
find /boot/grub/stage1
```  If your Ubuntu isn't installed as the first partition on the first drive (hd0,0), then you can look up the correct one to use by typing this in the grub prompt you have open.


Then, you'll need to make an entry in your /boot/grub/menu.lst for Windows
While still using your Ubuntu CD, type this:
```
mkdir ~/ubuntu
sudo mount /dev/sda1 ~/ubuntu [COLOR="Red"]#replace /dev/sda1 with the proper partition if it's not right[/COLOR]
gksudo gedit ~/ubuntu/boot/grub/menu.lst
```
Then, scroll on down to the bottom and add 
```
title Windows XP
rootnoverify [COLOR="Red"](hd0,2)[/COLOR]
chainloader +1
boot

```
Be sure that you put the right thing here, this would be the typical thing to put if you have Ubuntu, a swap partition, and then Windows.  When you're counting, start at 0.  hd0,2 means the first disk, third partition

This may be a little confusing the first time you do it, but once you do it once, it's very easy and the whole process of reinstalling grub only takes a few seconds.

After this, you should be good to go.  Look up how to restore grub if you need more help installing grub after Windows puts its bootloader on.
Also, feel free to ask back here if you need more help.
Good luck

edit:  I can't believe I know all that off the top of my head...Maybe I need to take a break from computing.  :|

---

### Post by omi291 on 2008-02-04
> **Pido said:**
> Recently I installed Ubuntu 7.10 on my once Windows XP running computer, now I allocated the entire 160g drive to Ubuntu but was wondering if somehow I could take maybe 60g of that and making it free space so I can run a Windows XP install CD and install it there?

Also would I need to reinstall GRUB after so I could pick which OS to boot into.

Thanks for any and all help.

Yes, you can partition your hard drive and dual-boot with windows; that's what i do too. I think GParted is used to manage partitions.

As for GRUB, i'm not sure since i'm still a pretty big linux newbie...but i'm pretty sure some other members will know what to do :)

---

### Post by rbc on 2008-02-04
The reverse is actually much easier, although there are ways to do it. If you have precious files stored already I would back them up, install XP, then install Ubuntu. Since you have only recently installed Ubuntu, this might be the way to go. If not, try this:
[http://ubuntuforums.org/showthread.php?t=395185&p=2388318](http://ubuntuforums.org/showthread.php?t=395185&p=2388318)

---

### Post by Pido on 2008-02-04
To jordanmthomas

I cannot use the live CD for Ubuntu 7.10 because my monitor doesn't support it or something instead I used the text based installation CD.

---

### Post by jordanmthomas on 2008-02-04
You can probably use the [Super Grub CD]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") to reinstall grub then, and the [gparted live cd ]("http://gparted-livecd.tuxfamily.org/")to repartition.

---

### Post by Pido on 2008-02-04
> **jordanmthomas said:**
> You can probably use the [Super Grub CD]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") to reinstall grub then, and the [gparted live cd ]("http://gparted-livecd.tuxfamily.org/")to repartition.

Forgive me for being a noob but, will I need to reboot and run from CD the GParted Live CD to create a partition? And THEN run the Super Grub CD to make me able to boot into either?

---

### Post by jordanmthomas on 2008-02-04
> Forgive me for being a noob
Please, don't worry about it.  This is absolute beginner's talk after all.  :)

You can boot off the GParted LiveCD and make a partition.
After this, your Ubuntu will still function correctly and GRUB will still be installed.  
When you're ready to install Windows, boot off its CD and install it in the new partition.  
After this, only Windows will boot because it gets rid of GRUB.  
So, you can use the Super Grub CD to install GRUB (I have never used it, but I believe it'll even add Windows to your menu.lst for you)
Once GRUB is installed, Ubuntu will definitely work, and if you add an entry for Windows, it will work too.

---

### Post by Pido on 2008-02-04
Thank you very much! This answers my question exactly! :)

---

### Post by dondad on 2008-02-05
> **jordanmthomas said:**
> Please, don't worry about it.  This is absolute beginner's talk after all.  :)

You can boot off the GParted LiveCD and make a partition.
After this, your Ubuntu will still function correctly and GRUB will still be installed.  
When you're ready to install Windows, boot off its CD and install it in the new partition.  
After this, only Windows will boot because it gets rid of GRUB.  
So, you can use the Super Grub CD to install GRUB (I have never used it, but I believe it'll even add Windows to your menu.lst for you)
Once GRUB is installed, Ubuntu will definitely work, and if you add an entry for Windows, it will work too.

One other possibility. Install Windows in a virtualbox. I have a couple of programs that I need about once every 6 month, so that is what I did.

---

