---
title: "How 2 Update Opera 9"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by Zmija on 2006-07-31
How 2 Update Opera 9 ... Ubuntu 6.06 LTS.... 

Version 9.00 
Build 344
Platform Linux
System i686, 2.6.15-26-386
Qt library 3.3.6

I used search but i Did not see the answer :(

---

### Post by Kimm on 2006-07-31
If thats what you have installed then your good to go.
It should just be a mather of downloading the correct package, and then install it...

sudo dpkg -i *package*

---

### Post by moma on 2006-07-31
Download Opera 9 from 
[http://www.opera.com/download/?platform=linux]("http://www.opera.com/download/?platform=linux")
Choose "**Other/Static DEB**" package.

Your download will propably land on $HOME/Desktop.
$ [COLOR="Green"]ls -l $HOME/Desktop[/COLOR]

Install it 
$ [COLOR="Green"]sudo dpkg -i opera-static_9.0-20060616.1-qt_en_i386.deb[/COLOR]

---

### Post by Zmija on 2006-07-31
Ok.... THNX

---

### Post by _simon_ on 2006-07-31
Personally I have been getting the weekly builds and finding them a big improvement!

Latest linux one is build 400

[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

[http://snapshot.opera.com/unix/Weekly-400/intel-linux/](http://snapshot.opera.com/unix/Weekly-400/intel-linux/)

---

### Post by Zmija on 2006-07-31
Cool... it's working fine (build 400)... but... 

Did "dpkg -i "uninstalled build 344 or?

---

