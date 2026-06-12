---
title: "Wine"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by bmarilena on 2005-10-05
Quote:
Originally Posted by xodeus
Hi.
This guide is for all those folks that want to install Wine the easy way and Maintain for the newest version.
This is taken from [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb) WinwHQ's own guide.
First add Wine Repo to your sources.list file
Code:

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak sudo gedit /etc/apt/sources.list &

and add the repo at the end of the file
Then update your apt and install
Code:

sudo apt-get update sudo apt-get install wine

__________________________________________________ ________________________
If you want to use this version with Internet Explorer then use Sidenet Wine Configuration Utility
For other applications you can use the guides at Franks Corner
__________________________________________________ _________________________
Update. I can't really test stuff here anymore as I've changed fully to amd64 and can't manage to chroot to test. So please, if you have any tested additions to this post, post it as "UPDATE #1" as reference to update post 1 and I will do so.


Hi
I tried, but after # sudo apt-get update
I got this message:
E: Malformed line 21 in source list /etc/apt/sources.list (dist)
I mention that the line is exactly the one I introduced myself (deb-src [http://wine.sourceforge.net/apt/binary/](http://wine.sourceforge.net/apt/binary/) ).
what should I do next?

Thanks a lot for help

Marilena

---

### Post by Ampersand on 2005-10-05
Make sure you've got a space before 'binary'

It looks like it should be:

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

---

### Post by bmarilena on 2005-10-07
:) thanks, you're right the space was missing, but still, didn't manage to configure...

Marilena

---

