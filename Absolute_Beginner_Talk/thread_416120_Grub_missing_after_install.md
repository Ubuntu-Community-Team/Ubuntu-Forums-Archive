---
title: "Grub missing after install"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by SpongeBob SquarePants on 2007-04-20
Evening all,

I've just built myself a new system.......ASUS M2N2-SLI, AMD 64 bit dual core, 2 GB RAM.......etc. Anyway, after the usual acpi crap with edgy, I decided to revert baclk to Dapper till my Feisty DVD arrives. Everything went fine during the install. The only problem i had when it came to restarting my system, for some reason Grub's not there and it just boots straight into XP again.

I repeated the install process, just in case something had gone wromng somewhere along the line. Again, the install was quick and efficient. But after restarting, no GRUB again.

Any ideas?


Kind regards...mel

---

### Post by ajmorris on 2007-04-20
> **SpongeBob SquarePants said:**
> Evening all,

I've just built myself a new system.......ASUS M2N2-SLI, AMD 64 bit dual core, 2 GB RAM.......etc. Anyway, after the usual acpi crap with edgy, I decided to revert baclk to Dapper till my Feisty DVD arrives. Everything went fine during the install. The only problem i had when it came to restarting my system, for some reason Grub's not there and it just boots straight into XP again.

I repeated the install process, just in case something had gone wromng somewhere along the line. Again, the install was quick and efficient. But after restarting, no GRUB again.

Any ideas?


Kind regards...mel

did you re-install grub to ur primary hard disk/ primary hard disk for MBR? Do you have 2 linux partitions?

---

### Post by SpongeBob SquarePants on 2007-04-20
> **ajmorris said:**
> did you re-install grub to ur primary hard disk? Do you have 2 linux partitions?

I have one primary partition that has XP in it, then a swap for Linux, then an ext 3 root partition for Kubuntu. As for installing grub in my primary partition, I don't think you get the option of where to install it with Dapper do you? I thought that by default it just installs it in mbr?!?

---

### Post by ajmorris on 2007-04-20
> **SpongeBob SquarePants said:**
> I have one primary partition that has XP in it, then a swap for Linux, then an ext 3 root partition for Kubuntu. As for installing grub in my primary partition, I don't think you get the option of where to install it with Dapper do you? I thought that by default it just installs it in mbr?!?

did you install it with the 'grub' command line. or with grub-install ?

---

### Post by SpongeBob SquarePants on 2007-04-20
> **ajmorris said:**
> did you install it with the 'grub' command line. or with grub-install ?

Sorry.....I'm not sure what those things even are. I ran the live distro, double clicked install and then used the GUIi. There was no option as to where to install GRUB that I can recall. Usually it just installs GRUB to the mbr and everything runs fine. Something about my new system isn't allowing that this time around however.

---

### Post by ajmorris on 2007-04-20
> **SpongeBob SquarePants said:**
> Sorry.....I'm not sure what those things even are. I ran the live distro, double clicked install and then used the GUIi. There was no option as to where to install GRUB that I can recall. Usually it just installs GRUB to the mbr and everything runs fine. Something about my new system isn't allowing that this time around however.

Oh, i am really sorry... i misread your post. I thought it said your re-installed grub not the distro. Unfortunately, this is going to require some command line use to fix.
Go into a Terminal (Applications >> Accessories >> Terminal) and type sudo grub. If this returns with an output saying "no command found" then boot into the live cd of ubuntu, and then come back and post here and i will tell you what to write.

---

### Post by SpongeBob SquarePants on 2007-04-21
> **ajmorris said:**
> Go into a Terminal (Applications >> Accessories >> Terminal) and type sudo grub. If this returns with an output saying "no command found" then boot into the live cd of ubuntu, and then come back and post here and i will tell you what to write.

Thanks AJ. I presume you mean type "sudo grub" from within the Live CD, since at the moment I can't access my ubuntu partition because of the GRUB problem. Anyway, the return is.......

"GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>"

---

### Post by SpongeBob SquarePants on 2007-04-21
Ah it's ok...I got it sorted. Don't ask me how, it was purely by accident...lol.

---

### Post by Anagonda on 2007-04-21
So what did you do? I changed the motherboard on my girlfriends pc. I thought now it is a good time to upgrade edgy to feisty with clean install.

Install went fine, but I after reboot I got an error 15 on grub. Booted with livecd, mounted system and under /boot there isn't any grub folder.
I tried to download the cd again from different mirror, no help, tried to burn with differend speed, no help. After that I tried to install it with feisty beta cd, that previously worked. Not anymore. I can run grub from livecd(ofcourse), but when I try to setup it on hd it says no files found, error 15. Nice...

---

### Post by SpongeBob SquarePants on 2007-04-21
Hi there,

I didn't say how I'd solved the problem because I'm not sure what I did or why it worked.

Basically, I installed Ubuntu twice and there was no GRUB. So I installed Simply Mepis, just to see if the problem was Ubuntu specific. Mepis installed GRUB, but the paths to Mepis and XP were wrong. I kept getting the error 22 message for both. So I tried installing Dapper again, and for some reason this time GRUB appeared, although the paths were wrong again to both XP and Ubuntu and I got error 22's no matter what option I chose.

So through trial and error I manually edited the pathways to both Ubuntu and XP until I could boot into both and then changed them in the /etc/resolv.conf file.

Problem solved...but I'm not sure why. Sorry if that doesn't help much.

---

