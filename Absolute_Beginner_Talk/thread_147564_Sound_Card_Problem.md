---
title: "Sound Card Problem"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by gigi1234 on 2006-03-20
Hi 'yall

I just installed Ubuntu on an old Dell box. The sound card is not being detected. I had been running Puppy Linux on this machine and the sound was detected just fine. The card as detected by ALSA in Puppy Linux is "CS4236B". 

I am kind of lost. What should I do to get the sound working under Ubuntu?

I found a command (sudo lspci -v | grep audio) that is supposed to detect the sound card but when I type this in nothing at all happens.

I have looked around on the forums but haven't found what else to try.

Any suggestions? Thanks a million in advance!

---

### Post by gigi1234 on 2006-03-20
I think I got it figured out. Just ran modprobe and that seemed to detect the  sound card.

---

