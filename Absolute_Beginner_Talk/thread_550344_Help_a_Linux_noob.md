---
title: "Help a Linux noob"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by Lithumian on 2007-09-13
I have tried Linux before but I always mess up trying to configure something and I have to reload it again. I'm on Windows right now but when I get some answers I'll go ahead and reload again, I have nothing to save anyways hehe.

So anyways, I have tons of problems when I start Ubuntu after a fresh installation, 1400X900 is all nice and funky with pretty colors, so I search and search and I found no solution to the problem. I kept having to restart my xorg file or w/e so I could go back to the desktop without the command line. I have a ATI 9800 Pro Atlantis with a ViewSonic VA1912wb monitor.

When I tried Linux I installed Wine and installed some Window programs, they seem to work but I couldn't install Steam or Steam Powered, because the file wasn't ".exe" and didn't find a good explanation to fix that.

I have Ubuntu 7.04 on a CD  and installed that too like a couple of weeks ago. I'm a Stage6 addict but I couldn't get the videos to work there because it was using some other program to play the videos on Stage6, isn't there some Divx program for Ubuntu?

I'm a Linux noob, so help please. :popcorn:

---

### Post by splintercellguy on 2007-09-13
Not sure about the card issue, but for the WIne thing, the Wine in the Ubuntu repos is very old, 0.9.33. Your best bet is to follow the instructions here: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb). And to invoke MSI installations, you can either do:

wine start installer.msi

or

wine msiexec /i installer.msi

---

### Post by Lithumian on 2007-09-13
Hehe, thanks but I will try that later until I can find the solution to my resolution problem.

---

### Post by Happy_Man on 2007-09-13
For your divx problems, you can install VLC Media Player (sudo apt-get install vlc) and then stream the divx file through that to watch.... that's what I always do.

---

