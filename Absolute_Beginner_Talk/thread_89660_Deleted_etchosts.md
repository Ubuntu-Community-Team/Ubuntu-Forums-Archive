---
title: "Deleted /etc/hosts"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by sjh on 2005-11-13
In a nutshell, I was messing around and deleted my /etc/hosts file.  I have a backup of the file but can't restore it because I can't get root privileges.  Seems sudo needs the hosts file to work.  Is there a way out of this problem?   I have not set a root password.

---

### Post by darth_vector on 2005-11-13
i did the same a while back. i dont remember having problems with sudo, though i remember having problems loging into graphical mode.

press Ctrl-Alt-F1, this will get you a textual login. login as yourself and type

sudo su -

and you should get a root shell. then you can restore your original hosts file.

press Ctrl-Alt-F7 to get back to your textual thingymigig.

---

### Post by jeremy on 2005-11-13
Alternatively you could do it using a live CD, ubuntu, knoppix, whatever...

---

### Post by sjh on 2005-11-13
Seems sudo has a problem authenticating without the loopback working, so it was Knoppix to the rescue.
Thanks for the replies.  All is well now.

---

