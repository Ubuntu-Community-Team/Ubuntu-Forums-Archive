---
title: "Installation stuck at 59%..."
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Thrasonic on 2007-02-24
Hey all, I'm installing 6.10 onto a hard drive and it has been stuck at 59% now for ten or so minutes.  Any thoughts on if it's supposed to do this, how to recover, what to do, if there's a way to see maybe an error log or something?

---

### Post by robophred on 2007-02-24
I crashed my laptop ubuntu install several times because of that.  It turned out that it was just taking several hours to download the packages.
Are you using the LiveCD to install it?  Or the alternate cd?
I had to use the alternate cd to install on the laptop (its cd-rom didn't work, so I set up the net boot), and the terminal interface just gives "Please wait..." when downloading files.

---

### Post by Thrasonic on 2007-02-24
Ah, maybe that's it.  It's the Live CD.  The PC's not hung and I see no hard drive activity at all, but I'll assume it's what you're saying and see if it changes over the next few hours...

---

### Post by robophred on 2007-02-24
I found that it was the download when I noticed that the laptop hd was periodically making a noise (light wouldn't light up though).  I later fixed it by installing only the core and not selecting the desktop environment, and installing that later with apt-get.  The result was a slightly screwy Ubuntu install which doesn't like OpenOffice fonts and has a grey-on-gray progress bar.  Then again, I am using the unstable Feisty.
You could try the alternate install cd to see if it works.

---

### Post by Golfred on 2007-02-24
I had exactly the same problem. I used the disk checker and found copy errors on the CD I'd burned from the ISO. I burned the ISO again at half my CD writer's max write speed and not only did I get an error free CD that installed smoothly but the burn time was actually less than when using the highest write speed!

Good luck, you'll be happy when everything is finally installed.

---

### Post by Thrasonic on 2007-02-24
Does the DVD download include all the apps so that nothing has to be downloaded during installation?  And if so where do I got download it?

---

