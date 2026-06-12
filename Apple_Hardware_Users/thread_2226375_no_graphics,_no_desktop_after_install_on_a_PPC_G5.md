---
title: "no graphics, no desktop after install on a PPC G5"
date: 2014-05-26
forum: Apple Hardware Users
---

### Post by Denis_Roy on 2014-05-26
Got my hands on a MAC G5 ( G5/2.0 DP 4GB), so I downloaded Ubuntu for the MAC (powerPC). I have a small hard drive to test this machines capabilities,  I also clean wiped it. So, the live cd boots, I get to the desktop and most apps, including the install starts and I cant see any content. Is, there a command to change the video resolution? My guess its using a video driver which is non conducive to my hardware.

---

### Post by bapoumba on 2014-05-29
*Thread moved to **Apple Users**.*

---

### Post by Denis_Roy on 2014-05-29
Tried installing lubuntu on an apple power mac PPC G5, it has two graphic ports (if it makes any difference).  Using the live CD and getting a half functional  desktop (Most app had no content), couldn't install with the install program. So, I used the alternate CD, install Lubuntu 14.4 LTS and now all I see is a mouse pointer and that's it, black screen. I can get to TTY 1 - 5. So, anyone have any ideas?

---

### Post by bapoumba on 2014-05-30
*Thread moved to **Apple Users**.*

---

### Post by Denis_Roy on 2014-05-30
I didn't know there was a dedicated forum for the Mac users. Anyway, I got tired trying to installing with half the graphic's. So, I installed with the alternate CD, which works. Unfortunately you end up with a dark screen and a mouse pointer.  And I posted anything thread. Help!

---

### Post by coffeecat on 2014-05-30
Threads merged, and thread retitled to the more descriptive title

---

### Post by luigiburdo on 2014-05-30
here more infos about :)

[http://ubuntuforums.org/showthread.php?t=2221421](http://ubuntuforums.org/showthread.php?t=2221421)

note if you have a Nv video board for now "debian wheezy 7.5" is the best for this configuration ... but  "no audio"
with lubuntu with nv video boards need be better fixed

---

### Post by Denis_Roy on 2014-05-30
I did read that thread, but I'm not sure it applies to me. HE mentions that he connected two monitors to two cards for the GUI to show up, I think. I on the other hand have a mouse pointer appearing, with a black screen. It's something to look at, but I'm not hopeful.

---

### Post by pauljwells on 2014-06-03
Long story short. Sell it. Background [http://ubuntuforums.org/showthread.php?t=2143402]("http://ubuntuforums.org/showthread.php?t=2143402") You picked the worst machine in the world for linux

---

### Post by rsavage on 2014-06-04
Dennis, my guess is you are falling back to the fbdev driver.  This normally happens to radeon users and is well documented on the known issues page.  

In my experience, 12.04 remains the best version to try and still has nearly 3 years of support.  As Paul noted there is a problem in 12.04 with one particular G5, but I believe that is not yours.

---

### Post by Denis_Roy on 2014-06-07
Well, I looked at my hardware, it a NV card. And the last guy who stated it worked said he changed cards to a ATI. So, I did install 12.4, but upgraded in the process, cause I had the same problem. 12.10 suck also.

---

### Post by rsavage on 2014-06-08
> **Denis_Roy said:**
> So, I did install 12.4, but upgraded in the process, cause I had the same problem.
I doubt it.  
 > 12.10 suck also.
Linux is not for you.

---

### Post by bapoumba on 2014-06-08
Hum.

---

