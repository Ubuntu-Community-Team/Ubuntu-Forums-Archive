---
title: "A new user's praise for Ubuntu ..."
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Eggnog on 2007-06-23
... and I want to praise these forums and their inhabitants while I'm at it.  I apologize in advance for the length of this post, but I just have some things I want to say.

I'm brand new to Ubuntu and Linux, having been steered in this direction recently by some Linux friends (two of whom don't even use Ubuntu) who discovered I had been browsing around DistroWatch and reading up on distros and Linux in general.  I played around with the Ubuntu and Kubuntu live CDs for a few days and then settled on Ubuntu.  While Kubuntu's interface seemed similar enough to Windows for the comfort factor, there was something about GNOME that just appealed to me.  So Ubuntu was installed on a second drive with a dual boot and a shared FAT32 data playground for both.  I used a 35 GB partition for Ubuntu with a 1.1 GB swap partition.  I hope that's enough.

So far I couldn't be happier.  I've had no deal-breaker issues at all.  Any little niggling issues I may have had from time to time (mostly of the Windows-to-Linux transition midset type) were sorted out by visiting these forums, using Search, and reading the fine advice given by the experts to other newbies like me.  It was here I learned about Envy which absolutely fixed some minor video issues I was having early on.  Once I had the proper nvidia drivers in place, which had the happy result of detecting my proper monitor as well, those issues disappeared.  It was here I also learned about the Ubuntu resources at psychocats.net which have proved invaluable.

I do have a few questions, though.

1.  Will I be able to upgrade from Feisty Fawn to the next release without having to do a completely new install of the new release?  How is that normally handled?

2.  Without getting into a KDE vs. GNOME flaming match, I notice more than a few threads here and there regarding people "finally" making the switch from GNOME to KDE.  Is there something going on that I should be aware of?  Was GNOME not the bet choice?

3.  If I decided to install Kubuntu too, for the purposes of learning KDE as well, is a triple boot from GRUB easy enough?  Will the installation detect both XP and Ubuntu and set up the triple boot?  Also, is there an app that allows you to edit GRUB?

4.  If, for some reason, I decided to uninstall Ubuntu is it difficult and will there be any leftover GRUB issues with the MBR?

I can easily see Ubuntu becoming my primary OS once I learn to use it over time, with XP only used for gaming or for those times when I absolutely have to use it for something or another.  Ubuntu seems to be less of a resource hog and appears to be leaner, meaner, faster and more stable.

Okay, I'm done now.  Thanks in advance for any answers to my questions.  Again, I apologize for the length.  ;)

---

### Post by shearn89 on 2007-06-23
Glad you enjoy it! I wiped windowsME of my laptop to install ubuntu, and its the best thing i've ever done!

w.r.t to the questions:
1. Yes, there's a program called Update Manager that automatically detects updates, and when the new release comes out, it can be used to download and install the new version with very little hassle.

2. I'm not sure, i use GNOME and Fluxbox (a lightweight desktop).

3. I think you can just download all the KDE packages using Synaptic (System -> Admin -> Synaptic, then search for KDE), and it will automatically add it to the available "Sessions" when you log in. Just click Actions -> Sessions -> KDE. A kde/gnome user will have to check this for you.

4. Why would you want to uninstall ubuntu? No, joking - i'm not certain. GRUB should still detect your windows install, so it may be that you are just using GRUB to boot windows. 

When i eventually scrape together enough money to buy my own desktop, i'll probs dual boot - windows for ipod and games, ubuntu for the rest. I know you can use cedega and things like that for gaming, but the ipod thing is much easier in windows.

---

### Post by PartisanEntity on 2007-06-23
> **Eggnog said:**
> 

I do have a few questions, though.

1.  Will I be able to upgrade from Feisty Fawn to the next release without having to do a completely new install of the new release?  How is that normally handled?

Yes, you can do an upgrade, new files will be downloaded and installed and you will end up with the new distribution without having to reinstall anything.

> **Eggnog said:**
> 2.  Without getting into a KDE vs. GNOME flaming match, I notice more than a few threads here and there regarding people "finally" making the switch from GNOME to KDE.  Is there something going on that I should be aware of?  Was GNOME not the bet choice?

Best is to try them both out and then you will know which one you like more, opinions differ and IMO it is a matter of taste.

> **Eggnog said:**
> 3.  If I decided to install Kubuntu too, for the purposes of learning KDE as well, is a triple boot from GRUB easy enough?  Will the installation detect both XP and Ubuntu and set up the triple boot?  Also, is there an app that allows you to edit GRUB?

You do not need to triple boot, you could simply install the Kubuntu meta-package which means you will end up with both the Ubuntu and Kubuntu desktop environments. This way you could choose which one to run every time you log into Ubuntu.

> **Eggnog said:**
> 4.  If, for some reason, I decided to uninstall Ubuntu is it difficult and will there be any leftover GRUB issues with the MBR?

Nope, you can delete the entire Ubuntu partition, re-merge it with any other OS you had on there and then repair the original boot loader.

---

### Post by rickycodie on 2007-06-23
about the triple boot there is no need, as stated above you can load kde onto ubuntu, or xfce, of any other desktop manager.

uninstalling ubuntu is as nice and un-ex-girlfriend like as it can be.( i mean two months later you won't be still finding it's crap.)

in my opinion kde is a little more resource heavy, but still by no means window$. i use gnome and always have.  kde is a one click desktop and i don't like that, but try for your self.  when you boot there will be a time when you choose a desktop manager .

---

### Post by shearn89 on 2007-06-23
the only reason KDE seems windows is because the Applications toolbar and the panel (where windows show up) are combined into one, like windows. the rest is totally 'nix.

---

### Post by rickycodie on 2007-06-27
i actually realized that i don't know that much about kde and so i loaded it and tried it. but still i like gnome better. i think that it's easier to navagate in.

---

### Post by Canis familiaris on 2007-06-28
> **Eggnog said:**
> 
I do have a few questions, though.

1.  Will I be able to upgrade from Feisty Fawn to the next release without having to do a completely new install of the new release?  How is that normally handled?

2.  Without getting into a KDE vs. GNOME flaming match, I notice more than a few threads here and there regarding people "finally" making the switch from GNOME to KDE.  Is there something going on that I should be aware of?  Was GNOME not the bet choice?

3.  If I decided to install Kubuntu too, for the purposes of learning KDE as well, is a triple boot from GRUB easy enough?  Will the installation detect both XP and Ubuntu and set up the triple boot?  Also, is there an app that allows you to edit GRUB?

4.  If, for some reason, I decided to uninstall Ubuntu is it difficult and will there be any leftover GRUB issues with the MBR?

(1) Yes you can.
(2) I think both are Good, but GNOME is better supported in *buntu, though KDE's great as well.
(3) You can install KDE as triple boot. I dunno it will overwrite your grub, but just in case backup your /boot/menu/grub/menu.lst in your fat32 drive and cut paste the Ubuntu kernels.
Note You do not really need to triple boot. Both Ubuntu and Kubuntu are just the same using different dektop enviroments. Just install kubuntu-desktop package by:
```
sudo aptitude install kubuntu-desktop
```
abd change from GNOME to KDE by logging out and changing from GNOME to KDE in your session manager.
(4) If you just remove Ubuntu without off loading GRUB from MBR, then you'll be unable to boot into Windows. You have to first uninstall GRUB.
 Download the [Super GRUB Disk]("http://supergrub.forjamari.linex.org/") ISO, burn it to a CD. This is a bootable CD. You can navigate and remove GRUB.
You can also remove GRUB by fixboot command in Windows recovery console in its install cd.

You can also use Super GRUB to restore your GRUB.

Just in case!

---

