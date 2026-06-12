---
title: "su - command does it exist in ubuntu?"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by bcashman on 2006-07-21
Hi,

Didn't know where else to put this. I installed kububtu and all seems to be working fine, but in the terminal I typed su -, and it asked for a password. I entered mine and it failed authentication. I know during installation I wasn't asked for a root password so how do I get su to work? Sorry if im in the wrong forum.

Bob

---

### Post by Daremo on 2006-07-21
> **bcashman said:**
> Hi,

Didn't know where else to put this. I installed kububtu and all seems to be working fine, but in the terminal I typed su -, and it asked for a password. I entered mine and it failed authentication. I know during installation I wasn't asked for a root password so how do I get su to work? Sorry if im in the wrong forum.

Bob

use sudo instead of su

---

### Post by moma on 2006-07-21
I want to add this

Your should use **sudo** instead of **su** in *ubuntu. Root account is by default locked & closed in Ubuntu for security reasons.  [COLOR="DarkRed"]Note that sudo requires your own (normal user) password, not the root passwd[/COLOR]. 

Read:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

If you want a permanent root prompt, type this command
$ sudo -i 
or 
$ sudo -i -H
------------------------------------------------------

FYI:
It is possible to open (unlock) the root account by giving it a password or using the passwd -u option.

$ sudo passwd root 
passwd: xxxxxxxx

And su - command will now work.
$ su - 

BUT KEEP IT LOCKED AND BE SAFE.
Do:
$ sudo passwd root -l

And root account is locked up (closed, disabled).
------------------------------------------------------

More about sudo.
The password you give on the sudo prompt expires after 15 minutes or so. You can change this and other values by editing the /etc/sudoers file. But you ought not edit /etc/sudoers manually, instead use the visudo editor.

$ sudo visudo

$ man sudo
for more info.

A very nice guide: [http://www.go2linux.org/sudoers-how-to](http://www.go2linux.org/sudoers-how-to)

Notice also:
The graphical equivalents of **sudo** are [COLOR="Blue"]gksu[/COLOR] or [COLOR="Blue"]gksudo[/COLOR] in the GNOME-desktop while KDE has [COLOR="Blue"]kdesu[/COLOR].

Sudo rocks!
// moma
   [http://www.futuredesktop.net]("http://www.futuredesktop.net")

---

### Post by infoseeker on 2006-07-21
I use
> sudo su

---

### Post by reacocard on 2006-07-21
sudo su
sudo -i
sudo -s

all produce the same thing as su, but use your password instead of root's.

---

### Post by bcashman on 2006-07-21
Thanks for the help. I found the info after i posted, but at the time this seemed to be the place to ask. Thanks again

---

