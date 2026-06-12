---
title: "Quiet boot?"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by habtish on 2006-11-17
I am a novice user and don't have the knowledge or skills to figure this out...
When I was running Dapper, during a boot, I could see all devices being initialized and if they passed or failed. This was somewhat informative as I would try and get help to get solutions on how to get my devices that were not recognized by Ubuntu integrated.


After upgrading to Edgy, All I get while booting up is a blank screen for about 15 - 20 Secs.


I read some posts on how the grub menu was setup in quiet mode under edgy and took that option out. Now I get output from grub while booting up (a flash of messages only lasting about 1.2 secs) and then I get the blank screen until Ubuntu loads up my Desktop.

Is there a way to get those messages back on or is it something that has been discontinued in edgy?

I hope I am clear enough in this post... I appreciate your help..

---

### Post by earobinson on 2006-11-17
dose the screen go blank like it is changing resoultions, if so i think your pretty much shot in the foot unless you use a different launcher (we changed how things are loaded in edgy) :( ... but i could be wrong

---

### Post by Bachstelze on 2006-11-17
You could also disable the cheesy splash screen and get back to the old-school bootup with all the esoteric text scrolling on your monitor to impress your friends :D

---

### Post by earobinson on 2006-11-17
how can that be done?

---

### Post by Bachstelze on 2006-11-17
In your /boot/grub/menu.lst the kernel lines end with 'ro quiet splash'. Removing 'splash' will get you a quiet boot with basically the same info that were on the pre-Edgy boot splash but in text mode and removing also 'quiet' will be the hardcore boot :D

---

### Post by Gaweph on 2006-11-17
so quiet splash, is what edgy has by default?

The ubuntu logo, and a progress bar, that is all i see, i kinda lke it, and it will be familiar to windows users, which is good becuase they wont get freaked out by all the text (Good move IMO)

---

### Post by Bachstelze on 2006-11-17
I still think the pre-Edgy boot splash (with some basic info) was better since it sometimes helped to troubleshoot if something went wrong during bootup. But honestly, it doesn't make that much of a difference.

---

### Post by jd65pl on 2006-11-17
I posted a poll on this topic before edgy was released. [http://ubuntuforums.org/showthread.php?t=280014](http://ubuntuforums.org/showthread.php?t=280014)

---

### Post by earobinson on 2006-11-17
thanks for the info guys!

---

### Post by habtish on 2006-11-17
On reading the other thread < vote > , People were suggesting removing the "quiet" option would fix this issue. I have done this and have not found it helpful. Are there extra configurations that need to be modified (usplash??) to activate verbose splash on boot?

To make things clear, I am not even getting the Ubuntu splash screen with a progress bar, the screen goes blank (like its changing resolutions as earobinson said)

---

