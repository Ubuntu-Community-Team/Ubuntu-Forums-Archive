---
title: "Server with GUI"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by remestre on 2007-04-17
We are a small printing shop, and currently use RHEL v3 (with a GUI, I think KDE) and use it as an FTP server running PureFTP (along with Webmin for easier administration of the FTP server), with about 100 virtual users that upload and download graphics files to their "private" folders. I would like to try Ubuntu Server to not only continue to run an FTP server to handle our virtual users, but also to host websites for some of our clients. I'm a Windows admin, and don't know Linux commands to run things from a prompt yet.

Would it be better to install Ubuntu Server, selecting the LAMP option during install, and then install a GUI like KDE or GNOME (and perhaps Webmin also?), or install Kubuntu which already has the GUI? Does this Kubuntu offer the LAMP option during install, or would I have to do that manually later? (Not sure how to do that if it needs to be done manually).

Any advise would be greatly appreciated, and look forward to learning and becoming adept at Linux Ubuntu. Thanks.

PS - If this section of the forum is not the right one to post this note, please forgive me and suggest which section would be better.

---

### Post by Zuph on 2007-04-17
If you're unfamiliar with configuring apache, mySQL, et al. for Linux, installing the lamp server then installing the GUI would probably be the easiest route.

One you have installed your LAMP server and it is connected to the internet, simply log in and type "sudo aptitude install ubuntu-desktop" for gnome or "sudo aptitude install kubuntu-desktop" for KDE.

---

### Post by remestre on 2007-04-17
Thank you Zuph for such a quick reply.

Any advice as to choosing between GNOME and KDE? I vaguely remember reading something about one being more geared towards technical people and the other one more towards non-technical users. I would prefer having a GUI that would be more powerful and allow me to do more as I make progress learning Linux Ubuntu.

---

### Post by christhemonkey on 2007-04-17
It is simply a matter of preferance.

You could try both!:
```
sudo apt-get install ubuntu-desktop kubuntu-desktop 
```
Then you can chose which session you want upon login.

---

### Post by Zuph on 2007-04-17
It's all user preference.  KDE tends to be more windows-like, while Gnome is a little different.  Neither is better or more powerful than the other.

---

### Post by bagguley on 2007-04-17
I have no experience of servers. But I can as a fairly new desktop user of ubuntu (tried KDE as well) that I find Gnome far more windows like thus making it an easier transition. KDE was what I imagine using MacOSX would be like.

Good Luck

As an afterthought you could always download the live dvds for each and play to your hearts content!

---

### Post by Rush_898 on 2007-04-17
Webmin is worth checking out also, as an alternative to a desktop environment.  Remote administration, intuitive, and removes some of the command line panic.  Just a thought, I'm not a unix admin but  I know where I work if we get audited w/ GUI on a *nix server it doesn't go over well.  :)

---

### Post by cmost on 2007-04-17
"I have no experience of servers. But I can as a fairly new desktop user of ubuntu (tried KDE as well) that I find Gnome far more windows like thus making it an easier transition. KDE was what I imagine using MacOSX would be like."

Actually you have that backwards.  KDE tends to be more comfortable for those coming over to Linux from Windows (while being much more powerful and configurable than Windows.)  Gnome strives for the simplicity of the Macintosh while retaining some elements familiar to Windows users.

---

