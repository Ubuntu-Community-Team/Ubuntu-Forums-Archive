---
title: "xmms package not available?"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by SDREnate on 2006-05-07
I'm new to linux, and I've been attempting to install xmms for a couple days, and nothing seems to be working. 
When I type "sudo apt-get install xmms", I get this message:

Reading package lists... Done
Building dependency tree... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate

I used the Ubuntu Package search and discovered that xmms is included there. 
So, I don't know what to do anymore. I've tried logging in as root.  I've searched around the forums and with google, but really can't find any pertinent info.

---

### Post by glotz on 2006-05-07
Doesn't XMMS come with Ubuntu? Tried Synaptic package manager?

---

### Post by JLu on 2006-05-07
Did you first update the package information from the repositories before trying to install xmms?  Try 
```
sudo apt-get update
sudo apt-get install xmms
```
(Alternatively, if you use Synaptic as glotz suggests, click the "Reload" button to update the info, then search for xmms and try to install it.)

---

### Post by Mustard on 2006-05-07
I would suspect there is a problem with your /etc/apt/sources.list if the above solution from JLu doesn't work.  I've seen some sources.list files with all the repositories commented out lately.  I'm not sure how people are doing it, but it pops up every now and again.

---

