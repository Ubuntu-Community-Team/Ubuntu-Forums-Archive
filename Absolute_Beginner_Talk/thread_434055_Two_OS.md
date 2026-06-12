---
title: "Two OS?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by SlyReaper on 2007-05-05
Everyone I've talked to has been singing the praises of Ubuntu, but I'm not ready to give up on windows completely (because it's pretty much all I know how to use).  Is it possible to install ubuntu without getting rid of windows?  I'd like to be able to switch between the two at will.

Thanks for any help that comes this way.

---

### Post by gamer91 on 2007-05-05
Ubuntu will run strait from the disk - all you have to do is change your boot order in your bios and place the cd in the drive before startup

---

### Post by jfinkels on 2007-05-05
> **SlyReaper said:**
> Everyone I've talked to has been singing the praises of Ubuntu, but I'm not ready to give up on windows completely (because it's pretty much all I know how to use).  Is it possible to install ubuntu without getting rid of windows?  I'd like to be able to switch between the two at will.

Thanks for any help that comes this way.

Yep, it's called "dual-boot"ing. You will have to resize your Windows partition to make room for Ubuntu, then install Ubuntu  in the now-freed space on your hard drive. You can do this all from the Ubuntu Live CD, search the forums for more information on dual-booting.

Remember to defragment your Windows partition twice before resizing :D

---

### Post by oilchangeguy on 2007-05-05
read this:
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)
it was written for a laptop. but this applies to any dual boot setup.

---

### Post by SlyReaper on 2007-05-05
Ah that's pretty sweet - I had the idea that you had to install it onto the HDD first.  But the trouble with that option is that I won't have a CD/DVD drive whilst doing that.  Can I install it to HDD and switch between Ubuntu and windows at will?  

Sorry if I come across as a noob, but that's because I really am.  Non-windows stuff is scary territory for me.

EDIT: whoa looks like loads of people replied while I was writing this...

---

### Post by derred on 2007-05-05
> **jfinkels said:**
> Yep, it's called "dual-boot"ing. You will have to resize your Windows partition to make room for Ubuntu, then install Ubuntu  in the now-freed space on your hard drive. You can do this all from the Ubuntu Live CD, search the forums for more information on dual-booting.

Remember to defragment your Windows partition twice before resizing :D

The best way to go is with a fresh install I always say. Backup all your data, and then just install Windows first, leaving a bit of space (unpartitioned as in a D drive in Windows) for Ubuntu, install Ubuntu and enjoy. GRUB, the Ubuntu bootloader will handle booting to whatever version of windows you have so just install it to MBR. 

At worst you'll have to do a fixmbr and/or fixboot from the recovery console of the install CD(in NT/XP) or an fdisk /mbr from the start-up disk(in 9x/ME)

Best of luck!

---

### Post by useLinux, on 2007-05-05
> **SlyReaper said:**
> Ah that's pretty sweet - I had the idea that you had to install it onto the HDD first.  But the trouble with that option is that I won't have a CD/DVD drive whilst doing that.  Can I install it to HDD and switch between Ubuntu and windows at will?  

Sorry if I come across as a noob, but that's because I really am.  Non-windows stuff is scary territory for me.

EDIT: whoa looks like loads of people replied while I was writing this...

All you need to do is

1. Insert the cd you burned ubuntu onto.
2. Restart the computer AND boot from that cd
3. When on ubuntu simply go to system > administration > GParted. 

(It was on ubuntu 6 but im not sure about 7.04 Of its not simply go to Applications > Accessories > Terminal

type in the code

```
sudo apt-get install gparted
```

Then it should be there:)  ) [/ESSAY]

Basicly resize your main Hard disk drive. Since your using windows, your looking for the drive with the biggest amount of space with the format ntfs

Resize it, taking about 10 - 20 GB off of it (Remembering 1024 MB = 1 GB)

Then click apply and exit gparted.

Click on the desktop "Install" and when asked where to install chose the radio button or "click the mad wee dot so its highlighted" next to the text that says "Use the biggest free amount of unused space" (thats not a direct quote, it will say something like that) then click next. It will install on that partion of your hard disk drive and when you restart your computer, remeber to boot from the hard disk and take out your cd. It will then ask you if you want to boot from Windows XP or Ubuntu :) 
Hope that helps

---

### Post by sailor2001 on 2007-05-05
there are video tutorials for ubuntu installing on youtube.Com.... and believe me it is a simple as it Can get........ just be patient and read diretions Carefully ........EXuse the Capital C & X as I'm using them for hot keys on my 3d desktop....and that's something great in feisty 7.04 (beryl)

---

### Post by Pistolla on 2007-05-05
Alls i can tells ya is that if it weren't for me "borking" certain settings i would've "jumped ship" last year (around October). Dual-bootin' is easy under Ubuntu (at least from Dapper-Drake on) 'cause the peeps here know what they are dealing with. Not just Windoze (of which i still dual-boot) but the "complexity" it seems to be...it is not!! Alls ya needs to do is "rewire" yer brain a little to understand Linux. It is 'bout the same, only it is a better system to which you can do things; or just run the 'puter with.
i am a fan of Linux, (Ubuntu in particular,) b/c of what they done to make it as easy a transition as possible:guitar: they rock they really do. Just keep looking at the posts here (not much time is wasted either) and you will see that it is true. Sorry if it sounds to "commercial. but i am impressed of what they do) but what they have done made me a convert simply b/c of their expertise.

---

### Post by sarcazmo on 2007-05-05
Do you have to create a new partition using gparted, or will ubuntu do that automatically?

---

### Post by SlyReaper on 2007-05-05
Ok thanks for all the replies guys.  So far, I've only booted from the disk, and very pretty it looks too.  However, should I be worried that when running ubuntu, my computer can't detect my wireless internet stuff?  :confused:

---

### Post by Pistolla on 2007-05-05
Ubuntu will give ya an option to do that. Pretty much self-explanatory You will see the options. Ubuntu may'nt have the graphics Windoze has, but it is better, for the most part.

Just use the "install live CD" if you have it. It is, pretty much, self-explanatory after that, it really is. They have done a tremendous job to help us windoze peeps acclimate to Linux. AND you don't have to be savvy to learn Linux

---

### Post by sarcazmo on 2007-05-05
Ok, just to make sure before I install it.  Even though I have XP on my system now, I can just choose the "Use the largest continuous open space" option and ubuntu will do the partitioning for me with minimal chance of destroying my xp?

---

