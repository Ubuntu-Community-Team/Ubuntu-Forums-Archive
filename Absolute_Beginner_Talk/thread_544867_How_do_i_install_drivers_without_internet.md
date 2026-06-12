---
title: "How do i install drivers without internet"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by DragonStorm36 on 2007-09-06
the computer i have instaled ubuntu on can't Access the internet, and i need nvidia drivers for my 4200 Ti AGP card. and i also will need wine.

So if anyone can help me i would Appreciate it.

---

### Post by o3rat on 2007-09-06
I would say if you have a USB jumpdrive or ipod, just download the drivers elsewhere onto them and just install it from them

---

### Post by DragonStorm36 on 2007-09-06
i have the drivers my usb but i still coundn't work out how to install it

---

### Post by sumguy231 on 2007-09-06
Where did you download them from, and what does the file look like? You need to download either the nvidia-glx or nvidia-glx-legacy package (depending on how older you card is) from packages.ubuntu.com. Once the .deb file is on there, just double-click to install.

---

### Post by bigboy_pdb on 2007-09-06
Are you able to get any sort of graphical interface on Ubuntu or are you only using a command line? Also, what type of file is the file that contains the drivers (i.e. "tar.gz", "deb", or "rpm")?

---

### Post by DragonStorm36 on 2007-09-06
> **sumguy231 said:**
> Where did you download them from, and what does the file look like? You need to download either the nvidia-glx or nvidia-glx-legacy package (depending on how older you card is) from packages.ubuntu.com. Once the .deb file is on there, just double-click to install.

i downloaded it from nvidia

its called: NVIDIA-Linux-x86-1.0-9755-pkg1.run

---

### Post by nonewmsgs on 2007-09-06
im sure ill be corrected if im wrong but i think you type 

<code>
sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run

</code>

yay my first code post

---

### Post by bigboy_pdb on 2007-09-06
I haven't used "run" files before, but from doing some searching it appears that nonewmsgs is correct.

The following sites might be of some use:
[http://forums.3dgamers.com/showthread.php?t=6588](http://forums.3dgamers.com/showthread.php?t=6588)
[http://www.linuxforums.org/forum/redhat-fedora-linux-help/41794-run-files.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/41794-run-files.html)

On a side note, nonewmsgs if you want the code to be in a box, use square brackets [ ]

---

### Post by DragonStorm36 on 2007-09-06
thanks i'll try that when i get home, so do i need Linux x64 driver or the linux x86 driver

---

### Post by nonewmsgs on 2007-09-06
it depends on your version of ubuntu.  you'll need the x64 if you are running ubuntu amd64 but otherwise the i86 should be fine.

---

### Post by reckless2k2 on 2007-09-06
hey can you carry it over to where a network connection is or do you have a wifi usb/pci? just throwing it out there. hahaha

---

### Post by DragonStorm36 on 2007-09-06
thanks, but at the moment i'm running on a intel P3. can't wait to get my 4000+ dual core. anyway thanks alot for your help.

---

### Post by DragonStorm36 on 2007-09-07
> **nonewmsgs said:**
> im sure ill be corrected if im wrong but i think you type 

<code>
sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run

</code>

yay my first code post
that didn't work but then i have no idea how to work the terminal, it said:
sh: can't open NVIDIA-Linux-x86-1.0-9755-pkg1.run

---

