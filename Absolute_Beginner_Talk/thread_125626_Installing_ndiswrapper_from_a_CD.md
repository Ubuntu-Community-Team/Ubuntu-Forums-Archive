---
title: "Installing ndiswrapper from a CD?"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by Danni on 2006-02-04
Hi there :)

I'm a complete newbie to Ubuntu, but want to give it a shot. Apart from my wireless card, everything I've plugged in has worked great, so I'm sure that it's the distro for me. Since my card has the broadcom chipset on it, I've read the howto, but come across a problem- I don't have a wired backup. 

I've got the relevent driver (someone else posted the correct driver for my card- apparently the bcmwl5a.inf works, the bcmwl5.inf doesn't) and I've got ndiswrapper-1.8.tar.gz on my CD. How do I install from the CD? I really don't want to be lugging my computer around if I don't have to :)

Thanks,
Danni

---

### Post by evilmrt on 2006-02-04
yeah, I need some help with this as well. I've been copying files over from windows, then rebooting everytime I need to download something else...there must be more people without a wired connection to fall back on? I have a Belkin F5D7001, and cant get it to work properly for anything...

---

### Post by evilmrt on 2006-02-04
just occurred to me...you know what would help? binaries!! this compiling from source crap is whats creating the headaches...I see many of the other distros have ndiswrapper binaries available...but not us...:( whats the reason for that?

---

### Post by nuzzy on 2006-02-04
do a "cp /mnt/cdrom/ndiswrapper-1.8.tar.gz ~" (or whatever path to the .gz file is) and then follow [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")

---

### Post by az on 2006-02-04
[QUOTE=evilmrt]just occurred to me...you know what would help? binaries!! this compiling from source crap is whats creating the headaches...I see many of the other distros have ndiswrapper binaries available...but not us...:( whats the reason for that?[/QUOTE]
ndiswrapper is in the kernel.  You just need to install ndiswrapper-utils.  Use synaptic.  It's on the install cd, so you don't have to go on the net.

You should try with the stock ndiswrapper.  To compile a more recent version may not be neccessary if you have the most recent .inf file (the correct one)

If you really need to compile something for your kernel, you need to install build-essential and gcc-3.4.  Unfortunately, gcc-3.4 is not the version of the compiler that everything else in ubuntu is built with, so it is not on the cd.

You need to download gcc-3.4, gcc-common and cpp-3.4 as well.

sudo dpkg -i *.deb
to install the packages you downloaded.

Seriously, try the ndiswrapper that ships with ubuntu before compiling a newer version.  You have been able to use broadcom chipsets in ndiswrapper for ages.

---

### Post by evilmrt on 2006-02-04
ok, will try! thanks mr. shatner

---

### Post by Danni on 2006-02-05
Ahh... I'll do that :)

(and that's the exact card I have too, if you add uk on the end :p)

---

### Post by Danni on 2006-02-05
Since I'm posting from Ubuntu I can say it worked :)

Thank you very much :)

---

### Post by az on 2006-02-05
W00t!

---

