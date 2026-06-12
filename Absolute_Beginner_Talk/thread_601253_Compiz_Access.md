---
title: "Compiz Access"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by corowakid on 2007-11-03
I'm attempting to enter the following:

sudo cat "# Fusion-icon PPA" >> /etc/apt/sources.list
sudo cat "deb [http://ppa.launchpad.net/maco.m/ubuntu](http://ppa.launchpad.net/maco.m/ubuntu) gutsy main restricted
universe multiverse" >> /etc/apt/sources.list
sudo cat "deb-src [http://ppa.launchpad.net/maco.m/ubuntu](http://ppa.launchpad.net/maco.m/ubuntu) gutsy main restricted
universe multiverse" >> /etc/apt/sources.list
sudo apt-get update
sudo apt-get install fusion-icon emerald emerald-themes

which is a series of terminal entries designed to get me access to Compiz and its components. I get "Access Denied" when I make the 1st entry, which appears strange (altho I am new to Linux) when I thought sudo would give me access.

Anyone care to hazard a guess as to why I can't go further. Thanks for any inputs.

Found the answer in earlier posts.

---

### Post by Maestro23 on 2007-11-03
**/etc** and everything under it is owned by** root.**  You need root privileges to change/edit anything in there. ** sudo** must preface your commands.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jw5801 on 2007-11-03
> **corowakid said:**
> I'm attempting to enter the following:

sudo cat "# Fusion-icon PPA" >> /etc/apt/sources.list
sudo cat "deb [http://ppa.launchpad.net/maco.m/ubuntu](http://ppa.launchpad.net/maco.m/ubuntu) gutsy main restricted
universe multiverse" >> /etc/apt/sources.list
sudo cat "deb-src [http://ppa.launchpad.net/maco.m/ubuntu](http://ppa.launchpad.net/maco.m/ubuntu) gutsy main restricted
universe multiverse" >> /etc/apt/sources.list
sudo apt-get update
sudo apt-get install fusion-icon emerald emerald-themes

which is a series of terminal entries designed to get me access to Compiz and its components. I get "Access Denied" when I make the 1st entry, which appears strange (altho I am new to Linux) when I thought sudo would give me access.

Anyone care to hazard a guess as to why I can't go further. Thanks for any inputs.

Found the answer in earlier posts.

Take a look at [this](http://ubuntuforums.org/showpost.php?p=3666276&postcount=948) post that I made in another topic to explain the difference between the command you're attempting to use (cat and echo have the same affect in this situation) and a command I suggested the other person use which works correctly. It's a rather detailed post so I link to it instead of copying it here.

---

