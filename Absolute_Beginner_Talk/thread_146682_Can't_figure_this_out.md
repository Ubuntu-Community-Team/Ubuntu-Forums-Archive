---
title: "Can't figure this out"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by Rickster on 2006-03-18
I have installed ubbuntu 5.10 server following the directions of this site
[http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p3](http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p3)
and everything went very well till I typed in /etc/network/interfaces...
I keep getting this error bash /etc/network/interfaces: permission denied.

I'm fairly new but have managed to get the gnu version networked and working fine awhile ago and I'm learning but not very good with the command line version.

could anyone help????[http://ubuntuforums.org/images/smilies/eusa_think.gif](http://ubuntuforums.org/images/smilies/eusa_think.gif)

---

### Post by IYY on 2006-03-18
The HowTo is telling you to edit the /etc/network/interfaces file. Now, since it's in the /etc directory, it will not be accessible to a regular user and you'll have to edit it with root access. Suppose you want to use the "nano" text editor:

**sudo nano /etc/network/interfaces**

---

### Post by xenmax on 2006-03-19
If you just typed "/etc/network/interfaces" in terminal and hit enter, its an attempt to execute the file - /etc/network/interfaces - which normally would be without execute permissions in which case you will get error you mentioned.
Why are you trying to exec this file? 
If you want read/edit the file, use any editor you prefer with sudo command like IYY suggested.

---

### Post by xenmax on 2006-03-20
Ignore my post above. Not sure what i was thinking! :mrgreen:

---

