---
title: "[SOLVED] Updating my own sources in Synaptic"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by MaxVK on 2008-02-23
HI, I'm curious about the use of sources with synaptic. Let me explain:

I'm always producing little (and not so little) applications for myself and currently I am using Gambas, which packages my compiled programs as .deb files.

If I install one of my own programs from one of these .deb files, and then find that I want to update it I currently have to remove the installed program, and re-install the newer version.

Is there any way to add a folder (For example) to my synaptic sources, so that if I place a newer version of an installed program there, synaptic will see it and update the installed version for me?

Thanks

Max

---

### Post by y-lee on 2008-02-23
Hmm never thought about it

tho [AptMoveHowto]("https://help.ubuntu.com/community/AptMoveHowto") is close. Maybe you can play around with it and the apt-move apt-move command and get it to do that. maybe read

```
man apt-move 
```

and examine the apt-move.conf file.

I don't have it installed and never used it so i don't know.

Good question tho :)

---

### Post by glennric on 2008-02-23
Check out the following link:
[http://ubuntuforums.org/showthread.php?t=42862]("http://ubuntuforums.org/showthread.php?t=42862")

You shouldn't have to uninstall the previous deb and install the new one.  Just type
```
sudo dpkg -i package.deb
```
and it will remove the old and install the new.

---

### Post by MaxVK on 2008-02-23
Thanks for the replies.

glennric: That link was exactly what I need, thanks!

Regards

Max

---

