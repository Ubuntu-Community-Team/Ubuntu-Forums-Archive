---
title: "Understanding init.d"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by Neumy on 2007-09-24
Hi all,

I just switched distros to Ubuntu 7.04 server - so far I am loving the change. I use my Linux Box as a LAMP server and like how Ubuntu does not install a bunch of useless programs that could be potential security risks, yet still has all the functionality of a fully loaded distro. Very nice!

I'm not as Linux savvy as I would like - but I can move around with relative ease. Currently, I'm trying to move my login scripts onto the box. 
- I've created a small text menu of a bunch of commands and such whenever someone logs on using SSH. On my old distro, I placed the files in `/etc/rc.d/`. It looks like I need to add my scripts to `/etc/init.d` here, but I can't seem to find the login file to activate my menu. I assumed that it would be `rc` or `rc.local` but when I make my code changes in there, it does not manipulate my login.

Can someone point me to the appropriate file that I need to modify?

---

### Post by Maestro23 on 2007-09-24
This thread may put you on the right path: [http://ubuntuforums.org/showthread.php?t=473823&highlight=login+scripts+in+Ubuntu](http://ubuntuforums.org/showthread.php?t=473823&highlight=login+scripts+in+Ubuntu)

I just ran a keyword search for "login scripts".  More threads out there.

---

### Post by Neumy on 2007-09-24
Thanks for the quick response. I did a search for `login scripts` and had no luck finding what I was looking for. The majority of the threads are regarding the Xwindow login.

Even if I want to echo a quick welcome message when a user logs into SSH using a `echo "**** HELLO ****"`, what file would I put this in to get this working?

Also, when I do login via SSH, the welcome message I get is: 
     The programs included with the Ubuntu system are free software;
     the exact distribution terms for each program are described in the
     individual files in /usr/share/doc/*/copyright.
Where do I find this to modify and/or remove?

---

