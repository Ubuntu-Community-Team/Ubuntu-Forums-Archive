---
title: "About to switch out my video card"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by mattisking on 2006-01-20
I've got a running (mostly) Ubuntu Dapper box that's gradually gone through updates ever since before Warty was released. That entire time it's had an ATI 7500 video card.

I just got an ATI 9200 to replace the 7500. I certainly don't need help switching out the card. What I'd like to know in advance, if possible, is what to expect from Ubuntu after the switch? 

Will it pick up the new card and reconfigure my xorg.conf (this I rather doubt). If not, what do I need to do to tell X that I have a new video card and I'll appreciate it greatly if it would reconfigure itself to use it?

Thanks in advance.

---

### Post by dueY on 2006-01-20
If it doesn't work and things are severely messed up then get to the console by pressing ctrl+alt+f1

Then type ```
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure your settings.

---

### Post by mattisking on 2006-01-20
Thanks!

---

### Post by dueY on 2006-01-20
[QUOTE=mattisking]Thanks![/QUOTE]

No problem.  And if it's anything like NVIDIA you will want to download the proprietary drivers if you haven't already...

---

### Post by mattisking on 2006-01-23
Wow, that went fantastically badly. I was down for days... nearly had to give in and just reinstall... I might still go this route because of how badly things are running right now. Ultimately I had kernel problems, bus failures, all sorts of stuff. What a nightmare. Anyway, my display is now running worse than before and I UPGRADED from an ATI 7500 to an ATI 9200. I'm sure I'll sort it out now that the forums are back online.

---

