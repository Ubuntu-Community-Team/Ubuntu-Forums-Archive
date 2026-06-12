---
title: "Can't boot into Ubuntu AT ALL after uninstalling KDE"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by mikecomua on 2007-08-20
Hello, I have originally installed Ubuntu Feisty on my computer but then decided to try KDE, so I typed in[PHP]sudo aptitude install kubuntu-desktop[/PHP]. Then I booted KDE OK, and worked with it for a few days. Afterwards, when I wanted to boot into Gnome Mac OS icons show up on the boot screen (I installed the theme) and I see taskbars with no icons.
Then I uninstalled and installed Gnome, but nothing worked. I posted my question on Ubuntu forums [http://ubuntuforums.org/showthread.php?t=529537]("http://ubuntuforums.org/showthread.php?t=529537") So I uninstalled KDE using Konsole and it said something about two packages not being uninstalled and it asked if it should continue and i said yes. So I entered Gnome from the  sessions menu, but there were the same empty taskbars.
By the way I downloaded a GRUB splash screen from KDE-look.org 
[http://kde-look.org/content/show.php/Ubuntu+7.04+Grub+Bootscreen?content=57961]("http://kde-look.org/content/show.php/Ubuntu+7.04+Grub+Bootscreen?content=57961")
Then I rebooted, Grub showed up, I selected Ubuntu, it loaded and then a black screen shows up with this[
PHP]/etc/init.d/rc:2:usplash_write: permission denied
/etc/init.d/rc:2:/etc/rcS.d/S85 u random: Permission denied
/etc/init.d/rc:2:usplash_write: permission denied
init:Unable to execute "/bin/sh" for rc-default: Permission denied
init:rc-default main process 4221 terminated with status 255[PHP]
;cry:
P.S. If my Ubuntu install is dead will I be able to safely format my Ubuntu partition and reinstall Ubuntu?
P.P.S. This was typed using a Ubuntu  LiveCD

---

### Post by A3sthetix on 2007-08-21
> If my Ubuntu install is dead will I be able to safely format my Ubuntu partition and reinstall Ubuntu?

Yes. Just make sure you use the correct settings in your partition manager when reinstalling.

I don't know if you have a dual-boot with Windows, but you should run a "chkdsk". I have gotten something similar when running Ubuntu 7.04 and running.

If you are not running a dual-boot... it appears the GUI files are corrupt or unavailable. You might need to reinstall -- hopefully someone more knowledgeable can help you out.

---

