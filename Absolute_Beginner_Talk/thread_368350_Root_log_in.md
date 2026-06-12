---
title: "Root log in"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by barrykgerdes on 2007-02-23
I have just spent 12 hours straight installing breezy badger on a new installation then upgrading to dapper drake. I need to log on as root to fix an error. I don't remember setting any password for root. how do I do it. The password I used on my previous installation does not work

barry

---

### Post by ardchoille42 on 2007-02-23
> **barrykgerdes said:**
> I have just spent 12 hours straight installing breezy badger on a new installation then upgrading to dapper drake. I need to log on as root to fix an error. I don't remember setting any password for root. how do I do it. The password I used on my previous installation does not work

barry

You don't. The root account is locked by default. Anything you need to do admin-wise can be done with sudo. If you can't sudo, then there's always logging into recovery mode.

Please read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I have been using Ubuntu on 11 boxes (5 of which are servers) since Warty and have never had to enable the root account. I have also helped over 100 people switch from Windows to Ubuntu and have never seen an instance when they needed to enable the root account. Enabling the root account makes your system less secure. Suppose I wanted to break into your computer. I know you have a root account so I would start with that. I can't break into your user accounts because I don't know the user names. And, I can't break into the root account if it's disabled.

Do youself a favour, keep the root account locked and use sudo/gksudo.

---

### Post by mcduck on 2007-02-23
Ubuntu doesn't use root account by default, and I wouldn't recommend enabling it either. Use 'sudo' to do what you need and your life with Ubuntu will be much easier.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

If you can tell more precisely what you need to fix I'll try to give more precise help :)

---

### Post by luisromangz on 2007-02-23
If you don't want to type sudo every time you need, you can always use "sudo su".

---

### Post by kinematic on 2007-02-23
> **ardchoille42 said:**
> I can't break into your user accounts because I don't know the user names. And, I can't break into the root account if it's disabled.


and you can't hack the root account if you don't know the root password ;)

---

### Post by mcduck on 2007-02-23
> **kinematic said:**
> and you can't hack the root account if you don't know the root password ;)

when you know the user name (root) it's just question of getting the password, and that can be cracked by brute force if nothing else. If it's user account you'd have to get both username & password ;)

---

### Post by ardchoille42 on 2007-02-23
> **luisromangz said:**
> If you don't want to type sudo every time you need, you can always use "sudo su".

That isn't recommended either. It's better to use 

```

sudo -i

```

as that sets up the environment better.

---

### Post by daemmon on 2007-02-23
the root password is the same as your password, by default. to activate root in the graphical log-in, you need to check some box in system->preferences->login, or something like this (don't know for sure, i'm writing from memory and i'm rather new to ubuntu myself)

---

### Post by ardchoille42 on 2007-02-23
> **daemmon said:**
> the root password is the same as your password, by default. to activate root in the graphical log-in, you need to check some box in system->preferences->login, or something like this (don't know for sure, i'm writing from memory and i'm rather new to ubuntu myself)

This is not true. The root account password and the sudo password are two different passwords. I believe the method used to lock the root account is "passwd -l".

From man passwd:
```

-l, --lock

Lock the named account. This option disables an account by changing
the password to a value which matches no possible encrypted value.

```

Also, enabling the root account is dangerous as well as unsupported configuration.

---

### Post by barrykgerdes on 2007-02-23
I  found out what I needed from another thread and remembered what I did last time.

All I wanted to do was to add some missing files to a folder that were removed when I upgraded. They were needed for a compile and could not be installed in the normal manner. The files are probably obsolete now but I could not tell the compiler that.

As a windows GUI user I am not very familiar with the linux command line commands and did not know how to copy a file from one folder to another.

The arguments about not having root access might be good in a commercial area but a private linux installation can be a bit cumbersome when the user also owns the computer and  only causes frustration when what is a minor problem in Windows becomes a hassle of changing users each time something goes wrong. 

Barry

---

### Post by mcduck on 2007-02-23
> **barrykgerdes said:**
> I  found out what I needed from another thread and remembered what I did last time.

All I wanted to do was to add some missing files to a folder that were removed when I upgraded. They were needed for a compile and could not be installed in the normal manner. The files are probably obsolete now but I could not tell the compiler that.

As a windows GUI user I am not very familiar with the linux command line commands and did not know how to copy a file from one folder to another.

The arguments about not having root access might be good in a commercial area but a private linux installation can be a bit cumbersome when the user also owns the computer and  only causes frustration when what is a minor problem in Windows becomes a hassle of changing users each time something goes wrong. 

Barry
Actually sudo is easier than root account, as you don't have to change user to do admin tasks, and it's also allows you to do them from desktop (even if you have root account enabled you should never ever log into desktop as root, that's just about the least safe way to use your computer!)

If you need to manage files as root and you don't want to do it from terminal just hit Alt-F2 and run 'gksudo nautilus' to open file manager as root. If you need this often just create a launcher for it in your menu or panel. (and be sure to close the window when you don't need it, so you won't wreck your system by accidentally deleting any files or something)

---

### Post by Ben Sprinkle on 2007-02-23
Easy. Reboot, stay at the gdm. Press CTRL+ALT+F2. Then you can do a root console login.

---

### Post by EvilMarshmallow on 2007-02-23
barrykgerdes,

Locking out root is *very* important on *any* computer, commercial or private, and here's why I'd argue that:

Most of my friends who aren't "into" computers use their Windows as an administrator all the time.  Their boxes are loaded with spyware and all other sorts of stupid crap all the time because they don't know what's safe to run and what's not.  This is why we have problems with spam and botnets and stuff... because when their box gets pwned, it becomes a zombie for some moron who's got nothing better to do than offer me v14gr4 or something.

If people didn't run their Windows boxes as admins, it would be that much harder to hack it, and we'd have that many fewer SPAMbots running around.  Face it, corporations don't fall victim to viruses as easily as home users because they pay IT people who focus on protecting their networks.  The average computer user at home doesn't have that... they just plug it in and want it to work, without thinking of the ramifications of what happens if they get pwned.

Root is a bad, bad thing.  Only use it if there's absolutely no other way.

---

