---
title: "Old but working Ubuntu Feisty, moving to new hardware. Scared!"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Hopworks on 2007-12-19
I'm ready to move to my new hardware. From Athlon 2600+ to P4 Prescott 3GHz. Also to a better video card. Scrapping my desire to use my 1650 pro 512mb because many have said getting radeon ATI hardware to work is a real chore. nVidia 6600 GT is much more friendly. Am I wrong?

But what I'm really worried about, is that Ubuntu Feisty Server WORKS on my 2600+ athlon. I noticed that the footprint for all the meat of my install is very small. How should I approach this? Copy it to a second drive so I can pull what I need from it? There is so much I had to configure, apache2, MySQL, SSH (SSL), PHP, MythTV, etc.

I don't wanna do that from scratch. Any suggestions? I certainly appreciate it!

Hop

---

### Post by Lord_Dicranius on 2007-12-19
Regarding the ATI vs nVidia video cards.  I have an ATI card and it's a big pain in the booty.  I don't have experience with an nVidia card in Ubuntu, but from what I've read it seems to be more friendly than ATI video cards.

---

### Post by mmb1 on 2007-12-19
I'm just the opposite, I have no experience with ATI cards, but I can tell you that my nVidia card works like a charm.

---

### Post by Palmyra on 2007-12-19
> **Hopworks said:**
> I'm ready to move to my new hardware. From Athlon 2600+ to P4 Prescott 3GHz. Also to a better video card. Scrapping my desire to use my 1650 pro 512mb because many have said getting radeon ATI hardware to work is a real chore. nVidia 6600 GT is much more friendly. Am I wrong?

Traditionally, nVidia is recommended over ATI.  I don't have either one, and I can't make personal recommendations.  I can forward you to:

[http://ubuntuhcl.org/pub/](http://ubuntuhcl.org/pub/)

See what others have said.  

> But what I'm really worried about, is that Ubuntu Feisty Server WORKS on my 2600+ athlon. I noticed that the footprint for all the meat of my install is very small. How should I approach this? Copy it to a second drive so I can pull what I need from it? There is so much I had to configure, apache2, MySQL, SSH (SSL), PHP, MythTV, etc.

I don't wanna do that from scratch. Any suggestions? I certainly appreciate it!

How about you Ghost the drive?

---

### Post by mmb1 on 2007-12-19
Hopworks, i think you've got the right idea, copying to a second drive seems to be the best solution.  Depending on the size of your footprint, you may be able to use a pen drive.

---

### Post by misfitpierce on 2007-12-19
ATI has come a far way in the past year. It is becoming simpler but yes Nvidia is still simpler i'll give you that. ATI is still my hero tho :)

---

### Post by Hopworks on 2007-12-19
> **mmb1 said:**
> Hopworks, i think you've got the right idea, copying to a second drive seems to be the best solution.  Depending on the size of your footprint, you may be able to use a pen drive.

I think my footprint is about 6 gigs. And I'm sure there is a lot of fat in that too. Problem is, I never really explored where your critical stuff is, in regards to MySQL configs, and the other components of LAMP and SSH, SSL.

In windows, it's your documents and settings, my documents, etc. In Ubuntu, I never figured out where my critical stuff is.

I know, just reinstall and go after it, but I didn't say it before... This LAMP server was my first experience with Linux, specifically Ubuntu. I came a long way, getting my XFS file system working on a slave drive, configuring MythTV to work, getting my database server and apache2, and PHP working like I want, and Samba. All a product of all the threads I read here, and responses from gurus. A lot of research!!!

I jumped through flaming hoops to get all that working, and so much research and trial and error.

I guess all that gained knowledge would be reinforced via doing it again, just didn't want to have to.

Hop

---

### Post by Hopworks on 2007-12-30
I don't know if this was the best thing to do, but I decided to see what would happen, and sure enough, everything works.

Without reinstalling, I just plugged the new hard drive into my new hardware, and everything works!!! Unbelievable! I had an issue with the NIC, but configured it, and now I'm online. WEIRD!

I'm sure I have underlying issues with the hardware, but the system is stable, from a FEISTY install on AMD hardware to INTEL hardware without hardly a twitch! I LOVE LINUX!

Hop

---

### Post by yaknowwat on 2007-12-30
Is that athlon a 64-bit (XP and 64 are both 64bit designs) version if it is, then it may and probably is more powerful when compared to a P4 prescott.

^ sorry didnot read post above my bad either way.

yes Linux is open source / freeware that is the advantage to it so it doesn't have all that Protection etc to bog down the system and allows easy painless upgrades.

---

