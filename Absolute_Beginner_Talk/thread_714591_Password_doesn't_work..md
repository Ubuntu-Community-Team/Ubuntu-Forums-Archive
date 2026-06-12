---
title: "Password doesn't work."
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Abfc on 2008-03-04
Apparently I'm retarded... I managed to screw something up so my password doesn't work; it keeps telling me I have an invalid password when I enter it to perform administrative tasks.
I was browsing some other forum for help with this and saw instructions to edit the password via the grub root thing, but I got errors there as well. I used the "passwd username" command and got the following:
"Enter new UNIX password: (so I did)
Retype new UNIX password: (I did again)
passwd: Authentication token lock busy
passwd: password unchanged"
So that's out...

What do I do?

---

### Post by aysiu on 2008-03-04
[This](http://forums.fedoraforum.org/showthread.php?t=92959) might help.

---

### Post by Rocket2DMn on 2008-03-04
If you need to change your user password, reboot the computer into Recovery Mode, so you have a root terminal.
Then run
```
passwd *yourusername*
```
You will then be prompted for a new password.  Then you can reboot and choose the regular login with
```
reboot
```

If that doesn't work, then check out aysiu's suggestion about mounting with rw options.

---

### Post by Abfc on 2008-03-04
In that link, Savage says something about removing /etc/passwd, does that mean the plain text file named "passwd" in /etc/?

---

### Post by Rocket2DMn on 2008-03-04
That is what he's talking about, yes, but I would just get the mounting options (rw) to work first.  I think removing the passwd file will have you recreate all your passwords, but that's not even possible if you can't get the drive to mount with rw permissions.
However, if that seems to be the logical next step, go for it I guess.

---

### Post by Abfc on 2008-03-04
> **Rocket2DMn said:**
> That is what he's talking about, yes, but I would just get the mounting options (rw) to work first.  I think removing the passwd file will have you recreate all your passwords, but that's not even possible if you can't get the drive to mount with rw permissions.
However, if that seems to be the logical next step, go for it I guess.

Actually, I tried recovery mode and changed my password and it didn't give me any errors and updated perfectly fine...But it says only root can remount.
Now, though, that I have administrative access back, what I was trying to install says that it can't be installed on my computer (i386). You think you could help me out with that while you're at it?

---

### Post by Virgilius on 2008-03-04
Did you type su or sudo su for root? that could be a solution.

---

### Post by Rocket2DMn on 2008-03-04
Yeah, first off are you back into normal mode?
If so, show me some output of your problem (from apt-get) and give as much other info as possible.

---

### Post by Abfc on 2008-03-04
> **Rocket2DMn said:**
> Yeah, first off are you back into normal mode?
If so, show me some output of your problem (from apt-get) and give as much other info as possible.

Yeah, I'm back to normal mode. But I'm really new to this, what's apt-get?

---

### Post by Rocket2DMn on 2008-03-04
apt-get is the primary program used to install packages from the command line.  Synaptic is the GUI frontend for apt-get.  For an in depth description of installing anything in Ubuntu, read here - [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
What were you installing and how were you trying to do it?

---

### Post by Abfc on 2008-03-04
> **Rocket2DMn said:**
> apt-get is the primary program used to install packages from the command line.  Synaptic is the GUI frontend for apt-get.  For an in depth description of installing anything in Ubuntu, read here - [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
What were you installing and how were you trying to do it?

I've been trying to install an mp3 codec or player, like aqualung or amarok, but when I try to do it in the Synaptic package manager they give me messages like:
"aqualung:
 Depends: libifp4  but it is not installable
 Depends: liblrdf0 but it is not going to be installed
 Depends: libmad0 (>=0.15.1b) but it is not installable
 Depends: libmodplug0c2 (>=1:0.7-4.1) but it is not installable
 Depends: libmpcdec3  but it is not installable
 Depends: libsamplerate0  but it is not installable"

I'm starting to think Linux hates me. ._.

---

### Post by Rocket2DMn on 2008-03-04
Go to System->Administration->Software Sources and enable the universe and multiverse repositories.  Then add the medibuntu repository so you can install the mp3 and dvd codecs, see here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
You will need libdvdcss2 and w32codecs

---

