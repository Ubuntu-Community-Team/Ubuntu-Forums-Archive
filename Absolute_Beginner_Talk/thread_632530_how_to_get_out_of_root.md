---
title: "how to get out of root"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by kahram.yoon on 2007-12-05
I am trying to install fonts and one forum on this site told me to type this :gksudo nautilus: into terminal and nothing happened, i think my root folder became my home folder.  so i went to this site [http://penguinfonts.com/howto/ubuntu.php](http://penguinfonts.com/howto/ubuntu.php) and it said that kfontview will help you install the fonts. so i put this into terminal and i get this error.

desktop:~$ apt-get install kcontrol
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

how do i fix this so i can install kfontview?

---

### Post by vikram on 2007-12-05
sudo  apt-get install kcontrol

---

### Post by thelatinist on 2007-12-05
The problem is probably that you are *not* root.  The command that you typed only opens the file browser with root permissions, it doesn't change anything in your terminal session. Try:

```
sudo apt-get install kcontrol
```

---

### Post by rich.bradshaw on 2007-12-05
gksudo will just run one program as if you were root - so that won't affect anything else. Nautlius is the file viewer, analogous to windows explorer.

As mentioned above, running

sudo apt-get install kcontrol

will install it.

sudo (do as a different user, default is root)

apt-get (using the apt packaging software)

install (install!)

kcontrol (the program you want)

You can use this for any program.

swap install for remove to uninstall.

---

### Post by The Cog on 2007-12-05
I would sugest that you follow instruction 2 from that howto (system-wide use) rather than instruction 1. Those commands need to be run as root (put the word **sudo** in front of them).

And **gksudo nautilus** does not have colons around it, its just
**gksudo nautilus**

---

### Post by Dr Small on 2007-12-05
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ArtInvent on 2007-12-05
For the record, in a terminal you will not 'become root' unless you use the command **sudo -i **
(Don't ever do this unless you absolutely know what you are doing. Sudo is safer for doing most things.)

As root you will see the prompt change to** root@[computername]**
and there will be a **#** prompt instead of a **$** prompt
If you see a **#** then you are probably root.

To exit from being root, use the command **exit** and the terminal will return 'logout' and you will be back to your original user.

---

