---
title: "Install Ubuntu on g3 Laptop"
date: 2008-04-10
forum: Apple PPC Users
---

### Post by deamon_knight on 2008-04-10
I have an old G3 laptop [_Apple PowerBook G3 333 (Bronze KB/Lombard)_]("http://www.everymac.com/systems/apple/powerbook_g3/stats/powerbook_g3_333.html")

I wanted to setup a dual boot with OSx 10.3 & Ubuntu. Install worked well with 7.04 live CD, however I have Gutsy on all my other linux installs and missed alot of the features. I tried to install Gutsy and no luck, live CD won't boot (Busybox, Known Issue, no luck with suggested fixes) and the Alt Gutsy install fails when detecting the CDROM drive. I don't understand THAT error at all, but whatever. I tried the new Hardy live from the daily beta and at least the live CD booted. With that hopeful signal I installed, however, at about 86% the install fails reporting "Bad Archive Mirror'. I also don't seem to have any network access from the live CD ( I know the network works in OSX and the previous install of 7.04) Any suggestions on how to get a version later than 7.04 installed?

Thanks

---

### Post by stream303 on 2008-04-10
Hmm..  have you burned the install cd's at a very low speed, even though it seems to install?

I thought hardy had that repository thing fixed, but maybe not yet.  I had to copy

/etc/apt/sources.list.apt-setup
to
/etc/apt/sources.list

This worked, but I found the repos were wrong thanks to Somethingkindaweird.  All the references to ubuntu-ports should now be archive...
[http://ubuntuforums.org/showthread.php?t=740394](http://ubuntuforums.org/showthread.php?t=740394)

---

### Post by slacka-vt on 2008-04-10
I have had the "bad archive' error before. This will also happen if the server is overloaded
and your connection times out. You should try it again as your failed installation was not a result of your machine but rather a "botched" connection with the repository. There has been a lot of updates lately and the servers have been getting "hammered" I'm sure.

~s

---

### Post by deamon_knight on 2008-04-10
My concern is that the problem is a lack of network support. I was not able to connect to the net in the live CD. I'm not sure if its a lack or RAM (256 in this system) or network support in hard or another factor. I'll download the latst build and take another shot.

---

