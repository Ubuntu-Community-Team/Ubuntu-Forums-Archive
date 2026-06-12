---
title: "Accessing a Nokia N72 via USB"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by ExpatPaul on 2007-11-07
As I own a Nokia N72 which I use as my MP3 player, I wanted to see if I could copy podcasts to the phone over a USB cable. After a bit of digging around (mainly [here]("http://matallo.org/how-tos/nokia-6680-ubuntu-with-dku-2-usb-cable/")) I have managed to do this using [OpenOBEX]("http://dev.zuckschwerdt.org/openobex/").

The steps I followed are:

Find what interfaces are available (0 and 1) and then connect using interface 1

```
sudo obexftp -u
sudo obexftp -u 1 -l
```

Access the Sounds folder on the phone and the Nokia folder on the PC (I'd already created the Nokia folder and copied into it enough MP3s to nearly fill the memory card)

```
sudo obexftp -u 1 -c E:\\Sounds/Digital -l
cd Nokia
```

And copy the files

```
sudo obexftp -u 1 -c E:\\Sounds/digital -p *
```

Although I'm feeling quite pleased with myself for having managed this, I was also wondering whether anyone knew of any better approach.

---

### Post by skymera on 2007-11-07
for my Samsung D900i

there was a USB setting, i changed from Modem to Mass Storage 

now i can mount my memory card on thr desktop..

maybe yours has a similar option

---

### Post by ExpatPaul on 2007-11-08
> **skymera said:**
> there was a USB setting, i changed from Modem to Mass Storage 

now i can mount my memory card on thr desktop.

That would be the ideal. Unfortunately I can't find an equivalent option on any of the Nokia menus. 

When I did just plug the phone in (which was the first thing I tried), Ubuntu couldn't see it at all. I don't know if there is an Administration option I need to be looking at here?

---

### Post by CanonKen on 2007-11-08
Just done the same thing with my Nokia 6300 tonight, it detected mine though when I plugged it in and I just had to select the data option on the phone ( had 3 choices Data storage, Nokia mode and printing & media, I backed all my music and images up and transfered more music to the phone by just dragging and dropping
PS the phone shows up if you open your home folder and look at the folder tree to the left, shows up as Disk

---

### Post by ExpatPaul on 2007-11-10
> **CanonKen said:**
> PS the phone shows up if you open your home folder and look at the folder tree to the left, shows up as Disk

That's what I was hoping it would do... but it didn't. It's possible that I'm missing some admin or security setting somewhere, but I can't see where it might be.

Still, FTP works...

---

