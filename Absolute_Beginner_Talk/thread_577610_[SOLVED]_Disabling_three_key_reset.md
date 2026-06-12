---
title: "[SOLVED] Disabling three key reset?"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by radioraheem8 on 2007-10-16
Hi all,

I just got VPN client working on my system, but the problem is, I'm using it to access the computers at work, which are Windows based.  Since a screensaver pops up after a couple minutes, I am forced to hit CTRL + ALT + Backspace to access them via proxy (not DEL).  Being new to ubuntu and all, I found that this resets my entire system.  Needless to say, this is a pain in the *** when trying to do work from home.  

Is there anyway to disable the three key reset, but still make the keys take effect on a proxy session screensaver?  Thanks for any help.

---

### Post by argie on 2007-10-16
From here: [https://help.ubuntu.com/6.06/kubuntu/desktopguide/sample/xorg.conf_disablectrlaltbackspacegnome](https://help.ubuntu.com/6.06/kubuntu/desktopguide/sample/xorg.conf_disablectrlaltbackspacegnome)
This should help:
Open a terminal. Then type:
```
gksudo gedit /etc/X11/xorg.conf
```
Then add this at the end of the file:
```
Section "ServerFlags"
	Option		"DontZap"		"yes"
EndSection

```
Save it and exit it. You'll have to restart X once you do that, so logout and log back in.

---

### Post by radioraheem8 on 2007-10-17
Thanks for the reply!  But when I try the first command you listed, I get a blank document.  From my understanding, shouldn't that be a file with other commands in it?  I'm on Feisty Fawn, if that makes a difference.  Should I just copy and paste that other part into the xorg.conf file, even if there is nothing else in it?

---

### Post by argie on 2007-10-17
Hmm, hold on. That file contains the configuration for X, it can't be empty. Can you do the following?
```
cd /etc/X11
```

Now paste the output of the following command in your next post.
```
ls
```

---

### Post by radioraheem8 on 2007-10-17
Whoa, it says no such directory exists.  Now I'm worried.  Here's the output:

$ cd /etc/x11
bash: cd: /etc/x11: No such file or directory
$ ls
01.wmv          cm.torrent  Part Two.doc  vpnclient-linux-4.8.00.0490-k9.tar.gz
betrayal 2.odt  Desktop     test1
cm              Examples    vpnclient

As you can see, I don't have much on my HDD at the moment.

---

### Post by Lord Illidan on 2007-10-17
Linux is case sensitive.

/etc/X11 is different from /etc/x11 or /ETC/X11 or /etC/X11

Copy and paste those commands **exactly**.

---

### Post by radioraheem8 on 2007-10-17
AH, I'm an idiot!  Ok, I did that, and the three key reset is disabled.  However, when I VPN into work, it seems the three key command isn't recognized at all, so I still can't bring down the screensaver.  Any ideas on that front?

Thanks for all the help so far.

---

### Post by radioraheem8 on 2007-10-18
Never mind, I got it.  My work Proxy has a Send Keystroke option under Edit.  

Thanks again for all your help guys.

---

