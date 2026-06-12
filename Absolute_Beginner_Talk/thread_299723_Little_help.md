---
title: "Little help"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Halonut1 on 2006-11-14
Ok, so i have ubuntu 6.06 finally running, and its on a laptop that in no way possible can get online(i cant only get dailup and its AOL dailup!!!) so, is it possible to get a DVD decoder/program(i dont know about this kinda stuff, atleast on linux) and a MP3 decoder, just like put it on a Thumb drive and install it?

any help would be great! once i get my DVD's and MP3's running on ubuntu the only time i will use windows is for photoshop(i am not good with gimp..)

---

### Post by Marsolin on 2006-11-14
It is possible to install deb files individually. The only thing you have to be careful of is to make sure that you have the dependencies as well.

Do you have access to another computer running Ubuntu with internet access?  If you do I suggest running the following

sudo apt-get clean
sudo apt-get -d install packagename1 packagenam2

The first line is to remove any previously downloaded files. The second will download, but not install the packages you want, including missing dependencies. Replace packagename1 and packagename2 with the programs you want.

Regarding your last comment, [Krita]("http://linuxappfinder.com/package/krita") makes a good alternative to Gimp if you are interested in trying to find a Photoshop replacement.

---

### Post by Halonut1 on 2006-11-14
No, i do not, see i formatted my hard-drive on accident when installing it on my laptop(long story short, hit the wrong button) and my parents are now paranoid, so no i dont. any other way? thanks for the help btw.

---

