---
title: "Linux seems to hate me.. except one distro..."
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Xylograph on 2008-02-10
Well. I have a large predicament...

PIII 1ghz, 512mb RAM and a 10Gb harddisk.

I have installed Fedora 8 (no sound, uses 640x480 res and wont go higher), OpenSUSE 10.3 (no sound, staggeringly slow, wont boot half the time), Ubuntu (this is the worst by far. Wont boot at all. The orange loading bar loads, makes the bongo noise, and then I get a black screen).

Ubuntu's problems dont end there. It seems to really hate me. Ive tried 4 different install CD's from downloaded ISOs to Magazine Coverdisks (LXF usually) and it will not boot on either my desktop (AMD Athlon64 3000+ , 1.5GB ram) or other laptop (AMD Turion64 1.4GHZ, 512MB ram). Admittedly I have some success on the Turion laptop. Everything works fine in Live, it boots quickly etc... After install very little works, it runs slowly and takes over half an hour to boot usually, fastest is about 10 minutes.

The only distro that works flawlessly is Knoppix 5.1 and the awful thing about it is it cant be installed.

Any advice to what distro I could use or advice to fix the ones I have?

---

### Post by JoshuaRL on 2008-02-10
Have you tried using the Alternate CD?  That won't load a Live environment, and it usually installs a little better.

Although, it seems that you have Xorg problems.  Try going into the rescue terminal and see what errors come up from:
```

startx

```

---

### Post by spiderbatdad on 2008-02-10
you might try linuxmint

---

### Post by amingv on 2008-02-10
Knoppix has always been good at recognizing hardware; and (*ding, ding*) you actually CAN install it.

Just open a console and type:

```
sudo knoppix-installer
```

Although many will not recommend it since it's not so adapted for regular use...

If you really wish to install Ubuntu, tell more about your hardware (graphic card, ect) and I'm sure someone will be able to help.

---

### Post by Xylograph on 2008-02-10
Hmm. I have tried the alternate install cd. That broke a hard disk almost. I managed to rescue it eventually with knoppix.

---

### Post by timbounceback on 2008-02-10
I love LXf :-). Anyway, have you tried PCLinuxOS?

---

### Post by Xylograph on 2008-02-10
I have indeed tried PCLOS (In fact im currently installing the copy from LXF103 as the live version ran perfectly, although flash vids had no sound, other stuff did, so I guess its fixable).

---

### Post by Dr Small on 2008-02-10
Sounds like you need new hardware O.O

---

### Post by Xylograph on 2008-02-10
3 new machines??


Hmm. I was installing PCLOS. it was about 50% done and the window disapeared. Any ideas?

---

### Post by kerry_s on 2008-02-10
> **Xylograph said:**
> Well. I have a large predicament...

PIII 1ghz, 512mb RAM and a 10Gb harddisk.

I have installed Fedora 8 (no sound, uses 640x480 res and wont go higher), OpenSUSE 10.3 (no sound, staggeringly slow, wont boot half the time), Ubuntu (this is the worst by far. Wont boot at all. The orange loading bar loads, makes the bongo noise, and then I get a black screen).

Ubuntu's problems dont end there. It seems to really hate me. Ive tried 4 different install CD's from downloaded ISOs to Magazine Coverdisks (LXF usually) and it will not boot on either my desktop (AMD Athlon64 3000+ , 1.5GB ram) or other laptop (AMD Turion64 1.4GHZ, 512MB ram). Admittedly I have some success on the Turion laptop. Everything works fine in Live, it boots quickly etc... After install very little works, it runs slowly and takes over half an hour to boot usually, fastest is about 10 minutes.

The only distro that works flawlessly is Knoppix 5.1 and the awful thing about it is it cant be installed.

Any advice to what distro I could use or advice to fix the ones I have?


knoppix is built on debian, so try straight debian.
net installer-> [http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-businesscard.iso)
kde install-> [http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-kde-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-kde-CD-1.iso)
xfce4 install-> [http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-xfce-CD-1.iso)

you do know how to burn a iso, right? remember burn as a image at 4x for the best results.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by amingv on 2008-02-10
Where does it die? Copying files? Configuring hardware?

Do you have any means of checking your HD for defects?

---

### Post by anemptygun on 2008-02-10
I would try the alternate install of xubuntu, which runs faster on older systems. The alternate cd is not a live cd so it should have less requirements.

---

### Post by Xylograph on 2008-02-10
Yes, i know how to burn an ISO. Only 2 of these were burned by me. The rest came with LXF.

Anyhoo, Ive formatted the harddisk with Knoppix and Im trying the PCLOS install again. If that fails Ill try Etch which came with LXF 103.

If that fails, Ill do the highly unadvisable install of Knoppix 5.1.1!

---

### Post by Xylograph on 2008-02-10
Wooohoooo!

PClinuxOS 2007 installed successfully after reformatting the disc with Knoppix and trying again!

Thanks for all the help!

I jsut cant understand why no version of Ubuntu will work on any pc or laptop I own or know of.

---

### Post by anemptygun on 2008-02-11
Yeah, interesting. But I'm glad something worked out for you! :KS

---

### Post by brokenhachi on 2008-02-11
well ubuntu worked fine for me. pclinuxos doesnt work (well the KDE version does but the gnome version doesnt).


the black screen thing sounds like you have an issue with your video card. so im guessing the live CD is the thing that doesnt work... heres what you do... 

on the grub screen, when it asks you to choose what you want to do, first do a media check.. then reboot and when you come back to that screen push i think its F3 (the one that says VGA at the bottom of the screen) and select something else. 

this is what i had to do to get any visual. once its installed though, it worked fine for me.

---

