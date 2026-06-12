---
title: "Ubuntu won't detect any wifi connections"
date: 2018-03-15
forum: Apple Hardware Users
---

### Post by posuceius on 2018-03-15
Hello, I am currently running on an Ethernet connection to access the Internet. I am a Linux newbie and I just recently installed Xubuntu with the GNOME interface.
The WiFi is seen as "working" however when it searches for WiFi connections none are found.
I am running a MacBook Pro late 2010 model with an Intel Core 2 Duo 2.4GHz.
The Internet adapter being used is a Broadcom 14e4:432b one (from lspci).
I have been told to use a wget from github which displays a bunch of info for help with these situations and I've got the pastebin link for it here: [COLOR=#111111][http://paste.ubuntu.com/p/hZnyNfBDs3/](http://paste.ubuntu.com/p/hZnyNfBDs3/)
[FONT=arial]I have tried going into "additional drivers" and using the additional driver that shows up in this. When I make it NOT use that alternative driver, that page tells me that my WiFi adapter is not working. The WiFi works on OSX, just not Ubuntu.
I have also tried using sudo apt-get install bcmwl-kernel-source to no avail, it makes no difference. I also tried apt-get for b43-fwcutter and other things related to b43 etc.

If I could get the WiFi adapter working in Ubuntu it'd be great as I need to use this Laptop at work and I'd rather run Ubuntu instead of OSX.

Thanks![/FONT][/COLOR]

---

### Post by kannanmanism on 2018-03-15
This problem is solved in this link: 
[https://ubuntuforums.org/showthread.php?t=2269723](https://ubuntuforums.org/showthread.php?t=2269723)

did you try this code below as said in the above link after re-installing the driver ?

sudo modprobe -r b43
sudo modprobe b43

---

### Post by posuceius on 2018-03-15
Hello, after doing what was done in the link above, my wifi shows connections however I'm unable to connect to any. It asks for the password but then after that it just waits a few seconds and then it stops trying to connect to the outer.

---

