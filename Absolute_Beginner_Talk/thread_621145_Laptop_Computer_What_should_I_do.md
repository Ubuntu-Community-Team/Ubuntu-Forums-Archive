---
title: "Laptop Computer: What should I do?"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Jurandyr on 2007-11-23
I have a tampered Compaq Evo n1020 notebook (I changed the HD from 40GB to 80GB and increased the RAM from 256 to 768MB) and I was told that Ubuntu has some problems with laptop computers. Being a complete newbie and wanting to dual-boot with XP, should I install Gutsy or wait for the more stable LTS release in april?

Also, which is better, Ubuntu or Kubuntu? I heard Kubuntu is behind on features, so if I want to use KDE is it better to install KDE on Ubuntu instead of just installing Ubuntu? o.õ

I fount on [this thread]():
> **nicors said:**
> Compaq Evo n1020: This laptop has many problems with Ubuntu power management. Maybe the problem is the chipset. The non-intel chipset (i'm not sure if was an ATI...) prevented to work corectly the power management. 

Compaq Evo n800: My current laptop. All works perfect. The only thing that I'm not sure if works is onborad modem becouse I don't use it. The only main difference with evo1020 is the chipset. 

But it's a post from February 2006, and there have been three releases since then. Was that problem fixed?

Oh, also my CDROM drive is kind of busted - if I try putting in a CD after the computer has been running for enough time to get hot, it won't read and when it's cool it reads slowly. Can I, like, extract the ISO to a 1GB flash drive and use that via USB? I don't think my BIOS allows it.

---

### Post by jken146 on 2007-11-23
LTS (Long Term Support) does not mean stable.  It means that updates will be released until a later date than if you installed a non-LTS version.  MY advice is to install Gutsy because it has the most up-to-date hardware compatibility (important for laptop users).  Dapper (6.06 LTS) is very old now.

---

### Post by jken146 on 2007-11-23
Also, I should say that KDE can easily be installed on Ubuntu and Gnome can easily be installed in Kubuntu.  It really doesn't matter which *buntu you pick to install if you're going to install another window manager.  You can choose which to use at the login screen.

---

### Post by bluepowder7 on 2007-11-23
if you still have that old 40G drive kicking around, i'd try to install that back in and do a full install of Gutsy on it (let it format the entire drive and use it however it wants to).  that way, you can check functionality of all that Gutsy currently has without affecting your WinXP installation (which presumably is on that 80G drive you're gonna remove and safely store for a few days or weeks).

then, if you're satisfied with how Gutsy is working, swap hard drives back so that the 80G is in the laptop, and do the Gutsy installation on that.  you'll have to be careful when it comes time to partitioning the drive, but Gutsy will recognize that WinXP is on there when it comes time to setting up your boot options.

---

### Post by steveneddy on 2007-11-23
> **jken146 said:**
> LTS (Long Term Support) does not mean stable.  It means that updates will be released until a later date than if you installed a non-LTS version.  MY advice is to install Gutsy because it has the most up-to-date hardware compatibility (important for laptop users).  Dapper (6.06 LTS) is very old now.

I agree. Laptop support is greatly improved with the Gutsy release.

Try a Live CD first to see how much of your hardware is recognized.

Intel wireless chips and nVidia video cards are better supported by the community and the vendor than other types of hardware.

---

### Post by Jurandyr on 2007-11-23
> **jken146 said:**
> LTS (Long Term Support) does not mean stable.  It means that updates will be released until a later date than if you installed a non-LTS version.  MY advice is to install Gutsy because it has the most up-to-date hardware compatibility (important for laptop users).  Dapper (6.06 LTS) is very old now.

I don't mean using Dapper, I mean waiting for Hovering Hummingbird, or Hardy Heron, or whatever. Ubuntu 8.04 if there are no delays.

> **bluepowder7 said:**
> if you still have that old 40G drive kicking around, i'd try to install that back in and do a full install of Gutsy on it (let it format the entire drive and use it however it wants to).  that way, you can check functionality of all that Gutsy currently has without affecting your WinXP installation (which presumably is on that 80G drive you're gonna remove and safely store for a few days or weeks).

then, if you're satisfied with how Gutsy is working, swap hard drives back so that the 80G is in the laptop, and do the Gutsy installation on that.  you'll have to be careful when it comes time to partitioning the drive, but Gutsy will recognize that WinXP is on there when it comes time to setting up your boot options.

I don't have the knowledge or the tools to do that to a notebook computer - I'd have to pay someone. But thanks for the suggestion. Maybe someone will let me do that to their PC for the sake of testing.

> **steveneddy said:**
> I agree. Laptop support is greatly improved with the Gutsy release.

Try a Live CD first to see how much of your hardware is recognized.

Intel wireless chips and nVidia video cards are better supported by the community and the vendor than other types of hardware.

Thel LiveCD recognized everything except my PS/2 mouse (it used the laptop's touchpad instead). I don't have wireless. My video card is an ATI Radeon IGP 340M. The LiveCD ran very slow, presumably because my CD drive is halfway busted.

Should I be worried about this: [https://bugs.launchpad.net/ubuntu/+bug/104535](https://bugs.launchpad.net/ubuntu/+bug/104535)

> **Jurandyr said:**
> Oh, also my CDROM drive is kind of busted - if I try putting in a CD after the computer has been running for enough time to get hot, it won't read and when it's cool it reads slowly. Can I, like, extract the ISO to a 1GB flash drive and use that via USB? I don't think my BIOS allows it.

This issue was not addressed - is there really no other way to install Ubuntu?

---

### Post by mivo on 2007-11-23
Kubuntu is basically Ubuntu minus Gnome plus KDE. They use the same underlaying core system and the same package sources. Kubuntu just comes with KDE "pre-installed" and is neatly "tweaked" and customized. I currently use KDE (vanilla) and actually start to prefer it over Gnome, though it's mostly because of the better software integration (Gnome is less busy, and cleaner), but that is really just a matter of preference. If you do mean to use KDE, just go with Kubuntu. It'll save you some time, and most of what you read here applies to all Ubuntu versions (and frequently to may Linux flavours).

Try the Live CD. It is risk-free.  (Just keep in mind that it is slower and less responsive than a real HD installation.)

---

### Post by bluepowder7 on 2007-11-23
> **Jurandyr said:**
> 

I don't have the knowledge or the tools to do that to a notebook computer - I'd have to pay someone. But thanks for the suggestion. Maybe someone will let me do that to their PC for the sake of testing.

it's probably easier than on a desktop.  the hard drive probably comes out either through an access panel, or as a unit with its own "caddy".  a few screws should get you access to it.  it's surprisingly easy once you try it, but if you're nervous then don't sweat it TOO much.


> **Jurandyr said:**
> 

This issue was not addressed - is there really no other way to install Ubuntu?

i think there was a method.  this same topic came up in another recent thread, and someone posted a blip about how to do it (or at least how to do it in windows).

here, this thread.  [http://ubuntuforums.org/showthread.php?t=618881](http://ubuntuforums.org/showthread.php?t=618881)  somewhere near the end i think...

---

### Post by Jurandyr on 2007-11-24
Thanks, bluepowder7! The thread you linked to linked to this howto here: [http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)

It looks easy enough and I have 2Mbit internet, so I'll try that as soon as I can.

Last question: Should I partition during the installation or should I use the GParted LiveCD? Remembering that my drive is not in prime condition.

---

### Post by candtalan on 2007-11-24
> **Jurandyr said:**
> Thanks, bluepowder7! The thread you linked to linked to this howto here: [http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)
It looks easy enough and I have 2Mbit internet, so I'll try that as soon as I can.

Last question: Should I partition during the installation or should I use the GParted LiveCD? Remembering that my drive is not in prime condition.

If you do not trust your cd drive you certainly should not use it for any serious install and certainly not partitioning, you may loose all -that is  *all* - of your data!

Maybe the cd drive can be improved by cleaning?

you can re-size your windows partition using windows built in facility I think. the resulting unpartitioned space on the hard drive can be picked up almost automatically during the 7.10 gutsy install. Back up your windows data first anyway!

---

### Post by mivo on 2007-11-24
It doesn't matter, really, but I would use GParted because it's a little easier to use.

---

