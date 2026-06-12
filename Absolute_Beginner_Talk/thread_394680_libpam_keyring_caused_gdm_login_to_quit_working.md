---
title: "libpam_keyring caused gdm login to quit working"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by tschneiter on 2007-03-27
Hi all-
On Feisty here (has been rock solid up until now). I was recently following steps to make it so I wouldnt have to enter my keyring password at login, as it seemed silly to log in, then type my password again to get on a network. 
At any rate, I followed the blog post written here: [URL="http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/"]
http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/[/URL]


After logging out, I can no longer log in to gnome/X! I can ctrl-alt-F1 to get to command prompt and go from there, but no gdm login. How the heck do I fix this??


Thanks for all of your help,
-confused.

---

### Post by octavianh on 2007-03-28
I ran into the same issue 2 days ago.  To fix it quickly, follow these steps:

- use CTRL-ALT-F1 to switch to the commandline console
- login to your normal username
- use "sudo -i" to go to root user mode
- use "apt-get remove libpam-keyring"
- use "reboot"

should work normally now <crosses fingers>

---

### Post by tschneiter on 2007-03-28
Actually, I tried that and it didnt cut the mustard. I still couldnt log in for a while, until I commented out everything that had "keyring" in the PAM files. Now, im back to work but I still would like to not type in my password twice on login/restore...


Hummph.:confused:

---

### Post by DSn0wMan on 2007-03-28
I would really like to log in without haveing to subsequently log in to the network manager. I wonder if this should be reported as a bug, or a feature request?

---

### Post by tschneiter on 2007-03-28
> **DSn0wMan said:**
> I would really like to log in without haveing to subsequently log in to the network manager. I wonder if this should be reported as a bug, or a feature request?

The point of installing libpam_keyring was that it SHOULD have made it so we didnt need to log in twice. Apparently many people have been able to get it working properly.

It isnt a bug, nor a feature request, as you should have to enter a password for your keyring, and the features are already in place to make it happen...
Now, a bug report on the feature, that may be a possibility.

---

### Post by DSn0wMan on 2007-03-28
I figured it out. The howto that you where following was not right. To get it woking there is only two steps.

1. sudo apt-get install libpam-keyring
2. add the following line to the end of /etc/pam.d/gdm: 

@include common-pamkeyring

I restarted, logged in and network manager did its thing without asking for a password.

---

### Post by tschneiter on 2007-04-02
Brilliant!

Thanks for the tip, everything seems to be proper now.

---

