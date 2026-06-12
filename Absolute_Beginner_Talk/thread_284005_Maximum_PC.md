---
title: "Maximum PC"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by brightmatter on 2006-10-25
I read an article in Maximum PC saying the install of Linux Ubuntu could be a snap on my machine.  I have not had that experience.  I am trying to install it on my laptop.  Is this forbidden?  I have a Compaq Presario 2100 laptop.  It is a terrible laptop and old to boot.  Windows XP hogs all possible resources leaving me with little to nothing for my Aps.

Here is the trouble.  I download the *.iso and burn it to disc.  I pop this disc in my laptop and turn it on.  I see a boot screen.  I choose run and or install.  After a bit, the desktop is available.  I assume I need to install it so I right click open and select open.  The CD goes nuts searching and possibly copying files.  I waited for 3 hours and it never stopped the CD ROM, not once.  I figured it was an error so I reboot and I try again.  This time I wait 9 hours.  Still the CD ROM is going nuts doing... something.  I re-burn the disc on a slow speed to make sure there were not disc errors.  Again, 6 hours later, I have a CD ROM working its buns off but going nowhere fast.  I download the *.iso again and burn the image again to a third disc and try again.  No luck.

Can anyone give me a clue?:confused: 

Brightmatter

---

### Post by Qrk on 2006-10-25
Sometimes laptop cd drives have a problem with the live cd installer. I'd try installing from the alternate cd, available from Ubuntu's website. 

The Alternate cd is perfect for older systems which have slow cd drives or a lack of RAM.

---

### Post by tubasoldier on 2006-10-25
I had the same issue with an old gateway laptop that I had. It turned out that it could not read burned disks at all. Waiting for a disk from ShipIt took care of that problem.
It may also be that it may have an issue with its ram. If that is the case then the downloaded file will be a little corrupt and may not be working properly.   

These are just a few ideas, maybe one of them might be right but it is a little hard to tell without actually hearing the drive or seeing the laptop.

---

### Post by CatKiller on 2006-10-25
The cd will keep running all the time - everything that happens in the live environment is run off the cd, which is why it's so slow. To install, use the Install icon on the desktop, or if your machine doesn't have a huge amount of RAM, download the Alternate cd for a text-based install instead.

Welcome to the community, and good luck.

EDIT: Man, I'm slow.

---

### Post by nickburns on 2006-10-25
Can I recommend using xubuntu flavor instead of the usual ubuntu.  I run it on my piece of junk laptop, and it runs really well.  It is a light weight version of ubuntu that is still very user friendly, and seems to work well with older hardware.

---

### Post by lloyd_b on 2006-10-25
On that machine, run the option to verify the CD.  I had a similiar problem, and it turned out that the older laptop (mine's a Sony, not a Compaq) had problems reading some types of CD-R's.  Net result is that even though the CD  works fine the the machine you burned it on, it won't necessarily work on the  laptop.

You might try the "alternative install CD" (that worked for me).  It uses a text-based installer that's seems much more robust that the installer on the Live CD.  Also, using a different type of CD-R could make a difference.

Lloyd B.

---

### Post by 3rdalbum on 2006-10-25
Here's the clue: "Windows XP hogs all my resources leaving me nothing for apps".

How much memory do you have? Ubuntu recommends 256 megs of RAM. It's possible to run the system installed with less than that, but installing from the Live CD really does require the full 256 megs.

If you don't quite meet the requirements, you can try downloading and burning the alternative CD, which is a text-based installer (your finished system will still have a GUI), or you could try Xubuntu.

---

### Post by the_one on 2006-10-25
ALL current OS's (WinXP, MacOS, Linux) are resource hogs because they are developed to use the latest hardware. Even WIn98 SE needed 128 MB to run well. But, linux can be tweaked to run on older hardware.

My guess is that you have less than 128MB of ram (probably 64MB). You'll have a rough time running apps even if you use the light-weight windows manager in  xubuntu (XFCE). Be prepared to compile a custom Kernel (very easy to do...really).

I Dual-Boot Ubuntu on a ThinkPad 600 with Windows 2000. I had to add 128MB of ram for Win 2000 to run fairly well. Ubuntu ran a little slower until I made a custom Kernel and took out support for hadrware I didn't have (Firewire, Bluetooth, USB2, SCSII, Palm Pilot, ETC.). I have Gnome, KDE, and XFCE and switch between them. GNOME is the slowest and, of course, XFCE is the fastest. XFCE doesn't have much eye candy but, is very responsive.

Older laptop CD drives have a hard time with the newer CD-R media. If you can find the darker colored media, give that a try. Some CD-RW media does better. Clean the lens if you can get at it. Other wise order a CD (you only have to pay shipping/postal costs). 

The Alternate Install Disk is the text based Debian Installer and will only install the basic Linux system on, but gives you the option to select which window manager you install (it downloads the additional packages you need), otherwise you'll only have the bash shell (command line) when you reboot. I think it was originally meant for server or keosk installations.

Hope this helps.
Good Luck....

---

### Post by az on 2006-10-25
> **brightmatter said:**
> After a bit, the desktop is available.  I assume I need to install it so I right click open and select open.  The CD goes nuts searching and possibly copying files.  I waited for 3 hours and it never stopped the CD ROM, not once.  

You do not have enough ram.  It is trying to fit everything into memory but is having a hard time, hence the continued disk activity.

Things you can do are to create and activate a swap partition before you start the installer and avoid selecting an other language than engligh - chosing another language loads a whole bunch of other languages into ram....  You can always add more ram.  

As stated, you need 256 megs to install Ubuntu using the live cd.  You can use the alternate cd to install with less, but you will be frustrated at the performance without enough ram.

---

### Post by barkej on 2006-10-25
You might want to give the alternate install disc a try.  I have an older gateway and the alternate install works like a charm.

BTW if you have very little ram you might want to check out Xubuntu.

---

### Post by brash on 2006-10-25
As far as I can tell from Google, most of the Compaq Presario 2100 laptops sold in the USA come with 512MB ram, and either an Athlon XP 2200 or Celeron 2.4G cpu, which should be plenty. See [http://gentoo-wiki.com/HARDWARE_Compaq_Presario_2100](http://gentoo-wiki.com/HARDWARE_Compaq_Presario_2100). 

So unless your system is different from the ones on that page, I don't think the problem is that the hardware is "too old" or not enough ram.

Make sure as said that you use the Install icon located on the desktop itself?

---

### Post by brightmatter on 2006-10-25
Yep... 1.6GHz CPU and 192Mb RAM

I will try the alternate install CD.  Thank you everyone who helped me with this problem.=D>

---

### Post by DarkN00b on 2006-10-26
> **brightmatter said:**
> Yep... 1.6GHz CPU and 192Mb RAM

I will try the alternate install CD.  Thank you everyone who helped me with this problem.=D>

You shouldn't have any problems installing with the alternate CD, but if you try to run the default Gnome desktop with that ram, expect to see your HD run practically nonstop. There are other GUIs that you could use though, like XFCE (the XUbuntu GUI) or IceWM are good choices.

---

