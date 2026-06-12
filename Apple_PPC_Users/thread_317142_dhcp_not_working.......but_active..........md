---
title: "dhcp not working.......but active........."
date: 2006-12-11
forum: Apple PPC Users
---

### Post by bigbadben on 2006-12-11
I use my new install off xubuntu on a nethwork (dhcp).

Iff i look under network dhcp is active and running. And it did detected all the numbers it needed for ip and the rest(automatic).

But going on the net is not working or even trying to see other computers to transfer files is not working.........???.........dhcp is active but not doing anithing......???????.....

any easy help :-?

---

### Post by bigbadben on 2006-12-11
oh mannnnnnnnnnn.....
nsf was not install by default........so i went into synaptic and installed it


Now everything works.........( i hope )......

---

### Post by stream303 on 2006-12-11
If by going to the net means you can ping but can't surf (resolve dns names), check your /etc/resolv.conf file for your isp's primary and backup nameservers.

This is a common problem seen by those behind routers.  I wrote a little howto for the networking forum that might help:

[http://www.ubuntuforums.org/showthread.php?t=307758](http://www.ubuntuforums.org/showthread.php?t=307758)

---

### Post by samden on 2006-12-12
> **bigbadben said:**
> oh mannnnnnnnnnn.....
nsf was not install by default........so i went into synaptic and installed it

Now everything works.........( i hope )......
What is nsf? 

If this fixes it, I would love to know what it is - I'm having heaps of problems myself. As it is I do not have synaptic connecting to the net until I fix the problem, but can install files off the install cds or download on another computer and transfer them.

Thankyou.

---

### Post by bigbadben on 2006-12-12
nsf = nsf kernel server
+
samba
=
all needed for share folder......


When i did try to install the 2 software, the network was working.
(i was so happy...)
after i did a restart, just to make shure everything was ok......
after restart the internet and my dhcp network was ok......
for now!!@@
so i went to sleep sooooooo happy.
but
:confused: 
this morning i tried again, and the laptop does not go no more on the internet. i cant have acces to the respertory and file sharing is nla...

w t h...](*,) 


i havent tried your tutoriel yiet ( stream303 ).
as soon as i come back from short trip to middleland :mrgreen: , ill try..
thx btw.

---

### Post by samden on 2006-12-13
I managed to figure out you meant nfs kernel server and installed that :) (Samba already installed). I had no joy at all with this - didn't make a difference on my machine. Still no internet.

Keep us posted on any success you have - whatever solves it for you may do for me as well.

---

### Post by Jimi... on 2006-12-17
I was having similar problems as you samden, absolutely no network. I went into network settings and my wired connection was disabled, I enabled it within properties but I also has to enable it in the main network settings part.

---

