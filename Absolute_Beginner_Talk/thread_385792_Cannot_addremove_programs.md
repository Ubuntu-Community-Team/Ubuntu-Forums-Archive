---
title: "Cannot add/remove programs"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Billy Bong on 2007-03-16
Hi Ubuntu community,

I installed Ubuntu the other week as an iso I downloaded via torrent from the website. What can I say...It is the biggest revelation in my computing life since I found out about Opera 3.11!!

But I have hit a snag...I wanted to get my Brother laser printer to work and failed...As a real linux newbie, I think I downloaded the wrong driver (for a start...ahem), the wrong package for installation and anything else I could do wrong. It didn´t work. I didn´t really care.

But now, whenever I try to add or remove a program I get the following screen ( sorry about the screen shot but I couldn´t seem to cut and paste the dialog to Text Editor.)

It really goes without saying but you help would be appreciated...greatly. If I was still in windows mode and at this early stage I would just reinstall but I think Ubuntu is beyond that.

Cheers
Billy Bong

---

### Post by Luk0r on 2007-03-16
Does it ask you for your root password whenever you run the Add/Remove window? It looks to me like it doesn't have superuser privs..

---

### Post by Billy Bong on 2007-03-16
Yes, I have to give my password...Ubuntu then goes through the motions but reports this at the end.

Cheers

---

### Post by Billy Bong on 2007-03-16
I tried again to install / remove a program and this is what I could cut and paste as the first screen.

E: hl1670nlpr: subprocess post-installation script returned error exit status 127

Billy

---

### Post by jhenager on 2007-03-16
Do you get an error trying to add another program? (such as a game or other small app)
This would tell us if it is just the printer, or Add/Remove.

---

### Post by ahmatti on 2007-03-16
Try running "sudo dpkg --configure -a" from the terminal.

---

### Post by Billy Bong on 2007-03-17
Hi jhenager and ahmatti,

Um, I can´t seem to add or remove any app.:( 

I ran ¨sudo dpkg --configure -a¨ from the terminal and it replied with the error messages about hl1670nlpr. I have since re-strated and ran it again, hoping to cut and paste the info, but now it&#347; just blank.

The Package Manager has lit up and if I roll over it, a balloon pops up saying

¨Unknown Error:
´exections.System error´ (E:The package hl1670nplr needs to be reinstalled, but I can´t find an archive for it)¨

I have d/l the packages from brother again and the installer just says I don´t have permission or it is corrupted (regardless of what printer package I try to install).

Cheers
Billy

---

### Post by Billy Bong on 2007-03-17
Sorry All,

I reinstalled Umbuntu edgy. I would have rather have found the problem, as that is the way forward in understanding but my limited knowledge of linux frustrated me. The support was great. Thanks to everyone. 

I´ll try and install the Brother printer drivers again and if I re-produce the problem...

I´ll be back.

Billy :)

---

