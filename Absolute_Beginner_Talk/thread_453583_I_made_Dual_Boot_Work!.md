---
title: "I made Dual Boot Work!"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by pwnage on 2007-05-24
Hi all, I am brand new here and brand new to Ubuntu/Linux.  I love it.

I had recently followed the instructions on how to install Ubuntu Feisty Fawn-Dual Boot with Windows XP, from my maximumPC magazine.

I did everything step by step although when I was all finished, I could boot into Ubuntu but not into XP.  It turned out that the XP partition somehow became "in-active" (something GRUB does, or more likely something I did?).  Anyways, I knew that the XP partition was ok and intact, but I just needed to "re-activate" it.

So I downloaded a copy of Ultimate Boot CD 4.03 from easynews, booted from that CD, found a program on the BootCD called "Active@ Partition Recovery-demo", pointed that to my XP partition, hit scan.  When it finished scanning, I did not receive any information that anything happened - so I quit the boot cd and rebooted my computer (remove the Ultimate Boot CD from the CD drive).  Next, the GRUB boot manager screen showed up displaying Ubuntu, other Ubuntu options, and Windows XP available as choices (as it did before although XP previously would not work, just Ubuntu).  I choose the XP partition and Voila, it booted up.  I then restarted the computer and this time chose Ubuntu, viola, it also boots up.  

SO...I wanted to post this hoping that it could help others get their dual boot systems working.  And PLEASE if any of the steps I used could be detrimental at ALL, please tell me by posting a better alternative.  I have ZERO idea what I am doing right now, I just know that this re-activated my XP partition, and allowed me to dual boot properly.

GOOD LUCK and Ubuntu/Feisty Fawn is AMAZING!!!!!!!!!!!!!!!!!!!

---

### Post by Bordy on 2007-05-24
Pwnage-
Glad that worked out for you. Did you let the installer partition your drive out, or do it yourself? I got extremely lucky in that I had no idea and no guidance for what I wanted to do, so I just loaded gparted form its own liveCD, shrunk my XP drive down, and installed Kubuntu to the remainder, so I never faced that problem.

So it showed up in grub but you couldnt access it?

---

### Post by Hobo Joe on 2007-05-24
Glad you like it!

Welcome to the forums. :)

---

### Post by pwnage on 2007-05-24
> **Bordy said:**
> Pwnage-

So it showed up in grub but you couldnt access it?

Yes it showed up initially but couldn't boot it..weird.  When I fdisk'd, i could see the XP partition said "inactive" so I figured I'd try to re-activate it...by looking around, I read that Ultimate Boot CD had some tools, and it turns out the first one I tried seemed to work!!!!

Yes, I did use partition magic 8 in the very beginning to partiion my XP drive into a 30GB chunk that I planned to use for Ubuntu, and a 2GB chunk for the swap file.

Maybe I did something wrong there :)

But either way, whenever I come across something that actually works for me, I plan to post it!  :)

GL!!

---

