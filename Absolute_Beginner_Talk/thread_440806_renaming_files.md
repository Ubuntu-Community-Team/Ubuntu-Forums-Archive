---
title: "renaming files"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by theemrsweets on 2007-05-12
Sorry for being a total noob but I don't know how to rename files.  I'm trying to rename \etc\samba\smb.config to smb.config.old and I have no idea how.  Tried to changed it by opening with a text editor and save as but it did not work.  Please help, Thanks in advance.

---

### Post by phiphedog on 2007-05-12
you need to use the mv command

as this is a system file you need root privliges

[COLOR="Red"]sudo mv /etc/samba/smb.config /etc/samba/smb.config_old[/COLOR]

You can do it using the gui by opening a file explorer window with root priviliges

[COLOR="Red"]gksudo nautilus[/COLOR]

---

### Post by Spinelli on 2007-05-12
> **theemrsweets said:**
> Sorry for being a total noob but I don't know how to rename files.  I'm trying to rename \etc\samba\smb.config to smb.config.old and I have no idea how.  Tried to changed it by opening with a text editor and save as but it did not work.  Please help, Thanks in advance.

You need to use the mv or cp commands. I think what you are trying to do is backup your smb.config file to smb.config.old

```
sudo cp /etc/samba/smb.config /etc/samba/smb.config.old
```

You also might want to remove the write permissions from smb.config.old.
```
sudo chmod a-w /etc/samba/smb.config.old
```

---

### Post by starcraft.man on 2007-05-12
> **theemrsweets said:**
> Sorry for being a total noob but I don't know how to rename files.  I'm trying to rename \etc\samba\smb.config to smb.config.old and I have no idea how.  Tried to changed it by opening with a text editor and save as but it did not work.  Please help, Thanks in advance.

Ummm, if you want to rename an individual file, all ya really need to do is right click on it and select rename.

In your case I assume ya want a back up, easy way to do that is from the terminal with the cp command, type this in the terminal to do it:

```
sudo cp /etc/samba/smb.config /etc/samba/smbconfig.old
```

Thats it, hope that helps. :)

Edit: geez, go to get a quick drink and two people post... bah, making me feel slow :p

---

### Post by heimo on 2007-05-12
To rename a file on command line, you use mv command (mv=move). To rename a system configuration file, you'll need superuser privileges, so you need to prefix the command with sudo.
```

sudo mv file1 file2

```So this should do it:
```
sudo mv /etc/samba/smb.config /etc/samba/smb.config.old
```EDIT: Also see what starcraft above says about copying. Same syntax, but command is cp.

---

### Post by Vixis on 2007-05-12
Newbie guide about commands in terminal:
[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

---

### Post by heimo on 2007-05-12
Also see Kyrals [Terminal for Beginners]("http://ubuntuforums.org/showthread.php?t=73885").

---

### Post by theemrsweets on 2007-05-12
Thanks so much.  Everyone has been really helpful.  I greatly appreciate it.

---

