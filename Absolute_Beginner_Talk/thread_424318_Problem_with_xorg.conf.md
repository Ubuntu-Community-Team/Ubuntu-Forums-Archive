---
title: "Problem with xorg.conf"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by SuperAndy on 2007-04-26
Right, I have been here before, but then the easter holidays and exams happened, so my linux experimentation has laid dormant.

The problem is, that when i try and boot into linux, i get an error message saying xwindow failed. or something along those lines.

The main thing i want to achieve at the moment, after playing with the xorg settings to my hearts content, is exporting this xorg.conf file to a place where i can get at it in windows. I am running x64 vista, which makes it hard to get to my linux partition from inside windows. And although i have a FAT32 partition, right next to the linux EXT3, i cant work out where it is. I thought it would be in the dev folder, and thinking it would be an sda, as its on my first sata drive, but had no joy.

I realise that [this]("http://ubuntuforums.org/showthread.php?t=414194") could help, but if i remember correctly, my xorg.conf file has the horiz and vert refresh rates in [i manually entered these to be specific to my monitor].

Any help would be greatly appreciated.

Andy

---

### Post by Happy_Man on 2007-04-26
Right, ok, when you boot into Ubuntu, you will get your "X Window failed" error message. Eventually, it will drop you at a text login. Log on, and then run this code:

```
sudo dpkg-reconfigure xserver-xorg
```
It'll ask you some stuff about your mouse, keyboard, refresh rates, whatever. Remember to use the spacebar to select stuff though. Once that's done, it'll put you back at the terminal. Reboot, and hopefully your computer should be back to normal!

---

### Post by jfinkels on 2007-04-26
> **SuperAndy said:**
> Right, I have been here before, but then the easter holidays and exams happened, so my linux experimentation has laid dormant.

The problem is, that when i try and boot into linux, i get an error message saying xwindow failed. or something along those lines.

The main thing i want to achieve at the moment, after playing with the xorg settings to my hearts content, is exporting this xorg.conf file to a place where i can get at it in windows. I am running x64 vista, which makes it hard to get to my linux partition from inside windows. And although i have a FAT32 partition, right next to the linux EXT3, i cant work out where it is. I thought it would be in the dev folder, and thinking it would be an sda, as its on my first sata drive, but had no joy.

I realise that [this]("http://ubuntuforums.org/showthread.php?t=414194") could help, but if i remember correctly, my xorg.conf file has the horiz and vert refresh rates in [i manually entered these to be specific to my monitor].

Any help would be greatly appreciated.

Andy

Working in Ubuntu, first you have to mount the FAT32 partition at a location in the / hierarchy of your choosing, then you can copy the file over (or do whatever).

---

### Post by SuperAndy on 2007-04-26
ok, is mounting a relatively easy thing to do from the text imput. i messed around a bit, typed mount, but that just gave me a list of mounted things. i presume i need some modifiers (?) to do this?

and thanks happy_man, but i have been doing that. tried many different combinations of things and stuff.

if i can get this FAT32 drive mounted, i should be able to paste the contents of the file for you all to see!

---

