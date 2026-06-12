---
title: "unable to launch firefox"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by bigbrownbear on 2007-06-24
I have ubuntu 7.04 installed on a clean machine, no other OS, and 2GHZ speed and 512MB Ram.  I cannot launch firefox through the icon or the application menu. All I get is the spinning wheel, then nothing, not even an error message. Synaptic states firefox is fully installed however. Can't access help files (if they exist) as they are not launching either. All other applicaitons work fine. Has anyone had this problem, or present a solution to getting firefox to appear? MY ADSL meter is ticking away...I'm new to linux, not highly skilled technically with computers. Thanks all

---

### Post by Crafty Kisses on 2007-06-24
> **bigbrownbear said:**
> I have ubuntu 7.04 installed on a clean machine, no other OS, and 2GHZ speed and 512MB Ram.  I cannot launch firefox through the icon or the application menu. All I get is the spinning wheel, then nothing, not even an error message. Synaptic states firefox is fully installed however. Can't access help files (if they exist) as they are not launching either. All other applicaitons work fine. Has anyone had this problem, or present a solution to getting firefox to appear? MY ADSL meter is ticking away...I'm new to linux, not highly skilled technically with computers. Thanks all

You might want to try to opening Firefox from the terminal, and see if it's any different.

---

### Post by Seisen on 2007-06-24
Does it say anything about another instance of firefox running?

---

### Post by bigbrownbear on 2007-06-25
Thanks all for the suggestions, problem is solved, firefox is launched and I am online. 
For those that have the same problem, I will explain. I went into terminal and wrote several commands (actually everyone I could think of) including: firefox google.com (nothing), gksudo firefox (nothing), Alt+F2, firefox safe-mode (nothing) and eventually gksudo apt-get install firefox browser (E: couldn't find package browser)- even though it was said by the package manager to be fully installed! 

Before jumping off something high, I decided to re-install the whole OS, but using the disc from Canonical; the originally installed disc was a copy purchased from linux specialists OSDisc.com. Both were 7.04, none were Beta version. Install went flawlessly, and Bingo, firefox arrived along with help files which were also missing on the original install. 

I am not going to flame OSDisc, there may have been a problem with my disc's media, or with the copying process particular to the disc I was sent, though I will make a bug report to them in case it's rectifiable. Also their customer service and delivery is first rate.  But for anyone who has taken the same route as me and found the same problem, it may be better to re-instal with a Canonical disc.  Good luck.  

And I started to learn to use terminal-bonus.

---

