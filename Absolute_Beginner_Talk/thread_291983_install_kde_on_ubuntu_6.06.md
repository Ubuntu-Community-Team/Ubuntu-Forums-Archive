---
title: "install kde on ubuntu 6.06"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by sadid on 2006-11-03
Hello!
I know this question has been asked before but the instructions dosn't work

i tried this:
1)
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install kubuntu-desktop

[color=red]
Couldn't find any package whose name or description matched "kubuntu-desktop"
[/color]

2)
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install kubuntu-desktop

3)
try with synaptic : repo>add cdrom>update
but nothing happen.

i have one of ubuntu shiped CDs that recieve from shipit.kubuntu.com by mail it`s also OpenCD for windows so might any problem with the CD(is any diffrence between Ship and download cd?)

---

### Post by Polygon on 2006-11-03
try going into synaptic, and eabling the multiverse and universe repos for each of the things you see there (should be things like ubuntu 60.6 LTS, ubuntu 6.06 LTS Updates, ubuntu 6.06 LTS backports, ubuntu 6.06 lts secuirty updates, etc etc

well anyway go to these, click edit (on the ones that say (binary) next to it) and then click all of the checkboxes. Do this for all of them (backports, udpates, lts, security updates) and then close out of the repo window, click update in synpatic, and then try going in the terminal and then doing 

sudo aptitude update
aptitude search kubuntu-desktop  (to make sure that you can actually see the package)
sudo aptitude install kubuntu-desktop

---

### Post by Kateikyoushi on 2006-11-03
I am sure the kubuntu-desktop is not on the ubuntu cd so you need the kubuntu cd if you want to install it from cd.

---

### Post by SunnyRabbiera on 2006-11-03
KDE is on the repositories... though I havent tried a full KDE install yet on ubuntu.

---

### Post by Ben Sprinkle on 2006-11-03
Don't add the CD, just sudo apt-get install kubuntu-desktop from the repositories.

---

### Post by sadid on 2006-11-03
thanks all
i have a dialup internet connection so avoid from any online update

---

