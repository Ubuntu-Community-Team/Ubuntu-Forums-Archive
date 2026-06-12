---
title: "How to login as root"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by furiousjoe on 2006-09-07
I've searched all over the place and I get wierd results, I did the sudo passwd root and changed the password to my preference, although when I try to login it says something about that I can't login that way.

The entire reason I need the root thing is because I need to install Nvidia drivers.

Many thanks in advance,

---

### Post by bunnynuts on 2006-09-07
Not sure I quite understand what your trying to say, so lets start from the beginning.  You have logged in with the user you created when you installed Ubuntu and are you then using the ```
sudo su
``` command to switch to root? If not try that, if so are you able to run other sudo commands?

---

### Post by furiousjoe on 2006-09-07
Hmmm so far so good, but now it says that I'm running as X Server? How do I get rid of this?

---

### Post by whizbaby on 2006-09-07
My goodness, a déja-vu...

[http://ubuntuforums.org/showthread.php?p=1474746#post1474746](http://ubuntuforums.org/showthread.php?p=1474746#post1474746)

about why you shouldn't need a root account and why you don't want to allow graphical root login.

---

### Post by taurus on 2006-09-07
> **furiousjoe said:**
> I've searched all over the place and I get wierd results, I did the sudo passwd root and changed the password to my preference, although when I try to login it says something about that I can't login that way.

The entire reason I need the root thing is because I need to install Nvidia drivers.

Many thanks in advance,
Try

```
su -
```
And if you want to install nvidia for your graphic card, use aptitude then...  Quick and easy and no need to log in as root first!

---

### Post by aysiu on 2006-09-07
Why do you need to log in as root to install Nvidia drivers? You don't.
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Zaid on 2006-09-07
"  sudo -i  " ?

---

### Post by whizbaby on 2006-09-07
> **Zaid said:**
> "  sudo -i  " ?

Try **man sudo** and stare at text right behind the **-i** option.

---

### Post by aysiu on 2006-09-07
> **whizbaby said:**
> Try **man sudo** and stare at text right behind the **-i** option.
Can you translate this to English? ```
       -i  The -i (simulate initial login) option runs the shell specified in the passwd(5) entry of the user that the command is being run as.  The
           command name argument given to the shell begins with a - to tell the shell to run as a login shell.  sudo attempts to change to that user&#8217;s
           home directory before running the shell.  It also initializes the environment, leaving TERM unchanged, setting HOME, SHELL, USER, LOGNAME,
           and PATH, and unsetting all other environment variables.  Note that because the shell to use is determined before the sudoers file is parsed,
           a runas_default setting in sudoers will specify the user to run the shell as but will not affect which shell is actually run.
```

---

