---
title: "Slow internet speeds with boot disk"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by thedogisdead on 2007-11-28
Hi everyone.  Been trying out Gutsy with the boot disk for a few weeks.  I am very impressed at how easily it found my wireless connection and how customisable, good looking, responsive and intuitive Ubuntu is.

I'm just concerned that the internet connection can feel extremely sluggish- can this be to do with the fact that I am trying to do everything of the boot disk?

It will veer from my standard, instantaneously page loading broadband connection to a snails pace, dial-up-esque slowfest.

Do you think this would be solved when I come to do a full install?

Thanks very much for your help.

---

### Post by civic_si on 2007-11-28
That has happened to me before and it was the DNS server that I was using. see if your ISP has a different DNS server that you can use and see if that fixes it.

---

### Post by frank002 on 2007-11-28
I Gutsy, disable IPv6.
 
Disable IPv6 this way:
Open a terminal window and type
gksudo gedit /etc/modprobe.d/aliases
scroll to line that reads alias net-pf-10 and change it to alias net-pf-10 off
save the file. Restart Firefox.

---

### Post by frank002 on 2007-11-28
The line should read alias net-pf-10 IPv6  change it to alias net-pf-10 off

---

