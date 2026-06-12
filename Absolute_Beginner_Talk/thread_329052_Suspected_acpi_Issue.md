---
title: "Suspected acpi Issue"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by tmptplayer on 2006-12-31
I am trying to install Ubuntu onto an HP a1540n (AMD 4200+ X2, GeForce 6150, 2GB RAM) with the default HP vs17e monitor.  I first tried to install Fedora 6.0 and I needed to turn acpi off to get through the installation.  That eventually did not work out because it booted in a video format that my monitor could not handle, so I switched to Ubuntu (v 6.10).  As I'm trying to install Ubuntu, it stalls and I think it is because of ACPI.  I do not know how to turn it off.  When I put in the boot CD (both alternate and normal) I see no command prompt to enter 'acpi=off' as was suggested in the sticky post, just a text menu from which I choose.

If you do not believe acpi is the problem, when I tried to do the text mode installation from the alternate CD the screen froze after it acknowledged my Logitec Mouse.  In the normal installation I just had an Ubuntu logo across the screen that never went away.

Thanks!

---

### Post by tmptplayer on 2007-01-01
For anyone who cares... I went back to the Dapper release, and it booted through the install and crashed with an error saying it isn't able to access my file system.

I then went to Herd1 for Feisty, and booted and installed fine.

---

### Post by Zer0Nin3r on 2007-01-02
> **tmptplayer said:**
> I am trying to install Ubuntu onto an HP a1540n (AMD 4200+ X2, GeForce 6150, 2GB RAM) with the default HP vs17e monitor.  I first tried to install Fedora 6.0 and I needed to turn acpi off to get through the installation.  That eventually did not work out because it booted in a video format that my monitor could not handle, so I switched to Ubuntu (v 6.10).  As I'm trying to install Ubuntu, it stalls and I think it is because of ACPI.  I do not know how to turn it off.  When I put in the boot CD (both alternate and normal) I see no command prompt to enter 'acpi=off' as was suggested in the sticky post, just a text menu from which I choose.

If you do not believe acpi is the problem, when I tried to do the text mode installation from the alternate CD the screen froze after it acknowledged my Logitec Mouse.  In the normal installation I just had an Ubuntu logo across the screen that never went away.

Thanks!
If you're still tyring to install the newer version of Ubuntu, you can hit 'Esc' to get to the console.  From there you can specify your commands.  I was having similar proglems in which I have to use the command 'noapic' to keep from hanging up.  From there I run into graphical problems.  (All garbled looking...)

---

### Post by yandros on 2007-03-07
I have the same issue and computer.  I installed a second drive and Ubuntu finally installed fine on it.  I tried to upgrade to fedora6 core and it completely crashed my grub.  Now I've got no way to boot at all.  I can get into a rescue mode on fedora but there's NO grub config files at all.  Ubuntu set them up perfectly... I'm gonna try rescue mode on ubuntu but I'll probably end up wiping that partition.

THIS SUX... why can't grub be easier?

---

### Post by yandros on 2007-03-07
ok I'm in ubuntu rescue mode... only device listed is /dev/null

lol

device.map has 
(fd0) /dev/floppy

WTF.... how do I probe my damn devices?

---

### Post by yandros on 2007-03-07
UBUNTU will not install graphically... and therefore doesn't install gnome and all the other crap... at least grub works fine but I can only get command line interface.

any suggestions... no help on the cd
 :/

---

