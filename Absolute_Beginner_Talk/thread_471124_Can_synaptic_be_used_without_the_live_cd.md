---
title: "Can synaptic be used without the live cd?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by HgBoy on 2007-06-11
I need to install two packages from synaptic, but dont have a working internet connection or the live cd handy. Is there a way to do this? (The packages make my modem work properly for the internet).

---

### Post by viciouslime on 2007-06-11
You can go to [http://packages.ubuntu.com]("http://packages.ubuntu.com") and download the deb files there. Then just double click them to install :)

---

### Post by HgBoy on 2007-06-11
my internet doesnt work. The modules are for my modem.

---

### Post by Bachstelze on 2007-06-11
What exactly do you need to install ?

---

### Post by gerscht on 2007-06-11
I suppose you'll have to download them on another PC then and transfer them via USB key or something else.
Depending on the depository they are in, a live CD might not be sufficient (I think the live CD doesn't have universe on it, the DVD does though)

---

### Post by HgBoy on 2007-06-11
sl-modem-daemon
sl-modem-source

They are for my dad's laptop. He is computer illiterate, and 200 miles away without a working modem. I removed XP and installed 6.10, silly me for thinking the modem would work :p I have installed these on my brothers laptop(identical) and it worked instantly.

---

### Post by Bachstelze on 2007-06-11
I don't believe those packages are on the CD. Just tell your dad to download them from [http://packages.ubuntu.com](http://packages.ubuntu.com) on a spare computer (at a friend's, in a library, wherever) and copy them on his laptop with an USB stick or whatnot.

---

### Post by viciouslime on 2007-06-11
> **HgBoy said:**
> my internet doesnt work. The modules are for my modem.

Use whatever connection you're using to post this, to go to the link above and download the packages :)

---

### Post by KIAaze on 2007-06-11
How to install packages without an internet connection:
> 1)Open synaptic
2)Click on File->Generate package download script
3)Go to the other PC (with GNU/Linux on it so that you can run the script) and run the script on it. It should generate something. Don't know what since I never tried it.
4)Get that thing back to the other PC.
5)Open synaptic and click on File->Add downloaded packages


For other solutions, see here:  [Programme and Package Installation methods]("http://ubuntuforums.org/showthread.php?t=414490")

---

