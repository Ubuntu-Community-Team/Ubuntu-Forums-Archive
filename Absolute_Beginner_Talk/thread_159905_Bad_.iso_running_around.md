---
title: "Bad .iso running around?"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by therunnyman on 2006-04-13
Hi all,

Over the last couple days, I see a lot of people having difficulty installing Ubuntu.  The culprit looks to be a bad image, but I don't know that anything has changed out that way.  Is it that something did change, or are a lot of people nabbing the .iso?  The latter, I think, could corrupt a download, so I'd say nab it at 11 am GMT or something.  The former, I can't speak to.  Anyone know whether or not a change was made to the image?

A gorilla ate my lunch,

therunnyman

---

### Post by Jason_25 on 2006-04-13
I download CD images all the time, and have never gotten a corrupt one.  The reason you see so many people with trouble is this is a support forum.

---

### Post by fng on 2006-04-13
Also, burning the iso images at full speed isn't a good idea. It always give me a bad uninstallable ubuntu cd.  
But when i burn the cd at 4 speed from the same iso, everything is fine.

---

### Post by horsey1901 on 2006-04-14
I agree burning an ISO at full speed can cause major problems.  I always burn my ISO's at about 80% of the drives capable speed and I dont get errors.  Have about 30 ISO burnt disks in my jukebox now and have not had a problem with any of them.  

I did however have problems when I first started burning ISO's at full speed about every 4th one crashed.

The Horse

---

### Post by enopepsoo on 2006-04-14
if you check the md5sum before burning there should be no problem with the image.
```
md5sum ubuntu510.iso
```
or whatever you called it.

---

### Post by aysiu on 2006-04-14
I'm with therunnyman on this, but [I appear to be in the minority](http://www.ubuntuforums.org/showthread.php?t=113925).

---

### Post by therunnyman on 2006-04-14
Problem is, I think, these downloads aren't landing on a Linux box.  A box of cat litter and a copy of Crash says most people who download Ubuntu are coming from Windows or Mac.  Otherwise, yeah, run a checksum.

In Windows, where I hail from, here's what you'd have to do to burn a good CD:

1. Defragment your drive.
2. Flash your drive's firmware.
3. Check for file system errors.
4. Defragment again.
5 Use the crumby "lite" CD-R software package that came with your drive.
6. Get rid of the wizards.

*7. Disable buffer-underrun protection.*

(We've been had...P-CAV and Z-CLV repurpose this technology for their writing scheme; otherwise, we'd never have use anything faster than 16x)

8. Set your burn speed to something below 16x.
9. Go through a Burn Image dialog.

*10. Make sure the software didn't set itself back to a high speed and enable buffer-underrun protection.*

11. Get your bag of runes, cast them, then consult the I Ching.
12. Burn a coaster.
13. Burn an image.

There are more steps, but I leave them out in the interest of brevity.

My opinion.  With science.

therunnyman

---

### Post by kchukchukchu on 2006-04-14
I found this thread where others are also having their installation stalled at exactly the same spot (where I got stopped) for CD burned at different speed:
[http://ubuntuforums.org/showthread.php?t=150654&highlight=install+base+system+problem](http://ubuntuforums.org/showthread.php?t=150654&highlight=install+base+system+problem)

I have burned 3 CDs and I did checksum (for MAC:  it's actually the md5 command, there didn't seem to be md5sum commands but it seemed to work the same way)  before the burn and also copied the CD image back to harddrive and checksummed again, and all results were the same as given one.  So, does this mean that there is a problem with the image itself, or hardward problem with my old computer (and others)?

It seemed to me that it's the Server install that didn't work (if this makes any sense), at least the other people in the above thread seemed to be installing server as well.

I am going to try to download an image from a different country link now to see if it works.

cheers, and have a great weekend!
K

---

### Post by Papa-san on 2006-04-14
I don't know, but for what it is worth, I got my package of cd's from ubuntu, and four of the five live cd's were bad... I took the good one and burned a couple of copies at 4x with gnomebaker. No issues with them, they work fine. Just hope they know about it!

---

### Post by kchukchukchu on 2006-04-14
hello, papa-san,

oh, ic,  but what does this mean?  So, it's not the original image problem then?    I mean, I checked sum AFTER I burned the CD so that should be the same as the original right?  

I'll try burning at lower speed now as well as a different country image and see if it works...  I'm so anxious.

But, i'm glad you got your one good CD at least:)

K

---

