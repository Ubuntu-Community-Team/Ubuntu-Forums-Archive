---
title: "Firefox loading is a DOG"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by professorTHC on 2007-11-10
Hello there Linux community =)
Im having some the same problem with firefox as i was before i performed a clean install.
Basically every webpage i try to load will take a long time to start, and then act normally. Which is usable, but it just adds a "....." period when waiting for a page to load, which as you know can get annoying really fast.
Another problem im having with Ubuntu is the scrolling. i dont know if its some graphical problem or whatnot ,but scrolling is REALLY jagged. And when i minimize and maximize firefox for example, the toolbar and rest of that top part there turns black for a second. 
as well as the top bar of a maximized window, it looks like it splits in half and looser color becoming grayed out in one half.
thats about it =P

---

### Post by kerry_s on 2007-11-10
Are you using the right drivers for your vid card?

---

### Post by frank002 on 2007-11-10
You don't say what version of Ubuntu you are using. When I had Feisty, Firefox was fast. After updating to Gutsy, it slowed down to a crawl. Someone on this board suggested I disable IPv6. That did the trick. If you are on Gutsy, disable IPv6 like thus:
 Open a terminal window and type
 gksudo gedit  /etc/modprobe.d/aliases
 Find the line that says alias net-pf-10 IPv6 and change it to read
 alias net-pf-10 off
 Save and restart Firefox. It should be ok.
 Hope this helps.

---

### Post by bithkits on 2007-11-10
What are your system spec's?

---

### Post by professorTHC on 2007-11-10
ooh that did the trick! gracias, thanks for your help guys =D

---

