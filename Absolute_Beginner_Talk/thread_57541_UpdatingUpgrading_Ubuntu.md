---
title: "Updating/Upgrading Ubuntu"
date: 2005-08-16
forum: Absolute Beginner Talk
---

### Post by EnderTheThird on 2005-08-16
I tried Ubuntu on my secondary computer a few months ago but I never really used it often enough to get comfortable.  I figured I'd try it again on my main computer with a dual boot, but with 5.10 coming out soon, I was wondering how that will work when released.  Does anyone know if I will need to re-install Ubuntu completely or will there be some sort of update procedure so I don't have to format and re-install everything?

Reading through these forums has gotten me really excited to try it out again, so I'm anxious to get my RMA'd HDD back so I can do the install, hopefully by the end of this week.  Unfortunately, I'll still need WinXP for my games (WoW) and for some of my apps for school, but I'd like to get more comfortable with Ubuntu and Linux in general because I love the idea of OSS and the communities behind it.  Thanks for your help!

---

### Post by aysiu on 2005-08-16
When the new one comes out, you may have to change your repositories in /etc/apt/sources.list.

Then, you type these two commands in the terminal, and you'll be up-to-date:

[i]sudo apt-get update
sudo apt-get dist-upgrade[/i]

---

### Post by EnderTheThird on 2005-08-16
Great!  Now if only Newegg would finish inspecting my RMA and get my replacement drive shipped back to me.  It's bad enough I had a 300GB HDD go bad, let alone waiting weeks for the replacement because UPS is slow.   :mad:   Thanks for the information though.

---

