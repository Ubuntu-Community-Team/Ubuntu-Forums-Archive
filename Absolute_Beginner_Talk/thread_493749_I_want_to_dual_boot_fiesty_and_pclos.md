---
title: "I want to dual boot fiesty and pclos"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-07-06
Pclos was the first distro  I tried. Then I found Ubuntu and fell in love. She hates it. She likes the xp ish feel that pclos has. If I dual boot how would I partition my hard drive to avoid getting the grub errors I've heard of other people getting. I want to prevent these problems before they drive me nuts heres what my partitions look like now. Can some one give me an idea of how I should set this up.

---

### Post by aquavitae on 2007-07-06
I've never installed Pclos (just run from the cd) so I don't know what the process is like, but I see no reason why you can't just install as normal.  What grub errors are you referring to?  Every grub error I've ever experienced has been easy to fix.  Btw, Pclos is not really any different to any other linux, its just got a winxp theme.  You could easily make ubuntu look more xp by changing the colours and theme, and renaming some of the icons.

Great wallpaper and theme, btw!  Where did you get it?

---

### Post by swoll1980 on 2007-07-06
She like pclos I cant argue with her if she likes it better she likes it better. changing her mind would be like changing the earths rotation

---

### Post by ramjet_1953 on 2007-07-06
I'm no expert on setting-up GRUB and will stand corrected, if I did this all wrong, but it did work for me.

I re-partitioned my HDD, using the stand-alone iso disk [COLOR="Blue"]parted[/COLOR].

After doing that I installed PCLinuxOS 2007 using its' Live CD.

After doing that, I realised that in one of the steps that I had not included my existing Feisty install and that when I re-booted, I did not have the option to select Ubuntu.

Un-deterred, I just used the [COLOR="Blue"]Super GRUB Disk[/COLOR] iso CD to recover my Ubuntu GRUB.

Having done this, I then booted Ubuntu and mounted the PCLinuxOS partion, went into /boot/grub/menu.lst and copied the contents.

I then just went into my Ubuntu /boot/grub/menu.lst and pasted it below the the line that says:

[COLOR="Blue"]### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
[/COLOR]
I then saved it and re-booted.

Presto! You now have Ubuntu's GRUB, with the option to boot into PCLinuxOS.

Oh, by the way, all of this has to be done in sudo mode, of course.

Not very elegant, but it worked for me.

Regards,
Roger :cool:

---

### Post by swoll1980 on 2007-07-06
I'm refering to the grub errors that involve it not being able to find OS' because of a partitioning issues I want to avoid this if possable

---

### Post by swoll1980 on 2007-07-06
Wow that seems like a hand full. Will I be able to do all this with 6 weeks of linux expierience.

---

### Post by mjwhitfield on 2007-07-06
go for it Swoll, I recently set up my friends PC with a duel boot between XP and Ubuntu and royally screwed GRUB.  It wasn't hard to fix, just make sure you have the super grub disk.

---

### Post by swoll1980 on 2007-07-06
where do I get super grub disk is it on either of the live cds?

---

### Post by ramjet_1953 on 2007-07-06
You can get the Super GRUB Disk iso from here:

[COLOR="Blue"]http://supergrub.forjamari.linex.org/
[/COLOR]
You can get the GParted iso from here:

[COLOR="Blue"]http://gparted.sourceforge.net/
[/COLOR]
Don't forget to burn both as an iso image, not a regular data CD

Also burn the images SLOWLY, no faster than 4X.

Regards,
Roger :cool:

---

### Post by swoll1980 on 2007-07-06
does anyone know how i get the md5sum for super grub

---

