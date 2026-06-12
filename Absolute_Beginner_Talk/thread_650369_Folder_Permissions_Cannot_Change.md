---
title: "Folder Permissions Cannot Change?"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by iancvt55 on 2007-12-26
Hi
I'm trying to change permissions on a folder i created /root/windowsdrivers. I click on permissions but can't change them. If I try to log on as root through the graphical interface it says not allowed through this window.
I guess there must be a command line method?
Any suggestions or help welcomed
thanks
Ian

---

### Post by taurus on 2007-12-26
Why would you want to change permissions to that directory or any directory under /root?  If you need to access it, use sudo/gksudo.

```
sudo ls -la /root/windowsdrivers
-or-
gksudo nautilus
```

---

### Post by iris-n on 2007-12-26
Yes, there is a CLI method:

```
sudo chown -R <yourname> <yourfolder>
```

This way you become the owner of the folder, and can change permissions at will.

I believe there's also a method with chmod, but i'm not familiar with the commands.

---

### Post by LinuxIsInnovation on 2007-12-26
You need administrative privileges to modify the permissions

> $sudo nautilus

---

### Post by iancvt55 on 2007-12-26
Thanks guys thts got me moved along.So I guess I shoudn't create foldsers under /root ?

---

### Post by taurus on 2007-12-26
You should do your work or save files in your own $HOME directory.

---

### Post by The Cog on 2007-12-26
You should normally put all your files somewhere under your own home directory. The rest of the filesystem is for system files or files that are shared between all users. And /root is specifically roots home directory.

Knowing this, if you still want to do things outside your home folder for any reason, or want to run other programs that need administrative rights, you can put the word sudo in front of the command. If you are launching GUI applications instead of command-line ones you should use gksudo instead of sudo.

---

