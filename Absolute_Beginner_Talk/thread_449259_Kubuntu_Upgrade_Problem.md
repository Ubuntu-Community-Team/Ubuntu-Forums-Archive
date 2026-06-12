---
title: "Kubuntu Upgrade Problem"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by doctorj on 2007-05-20
Hi,

I have just installed Kubuntu 6.10 and have after the install upgraded 149 packages as was indicated to me these were available.

At the end of doing this a Upgrade Wizard ran through and suggested that Adept Package Manager could be closed and a distribution upgrade tool would start to upgrade me to a new version of Kubuntu.

The problem is that the "distribution upgrade tool" does not start. I click on the "Finish" button provided me on the Upgrade Wizard. Nothing happens. Adept just remains on the screen and no upgrade tool starts.

What can I do to effect this upgrade?

---

### Post by Kobalt on 2007-05-20
What you can do is this : first **backup any important data**. Then, make sure to have the kubuntu-desktop package installed. Edit your /etc/apt/sources.list as root. Change every occurrence of edgy to feisty. Comment (put a # at the begining of the line) every repos that is not official Ubuntu. Run this : ```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade
```
And make sure everything is fine before rebooting : ```
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
```

---

