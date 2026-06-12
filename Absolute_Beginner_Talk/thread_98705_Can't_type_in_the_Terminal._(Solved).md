---
title: "Can't type in the Terminal. (Solved)"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by buyj3llo on 2005-12-03
I just downloaded linux this morning, and i'm already lost.

I just tryed to go to a website, but I was told that i needed java. So then I go over to the java web site and download java( linux version). I didn't really know how to install stuff on linux so I followed the the directions from the java website:

[I]Follow these instructions:

   1. At the terminal: Type:
      su[/I]
**this part worked fine**

   2. Enter the root password.
**but when i try to type in my password, it won't type. I'm pressing the keys but nothing is showing up in the terminal screen. what's going on?**

---

### Post by BabaFree on 2005-12-03
Just type it and press enter.  Mine doesn't show anything when I'm typing the password either (which I'm assuming is normal) but it still types it and when I press enter it works.  Also, in most instances where I've seen the "su" command, the "sudo" command is usually used in Ubuntu.  
     As far as Java is concerned, try this thread.  It helped me out

[http://www.ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs]("http://www.ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs")

I hope this helps.
Baba

---

### Post by buyj3llo on 2005-12-03
I typed in my password and pressed enter and it still didn't work. but when i put in "sudo" instead of "su" I got this:

[I]jamal@ubuntu:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
[/I]

It didn't ask me for a password this time. Is that rigth? I have no idea what i'm doing, and I don't want to mess anything up by pressing the wrong button. What does this all mean?

---

### Post by m0biu5 on 2005-12-03
When you use sudo or su in the terminal, you type in the password but it doesn't show up - this is a security measure. If you do the commands and hit enter after the password is entered, it should work. Alternatively , you can use a root terminal  (im not sure of the location in 5.10) to execute commands as root.

---

### Post by aysiu on 2005-12-03
sudo can't be a command by itself. It has to be coupled with another command. 

Sudo by itself: ```
sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
```

Sudo coupled with another command: ```

sudo apt-get update
Password:
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:4 http://security.ubuntu.com breezy-security Release [19.6kB]
Get:5 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Get:6 http://archive.ubuntu.com breezy-updates Release [19.6kB]
Get:7 http://archive.ubuntu.com breezy-backports Release [19.6kB]
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Fetched 59.4kB in 1s (34.5kB/s)
Reading package lists... Done
``` Notice how I was able to enter my password, but nothing displayed as I typed it in?

---

### Post by buyj3llo on 2005-12-04
...ooooooooohhhhhhhh:D ! I get it now, thanks

you guys are freakin awesome! thank you![-o<

---

