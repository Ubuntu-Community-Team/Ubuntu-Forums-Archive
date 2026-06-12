---
title: "[SOLVED] Large hard drive ??"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2008-03-15
I'm wondering if there are any size limitations on usb hard drives ?  Thot I read something about it ?  I'm running Hardy 64 bit.and thinking of getting a 750 gig WD hard drive .. any thots ??
Thanks  )

---

### Post by iansane on 2008-03-15
no probs with my 300 gig. Is that still considered big anymore?:)

---

### Post by MrKlean on 2008-03-15
I dunno LOL!!  My FIRST puter had an internal 20 MEG LOL!! That was big for the day LOL!!!  have a 150 gig.. a 250 gig.now gonna get a 750 gig...

---

### Post by PeterJS on 2008-03-15
64bit systems can address up to 16 exabytes of RAM and I can't imagine they couldn't handle file systems at least that large. Ext3 tops out at being able to handle 32 Terabyte disks (I don't think any of these exist yet). ZFS tops out at 16 exbytes of data which is well past the quantum energy capacity of the entire earth. I don't think you have anything to worry about :)

---

### Post by rustutzman on 2008-03-15
I'm running a 750 and a 500 GB sata with a 300 GB pata with no problems.

Russ

---

### Post by MrKlean on 2008-03-15
Thanks guys  )  If I use the ext3 to format it, I should have no problems, or is there a better file system I should use ??
Thanks ; )

---

### Post by maniac_X on 2008-03-15
> **MrKlean said:**
> I dunno LOL!!  My FIRST puter had an internal 20 MEG LOL!! That was big for the day LOL!!!  have a 150 gig.. a 250 gig.now gonna get a 750 gig...

ROFL! I remember back in the day too! My first comp came with 8MB soldered onto the mobo and a hugmongus HDD of 1GB. Luckyly there were slots to add more memory. Remember also back then we had to buy 2 sticks ata time cause you could only expand the memory in matched pairs. I still have that comp. 20MB HDD though...WOW, that is small!!!!! ROFL!! :lolflag:

---

### Post by IanW on 2008-03-15
Kids today! My first machine was a [Sinclair Spectrum](http://en.wikipedia.org/wiki/Sinclair_Spectrum), with 48K of memory, and used a tape deck for storage!

Given that USB drives are available in sizes up to 2TB, I don't think you'll have any problems.

---

### Post by MrKlean on 2008-03-15
well, I used to connect at 300 baud..WOW !!   On a co. called qlink...should have bought stock..who knew.... Qlink is now called.....AOL !!!

---

### Post by AmericasCup222 on 2008-03-15
Lol, I still use a 6.8 gig maxtor I got donated to me...Looks like its time for an upgrade!

---

### Post by iansane on 2008-03-16
My only concern with the ext3 file system is, what if you ever want to access it from a windows machine? Not sure how that works. If Ubuntu is only OS using the whole drive then I guess it doesn't matter, but I like having NTFS on my big drive so both systems acess it with no problems and still get the full functionality and security of NTFS when in windows. My windows and Ubuntu are on totally seperate drives though and the big one is just a shared back up drive.

---

### Post by PeterJS on 2008-03-16
There's an ext2/3 driver for windows, it's pretty good. It supports both reading and writing ext2/3 paritions:

[http://fs-driver.org/](http://fs-driver.org/)

---

