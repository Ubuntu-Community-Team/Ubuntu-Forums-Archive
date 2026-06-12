---
title: "What do dpkg --get-selections and dpkg --set-selections do?"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by harisund on 2006-05-01
Could somebody give me a nice example of the above 2 in action? 

I am thinking something along the lines of a backup after reinstallation or something like that.

I just saw the two switches and want to know whether anybody has used them at all, and if so under what circumstances. 

Thanks !

---

### Post by mjm115 on 2006-05-01
To find out more info about dpkg, you can take a look at [this site]("http://www.opensourcemanuals.org/manual/dpkg/").

To answer your questions though:

To make a local copy of the package selection states:
**dpkg &#8722;&#8722;get&#8722;selections**


You might transfer this file to another computer, and install it there with:
**dpkg &#8722;&#8722;set&#8722;selections**

Note that this will not actually install or remove anything, but just set the selection state on the requested packages. You will need some other application to actually download and install the requested packages, i.e. apt-get or Synaptic.

---

### Post by az on 2006-05-02
[QUOTE=harisund]Could somebody give me a nice example of the above 2 in action? 

I am thinking something along the lines of a backup after reinstallation or something like that.

I just saw the two switches and want to know whether anybody has used them at all, and if so under what circumstances. 

Thanks ![/QUOTE]


So I go visit my brother who is on dialup.

I stick in my usb drive, open a terminal and run

dpkg --get-selections > file

and I save that file to my usb drive and take it home.

Once home, I boot up my system which is running a fresh install of breezy and run:


cat file > dpkg --set-selections

and then 

sudo apt-get dselect-upgrade

and apt will download and install all the packages that are installed on my borhter's box.  I can then save everything in /var/cache/apt/archive to a cd (wiki.ubuntu.com/AptMoveHowto/simple) and bring it to him.

---

### Post by harisund on 2006-05-02
Ah now that"s an interesting example. Thanks !

---

