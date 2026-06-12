---
title: "Best/easiest way to transfer my music from my iMac to Ubuntu PC?"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by northerndude81 on 2007-09-15
Here's the story:  I have much, much music on my iMac laptop, and, correspondingly, on my iPod.  Dilemma is that I just built a desktop PC and put Ubuntu on it, now I plan to sell the iMac laptop and use the PC with Ubuntu on it exclusively.  How can I get all my music onto the Ubuntu machine?  From my understanding I will have to reformat the iPod in Windows (thereby losing all the music stored on it) before I can use it with Ubuntu, so I assume I can't simply plug the iPod into Ubuntu as it is and "rip" the iPod data onto my Ubuntu machine.  I thought about simply burning all my music to CDs from the iMac, but that would be more trouble than I'd like (I have a TON of music).  What is the simplest way to accomplish what I want to do?

Oh also I tried to "network" my iMac and Ubuntu PC by just connecting one end of an ethernet cable to the Mac and the other end to the PC to see if I could share the files that way, but nothing happened.  I know nothing about computers and networking so if that was a really dumb idea sorry, but I just thought I'd say what ideas I'd had.

---

### Post by Palmyra on 2007-09-16
You could attempt networking the two computers, but I can't say how well this would work, because I have never attempted to do this myself.

I have moved a bunch of files from a desktop to my first laptop, and then to my second laptop, and each time, I used an akward method.  Basically, everything was uploaded to a free online host, and from the recipient computer, I downloaded everything I previously uploaded.  I would not recommend this in your case, or any other person's case if there are better options.

If you downloaded the music legally from iTunes, I believe iTunes allows you re-download any files you have already paid for.  If this is the case, simply download everything from your Ubuntu PC.  The problem is, if I am not mistaken, iTunes or anything like it, is not available on Ubuntu.

I can't tell how you easy networking a Mac and Ubuntu computers is, but I am sure it is possible.  Keep an eye out.

---

### Post by dwhitney67 on 2007-09-16
You can install either an SSHD or an FTPD on your Ubuntu system.  I'm almost certain that Macs come with an SSH client, and undoubtedly FTP.

Alternatively you can burn your music to CD or DVD and move it over that way, and have a backup in case the worst should ever occur in the future.  I bet there are thousands of people who purchase music, but never think to back it up on permanent media.  They believe that their HDD will last forever.

---

### Post by northerndude81 on 2007-09-16
Yeah I thought about burning it to CDs but it'll take about a million CDs.  (I don't have a DVD burner.)  Was looking for a quicker/easier way.  Anybody?

---

### Post by Paul133 on 2007-09-16
You could put all thefiles on your iPod (not in the iTunesDB folder so it'll play, but just on the root of the iPod, treating it as an external HD and then copy everything off it onto Ubuntu. For the record, Ubuntu will not play iTunes DRM'd files. You'll have to get rid of the DRM, either through Tunebite, or by burning and re-ripping the songs (use a CD-RW, not CD-R's).

---

### Post by dwhitney67 on 2007-09-16
Here in the US one can purchase a 500 GB "My Book" external storage HDD for $159 (goto amazon.com).

Seriously, the easiest way _for me_ would be to network the two systems together, then transfer the files across using Secure Copy (scp), which requires an SSH-daemon to be running on the Ubuntu system.

If you are not comfortable with networking, SSH, or even FTP, then go with CDs, DVDs (buy an external drive), or mass storage.

---

### Post by GuitarRocker2562 on 2007-09-16
I am 99.99% sure that ubuntu can read macpods, and therefore, follow apples tutorial for copying music from a old mac to a new one via iPod, and just correspond the copying to the new mac to the folders in ubuntu.

---

### Post by SendDerek on 2007-09-16
Crossover ethernet cable?

---

### Post by Brightbelt on 2007-09-16
I'm not very knowledgeable in this area but I have converted an iPod from a PC format to a Mac format and I kept all my music in the process.

I did it through a program called I-Pod Copy. See [www.wideanglesoftware.com](www.wideanglesoftware.com)  It costs about $19. I don't know if it will handle a Linux OS or not, but there ARE many other iPod copy programs and one of them might handle a Linux platform.

Also Apple allows so many transfers (like 5) to new computers in terms of playing purchased content. 

Good Luck, Frank B.

---

### Post by Onythias on 2007-09-16
I had a similar situation when I recently moved all of my music to my PC running Ubuntu.  I had a mac formatted Ipod, and GTKpod recognized it and could pull the files off just fine.  The only two hang ups I had were that I couldn't edit (write) the database, so I couldn't then add files in the reverse, and gtkpod seemed like it couldn't get get m4a sound files (thankfully I didn't have too many of those).

---

### Post by moon2js on 2007-09-16
I have never heard of an iMac laptop, but any relatively recent Apple machine should be able to do Windows and Unix style file sharing out of the box.

Also, I wouldn't bother trying to get music off the iPod itself. Just transfer your iTunes library on the Mac (which contains the original versions of what's on your iPod) to your new computer. The iPod's way of storing your music is all obscured and complicated (and you will need special software), and it's best to get your music collection from the source.

If any of your music is DRM'ed, then I would look into how you can play that on Ubuntu before you transfer. I have no experience with DRM.

What you need is a physical connection between the two computers; ethernet cable is probably the easiest, but you can't use a regular ethernet cable directly between two computers. You need to plug the ethernet cable from Computer A to a router and another cable from Computer B to the same router (thusly creating a LAN).

Or, as someone already mentioned, you could get a special crossover ethernet cable (as any tech guy at a computer store) and then you can stick that directly between the two computers sans-router.

After you've got a direct connection, there's tons of ways to move files. You can set up the 'buntu box with samba, ssh, or ftp and then connect to it with the Mac (or vice versa) and get/drag files over.

If that sounds daunting, you could what Paul133 said. Reformat the iPod in Windows with file-storage enabled (the original files of the music collection should be in the iTunes library on the Mac) and then use the iPod as a glorified external storage device - copying the iTunes Library to the iPod in the Finder, NOT iTunes.

---

