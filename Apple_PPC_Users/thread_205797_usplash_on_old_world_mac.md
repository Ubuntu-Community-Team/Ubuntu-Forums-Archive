---
title: "usplash on old world mac?"
date: 2006-06-29
forum: Apple PPC Users
---

### Post by iamdigitalman on 2006-06-29
hey all. after getting ubuntu 6.06 on my wallstreet, and getting it just the way I like it, now comes the question: how do I enable the bootsplah? the way I boot, is by using a small 64mb partition that holds Mac OS 9.2.2 and bootx. the first 10 partitions are for OS 9, #9 being the one with the actuall OS on it, #11 being my root ubuntu partiton, and #12 being swap. when I use bootx, there is a bunch of text that goes by, then I get to the part where there are a bunch of [ok] s on the right, so I assume that's where ubuntu takes over, as I have seen this back on 5.10. 

so, is there a way to simply show the ubuntu logo? or is that not able with bootx? 

thanks. -digital ;)

---

### Post by nkbj on 2006-06-29
Just add "quiet splash" - without the quotes - to the BootX kernel options line.

---

### Post by iamdigitalman on 2006-06-29
[QUOTE=nkbj]Just add "quiet splash" - without the quotes - to the BootX kernel options line.[/QUOTE]

thanks, but now the splash screen has the same damn rooling vertical lines that it did with the flying text. any way to fix this? it's fine once it gets to gnome, but before that, I've got these ugly lines to deal with.

oh, and when I was searching for how to get linux on an old world mac, bootx was the first thing I came across. it works, but I really dont like having to boot to OS 9 first. is there another bootloader for ubuntu? yaboot is what I have on my B&W G3, but that's a new world mac.

thanks. -digital ;)

---

### Post by nkbj on 2006-06-29
[QUOTE=iamdigitalman]oh, and when I was searching for how to get linux on an old world mac, bootx was the first thing I came across. it works, but I really dont like having to boot to OS 9 first. is there another bootloader for ubuntu? yaboot is what I have on my B&W G3, but that's a new world mac.[/QUOTE]

There is a bootloader named quik which does not require Mac OS, but I have no experience with that.

---

### Post by iamdigitalman on 2006-06-30
[QUOTE=nkbj]There is a bootloader named quik which does not require Mac OS, but I have no experience with that.[/QUOTE]

yeah, I looked into that, and it seems it's still extreamly buggy, as it trys to use the same syscalls as yaboot, and therefore, working with openfirmware on oldworld macs is extreamly risky buissness, I decided to leave well enough alone.

so, anyways, is there any way to get rid of those rolling lines of corruption? would take a pic if I had a cam. really odd. I tryed atleast 10 different kernel arguments, they either dont work, or it makes things worse, ala multicoloured logo, and more rolling lines.

thanks -digital ;)

---

