---
title: "How to install driver for CanoScan N1220U..."
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-06-12
Hi - 
I've traced down what I'm pretty sure is the driver for my CanoScan N1220U scanner. The driver is called:

Plustek-usb-0.51-14.tar.gz

I've extracted it and looked through all the folders and files for installation instructions, and I've found none.  The site from where I downloaded it is of little help:

 [http://www.gjaeger.de/scanner/plustek/](http://www.gjaeger.de/scanner/plustek/) 

Does anyone know how to install this driver??? 

I appreciate any help or suggestions. 

Many Thanks, .....Frank B.

---

### Post by bbarcelo on 2007-06-13
You could always try installing the Windows version of the driver by using ndiswrapper (or GUI version - ndisgtk).

From Terminal:
```
apt-get install ndisgtk
```

---

### Post by paradoc on 2007-06-13
Try this (from one of my previous postings)
> I have a Canon N1220U USB scanner without any documentation that was immediately picked up by terminal> sudo-find-scanner (one might need sudo apt-get install sane-utils as well).
The excellent xsane app kicked in (at 150 dpi) with adjustable and rapid results.

I hope this helps you, it worked fine for me!

---

### Post by Brightbelt on 2007-06-13
Thanks guys, but both of those (sane-util & ndisgtk) show that they have already been done. 
I'll keep trying, ...Frank B.

---

### Post by paradoc on 2007-06-13
Surprised it didn't pick up your scanner as it did (easily) for me

maybe you should have let Ubuntu ID the scanner first before applying the sane-utils
```
(in Terminal)sudo-find-scanner
```
      and *then* 
```
sudo apt-get install sane-utils
```

I was using Edgy at the time, but it's the same difference I should think

---

### Post by Brightbelt on 2007-06-13
Paradoc, I did some online research when I downloaded the driver, and I actually read that this scanner indeed worked "out of the box" on Edgy, but that there are known driver issues with Feisty, which is what I'm running. 

I also should have mentioned before that this code:

```
sudo-find-scanner
```

did not result in anything for me. 

I'm still open to ideas !!! Many Thanks,. .....Frank B.

---

### Post by paradoc on 2007-06-13
I'm sure that someone out there has the answer.....this is one of many incompatibilities, it seems,when using the latest version or so I've heard.
Unfortunately, Frank B, I don't have the answer.  Felicitations & Best of Luck!

HELP!..........Somebody?

---

### Post by Brightbelt on 2007-06-13
Paradoc, 
I got it working !!! Actually, I got it working by following a French Ubuntu Document, here:

[http://doc.ubuntu-fr.org/category/scanner/feisty](http://doc.ubuntu-fr.org/category/scanner/feisty) 

It may even be available in English, but this was one of the links Google threw up at me. I should add that I tried other methods from the Google list that did not work. But this one did !!

Many Thanks for all your help; I appreciate your time,.....Frank

---

### Post by Brightbelt on 2007-06-13
I want to mention,....in the French Ubuntu document, the code is still in English, so don't be too scared of it. ;)

Also, after following the directions, un-plug your scanner, reboot and then plug it back in. And you should be good to go.

Thanks, ...Frank B.

---

### Post by paradoc on 2007-06-13
Smart Googling, Frank B..!

I think I might try a few foreign tours of my own............and in English,too!!

______________
(Thought) "The Sun never Sets on the Br.........er, I mean,  Ubuntu Empire"

---

### Post by Brightbelt on 2007-06-13
Thanks Paradoc !! I have to admit,  solving a Linux hardware config problem makes you feel pretty smart. 

Thanks for your assistance, as well. It gave me the push I needed.
;) Frank B.

---

