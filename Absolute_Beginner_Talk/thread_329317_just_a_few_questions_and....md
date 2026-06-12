---
title: "just a few questions and..."
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by squeedps on 2007-01-01
I just want to say thanks to the people that work on Ubuntu.  It's been an interesting experience so far.  I had a flawless install on a dual-boot.  The disc I got my hands on had 5.10 on it but I quickly found the upgrade procedure to 6.06.  I was up, running and upgraded in just a little over an hour.  Something I never expected to happen given my experience with WinXP.  8 hours+ is my typical fresh install time for that.


Ok.  Since I said I was asking some questions, that's what i'm going to do.

1. On the GRUB loader, there is 3 versions of the kernel listed.  I know that has to do with giving yourself the ability to go back in case something is wrong with the most recent one.  Since I know that the 6.06 version is working, is there a way to clear out the other two?

2. I am an avid Firefox/Mozilla fan.  I broke away from IE a long time ago and haven't looked back since.  I see that the installer loaded 1.5.0.8 but i would like to upgrade to 2.0.0.1.  I searched in the Synaptic Package Manager but I can't find anything in there.  What is another method I can go about upgrading to this?



So far, this is all I can come up with.  I know there is more but right now I'm just playing around with the web.



Shaun (squee)

---

### Post by bruenig on 2007-01-01
Paste your /boot/grub/menu.lst in here.

---

### Post by squeedps on 2007-01-01
had to scroll down a bit, but this is what i have.  oh, and i did just think of another question. i have an amd64 and would like to use the 64-bit version of ubuntu.  is there some way i can change over from the 386 version without a disc.  i don't have a burner on my system to make a new one.

> title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.12-10-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


---

### Post by riven0 on 2007-01-01
You may want to look at [this howto for Firefox]("http://www.ubuntuforums.org/showthread.php?t=325565&highlight=upgrading+firefox"). Not exactly an upgrade, but it gives you the ability to use 2.0.0.1 in place of your current version.

Edgy, however, already has Firefox 2.0 as default.

---

### Post by bollix47 on 2007-01-01
1.  You can search synaptic for your old kernel version and mark them for removal.

2.  You could use the method [here]("https://help.ubuntu.com/community/FirefoxNewVersion").

      or

      You could upgrade to Ubuntu 6.10 where Fx 2 is the default.

      or 


      You could download [Automatix]("http://www.ubuntuforums.org/showthread.php?t=177646") and install Fx 2 that way.

---

### Post by meng on 2007-01-01
You can delete the sections associated with older kernel versions (or just comment out the lines by placing # at the beginning). If you want to go further, you can actually remove the older kernels themselves:
e.g. to get rid of /boot/vmlinuz-2.6.12-10-386
go to terminal and type
sudo rm /boot/vmlinuz-2.6.12-10-386

---

### Post by Sklasko on 2007-01-01
A word of warning: This may or may not be a common problem with FF2.0 but when I upgraded my Java failed to work and Flash experienced problems. I've stuck with the 1.5x line since. Works fine, no plans to upgrade.

---

### Post by Tomosaur on 2007-01-01
You can delete the old kernels, or you can just edit the GRUB menu to hide them. I prefer the second method, you never known when you need a fallback :)

Take a look at the link in my sig.

If you want to delete the old versions, you need to open up a terminal and then delete the kernels you don't want any more. They're in /boot and have the naming format 'vmlinuz-<version>'.

---

### Post by squeedps on 2007-01-01
thanks for the quick help.  i'll keep the second newest one but get rid of the third.  no point in keeping 3 versions of the kernel.

i've seen some posts on people having problems with Edgy and for right now, i'll stick with Dapper.

I posted earlier but it may have gotten overlooked, but is there a way to switch to 64-bit without a live disc?  i don't have a burner handy and would like to use the best possible with my amd64.

---

