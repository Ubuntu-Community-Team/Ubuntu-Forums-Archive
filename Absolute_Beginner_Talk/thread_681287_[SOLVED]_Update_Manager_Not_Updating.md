---
title: "[SOLVED] Update Manager Not Updating"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by MicrosoftlessMesh on 2008-01-28
Good evening Ubuntu community.  I have something I need to throw out there and see if anyone has an idea of what could have gone awry.

I have had two installation of Ubuntu on this box since initially installing this fine operating system.  When I installed it the first time I had quite a few many updates (over 100) to install initially.  I installed them everything was fine.

As time went on a faulty CD-ROM drive, and my desire to setup my partitions on a different hard drive, I installed Ubuntu the second time, but this time I was not connected to the internet.

Now my update manager says "Your system is up to date" all the time, and has never prompted me to install any updates at all.  Would not being connected to the web affect this somehow?

Any help would be appreciated.  Thank you in advance.

---

### Post by jpeddicord on 2008-01-28
Update Manager needs an Internet connection to be able to get update information. Unless you have an update CD/DVD from a newer version of Ubuntu, you will not be able to get these updates nor will Update Manager find them.

---

### Post by nowshining on 2008-01-28
yes - u'll have to either wait - i think it checks once every 24hrs. or go in and check manually for updates

u can also do it thru ther terminal

sudo apt-get update

let it update / enter ur pw - don't worry as it won't show as u type - just type it out as usual, and when done press enter,

then once it checks for updates

sudo apt-get upgrade

after that it should ask if u want to continue or not or just continue if asked y/n press the letter y on ur keyboard for yes or n for no, then press enter. Once done u should be back at a command prompt - type exit to close the terminal or press the X on the terminal window.

---

### Post by RomeReactor on 2008-01-28
Hi. If I read your question correctly., you performed the installation without an internet connection, but you are now connected to the internet, correct? If that's the case, Ubuntu disabled your software sources during the installation process when it didn't find an internet connection. Go to 'System->Administration->Software Sources' and on the first tab check all the repositories, except for source.

---

### Post by MicrosoftlessMesh on 2008-01-29
> **RomeReactor said:**
> Hi. If I read your question correctly., you performed the installation without an internet connection, but you are now connected to the internet, correct?

Yes you were right indeed.  Thank you so much for your help.  I did as you suggested and even still my *Update Manager* said my system was still up to date, but I did the commands that **nowshining** suggested and when I ran those commands all kinds of stuff started updating.  

I cannot thank you guys enough.  I am sorry also if my words are jumbled, I am a fifteen years+ Windows user, and I'm trying to learn all that I can.  Nice avatar BTW!

---

### Post by nowshining on 2008-01-29
lolz, it's okay :) u'll get the hang of it soon, then well u'll just fell at home in ubuntu after awhile and forget all about Microsoft - just about of course and of course the virus/spyware mess will be gone and u;'ll have a sound mind now :)

---

