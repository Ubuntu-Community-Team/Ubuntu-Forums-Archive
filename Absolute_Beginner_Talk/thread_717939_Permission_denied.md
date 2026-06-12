---
title: "Permission denied"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Cruciatum on 2008-03-07
Right, I think I'm really close to resolving my lack of sound problems.

At the moment, I need to get into /etc/modprobe.d/alsa-base and modify some stuff (which you may already know etc.)

Only problem is, I have a somewhat limited knowledge of the terminal application, and when I put that into it, I get the message: "bash: /etc/modprobe.d/alsa-base: Permission denied"

There's probably a simple explanation and solution to this, right? *hopes*

Cheers guys.

---

### Post by Cruciatum on 2008-03-07
Am I right to assume is has something to do with being in the root?

---

### Post by Linux_Man on 2008-03-07
Put sudo in front of your command. That should solve it.

---

### Post by SunnyRabbiera on 2008-03-07
yeh to modify certain files you may need to be in administration mode, try typing in sudo /etc/modprobe.d/alsa-base

---

### Post by Cruciatum on 2008-03-07
> **Linux_Man said:**
> Put sudo in front of your command. That should solve it.

Yeah, I tried that and it gave me "sudo: /etc/modprobe.d/alsa-base: command not found"

---

### Post by taurus on 2008-03-07
You want to edit it so you need to include an editor.

```
gksudo gedit /etc/modprobe.d/alsa-base
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by lswest on 2008-03-07
it should be:
```
gksudo gedit /etc/modprobe.d/alsa-base
``` since i assume you want to edit the config file

*EDIT* looks like someone beat me to it

---

### Post by Oldsoldier2003 on 2008-03-07
> **Cruciatum said:**
> Yeah, I tried that and it gave me "sudo: /etc/modprobe.d/alsa-base: command not found"
paste this:

```
sudo nano /etc/modprobe.d/alsa-base
```

that will open the file in nano for editing

---

### Post by Oldsoldier2003 on 2008-03-07
> **Cruciatum said:**
> Yeah, I tried that and it gave me "sudo: /etc/modprobe.d/alsa-base: command not found"
paste this:

```
sudo nano /etc/modprobe.d/alsa-base
```

that will open the file in nano for editing

edit: lol people posting like made today :) gotta love the amount of help here on this forum!

---

### Post by Cruciatum on 2008-03-07
Cheers guys :) That's solved it for me.

---

### Post by PeterJS on 2008-03-07
That should cover the problem, but for a bit more explanation of what's going on. Everything outside of your home directory is owned by root, and generally in the group root (or something relevant to it's purpose for the exceptions), with world write permissions disabled. But you might say to yourself, but I have an admin account, I should be able to edit the system files, and you right that you have an admin account, but an admin account only has elevated (root) privileges when they are explicitly requested with sudo, or gksudo (the graphical version). This has a couple of benefits, if mythical linux malware does get on your system it can't cause any system wide damage. It also gives you the user a bit of warning to think about what you're doing, you can't cause system wide harm without authenticating through sudo with you're password.

EDIT:
Wow, this tread moves fast...

---

### Post by lswest on 2008-03-07
yup, it's solved now too, so you can mark it as solved using the thread tools at the top of the thread (at the OP) and no problem, glad we could help ^^

---

