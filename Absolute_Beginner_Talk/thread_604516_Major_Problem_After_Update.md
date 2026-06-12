---
title: "Major Problem After Update"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by FireJin3 on 2007-11-06
HI, I hope you guys can help me.

I installed Ubuntu Studio(amd64), and it was running great for the past 2 weeks.
Recently I was trying to install cinelerra on my system, but it didn't work because certain dependencies weren't working, so I gavce up.

When I restarted the system, I saw that I had a butt load of updates, that I installed, when I restarted my system again, everything went to hell.

- There is no sound, either gstreamer is messed up or it doesn't see my sound card.
- There are no icons, not even the "close" or minimize icons usually on the top right.
- The applications bar on the top left doesn't open up at all.
- My mouse is twitchy and can't keep steady.

I hope any of you guys can help, thanks.

---

### Post by juantovarm on 2007-11-06
ok, sometimes the system breaks down after a ditribution upgrade. that's why some people do not recommend upgrading but fresh installs -if you go for the latter it's best to have your home partion separate, if not, just copy it to a cd including the hidden files and once you have your new system up and running, just copy everything back to your new home folder.-

In your case you could either:
1- go back to 7.04 and if you'd like cinerella for ubuntu studio, here are the repos: [http://cvs.cinelerra.org/getting_cinelerra.php#packages](http://cvs.cinelerra.org/getting_cinelerra.php#packages)
 , just add them to your /etc/apt/sources.list  file. You can do that by typing in the terminal: sudo pico /etc/apt/sources.list and add them at the end. After that remember to do in the terminal: sudo apt-get update  and then you'll be able to install cinerella

2- do a fresh install of gusty. 

IMHO, either way is a lot easier than troubleshooting every problem you have

---

### Post by FireJin3 on 2007-11-06
Alright, thanks. 

I reinstalled gutsy and got myself up and running, I&#314;l be doing a lot more backups from now on.

---

