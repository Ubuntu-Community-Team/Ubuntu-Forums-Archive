---
title: "Making Apt-Move CD"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by Unoone on 2006-05-19
Ok, I'm working my way through the Ubuntu tutorial on using apt-move to make a backup repository cd.  I am stumped at "must make an apt configuration file- ~/myapt.conf". How do I make this file from the terminal and what dir do I place it in? BTW, I added more .deb's to the apt cache that I intend to backup. Can I re-run the process with apt-move and write over the "mirror" dir files?

Also, concerning the commands:

rm dists/breezy/Release
apt-ftparchive -c ~/myapt.conf release dists/breezy/ > Release
mv Release dists/breezy/Release

I think that success in this next step relys on making the &#8220;myapt.conf" file. Thanks for your help. ](*,) :D

---

### Post by aysiu on 2006-05-19
~/myapt.conf is the same as saying /home/unoone/myapt.conf

---

### Post by Unoone on 2006-05-20
Thanks. I really need to get to know more Linux commands. Or is that "debian" commands? I don't know. The only time that I use a Linux command in Ubuntu is when I have to configure or install something. And that's on the days that I'm actually using Linux or a computer. Thanks for your help.

---

