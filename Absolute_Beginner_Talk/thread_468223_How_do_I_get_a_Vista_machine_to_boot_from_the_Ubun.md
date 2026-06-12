---
title: "How do I get a Vista machine to boot from the Ubuntu 7.04 CD?"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-06-08
I am going to set up a dual boot with Vista and Ubuntu 7.04. The computer is brand new and already has Vista on it. I just need to know how to get the computer to boot from the Ubuntu CD.  There must be some selection at the beginning of a Vista boot when you turn on the computer, so it'll boot from the CD. Can someone tell me?
Thanks.

---

### Post by Najand on 2007-06-08
You must change the BIOS setting. You can usually enter BIOS setting by pushing one of Del or F2 or F12 Buttons.

---

### Post by Nekiruhs on 2007-06-08
Your BIOS takes care of booting from CD not vista. Is the disk in when you turn it on? Did you burn the disk as an ISO or as data. Check if you only have one file on the disk or many. Tells us what you have found

---

### Post by Rotaj on 2007-06-08
It probably has nothing to do with Vista, but rather your BIOS.
If you consult your computer manual, it should tell you how to access the bios. Sometimes this information is on screen during the early part of the boot process.

---

### Post by dannyboy79 on 2007-06-08
some computers even have what's called a boot device menu, and you don't even need to change anything in the bios, sometimes it's the F8 key, hit it repeatedly BEFORE you see anything about VISTA, then chose the CDROM and it will boot Ubuntu. If F8 doesn't work, check your manual or call for support as you prbably paid for it.

---

### Post by lambros on 2007-06-08
Hope this helps:
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

Lambros

---

### Post by swarup on 2007-06-08
Thanks everyone. 

As it turns out, F12 does the trick in Vista. It brings you right to the boot menu. 

I tried the DEL key, but that didn't do it.

---

### Post by mlsquad on 2007-06-08
> **swarup said:**
> As it turns out, F12 does the trick in Vista.As mentioned, this doesn't have anything to do with Vista.  It's your computer's hardware that decide where to find the OS, not the OS itself.
Hope everything runs well.

---

### Post by Najand on 2007-06-08
> **swarup said:**
> Thanks everyone. 
 As it turns out, F12 does the trick in Vista. It brings you right to the boot menu. 
Good you could make it.
> I tried the DEL key, but that didn't do it.
Well, different systems, use different keys for that. Some use "F12" like yours, some others use "del"... Not a big deal.... Have fun.

---

### Post by swarup on 2007-06-08
I was going to do a triple boot with Vista/XP/Ubuntu 7.04, but from the website   

[http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/](http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/)

    , it sounded kind of complicated. So I think I'll stick with the dual boot for now (Vista/Ubuntu). I wanted to included XP as well because there are some Windows programs I have which do not run in Vista.

---

### Post by swarup on 2007-06-08
In addition, it seemed to require that you start with Ubuntu first, and I already have Vista on the system-- which I didn't particularly feel like deleting.

---

### Post by boracon on 2007-06-08
> **swarup said:**
> I was going to do a triple boot with Vista/XP/Ubuntu 7.04, but from the website   

[http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/](http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/)

    , it sounded kind of complicated. So I think I'll stick with the dual boot for now (Vista/Ubuntu). I wanted to included XP as well because there are some Windows programs I have which do not run in Vista.

I recommend trying Virtual PC 2007 free from MS. I have Vista Business installed, about to install Ubuntu and I run my Vista incompatible programs in a XP virtual machine. It's been working really well for me. Virtual PC supposedly (according to MS) won't work with Home Premium but loads of people have installed it and seem to be doing OK

---

### Post by swarup on 2007-06-08
(I think people may not have seen this entry, because it got stuck at the end of page 1 when I wrote a quick reply which went on page 2....)

I was going to do a triple boot with Vista/XP/Ubuntu 7.04, but from the website

[http://www.hevnikov.com/blog/2006/11...e-boot-screen/](http://www.hevnikov.com/blog/2006/11...e-boot-screen/)

, it sounded kind of complicated. So I think I'll stick with the dual boot for now (Vista/Ubuntu). I wanted to included XP as well because there are some Windows programs I have which do not run in Vista.

---

### Post by Najand on 2007-06-08
Hmm, you don't need to delete vista at all.... You may resize it though...  Actually I don't think making a triple boot harder than a dual boot...
You need 4 partitions.
You should install vista first.
Then install XP on the 2nd partition. (Don't worry if it couldn't start Vista after installing XP)
Then install Ubutnu on 3rd and swap partition on the 4th one. When you install ubuntu it will recognize your XP and VISTA automatically... 
That is all.

---

### Post by dannyboy79 on 2007-06-11
> **Najand said:**
> Hmm, you don't need to delete vista at all.... You may resize it though...  Actually I don't think making a triple boot harder than a dual boot...
You need 4 partitions.
You should install vista first.
Then install XP on the 2nd partition. (Don't worry if it couldn't start Vista after installing XP)
Then install Ubutnu on 3rd and swap partition on the 4th one. When you install ubuntu it will recognize your XP and VISTA automatically... 
That is all.

as an FYI, Grub can't boot more than 1 windows OS from the same hard drive UNLESS you use the HIDE and UNHIDE options within grub. OR you could only have vista or winxp within grub's menu, then that would take you to NTLDR or whatever VISTA's bootloader was and then boot into WINXP or VIsta from there. here's an example of installing more than 1 windows install on the same hard disk and using grub to boot them. 

title          Dos 7.10 @ hdc1
hide           (hd0,0)
unhide         (hd1,0)
map            (hd1) (hd0)
map            (hd0) (hd1)
root           (hd1,0)
makeactive
chainloader    +1

title          Win98 @ hdc2
hide           (hd0,0)
hide           (hd1,0)
unhide         (hd1,1)
root           (hd1,1)
makeactive
map            (hd1) (hd0)
map            (hd0) (hd1)
chainloader    +1

And in actuality, he talks about even having to hide windows from other drives if you are chainloading them. This is 1 grub menu.lst booting over 100plus systems on 4 hard drives split up between 144 partitions. See below: (here's the link to the entire article: [http://www.justlinux.com/forum/showthread.php?t=143973](http://www.justlinux.com/forum/showthread.php?t=143973))

title          Win2k @ sdb1
hide           (hd0,0)   # hiding DOS 6.22 partition in hda1
hide           (hd1,0)   # hiding DOS 7.10 partition in hdc1
hide           (hd1,1)   # hiding Win98    partition in hdc2
hide           (hd2,0)   # hiding Win XP   partition in sda1
unhide         (hd3,0) # unhide Win2k partition for execution
root           (hd3,0)
makeactive
map            (hd3) (hd0)
map            (hd0) (hd3)
chainloader    +1

title          FreeDOS @ sdb2
hide           (hd0,0)   # hiding DOS 6.22 partition in hda1
hide           (hd1,0)   # hiding DOS 7.10 partition in hdc1
hide           (hd1,1)   # hiding Win98    partition in hdc2
hide           (hd2,0)   # hiding Win XP   partition in sda1
hide           (hd3,0)   # hiding Win2k    partition in sdb1
unhide         (hd3,1)
root           (hd3,1)
makeactive
map            (hd3) (hd0)
map            (hd0) (hd3)
chainloader    +1

---

### Post by xthund3rh3adx on 2007-06-11
then dont use GRUB, use another bootloader.

---

### Post by Najand on 2007-06-11
And what is the problem with hiding and unhiding them?

---

### Post by dannyboy79 on 2007-06-12
> **Najand said:**
> And what is the problem with hiding and unhiding them?

there is no problem at all, I was merely informing you. Also, I was responding directly to your statement that doing a triple boot isn't any harder than doing a dual boot which is incorrect to someone who has never done it and doesn't understand grub or understand what's going to occur. Since I am someone who has had experience with this I wanted to let  you know that Ubuntu does NOT automatically add entries to grub for both Vista and XP. what it does is if you install Xp first, then Vista, vista will get added to NTDLR and will be a boot option when trying to boot windows xp, so when you install Ubuntu, all grub will add is the XP boot option, then the only way to get to Vista is to boot XP from grub which will bring up NTLDR and then you can either pick XP or VISTA. I could have it backwards but the main point is that Ubuntu does NOT add both entries to your menu.lst, it only adds one to a windows boot loader which then boots either of your windows installs. IF you want grub to boot them all directly (chainloading) then you need to use the hide and unhide options which there is nothign wrong with it, only informing you and other users if your or them weren't aware of it.

---

