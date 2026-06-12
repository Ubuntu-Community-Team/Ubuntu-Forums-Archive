---
title: "&quot;Firewall&quot; Problem with Azureus"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Steggy on 2006-04-28
Hello,

I recently tried using the Azureus bittrroent client, after setting up port forwarding on my router. However, while I have not NAT problem, Azureus is reporting that it is running into a filewall. Because of this (I believe), Azureus is not downloading anything. Now, I should be able to allow Azureus through my firewall--the problem is, I have no firewall on this computer.

I had pretty much given up on the subject and moved on, but then I read in another post on these forums that Ubuntu automatically closes all ports on the computer, acting like a firewall. Now, my question is, would this feature be causing my problem with Azureus? If so, how do I go about letting Azureus work?

Thank you.

---

### Post by capitalistpiglet on 2006-04-28
First install firestarter it is a gui for the firewall, once it is installed run it and add a inbound rule which opens up a port in the 10,000 range, not one of the standard ports. Then just configure azureus to use that port by going to tools>options>connection and selecting that port  as the incomingt tcp listen port.
That should solve your problem

---

### Post by r4ik on 2006-04-28
EDIT: Late again :)
Try,

sudo apt-get install firestarter

Then follow this link,

[http://www.ubuntuforums.org/showthread.php?t=164548&highlight=Azureus](http://www.ubuntuforums.org/showthread.php?t=164548&highlight=Azureus)

Second option,

[http://www.ubuntuforums.org/showthread.php?t=159745&highlight=Azureus](http://www.ubuntuforums.org/showthread.php?t=159745&highlight=Azureus)

Third option do a "Azureus" search.

Good luck !

---

### Post by YuHoo on 2006-04-28
Something to keep in mind, your ISP may block the normal 6881-6889 ports because they see BitTorrent in the same league as Kazaa and other crap. Try higher ports, enable UPnP (Universal Plug and Play) so that Azureus can automatically configure itself, and finally, if all else fails, use bit tornado -- just as good, not as pretty.

---

### Post by linuxfanatic1024 on 2006-04-28
Are you using a so-called "broadband router"? If so, that could be your problem, and the answer would be to tell it to forward certain ports.

I do know for a fact that Ubuntu doesn't have a firewall set up by default, so I don't know what else it could be.

Firestarter could CAUSE problems too, just so you know, but it isn't recommended to run without a firewall.

---

