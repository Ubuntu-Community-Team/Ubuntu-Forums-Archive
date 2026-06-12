---
title: "Can't Edit File"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by nalencer on 2007-11-27
I'm attempting to edit one of the system files, but it claims I don't have permission. I'm on an admin account, in the root group, etc. The file's parent group is root... am I missing something? Shouldn't I be able to edit it? In case it matters, the file is \etc\fstab.

---

### Post by poudin on 2007-11-27
try sudo vim /etc/fstab

i would definitely make a backup before editing it manually.

cp /etc/fstab /etc/fstab.original

hope this helps

---

### Post by edwardTheGreat on 2007-11-27
try 
```
sudo gedit /etc/fstab
```

(gedit is the program to edit file)

and as poudin said back up the file

```
cp /etc/fstab /etc/fstab.original
```

---

### Post by rsambuca on 2007-11-27
> **edwardTheGreat said:**
> try 
```
sudo gedit /etc/fstab
```
This code is incorrect.  The correct usage for gedit is gksudo.```
gksudo gedit /etc/fstab
```

---

### Post by jordanmthomas on 2007-11-27
> **edwardTheGreat said:**
> 
```
cp /etc/fstab /etc/fstab.original
```

You'll want a sudo on that as well:
```
sudo cp /etc/fstab /etc/fstab.original
```

---

### Post by jordanmthomas on 2007-11-27
> **nalencer said:**
> I'm attempting to edit one of the system files, but it claims I don't have permission. I'm on an admin account, in the root group, etc. The file's parent group is root... am I missing something? Shouldn't I be able to edit it? In case it matters, the file is \etc\fstab.

Although you're in the root group, only the owner (root) has write permissions on /etc/fstab
```
-[COLOR="Red"]rw-[/COLOR][COLOR="YellowGreen"]r--[/COLOR]r-- 1 root root 473 2007-10-21 20:12 /etc/fstab
```

The group root only has permissions in green, while root himself has the one in red.

---

### Post by nalencer on 2007-11-27
Now, this is something I'll need to know in the future, I'm sure: how do I log in as root? I attempted it from the main login window, and it said that root can't log in from there. So where *can* he log in from?

---

### Post by jordanmthomas on 2007-11-27
If you give root a password, he can log in in any terminal.
If you want to log in to X as root, there's an option to allow local administrator to log in in 
system --> administration --> login window
on the securtity tab I believe. 

I'll likely get flamed for even telling you that, but I believe people should use their computer like they want.  Most Ubuntu users think actually *using* the root user is a bad idea, but live and let learn I say.  Once you screw something up, you'll probably decide not log in as root anymore.  I do suggest that if you log in as root you set your wallpaper to be bright red or something to remind yourself to be careful.

The way Ubuntu is set up, you don't need to log in as root.  Just use sudo or gksudo to elevate your permissions when needed.

---

### Post by asaz989 on 2007-11-27
You can't log in as root in the graphical desktop - and since that's the only easy way I know of logging into Ubuntu in general, you can't log in as root at all.

Instead, you use sudo and gksudo and stuff like that to temporarily switch user to root (e.g. sudo gives you root access for 5 minutes after entering the password for every command that has sudo in front of it).

For text editing, what I usually do is edit it in the text editor, then when I want to save, use the chmod function to give myself write permission, save, then take away that permission afterward.

Here are the commands.

Add write permission for "group" and "others", semi-verbose mode:
```
sudo chmod -c go+w [filename]
```

Remove write permission for "group" and "others", semi-verbose mode:
```
sudo chmod -c go-w [filename]
```

---

