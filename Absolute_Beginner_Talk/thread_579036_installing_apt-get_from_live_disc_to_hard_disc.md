---
title: "installing apt-get from live disc to hard disc?"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by doanotherlinux on 2007-10-17
After installing Xubuntu AND Ubuntu I have had problems with Apt-Get not being installed.  Even after I try fresh reinstalls I only get to the Ubuntu loading screen and I get a message saying the start up failed because apt-get is not installed.

After SEVERAL reinstalls with both Xubuntu and Ubuntu it tells me the same thing.

My first install of Xubuntu worked great.  But after installing Java I started having this problem.  I've read that thats a common thing.

So can one of you help me out here?

---

### Post by doanotherlinux on 2007-10-17
Anyone?

---

### Post by doanotherlinux on 2007-10-17
If there is any other way to get apt-get on here besides using the live disc please let me know.

And please do it in a very dumbed down fashion.  As I have no clue what I'm doing.

---

### Post by JacobSteelsmith on 2007-10-18
Try entering these two commands (one at a time) into your command prompt:

sudo aptitude update
sudo aptitude install apt-get

---

### Post by doanotherlinux on 2007-10-18
This is going to sound real stupid.  But.

Where is my command prompt?

---

### Post by JacobSteelsmith on 2007-10-18
I use kubuntu, but I think in ubuntu it's at:

Applications - Accessories - Terminal

---

### Post by doanotherlinux on 2007-10-18
Now if I do that with my Live Disc will that do the trick?  Because the apt get thing won't let me into the Ubuntu on my hard disc.

---

### Post by JacobSteelsmith on 2007-10-18
so you get nothing? No black and white screen with a command prompt and a flashing cursor? Just a message saying you should reinstall?

---

### Post by doanotherlinux on 2007-10-18
I get the black screen with all kinds of text telling me apt get is not installed and a cursor that will let me type dos stuff.  Should I do it on there?

---

### Post by JacobSteelsmith on 2007-10-18
Yep. You may need to login first.

---

### Post by doanotherlinux on 2007-10-18
Neither of those commands work from there.

---

### Post by captaink on 2007-10-18
All right, this is a strange issue, but let's try the other.

As you start your computer, you may see a message that says something about "grub". In that time, before the counter starts zero, press escape.
Then, you end up in a menu, usually with two entries or three (if you have another OS, like windows, dual boot). Choose the second ubuntu that says at the end "Recovery mode" and press enter.
That logins you as root. Normally, after the warnings about "no apt-get..." it should throw you to the command promt, waiting for your command. It may look like this:

```
root@mypc$
```

There you can enter the commands described by the other user:

```

aptitude update
aptitude install apt-get

```

Note: there is no need for "sudo" here.

---

### Post by doanotherlinux on 2007-10-18
Thanks.  I'll give that a try

---

### Post by JacobSteelsmith on 2007-10-18
Make sure you post the exact text of any error messages too. Good call on the recovery mode.

---

### Post by doanotherlinux on 2007-10-18
I tried that.  It told me aptitude is not installed.

---

### Post by JacobSteelsmith on 2007-10-18
Ok. Now try this. Use the same instructions as before to get to the command prompt. Enter the following:

wget [http://archive.ubuntulinux.org/ubuntu/pool/main/a/apt/apt_0.6.46.4ubuntu10_i386.deb](http://archive.ubuntulinux.org/ubuntu/pool/main/a/apt/apt_0.6.46.4ubuntu10_i386.deb)
dpkg -i apt_0.6.46.4ubuntu10_i386.deb

That should install apt, I hope. Otherwise, your best bet is to download another copy of ubuntu and reinstall. That would rule out a corrupt source disk.

---

### Post by doanotherlinux on 2007-10-19
I tried that.  It said wget is not installed.

Fresh installs and new install disks are doing nothing for it either.  Still gives me the same problem.

WTF?

---

### Post by Frak on 2007-10-19
Do a
```
sudo editor /etc/environment
```
And make sure that it looks like this
```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11
```
Then press Ctrl+x, y, enter

---

