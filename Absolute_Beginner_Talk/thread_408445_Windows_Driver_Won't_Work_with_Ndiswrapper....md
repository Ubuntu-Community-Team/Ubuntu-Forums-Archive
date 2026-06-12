---
title: "Windows Driver Won't Work with Ndiswrapper..."
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by ImmortalGrey on 2007-04-13
Alright, I've been running Windows for the past 3 weeks because I cannot for the life of me figure out how to get my wireless PCI card to work.

I have a Netgear WG311v3 card, and I'm running the KDE environment... I have Ndiswrapper installed and configured, the step I was on was to install the correct Windows driver using Ndiswrapper... So I hunted down the right driver, and attempted to install it... But I kept getting a message back stating that the driver was incorrect...

So I put in the CDROM that came with the card, and ripped the driver off of that and tried using it, (which works fine in XP), and STILL a no-go.

It's been 3 weeks now, and I really want to get back into Linux.  Can someone walk me through installing this?

Thanks.

---

### Post by Seisen on 2007-04-13
Have you tried a different version of ndiswrapper and what driver are you using?

---

### Post by NICU on 2007-04-13
What version of Ubuntu/Kubuntu/Xubuntu are you using?  When you use ndiswrapper which files are you telling it to use?  Are there multiple files on the CDROM that came with the card?

---

### Post by ImmortalGrey on 2007-04-13
> **NICU said:**
> What version of Ubuntu/Kubuntu/Xubuntu are you using?  When you use ndiswrapper which files are you telling it to use?  Are there multiple files on the CDROM that came with the card?

1.  KDE Version 3.5.5

2.  Ndiswrapper Version 1.38 (I'm almost positive)

3.  The walkthrough guide in the installation wiki told me to use "WG311v3.inf", but now that I think about it, that's not even the driver is it?  It's just the setup info?

4.  Yes, I have multiple files on the CDROM, there are some Adobe Acrobat read files, but as far as drivers are concerned, I have drivers for Windows 98. 2000, ME, and XP, along with those INF files.

---

Now, where do I go from here?

---

### Post by OU812 on 2007-04-13
I have been using ndiswrapper a lot recently, but in slackware. Here is a wiki that I found helpful

[http://alien.slackbook.org/dokuwiki/doku.php?id=slackware:ndiswrapper](http://alien.slackbook.org/dokuwiki/doku.php?id=slackware:ndiswrapper)

You also my want to copy only the .bin, .sys, and .inf files to your hard drive so just the needed files are in one spot.

john

---

### Post by mystman on 2007-04-13
What Kernel are you using and what version of ubuntu?  It may not be starting up if you use some of the kernels.  For 6.10 ndiswrapper won't work unless you use 2.6.17.10-generic, I believe.  That's what I used before I started using Feisty, and it worked fine.  I even have the same card as you.

---

### Post by mystman on 2007-04-13
> **ImmortalGrey said:**
> 1.  KDE Version 3.5.5

I'm pretty sure he meant Ubuntu, not KDE.

---

### Post by ImmortalGrey on 2007-04-14
I've got Ndiswrapper itself to work ...

I have it installed and functioning, the problem is, I have it install the driver from the list of drivers that are supposedly compatible with my PCI Card, and when I check it with 

```
ndiswrapper -l
```

I get "Invalid Driver!".  Yet I've checked and double checked, even looked up my specific information using the "lspci" command and everything, and this is the right driver.  So how can it be invalid?

EDIT:  I'm on Edgy.

---

### Post by OU812 on 2007-04-14
Maybe try downloading the drivers from the manufacturer's website. Perhaps there is a newer version that is more compatible.

john

---

### Post by Shmook on 2007-04-15
I was in the same boat until I copied two .sys files related to the chipset to /etc/ndiswrapper/*driver*/ -- different card tho.

Don't ask me why it worked, but it did. Also, did you goto [the ndiswrapper list?]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")? It's got info on your card and a link to a driver that someone claimed worked.

---

### Post by ImmortalGrey on 2007-04-15
> **Shmook said:**
> I was in the same boat until I copied two .sys files related to the chipset to /etc/ndiswrapper/*driver*/ -- different card tho.

Don't ask me why it worked, but it did. Also, did you goto [the ndiswrapper list?]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")? It's got info on your card and a link to a driver that someone claimed worked.

I've tried both the driver from the list, and the driver that came with my CDROM, neither are working...

Perhaps I should try v2 and v1 of the PCI's model...

@ OU812:  The manufacturer's website offers the same driver from both my CDROM and the Soundforge website. =(

---

