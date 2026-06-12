---
title: "Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multive"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by billh1241 on 2006-03-07
I can not get the backports to install. I get alot of lines like this:  Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)  
 Any ideas?  I thank you for the help, in advance.

---

### Post by carlosqueso on 2006-03-07
try clicking the refresh/reload button in synaptic, or using ```
sudo apt-get update
``` from the commandline.  That should clear that up.

---

### Post by billh1241 on 2006-03-07
that is what I receive in terminal when I do the sudo apt-get update.  Many lines like the couldn't line.

---

### Post by aysiu on 2006-03-07
See the bottom part of this page:
[http://www.psychocats.net/linux/sources](http://www.psychocats.net/linux/sources)

---

### Post by billh1241 on 2006-03-07
I followed the instructions on the resources page and it did not work.  I did it twice and the same result.  Seems to get some and then fails and also stated there are duplicates.  Maybe I should just wait until tomorrow and try again with the resources instructions.   Thanks.

---

### Post by billh1241 on 2006-03-07
I just tried again, hate to give up...and it worked...I must have bad fingers that do not type the right letters..  Thanks again, you guys on the forums are just great, and do not make up newbies feel like complete dummies.

---

