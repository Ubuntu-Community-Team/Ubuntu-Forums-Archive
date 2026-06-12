---
title: "wg111v2 problem ino its a repeat"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by jimrie on 2007-12-19
hi i have just done a install of 7.10 (which is great by the way) but i am having a bit of trouble getting my wg111v2 netgear to work, it did work to a point, as in it would connect for about 30seconds and then disconnect but then it would show that it is connected but no download or upload or anything loading on the screen, after a while it will show that it is dissconnected and i would try and reconnect, but with no success, i have tried ndiswrapper, but that didn't work, but the instructions that i followed were very confusing and for a prievious version of ubuntu,
details of my computer
packard bell mc 2469
nvidea 7300se
pentium d 820
dual booting xp essentials and ubuntu
1 gb ram
wg111v2

any help would be greatly appreciated, if of slow response it is because i am having to switch between os's to tell you lol, i need very simple instructions as i am a total noob, i know if anyone can help it will be you, thanks again 

james

if you have a solution please dont hesistate to email me at 
[email]jimrie0148@googlemail.com[/email]
(please dont abuse it, it is my personal - thanks)

---

### Post by jimrie on 2007-12-21
thanks for all your help, i guess what i heard about you guys is wrong, i mean the "linux revelution" will never happen with you picarks here :confused::confused::confused:

---

### Post by sennep on 2007-12-25
I also have the WG111v2, this is what I did to make mine work

[http://ubuntuforums.org/showthread.php?t=615568#5](http://ubuntuforums.org/showthread.php?t=615568#5)

---

### Post by jimrie on 2007-12-25
cheers m8 will have a go of that, seems your the only person who can help and on christmas, once again thanks alot:)

---

### Post by sennep on 2007-12-26
No problem man, let me know if it works :)

---

### Post by jonmartin on 2007-12-26
> **jimrie said:**
> cheers m8 will have a go of that, seems your the only person who can help and on christmas, once again thanks alot:)
Hi, wheenie, maybe people have other stuff on their mind on christmas ... dunno, just a thought.

Anyway, I've got the same problem and it sortof went away when I switched to using ndiswrapper and the windows driver. 

Search for ndiswrapper in synaptics and install it. Also install the gui conf tool for ndiswrapper; ndisgtk. After installation you can start it from your System -> Administration -> Windows WIreless Drivers. You need to point it to the correct inf file that came with your windows driver. Complete info on that is available at the list of supported cards in the ndiswrapper wiki at ndiswrapper.soruceforge.net. After installing the driver into ndiswrapper, start wireless config from within the ndiswrapper gui tool, and then you should be all set.

My experience so far is that ndiswrapper is more stable than native linux drivers ... some of them requires firmware code that you must extract from windows drivers anyway.

---

### Post by jimrie on 2007-12-27
jon martin why dont you just crawl into a hole and die, oh thats tough calling people online, sennap ur a decennt guy cheers for your help :) gonna try it in a min

---

