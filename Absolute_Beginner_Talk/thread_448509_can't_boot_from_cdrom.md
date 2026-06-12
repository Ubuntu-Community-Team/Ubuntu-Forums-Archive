---
title: "can't boot from cdrom"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by KriZo on 2007-05-19
I want to install Ubuntu insted of Kubuntu, but i can't boot from my cdrom drive. In my BIOS my first boot device is CD rom, but it seems like my BIOS makes i own choices, the first thing i boots is the GRUB loader. Is there any way were i can disable GRUB temporary and then activate it again? Or can i do any thing else to install Ubuntu? It's starting to pissing me off that i can't install Ubuntu.

---

### Post by overdrank on 2007-05-19
> **KriZo said:**
> I want to install Ubuntu insted of Kubuntu, but i can't boot from my cdrom drive. In my BIOS my first boot device is CD rom, but it seems like my BIOS makes i own choices, the first thing i boots is the GRUB loader. Is there any way were i can disable GRUB temporary and then activate it again? Or can i do any thing else to install Ubuntu? It's starting to pissing me off that i can't install Ubuntu.

Hi did you use this" how to" to burn the cd
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Did you have any trouble using the kubuntu cd? And you can have both!
[http://ubuntuforums.org/showthread.php?t=302743&highlight=kde+gnome](http://ubuntuforums.org/showthread.php?t=302743&highlight=kde+gnome)
Good luck!:popcorn:

---

### Post by KriZo on 2007-05-19
Yes i burned it the same way as the how to says. I tried to boot my windows XP cd'rom and my Kubuntu cd, but i can't load any of these cd's either.

---

### Post by Psicolonia on 2007-05-19
this has happened to me before... boot from cd stoped working but appears in the bios setup... i also don't know how to set this up... :(

---

### Post by pixelstuff on 2007-05-19
hi
I had the same problem today, but I don't know if my solution is of any help for you! But so far nobody else had an idea, so here it goes: I have a  [[COLOR="Sienna"]Puppy Linux[/COLOR]]("http://www.puppyos.com/") Live CD  and a so called [COLOR="Sienna"]Wakepup floppy[/COLOR] that you can get [[COLOR="Sienna"]here[/COLOR]]("http://www.murga-linux.com/puppy/viewtopic.php?t=7979"). With this I let Puppy (from its startmenu) install itself plus install a new Grub on the MBR. (It's a matter of minutes) Then I was able to boot from the CD that I wanted to boot from. 
The good news is: Puppy is cool and worth the download. But I am still curious if there is an easier solution, I quess it is just some key to push :lolflag:
good luck!

---

### Post by halitech on 2007-05-19
if you are already running Kubuntu, just open a terminal and type

```
sudo apt-get install ubuntu-desktop
```

and install it that way. then you can select which you want to run and if you want to get rid of KDE, from a terminal type

```
sudo apt-get remove kubuntu-desktop
```

and you are good to go

---

