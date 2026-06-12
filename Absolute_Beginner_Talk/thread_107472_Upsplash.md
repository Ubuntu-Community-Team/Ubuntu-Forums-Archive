---
title: "Upsplash"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by Deneb Algedi on 2005-12-23
Upsplash menu?
Is this really necessary?
Can't you just remove it or turn it off.
It only slows down the boot when  i start my pc.

---

### Post by codejunkie on 2005-12-23
[QUOTE=Deneb Algedi]Upsplash menu?
Is this really necessary?
Can't you just remove it or turn it off.
It only slows down the boot when  i start my pc.[/QUOTE]
are you asking about turning off grub which lets you choose which os to boot into, or usplash the graphical boot screen that shows the ubuntu logo and the progress bar?

---

### Post by Deneb Algedi on 2005-12-23
The graphical thingie.
I've an old computer and it takes long to boot so i was wondering if removing it might speed up the boot?
PS. Will this make a difference(seems logical it will), otherwise i won't be worth the trouble?

---

### Post by nitricacid on 2005-12-23
To remove your start up splash simply type this in a terminal
```
sudo gedit /boot/grub/menu.lst
```

Once the text editor comes up find this like
```
/boot/vmlinuz-2.6.12-10-386 root=/dev/hda6 ro quiet splash
```
and remove the 'splash' from the end.

In my /boot/grub/menu.lst I had atleast 3 different lines of code ending in splash.
Simply put, just delete splash from the end of any lines.

---

### Post by yaddoshi on 2005-12-23
I assume this is where I would change the Kubuntu upsplash logo back to the default Ubuntu one too?

---

### Post by ssalman on 2005-12-23
Have you seen these HowTos:
[http://ubuntuforums.org/showthread.php?t=89491]("http://ubuntuforums.org/showthread.php?t=89491")
[http://ubuntuforums.org/showthread.php?t=80423]("http://ubuntuforums.org/showthread.php?t=80423")

the 1st one is good and easy to do (I saved about 25 sec of boot time), the 2nd is a little more advanced. I hope this helps :-)

---

### Post by embeemb on 2007-03-01
Hi,

I wanted to get the upsplash screen thingie, but ended up messing up logging in to GNOME, now I can only login to dapper using the KDE Session.

I was wondering, what should I do to reverse this? I want to basically add "splash" to the /boot/grub/menu.lst file but not sure where to do it.

Apologies if I'm not making much sense!

---

