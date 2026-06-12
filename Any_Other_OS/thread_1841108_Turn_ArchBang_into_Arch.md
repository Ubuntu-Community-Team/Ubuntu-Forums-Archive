---
title: "Turn ArchBang into Arch"
date: 2011-09-08
forum: Any Other OS
---

### Post by Dlambert on 2011-09-08
Hello, my only internet connection comes via 3g modem, and everytime I try to install Arch, I get to the screen and have no clue from there (no internet). Anyways, So I installed ArchBang. My laptop is up and running it, and I was wondering what do I have to do to this Arch Bang install to turn it into solid Arch. And install xfce or Gnome on top, I really like the arch philosophy and I would love for someone to help me with this. Thanks

---

### Post by mips on 2011-09-08
> **Dlambert said:**
> ...**and I was wondering what do I have to do to this Arch Bang install to turn it into solid Arch**. And install xfce or Gnome on top, I really like the arch philosophy and I would love for someone to help me with this. Thanks

Nothing, it's already Arch except someone else decided on the default packages  & configs for you. Install whatever you want and reference the Arch wiki where needed.

That said you are kinda missing out on the arch philosophy not doing your own thing.

---

### Post by Rumor on 2011-09-09
I sort of agree with MIPS, especially in that "someone else" deciding on the default packages and configs is not the Arch Way.

If you really want to go the Arch Way, I'd suggest you look at your /etc/rc.conf file and see what (if any) modules are being loaded on boot. make a note of the networking section. What values did Archbang use? 

Refer to the Arch wiki page on the rc.conf file and the Beginner's Guide on the networking section. It might not hurt to take a look at your /etc/resolv.conf file and see what values got put there too.

Armed with the proper module for your modem, and a set of networking values you know work, you could then do another Arch install and see if you can get your laptop to connect to the internet.

Good luck!

---

### Post by Dlambert on 2011-09-09
Thanks

---

### Post by 23dornot23d on 2011-09-09
The package manager is [[COLOR=Red]_***pacman***_[/COLOR]]("https://wiki.archlinux.org/index.php/Pacman") ( and another is [[COLOR=Blue]_***yaourt***_[/COLOR]]("https://wiki.archlinux.org/index.php/Yaourt") - )

We will start with pacman - as yaourt was not installed in archbang straight off when I was trying it out .....
 ( let us know what it returns ...... we will try to help if possible )
this should upgrade it below ..... 


[B]pacman -Syu

[/B][I][U]This got it upto the latest kernel and then after that I added desktops and the Nvidia graphics driver for
my machine .......

As said Arch is more to do with learning the system from the base up ..

Archbang gives you a quick leg up though to get a running system ....

[/U][/I]

---

### Post by BrokenKingpin on 2011-09-09
> **mips said:**
> That said you are kinda missing out on the arch philosophy not doing your own thing.
Who cares... saves a lot of time and you end up with a similar result (especially if you like Openbox). You can still do your "own thing" from there... it's not like you are left with a 20 gig install of **** you don't need.

---

### Post by handy on 2011-09-09
> **23dornot23d said:**
> 
...

As said Arch is more to do with learning the system from the base up .. 

Which stands you in good stead when you have to solve a problem because Arch IS different.

> **23dornot23d said:**
> 
Archbang gives you a quick leg up though to get a running system ....


Which many already proficient Arch users may find very helpful if for some reason they happen to be doing multiple installations.

The average Arch user installs once, tweaks their install as they see fit & just keeps on upgrading (often daily) for the following years until their HDD fails.

To the OP, down the bottom of the following linked to page are some how-to's starting with [Arch] they (some more than others) are well worth knowing about:

[http://spiralinear.org/forum/viewforum.php?f=17](http://spiralinear.org/forum/viewforum.php?f=17)

---

### Post by Dlambert on 2011-09-10
Attempting a Net install on my laptop at my moms house. Ill let you guys know!

---

### Post by Dlambert on 2011-09-10
No joy. Waiting for boot device error

---

### Post by handy on 2011-09-10
> **Dlambert said:**
> No joy. Waiting for boot device error

Have you had a good look at the Beginners' Guide?
It may benefit you to identify your system's hardware resources & have a search in the Arch wiki & if you still need to the Arch forums.

It is less of a problem everyday, but still, the major problem that Linux users can strike is having a difficult hardware setup.

---

### Post by mips on 2011-09-10
> **Dlambert said:**
> No joy. Waiting for boot device error

What image are you using and how did you create the boot media/usb?

---

### Post by Dlambert on 2011-09-10
> **mips said:**
> What image are you using and how did you create the boot media/usb?

I tried both, Net and core. And used UnetBootin from Ubuntu. Ext4 and FAT. I have a 4Gig Swap file, and the rest is all ubuntu.

---

### Post by mips on 2011-09-10
> **Dlambert said:**
> I tried both, Net and core. And used UnetBootin from Ubuntu.

Try not to use Unetbootin, it can create problems at times.

Write the image to usb stick using dd.

```
sudo dd if=*name of archlinux.iso* of=/dev/sd[x] 
```

```
sudo fdisk -l
```
Will tell you what to substitute for [x].

---

### Post by Dlambert on 2011-09-10
> **mips said:**
> Try not to use Unetbootin, it can create problems at times.

Write the image to usb stick using dd.

```
sudo dd if=*name of archlinux.iso* of=/dev/sd[x] 
``````
sudo fdisk -l
```Will tell you what to substitute for [x].

Ill try, im upgrading this laptop to 11.10

---

### Post by Dlambert on 2011-09-10
Sweet! its working, so just boot off that? No bootloader required? I'm using the Net-install.

---

### Post by Dlambert on 2011-09-10
The drive still shows up as empty though??

---

### Post by Dlambert on 2011-09-10
isolinux missing error

---

### Post by mips on 2011-09-10
What .iso image file are you using, link?

---

### Post by Dlambert on 2011-09-11
I wrote the iso to SDC1, which didn't write mbr. Anyways, i have arch installed and up and running with Gnome3. Some problems though, some menu items are duplicated. And I still need to install my bcm4312 driver.

---

### Post by mips on 2011-09-11
> **Dlambert said:**
> I wrote the iso to SDC1, which didn't write mbr.

You specified a partition while you should have specified the root device.

```
sudo dd if=name of archlinux.iso of=/dev/sdc
```

---

### Post by Dlambert on 2011-09-11
> **mips said:**
> You specified a partition while you should have specified the root device.

```
sudo dd if=name of archlinux.iso of=/dev/sdc
```

Yeah, i figured that out. Late. Anyways any idea about the menu items? Or the bcm4312, havent looked it up yet. (only on ipod)

---

### Post by mips on 2011-09-11
[https://wiki.archlinux.org/index.php/Broadcom_wireless](https://wiki.archlinux.org/index.php/Broadcom_wireless)

I dunno how they generate the menu in Archbang. Have a look at,
[https://wiki.archlinux.org/index.php/Openbox#Manual_configuration_of_menus](https://wiki.archlinux.org/index.php/Openbox#Manual_configuration_of_menus)
[https://wiki.archlinux.org/index.php/Openbox#Obmenu](https://wiki.archlinux.org/index.php/Openbox#Obmenu)

---

### Post by Dlambert on 2011-09-11
No no. I installed pure arch, using the netinstall. I configured it all, but then i noticed the application menu is messed up(doubles). I am not using archbang, I have installed Archlinux, and configured it.

---

### Post by mips on 2011-09-11
Sorry.

Suggest you google and check the arch forums, someone else is bound to have experienced the same problem.

---

### Post by Dlambert on 2011-09-11
I cant get the building of the wireless driver. None of the dirrections are working...

---

### Post by Dlambert on 2011-09-12
I gave up, I will install Arch when I have a laptop that doesn't require proprietary wireless drivers. Now I'm back to getting Ubuntu as close to rolling release as possible.

---

### Post by mips on 2011-09-13
> **Dlambert said:**
> I gave up...

I kinda expected that to happen.

Did you install the base-devel stuff before trying to build a package or using AUR?

---

### Post by Dlambert on 2011-09-16
> **mips said:**
> I kinda expected that to happen.

Did you install the base-devel stuff before trying to build a package or using AUR?
Yes..

---

