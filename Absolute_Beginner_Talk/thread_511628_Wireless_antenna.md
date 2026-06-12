---
title: "Wireless antenna"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by NetMonster on 2007-07-28
Hello everyone :) I'm relatively new to Linux and I'm trying to set up a wireless network with our second computer. I have an ASUS Wi-Fi-AP Solo wireless antenna. Where can I find the necessary software for Ubuntu to recognize it?

Thanks!

---

### Post by agurk on 2007-07-29
Your wireless chipset seems to be the Realtek 8187. As I understand it, by reading other posts on the subject, is that Ubuntu comes with a driver which only lets you connect to unencrypted networks. If you want to be able to use WEP or WPA, you'll need to use either ndiswrapper + Windows driver, or compile a Linux driver yourself. I'd try the latter first, there are some instructions over at [http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187)

---

### Post by NetMonster on 2007-08-05
Thanks, I'll try that :)

---

### Post by NetMonster on 2007-08-05
Sorry, I seem to need a little help here. The first two commands of the suggested script (ifconfig,rmmod) result in errors. It can't find the connection or the module.

BTW sorry if this is a dumb question but what is this "chipset" you mentioned? I've never heard of the term. I guessed it's part of the card, but I should have asked from the start.

(I think I spotted a more appropriate place for my question, I'll post it there and link)

---

### Post by NetMonster on 2007-08-05
I transferred the conversation here:

[http://ubuntuforums.org/showthread.php?t=518229](http://ubuntuforums.org/showthread.php?t=518229)

Let's continue there.

---

