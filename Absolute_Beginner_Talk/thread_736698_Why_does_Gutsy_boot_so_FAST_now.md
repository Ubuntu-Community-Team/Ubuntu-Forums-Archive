---
title: "Why does Gutsy boot so FAST now?"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by paxorius on 2008-03-26
This isn't a problem but rather a strange quirk that I don't understand.  Ever since I installed Startup-Manager (a tool for easy editing of the GRUB menu.lst) my laptop boots up about 3 times faster.  The only things I changed with the tool were to eliminate the memtest and recovery kernel choices from the menu and add some color. So, now the only choices on the menu are Ubuntu (default) and XP Pro listed under Other.  It used to take 3 minutes for my computer to boot to the desktop.  Now it takes 30 seconds to the login screen and then 24 seconds from there to the desktop.  Why the speed increase?
By the way -- I was gonna use PCLinuxOS but it wouldn't let me access my flash drive.... so, Ubuntu it is!

I have a Thinkpad T40 (Pentium M 1.4GHz, 1GB RAM, ATI Radeon 7500, 40GB HDD partitioned into equal parts for XP and Ubuntu).

---

### Post by Dekkon on 2008-03-26
The power of tweaking can actually give some decent results. ;)

---

### Post by Victormd on 2008-03-26
3 minutes?? I think there was something very wrong with your machine because my takes ~30sec. to boot...
Startup-Manager could have done something that helped you A LOT! :)

---

### Post by jken146 on 2008-03-26
Changes to usplash settings (usually the resolution) can have a marked effect on boot times.  You can look in /etc/usplash.conf to do it manually.

[http://web.telia.com/~u88005282/sum/index.html](http://web.telia.com/~u88005282/sum/index.html)

---

### Post by chilinski on 2008-03-27
My X41 was always slow to start, too. When I ran XPPro on it, I'd turn it on and go get coffee in the morning. Most times I'd log off at night rather than do a shutdown because it was so slow. Ubuntu was signficantly better but still slow. 

A month ago, I got an EEEPC. I run Ubuntu on it. It boots in about 20 seconds.

---

