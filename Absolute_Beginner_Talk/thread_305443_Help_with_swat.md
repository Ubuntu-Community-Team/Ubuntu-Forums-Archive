---
title: "Help with swat"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by l.j. on 2006-11-23
Hi guys hope this is a simple one ive installed samba I can see my share on the windows network. but cant access it ive installed swat to edit the .conf file but cant enable it im trying to access through a browser just a little confused i little clarity would be appreciated:D

---

### Post by Gary Nored on 2006-11-26
To use swat you must have netkit-inetd installed. If it is installed first, installing swat will fix the configuration file so that it can be used. 

If not installed first, edit /etc/inetd.conf to remove  #<off># from the line containing the word swat. 

Then restart the inetd daemon:

# /etc/init.d/inetd restart

This is as far as I've gotten. Swat comes up, but the Globals button doesn't show in my copy, so maybe I've done something wrong. 

Regards, 

Gary

---

### Post by Gary Nored on 2006-11-26
And another thing: 

You must have a password assigned to root. Then when you start swat, enter "root" as the user and provide the root password. It should work now.

Cheers,

Gary

---

