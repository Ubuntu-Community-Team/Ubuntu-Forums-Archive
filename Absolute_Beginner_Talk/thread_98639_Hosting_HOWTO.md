---
title: "Hosting HOWTO??"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by pompeyjohn on 2005-12-03
Hi there,

I currently have two web site both using paid for hosting, and was considering hosting them myself on my ubuntu machine. Is this particularly difficult to do? and it there a howto for this?

cheers!

---

### Post by Koybe on 2005-12-03
It's quite easy. You juste need to learn a bit about apache2.
There is a straight on tutorial [here](https://wiki.ubuntu.com/ApacheMySQLPHP?action=show&redirect=Apache)

But you can find other information on the [Apache Foundation Site](http://httpd.apache.org/docs/2.0/)

Good luck

---

### Post by Terry of Astoria on 2005-12-03
I figured it out and did it. I even have a php/mysql server that works. It took me  (no expert) a few hours, but it is worth it. I got webcalendar and textpattern working. It's going to be an online news site for my area.
  Of course, you'll need the bandwidth. . .
There's help on the forums here if you want to try. 
I used a separate machine for my server because it's probably a good idea.
Usually if I'm not mistaken , most server admins don't have a gui installed on their server. I do but I don't think I ever used it for configuring the server. 
In fact, once I had openssh-server installed, I simply logged in from my workstation in order to set up my server. I then found had total command of it from the command-line, and further, that I was able to do it from there.  :-)
See "server talk" - [http://ubuntuforums.org/forumdisplay.php?f=45]("http://ubuntuforums.org/forumdisplay.php?f=45")

---

### Post by pompeyjohn on 2005-12-03
Thanks so much guys. Something else to add to the reading list!!

The three things I have found about linux so far

1. I never expected to read so much
2. I never expected to learn so much
2. I never expected to enjoy it as much as I do

This whole free computing thing is pretty damn groovy :D 

Thanks again for the replies - much appreciated.

---

### Post by greenway on 2005-12-03
You might want to find out if you're on a static or dynamic IP first. If your ISP provides you with a static IP; you good to go! If you're IP is provided by a DHCP  server at your ISP; you might want to look into Dynamic DNS first before you start setting up your server (or afterwards, doesn't really matter but ofcourse you would like others to be able to find your website).

for articles on DDNS, take a look at:

[http://www.webmonkey.com/webmonkey/03/11/index2a.html?tw=backend](http://www.webmonkey.com/webmonkey/03/11/index2a.html?tw=backend)

[http://www.linuxhomenetworking.com/linux-hn/dns-dynamic.htm](http://www.linuxhomenetworking.com/linux-hn/dns-dynamic.htm)

---

