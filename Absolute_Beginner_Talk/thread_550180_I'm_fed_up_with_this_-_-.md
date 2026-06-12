---
title: "I'm fed up with this -_-"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2007-09-13
I've tried like 4 different distros on my laptop (formatted vista off of it) and none of them will boot.  I got ubuntu installed, but then I get a black screen of death RIGHT AFTER it loads.  Fluxbuntu used to work, now it doesn't.  If freezes up at different sections over 5 times that I tried.  Is the linux god trying to tell me I'm not suppose to have linux on my laptop?

---

### Post by Aprilius on 2007-09-13
Did you try booting ubuntu in safe mood instead?

Also do try a memory test. I used to have the very same problem because the ram was faulty.

---

### Post by arochester on 2007-09-13
What is the make and model of your laptop?

---

### Post by Nulifier on 2007-09-13
This sounds like it is a problem with your graphics card.

If you can get into recovery mode (the second option on grub, the boot loader) then type the following:
sudo nano /boot/grub/menu.lst

you are looking for something like this (the top line will be what grub shows when it loads):
```
title           Ubuntu gutsy (development branch), kernel 2.6.22-11-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-11-generic root=UUID=d677a732-dd99-40be-a00be-a042-f05e1f0b038a ro quiet splash

initrd          /boot/initrd.img-2.6.22-11-generic
quiet
```

On the third line remove the *quiet splash* part (you can add it back in later)
press Crtl-O and then Ctrl-x to save and exit

type sudo reboot and try booting again. This time it will not show you a splash it will simply show the system booting.
On my system this was enough and it booted fine for some reason. but if it doesn't then tell us the error messages that it outputs.

---

### Post by w4ett on 2007-09-13
Isn't this the same problem as your current thread here?:

[http://ubuntuforums.org/showthread.php?t=549682](http://ubuntuforums.org/showthread.php?t=549682)

---

### Post by zetsumei on 2007-09-13
someone in the irc channel said it must be a kernel thing if I couldn't get fluxbuntu (I used the very same cd on my other desktop and it worked like a charm) or ubuntu to work.  Has anyone heard of zenwalk os?  I might give that a try to see if that'll work.

---

### Post by Anzan on 2007-09-13
Yes, Zenwalk is a good distro.

---

### Post by fredj on 2007-09-13
You are still not answering any questions such as the type and make of the computer you are
trying to install on. So really you are just wasting our time and yours.

---

### Post by zetsumei on 2007-09-13
Sorry I thought I did.  It's a dv6000 hp laptop that had vista on it.

---

### Post by tgalati4 on 2007-09-13
Try removing the Windows stickers.

Go into the BIOS and turn off "Plug and Play OS"

Try a few more distros.  Do a search in the forums on DV6000 and see what comes up.

---

### Post by newman on 2007-09-13
Your first mistake was that you removed Vista. Why remove an OS that is designed to work with that laptop, and replace it with something that MIGHT work ???

---

### Post by nonewmsgs on 2007-09-13
> **newman said:**
> Your first mistake was that you removed Vista. Why remove an OS that is designed to work with that laptop, and replace it with something that MIGHT work ???

maybe he didn't agree with the EULA.  give the guy a break, the first thing i'd do with a vista laptop is put linux on it.

---

### Post by chris062689 on 2007-09-14
I have a HP dv9000 and it works like a charm!

---

### Post by cubeist on 2007-09-14
I am pretty sure it is a problem with ACPI... I have a hp dv9000 that had the exact same problem.  Follow these instructions and Ubuntu should work like a charm

[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)]("https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)")

Good luck... post back with results

---

### Post by Ripfox on 2007-09-14
Yes...I have a dv6000 hp lappy as well...look through my posts and you will find various answers to the problems you have. I have Ubuntu working FLAWLESS on one of these machines, including 3d acceleration for Beryl and Ultima Online working on a freeshard under Wine...makes me happy. :)

The acpi thing only affects some models, it did not affect mine, but I am sure that is what it is.

---

### Post by Ripfox on 2007-09-14
> **newman said:**
> Your first mistake was that you removed Vista. Why remove an OS that is designed to work with that laptop, and replace it with something that MIGHT work ???

lol...is all I can say. In fact, Vista does NOT work so good.

---

### Post by zetsumei on 2007-09-14
I would use Vista, but M$ changed everything about it from XP to Vista.  I HATE the new file system.  There's a User folder for your user, with 50 billion folders inside it.  I mean, who seriously needs a folder for Contacts, Documents, Music, Video, Downloads, and some other crap.  I mean all you should need is Documents, Music/Video and thats all.  If I have to I'll sell my Vista cd on craigslist and tell them if they have a dv6000 series laptop then if they pay me, I'll give them the Vista cd for it LOL.

---

### Post by danny joe ritchie on 2007-09-14
> **newman said:**
> Your first mistake was that you removed Vista. Why remove an OS that is designed to work with that laptop, and replace it with something that MIGHT work ???

That's exactly what I would have done!

---

### Post by Carbon Tiger on 2007-09-14
To the OP.

I have a dv6000 laptop and had the black screen problem too and here's how I fixed it. 

Turn on the computer go into the GRUB loader and edit the boot command, find the main boot (not safe mode or anything) and add this to the end: noapic nolapic then run the new boot command. It should load, then install the restricted nVidia driver from the menu and reboot. That fixed mine. 

If adding the above to the end of the boot line didn't work try this, NOAPIC NOAPCI NOLAPIC NOIRQPOLL NOSMP 

That should do it once you get the right driver installed.

---

### Post by cubeist on 2007-09-14
just a little fyi... you usually only need to disable the acpi, smp, etc for the live cd... once you have ubuntu installed acpi seems to work ok on most hp laptops (works ok on my dv9000).  But if I need to boot into the live cd I need to add all those noacpi, noapic, etc options.

edit - there is nothing wrong with removing vista and using linux 100% of the time (I switched from mac to linux).  But keeping vista allows you to run specific apps or games from time to time that may not work in wine, also if you ever want access to iTunes or other such services, sometimes you need a windows OS...

---

### Post by sloggerkhan on 2007-09-14
I wouldn't agree to the vista EULA....

---

