---
title: "Cannot get past the login screen"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by mikem1946 on 2007-03-23
why cant I get past the logon screen,it keeps aking for "user name& password, I only use the live CD Ubuntu linux..help!!

---

### Post by taurus on 2007-03-23
If you are using the LiveCD, it should boot directly into Gnome window manager.

---

### Post by AndrewBarber on 2007-03-23
Please use more meaningful title's.

If you leave it, after 30 secs it logs in as 'user'

---

### Post by dfreer on 2007-03-23
You are currently using the Live Ubuntu CD? It shouldn't ask for a username/password. If you installed Ubuntu, the username/password should be whatever you set it as when installing.
If you can't remember your username/password, you can boot into recovery mode and find out your username with this command:
```
grep '1000' /etc/passwd
```
It should look something like this:
```
**[B]yourusernamehere**[/B]:x:1000:1000:XXXXXXXXXX,,,:/home/XXXXX:/bin/bash
```

You can change the password to that account with this command:
```
passwd *yourusernamehere*
```

---

### Post by nudnik on 2007-03-23
> **mikem1946 said:**
> why cant I get past the logon screen,it keeps aking for "user name& password, I only use the live CD Ubuntu linux..help!!

AAAAGGGGGHHHH!!! 

No matter what anyone says....that is a fantastic name for a thread!

---

### Post by jhenager on 2007-03-23
> **nudnik said:**
> AAAAGGGGGHHHH!!! 

No matter what anyone says....that is a fantastic name for a thread!

I always liked AAAAARRRRRRGGGGGGHHHHHH!!!, but to each his own.

As mentioned above, it should not ask for a username/password. I never saw that, anyway.
Possibly check the CD to see if there are problems with it? MD5 checksum?

---

### Post by AndrewBarber on 2007-03-23
Normally if you hit keys during gdm login it will display a proper login screen.

---

### Post by ipyrat on 2007-12-06
I have a similar problem when I install ubuntu it ask for name username password i put those in and when i get to the command line asking for username and password but the ones i chose do not work.Also now i can type in username but when i try to put in password it does nothing.wont type.any help?If ubuntu wants to compete with any other os you guys need to fix the install.Google this problem and see how many people have this issue.LOTS.thank you

---

### Post by dfreer on 2007-12-06
When you enter your password in the terminal, it will not show any indication that you are typing. Just type your password and then hit enter.

---

### Post by aysiu on 2007-12-06
> **ipyrat said:**
> If ubuntu wants to compete with any other os you guys need to fix the install.Google this problem and see how many people have this issue.LOTS.thank you Unfortunately, it's not easy to fix a problem that isn't easy to reproduce. Yes, it happens, but only occasionally. I've seen it pop up about once every three months or so on these forums, but no one has a solution because most people don't experience it (I certainly haven't). The best explanation I've found is that the CD image might have corrupted during download, but that hasn't been confirmed.

More details here:
[https://answers.launchpad.net/ubuntu/+question/9193](https://answers.launchpad.net/ubuntu/+question/9193)
[http://ubuntuforums.org/showthread.php?t=174567](http://ubuntuforums.org/showthread.php?t=174567)
[http://ubuntuforums.org/showthread.php?t=426963](http://ubuntuforums.org/showthread.php?t=426963)

---

### Post by Cushie on 2007-12-06
I am having a similar problem with Gutsy (Mint) installed for about 2 weeks.  Suddenly I can't get past the login screen (a title 'Gnome Desktop' and a footprint logo appear).

I have checked 'home' name and that is ok, I have reset 'passwd' at least twice, but cannot get past the login.  It does not say 'error' or c'heck Caps Lock', just returns to the login entry box.  Any help would be welcome.

---

### Post by aysiu on 2007-12-06
> **Cushie said:**
> I am having a similar problem with Gutsy (Mint) installed for about 2 weeks.  Suddenly I can't get past the login screen (a title 'Gnome Desktop' and a footprint logo appear).

I have checked 'home' name and that is ok, I have reset 'passwd' at least twice, but cannot get past the login.  It does not say 'error' or c'heck Caps Lock', just returns to the login entry box.  Any help would be welcome. I think this is a separate issue from the live CD asking for a username and password.

---

### Post by Cushie on 2007-12-06
OK I'll repost a new problem.

---

