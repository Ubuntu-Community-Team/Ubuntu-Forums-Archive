---
title: "[SOLVED] Ubuntu 8.04 (Hardy Heron) on a Mac Mini"
date: 2008-06-09
forum: Apple Hardware Users
---

### Post by meshal on 2008-06-09
Hello everyone. Im a mac user and I was thinking of putting the new Ubuntu OS on my Mac Mini(1.83GHz Intel Core 2 Duo, 1 GB Ram, MB138LL/A) through boot camp. All I could find was how to install Ubuntu 7.04 on it ([https://help.ubuntu.com/community/Mac_mini](https://help.ubuntu.com/community/Mac_mini)). I was wondering if it was possible and if the procedure was any different from the one mentioned above. Also, I just upgraded my Macbook Pro's Ram and I heard that the old Ram that was in there is compatible with the Mac Mini so im going to try and install it (This gives me 2 GB, which makes Ubuntu run super fast from what I hear). Finally, I was wondering if I would have any major hardware problems if I add Ubuntu 8.04 to my Mac Mini (Such as the wireless Apple keyboard and mouse, WiFi card, Ethernet, soundcard, etc...)

Thank you!

---

### Post by cyberdork33 on 2008-06-09
that page should be the same (basically) for 8.04. There are not many hangups on Mac Minis. Feel Free to come ask about any issues you might have.

---

### Post by meshal on 2008-06-10
So I just partitioned my Hard drive into two parts, inserted The Ubuntu x86 disc that i burned into my Mac mini, and rebooted. I held down alt and was able to get to the main Ubuntu menu and Ubuntu began loading. After that the screen just goes black and I cant see the desktop. I dont know whats wrong cause it seems to be loading and all. I also tried to click install Ubuntu from the menu but that just lists errors. What do I do to get to the Ubuntu desktop?

---

### Post by cyberdork33 on 2008-06-10
listing some of the errors you are talking about would help...

Did you veryify the disc?

You might try the alt install disc as well.

---

### Post by meshal on 2008-06-10
Yes I did verify the disc. It seems to be ok. All I get now is a black screen after the ubuntu loading screen. I tried to repartition and repeat but all the disc does is give me the loading bar and then the screen turns black. Whats the alt install thing you were talking about?

---

### Post by meshal on 2008-06-10
Hey guys. I just found a perfect method in a blog that helps a lot. It describles exactly my case. Heres the link to anyone who might need it [http://blog.costan.us/2008/04/ubuntu-804-on-mac-mini.html](http://blog.costan.us/2008/04/ubuntu-804-on-mac-mini.html)

---

### Post by cyberdork33 on 2008-06-11
It sounds like xorg is failing to start correctly. I don't understand how that blog post helped with this issue, as it does not even address anything like you mentioned.

Just FYI, there are 2 versions of the install discs. The first is a LiveCD that you can boot and use Ubuntu. The second is the alternate install disc. This disc is a textmode installer with no desktop. Since it does not start up xorg, you can get your system installed on much more hardware, then make adjustments to the installed config files to get things working.

---

