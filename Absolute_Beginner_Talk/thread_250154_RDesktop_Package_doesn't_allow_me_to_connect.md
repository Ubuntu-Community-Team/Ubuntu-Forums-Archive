---
title: "RDesktop Package doesn't allow me to connect"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2006-09-03
I installed RDesktop through the Synaptic Package Installer but I still cannot connecto to the Ubuntu box via machine name or IP.  What am I doing wrong?

---

### Post by apiper on 2006-09-03
From [http://www.rdesktop.org/:](http://www.rdesktop.org/:)
> rdesktop is an open source client for Windows NT Terminal Server and Windows 2000/2003 Terminal Services...
Which means that rdesktop won't connect to a box running Ubuntu as its Linux, not Windows...

It sounds like you're trying to set up a remote desktop session on a machine running Linux, in which case FreeNX might be what you're after:

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

Hope this helps!

---

### Post by kc5hwb on 2006-09-03
Well, perhaps I have the name of the package wrong, but whatever it is, it is a package that was listed in the Synaptic Pkg Mgr, so I can't imagine that it wouldn't be supported by Ubuntu.  I installed it thru the SPM, not from a RPM download...there is no reason why it shouldn't work.

I will verify the name of the package and update this thread.

---

### Post by apiper on 2006-09-03
No worries - I could probably have been a bit clearer myself. So here goes:

rdesktop is a tool which runs on Linux machines and lets you **log into Windows machines and run remote Windows desktop sessions**. I use rdesktop at work all the time on my laptop (which runs Ubuntu) to connect to remote machines running Windows 2000 Server and Windows XP, etc.

rdesktop definitely doesn't let you to log into other Linux machines though. That job's done by VNC, FreeNX and others. 

Here's some instructions for setting up VNC - I've not tried them myself, but they seem to work for others (read at least the first 7 posts!)

[http://www.ubuntuforums.org/showthread.php?t=191564](http://www.ubuntuforums.org/showthread.php?t=191564)

Good luck! :)

---

### Post by kc5hwb on 2006-09-03
Ok, I see what you are saying, thanks for the info.  Perhaps I thought that RDesktop worked both ways.  Does FreeNX allow RDP connections coming **into **the box?  I would rather use that than VNC, it just a preference.

---

### Post by apiper on 2006-09-04
The FreeNX **server** sure does, so you'll have to set up a FreeNX server on the box you want to connect to. You'll also need to use the **NX Client** on the machine you're connecting from.

Here's the Wikipedia page on NX (FreeNX is a free implementation of this):

[http://en.wikipedia.org/wiki/NX_technology](http://en.wikipedia.org/wiki/NX_technology)

Have a read of that Wiki page I linked to in my first post too. It should help you set up the FreeNX server and client on your machines.

Cheers :)

---

### Post by kc5hwb on 2006-09-04
I don't want to setup a NX Client on my machines that I connect from, I want to use the MSTSC (Microsoft Terminal Services Connection) that is built into Windows XP.  Is this possible at all?  If not, I may just go with VNC.

---

### Post by apiper on 2006-09-04
Ah I didn't realise that you were usng a Windows machine as the connecting client machine. 

This doesn't really change matters though, as MSTSC won't work for remote connections to Linux boxes (I guess that this is probably because Miscrosoft own the patents on the MSTSC server and won't let anybody implement an open-source version), so you'll have to install *some* form of 3rd-party client software in order to connect to that Linux box. 

FreeNX is more secure than VNC by design, so I know which choice I'd make... ;)

---

### Post by steve.horsley on 2006-09-04
I've also seen people comment on FreeNX being much faster than VNC. I've never tried it myself though.

---

### Post by kc5hwb on 2006-09-04
Ok, I see what you are saying, thanks for the info.  Perhaps I thought that RDesktop worked both ways.  Does FreeNX allow RDP connections coming **into **the box?  I would rather use that than VNC, it just a preference.

---

