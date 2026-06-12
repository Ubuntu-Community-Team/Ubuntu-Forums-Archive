---
title: "Is it possible?"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Neo_Angelo on 2006-11-07
Hi guys, i'm a complete n00b to Linux.

now i've been sent a copy of ubuntu 6.10 is it (dapper drake or something) and installed it with a dual boot.

now then my problem is i can't do anything with my ubuntu since i need to access the net.

i use a wireless car to access my dads computer downstairs and on my Window OS i have installed the drivers and whatnot for it.

my problem is when i try to install the disc on ubuntu i get an error message because linux can't read .exe's or something.

what i'd like to know is how do i get my drivers/install my wireless card to ubuntu so i can access the net. and is there a way to transfer programs from one MS to another.

i use photoshop on my Windows MS and wish to have it on linux...is this possible and how?

thanks in advance.

---

### Post by K.Mandla on 2006-11-07
> **Neo_Angelo said:**
> i use a wireless car to access my dads computer downstairs and on my Window OS i have installed the drivers and whatnot for it.
Can you tell us what kind of wireless card you use? and what kind of computer you're using?

> **Neo_Angelo said:**
> my problem is when i try to install the disc on ubuntu i get an error message because linux can't read .exe's or something. ... i use photoshop on my Windows MS and wish to have it on linux...is this possible and how?

Yup. Linux won't run Windows programs, unless you use something like Wine, which is sort of like a command interpreter for Linux. Some things work, other things don't. It depends. :rolleyes:

---

### Post by Neo_Angelo on 2006-11-07
ahh the thing is i threw away th box with my wireless card info on it. my pc is a DELL Dimension 1100. 

my wireless card is 54MBS 802.11g Wireless lan cardbus PC card.

---

### Post by Zeke73SG on 2006-11-07
If you are looking for a Photoshoplike (it's a word) program try Gimp, it does basically everything that Photoshop does.

---

### Post by Neo_Angelo on 2006-11-07
i don't like GIMP, i prefer photoshop. my main concern is getting myself on the net with it. once i've done that i'll be able to figure everything else out myself while i'm on linux....right now i have to switch when i get advice and remember it lol.

---

### Post by Swab on 2006-11-07
OK, open up a terminal (applications > accessories)and type
```
sudo lshw
```

It will ask for your password.  Copy and paste the results back here for us to see.

---

### Post by Neo_Angelo on 2006-11-07
ok i will do thanks. i'll be right back...need to swap OS'es

---

### Post by mattkirwan on 2006-11-07
Neo_angelo, is your wireless card an external one? do you plug it into a PCMCIA slot? / USB Slot? I had a quick look at the specs for the dimension 1100, couldn't see any built in wireless.

Matt Kirwan
[www.nawrik.com]("http://www.nawrik.com")

---

### Post by Swab on 2006-11-07
> **Neo_Angelo said:**
> ok i will do thanks. i'll be right back...need to swap OS'es

Hmm... there will be a lot of output... need to save it to a file and transfer it over to Windows so you can paste it here.

Something like..

```
sudo lshw > hardware.txt
```

then copy the file to a USB pen, or floppy so you can open it in Windows.

---

### Post by Neo_Angelo on 2006-11-07
> Neo_angelo, is your wireless card an externl one? do you plug it into a PCMCIA slot? / USB Slot? I had a quick look at the specs for the dimension 1100, couldn't see any built in wireless.

yeah its one you clip into the motherboard and it sticks out at the back. its a card thingy. (yeah my terminology sucks).

> Hmm... there will be a lot of output... need to save it to a file and transfer it over to Windows so you can paste it here.

Something like..

i was a muppet and tried to copy and paste it while switching. i'll write it down and do it ha ha.

---

### Post by Neo_Angelo on 2006-11-08
heres the responce i got from the command:

> Sudo: unable to lookup (none) via gethostbyname ()

Any idea's what i need to do now?

---

