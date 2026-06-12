---
title: "Ubuntu to Kubuntu"
date: 2005-07-18
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-07-18
Got a full CD installation for Kubuntu. I want to change and see, but currently I have way too much time invested in Ubuntu to scrap it. Will I loose my Ubuntu settings, files and programs when I change?

If I understand correctly, only the desktop change bewteen the two, the rest stay the same, but I am not willing to take my chance.

Else I will have to dual boot, but have only one 40G hard drive dedicated to Linux. I think the correct way would be to add a third, say 10G, partition to the existing two and make it bootable. But now where I am unsure, when you originally partition for Ubuntu, you actually create two partitions. One big one, bootable and one swap partition. (I choose defaults.) I don't mind sharing a HDD between two versions of Linux cause all files should be accessable between the two. 

BUT. Come to booting. I have XP and Ubuntu currently. What will happen if Kubuntu swipes the Ubuntu away, cause my MBR sits with Ubuntu, thus I'm worried that XP will "dissapear."

---

### Post by sal on 2005-07-18
just do this:

apt-get install kubuntu desktop

it will install the kubuntu so that way you can log into ether gnome (ubuntu) or KDE (kubuntu). at a point in the install it will ask you wich display manager you want to use.
it will ask gdm (gnome display manager) or kdm (K display manager).

---

### Post by GrootBrak on 2005-07-18
[QUOTE=sal]just do this:

apt-get install kubuntu desktop

it will install the kubuntu so that way you can log into ether gnome (ubuntu) or KDE (kubuntu). at a point in the install it will ask you wich display manager you want to use.
it will ask gdm (gnome display manager) or kdm (K display manager).[/QUOTE]
 I'm not with you on this. I have the installation on disk. Will it work with apt-get.

---

### Post by damonw5 on 2005-07-18
[QUOTE=GrootBrak]I'm not with you on this. I have the installation on disk. Will it work with apt-get.[/QUOTE]
 You can add the CD as a repository in Synaptic. Then install "kubuntu-desktop." Your Ubuntu system will still be there, and your MBR will stay the same. When you login, when you click "sessions" you will have the option of booting into KDE as well as the option of booting into GNOME. That's the only difference. 
If you want to make it easier to uninstall, though, you might want to resize your Ubuntu partition and create a new partition for Kubuntu. They can share the same swap partition, I believe.

The first way won't touch your MBR. The second way will add another item or two to the GRUB boot menu. Either way XP won't disappear.

---

### Post by davidgypsy on 2005-07-18
[QUOTE=GrootBrak]I'm not with you on this. I have the installation on disk. Will it work with apt-get.[/QUOTE]

I tried this already, and ended up going back to Ubuntu/Gnome because of severe stability problems with Konqueror in KDE. In was basically unusable. :???: No apparent reason or fix for it. Apparently even upgrading to KDE 3.4.1 doesn't help. 

And Kynaptic is hopeless compared with Synaptic. I wonder why the powers that be don't just put Synaptic into Kubuntu instead... :-\"and fix the stability problem...:-\"

Ubuntu rocks! :)

---

### Post by GrootBrak on 2005-07-19
[QUOTE=davidgypsy]I tried this already, and ended up going back to Ubuntu/Gnome because of severe stability problems with Konqueror in KDE. In was basically unusable. :???: No apparent reason or fix for it. Apparently even upgrading to KDE 3.4.1 doesn't help. 

And Kynaptic is hopeless compared with Synaptic. I wonder why the powers that be don't just put Synaptic into Kubuntu instead... :-\"and fix the stability problem...:-\"

Ubuntu rocks! :)[/QUOTE]
 Thanx Will consider it. I can't even get Conquerer to open in Ubuntu.

---

### Post by wvslkr on 2005-07-19
My 2 cents. I run both and have not had any stability problems with either DE.  Also use XFCE occasionaly, depending on my mood.  Will agree Synaptic is much better than Kynaptic.  I started with Kubuntu and did have some problems with it.  When my CD's arrived I reinstalled with Ubuntu and added Kubuntu desktop via synaptic.  All rock solid from there.

May have to install something else soon, nothing to fix here.

Cheers. :)

---

### Post by Lord Illidan on 2005-07-19
I use Kubuntu with Synaptic...it is much, much better than Kynaptic...

Stability issues, yes, even when closing an app in KDE, it pops up a message saying that it has crashed...
I think I will go back to Gnome...

---

### Post by GrootBrak on 2005-07-19
Thanx folks. I've heard enough already. Will install from Synaptic and try it out. The main reason for trying is that soooooo many new apps won't even start in Ubuntu. Some I've figured out only run in a terminal. Most KDE games however open with no problems. But that is going to be a new thread. 

The mods can close this one for me as far as I'm concerned.

---

