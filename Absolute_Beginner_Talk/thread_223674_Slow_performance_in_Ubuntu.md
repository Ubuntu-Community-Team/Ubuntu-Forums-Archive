---
title: "Slow performance in Ubuntu"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by tromik on 2006-07-26
Installed Ubuntu 6.06 recently, and I'm finding that after running Opera, X-Chat, Gaim, and AmaroK for even just a couple of hours, everything really starts to slow down. I'm not calling Ubuntu slow, but I'd like to know if it's something I'm doing, and it very well could be.

Specs:
AMD 2400+ XP
256mB ram
MSI KT4V mobo
Geforce 3 vanilla
Lan and sound are on-board

I have two hard drives, one 80gB and one 20gB. The 20gB is split into three partitions: 10gB for Ubuntu, 9.5gB for storage, and 500mB for the swap. At least, I think it's 500, I left the default amount when Ubuntu was installing.

I don't have too many applications installed, and I don't do much at the same time beyond surf, chat and listen to music. When I watch a video I basically close everything else.

I should note I have XP SP2 installed on the drive, and it runs quite well despite my low specs.

Anyone have any ideas?

---

### Post by avtolle on 2006-07-26
Sounds like something is using up your memory. From the terminal, type in "top" to see what is eating up your ram.

---

### Post by airjunman on 2006-07-30
> **avtolle said:**
> Sounds like something is using up your memory. From the terminal, type in "top" to see what is eating up your ram.

I have the same problem ... I use a P4 2.8GHz/512MB RAM with Ubuntu 6.06 and XP on dual boot... I used to use Firefox as my browser earlier, but then I felt it got really slow so switched to Opera... I like Opera for the ease of using the mail client in-built along with the general feel ... but now we seem to be going down the same road again with Opera this time ... I open a page in Firefox now and that seems faster, so I dont think it has much to do with the browser...it seems like whichever one I use over a period of time suffers a dramatic fall in speed ...:mad: 

I tried "top" at the command prompt and it gave me pretty much wat I expected it to ... Opera had CPU usage at abt 80%-95%, and a lot of the time when the pages were already displayed and it was doing no additional work like fetching pages ...

Any help is welcome.. thanks in advance :)

---

### Post by adamkane on 2006-07-30
Ubuntu ships with a safe but slow 386 kernel. To get any performance out of Ubuntu you need to install the 686 or k7 kernel:

Intel Pentium (Other than Pro or 486):

```

sudo apt-get install linux-686 linux-image-686 linux-headers-686 linux-restricted-modules-686

``` 
AMD K Series (Duron, Athlon, Sempron):
 
 ```

sudo apt-get install linux-k7 linux-image-k7 linux-headers-k7 linux-restricted-modules-k7

``` 

Reboot.

Once you do this, you'll be able to run amaroK in the background, and no longer worry about crashes.

---

