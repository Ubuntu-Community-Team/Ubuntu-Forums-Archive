---
title: "Black Screen on zenbook (UX32VD) at startup"
date: 2012-07-14
forum: Asus Ubuntu Support (CLOSED)
---

### Post by LudoTW on 2012-07-14
Hello,

I am very new to ubuntu as well as to my zenbook. I have been on the machine for the past 24hrs (with just 4hr sleep). 
I have now a fresh install of the 12.04 release (no kernel update yet) and got rid of window. I use EFI to boot. It boots well.

Well, actually not so. I get a black screen at the startup. I have to put the computer in sleep mode (fn + f1) and wake it up to have the image back. While it's black the HDD works and I can hear the drum sound at the beginning.
Should I update the kernel? What is wrong?

Besides this the screen flickers few times at the bootup, and also if I change its settings (ex resolution).

PS: there are long threads on the zenbook, but it is difficult to find what one is looking for while browsing through their pages, so I thought I would start a new thread specific to the particular issue I have. Please let me know if this is not a good practice!

Ludo

---

### Post by peter rus on 2012-07-16
Hi Ludo, 

You are probably better of running the Quantal development release ([http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)). It works out of the box alot better. Quantal however is currently in alpha state, this might mean it can break any day so it is a bit of risky. But as long as there are no better alternative's I will keep doing this. I have described the procedure here: [http://ubuntuforums.org/showpost.php?p=12105892&postcount=60](http://ubuntuforums.org/showpost.php?p=12105892&postcount=60). If you run in the same problems as I do you could always post in that thread.

If you really dont feel like running Quantal (which is the next upcoming release of ubuntu, in case you didn't get that already ;) there are some repository's containing updated bleeding edge packages (like xorg-edgers and x-swat for example) but I have had limited succes with them.

---

### Post by LudoTW on 2012-07-18
Hi Peter,

Thank you. Besides the black screen, as I mentioned, the display flickers with 12.04. I have followed you, trying (not yet installing) the daily built 12.10 and it seems indeed that there is no more display issue.

Could the flickers be related to what you quote in [your post]("http://ubuntuforums.org/showpost.php?p=12105892&postcount=60"), that is the enabling of the semaphores on the graphic card (writing the word without actually understanding what a semaphore is for a graphic card)?

Has anyone else encountered this infrequent but worrying flicker of the screen on his/her zenbook, specially at the startup and when changing the screen settings?

Ludo

---

### Post by peter rus on 2012-07-18
I did indeed experience that on 12.04 and I dont think it has something to do with the semaphores setting. In one of my posts in the thread ([http://ubuntuforums.org/showthread.php?t=2005999&page=8](http://ubuntuforums.org/showthread.php?t=2005999&page=8)) I described what this do.

I am currently on quantal, but as seen in my last post. This does not work anymore.

---

