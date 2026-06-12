---
title: "Help! Can't boot"
date: 2008-06-04
forum: Apple Hardware Users
---

### Post by Scientia on 2008-06-04
Help! i'm running a PPC iBook 700mhz, and had problems with display brightness keys and suspend. I edited my yaboot.conf and xorg.conf following these, [http://ubuntuforums.org/showthread.php?t=798974](http://ubuntuforums.org/showthread.php?t=798974) 
```
image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="nosplash [COLOR="Red"]video=radeonfb:1024x768-24@60[/COLOR]"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="nosplash [COLOR="Red"]video=radeonfb:1024x768-24@60[/COLOR]"
```

and [http://ubuntuforums.org/showthread.php?t=802528](http://ubuntuforums.org/showthread.php?t=802528) (mchladek's post)
When i restarted, it showed stuff until after the ubuntu loading strip, and then just a blank screen. Any way to revert back to what i had before the xorg.conf changes, or is installing from the cd the only way?

Help! Thanks

---

### Post by wdaniels on 2008-06-04
What did you use to edit xorg.conf? If you did it with gedit then (by default) it would make a backup called xorg.conf~. Editing it by certain other methods also creates a backup - just take a look in /etc/X11 and see what you've got. Otherwise, you could reconfigure X manually using:

```
sudo dpkg-reconfigure xserver-xorg
```

Also, since xorg 7.2, apparently if you just delete the xorg.conf file:

```
sudo rm /etc/X11/xorg.conf
```

...then restart X (Ctrl-Backspace) it should regenerate a new one as per the defaults.

---

### Post by Scientia on 2008-06-04
I can't boot up the system properly, all i get is a blank screen(black), but i can hear the computer running. Is it possible to do the above from the startup boot menus or using the install cd?

I'm seriously screwed. All help welcome.

Thanks

---

### Post by wdaniels on 2008-06-04
Yes, if you press Ctrl-Alt-F2 (when you have the blank screen) it should switch to a text console.

---

