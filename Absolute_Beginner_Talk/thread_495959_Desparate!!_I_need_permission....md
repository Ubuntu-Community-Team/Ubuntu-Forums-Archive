---
title: "Desparate!! I need permission..."
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by GlennW on 2007-07-08
Ubuntu is awesome! I don't mind tinkering, fiddling, and tweaking. But I'm absolutely tired to be constantly denied permission to my own files! I'm the only user. I've been reading about others with either the same condition or very similar situations and tried to implement all the sudo instructions as root! All to no avail. I need to install AVG plus make some other changes where I need to write but keep getting denied.

Please, I don't want to go back to XP........................

---

### Post by taurus on 2007-07-08
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Nekiruhs on 2007-07-08
Just enter sudo before the command for terminal apps and gksudo for graphical apps.

---

### Post by mikewhatever on 2007-07-08
To install AVG, use the following command> sudo dpkg -i avg*.deb
What other changes do you need to make, can you be more specific.
You are only frustrated because you are used to the way Windows manages permissions, allowing everything. Think of it a little, it's a bad practice.
> Please, I don't want to go back to XP.
What, just because of this!!!

---

### Post by nbv4 on 2007-07-08
Whenever you get a permission error, just add sudo in front of the command, then try it again. If it's a GUI application, use "gksudo" instead. If you're using sudo and it's still not working, then there is definitely something wrong. 

Basically, anything thats not in your home directory, you aren't allowed to mess with unless you give the password. You can always set it up so all users have full acess to every file on the system, but thats opening yourself up for trouble.

Once you get everything set up, you'll never have to touch sudo ever again.

---

### Post by kevinlyfellow on 2007-07-08
You can also become the root user with
```
sudo su -
```

If you don't want to remember that and prefer something less cryptic, you can issue this command
```
echo 'alias become_root="sudo su -"' >> .bashrc
```
After that, you just need to type "become_root" and it will prompt for a password and then log you into root.  Of course you can change that command to just about anything you want.

---

### Post by forrestcupp on 2007-07-08
But telling people who don't know what they are doing to run their system as root is reckless and very dangerous.  You do not need to run as root, you just need to learn how Linux works.

Just install AVG like mikewhatever told you, and please don't run as root unless you like spending your life searching through the help forums.

Most of the files a normal user needs to access should be in the /home directory, and you don't need special permission for that.

---

### Post by kevinlyfellow on 2007-07-08
> **forrestcupp said:**
> But telling people who don't know what they are doing to run their system as root is reckless and very dangerous.  You do not need to run as root, you just need to learn how Linux works.

Just install AVG like mikewhatever told you, and please don't run as root unless you like spending your life searching through the help forums.

Most of the files a normal user needs to access should be in the /home directory, and you don't need special permission for that.

Running as root is standard (many/most distros don't even have sudo installed by default), its not insecure, just so long as its not the for doing things like browsing the web and stuff like that under that account.  I strongly discourage logging in through gdm as root, or giving a normal user far too many privileges.  But good point, **do not use the root account to do everyday tasks, only administrative ones!!!**

---

### Post by Ziggyz on 2007-07-08
Even with the information posted above, I cannot log into root, whats wrong?

---

### Post by taurus on 2007-07-08
I guess I answered your wrong post then!

---

### Post by Ziggyz on 2007-07-08
Sorry about that I was going through editing it.

---

### Post by GlennW on 2007-07-08
Thanks for the responses. My present issue is that to install AVG it has to me moved to the file system /usr/local/src. I read this on the download page for AVG. I have permission to write to Home Folder but not to File System. Am I mistaken or can an app like AVG be installed somewhere where I've got permission. Forgive my ignorance but I'm a complete noob at this and need some hand holding. Thanks for your understanding.

---

### Post by Nekiruhs on 2007-07-08
use the command sudo cp or sudo mv to copy or move it to the directory. Or for a GUI way type gksudo nautilus and do your copy paste there.

---

### Post by GlennW on 2007-07-08
Thanks Nekiruhs, I'll give it a shot. However, I need to know if AVG needs to reside in Home Folder or File System.

Thanks

Here's what happened when I attempted to open nautilus:

root@glenn-desktop:~# gksudo nautilus

(gksudo:6247): Gtk-WARNING **: cannot open display:

---

### Post by kevinlyfellow on 2007-07-09
> **GlennW said:**
> Thanks Nekiruhs, I'll give it a shot. However, I need to know if AVG needs to reside in Home Folder or File System.

Thanks

Here's what happened when I attempted to open nautilus:

root@glenn-desktop:~# gksudo nautilus

(gksudo:6247): Gtk-WARNING **: cannot open display:

Try to run that as a normal user.  From where you were, not necessarily where you are now or when you see this
```

exit
gksudo nautilus

```

---

### Post by desijays on 2007-07-09
nice sig nekiruhs

---

### Post by GlennW on 2007-07-10
Thanks for all the responses and the helpful advice. 

[INDENT]gksudo nautilus[/INDENT]

This has apparently solved my immediate problems.

ciao...

---

