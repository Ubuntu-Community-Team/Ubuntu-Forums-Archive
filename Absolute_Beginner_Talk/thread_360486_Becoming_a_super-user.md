---
title: "Becoming a super-user"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by gr0kzer0 on 2007-02-13
I'm running Breezy due to limited RAM.  I did the manual install, as I want to keep Windows as well.  During the installation, I was asked to create a root password, then to create a user account for myself.

Now there are a bunch of things I want to do, which only root or a super-user can do.  But I can't log in to the GUI as root,  and I don't know the shell commands yet.

So, can anyone please tell me the shell commands for giving my user account super-user status?

---

### Post by 23meg on 2007-02-13
> During the installation, I was asked to create a root password, then to create a user account for myself.
You were asked to create a user password, not a root password. By default, you can't log in as root.

You should instead use *sudo* and *gksudo* to temporarily get root status.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Norfolk 'n' Good on 2007-02-13
Open the terminal and type

```

sudo -s

```

However, use this cautiously.  I speak from bitter experience!

---

### Post by Maestro23 on 2007-02-13
> **Norfolk 'n' Good said:**
> Open the terminal and type

```

sudo -s

```

However, use this cautiously.  I speak from bitter experience!

Norfolk, you have opened up Pandora's Box for the OP..:)

---

### Post by Norfolk 'n' Good on 2007-02-13
Yeah I know... hence my warning.  Though sometimes the only way to learn is a few rebuilds! :)

---

### Post by Maestro23 on 2007-02-13
> **Norfolk 'n' Good said:**
> Yeah I know... hence my warning.  Though sometimes the only way to learn is a few rebuilds! :)

True...very true.:)

---

### Post by gr0kzer0 on 2007-02-13
23meg, I know what you mean about being asked to create a user account, then using sudo.  That was how things were on my last computer, when I did the auto install - I was asked to create a user account which then had super-user status, and there was no root by default.

But that is *not* what happened this time, with the manual install.  The computer asked me to give a password for *root*, then told me to create a user account for my own use.  I was pretty surprised when it happened, in my experience Ubuntu never had a password for root by default.  But with the manual install it asked me to give the *root* account a password.  And I can log in as root on a command line.

So please, can someone tell me how to give a user super-user status, so I can do admin stuff from the GUI?  Please?

---

### Post by Crooksey on 2007-02-13
> **23meg said:**
> You were asked to create a user password, not a root password. By default, you can't log in as root.

You should instead use *sudo* and *gksudo* to temporarily get root status.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You cant login from a login screen, but technically you can via the command line.

```
sudo su
```

Will switch you to a root prompt, that wont expire.

---

### Post by gr0kzer0 on 2007-02-13
> **Crooksey said:**
> You cant login from a login screen, but technically you can via the command line.

```
sudo su
```

Will switch you to a root prompt, that wont expire.

Thanks for that, Crooksey.  But I've just done some googling, and discovered that the command I want is```
usermod
```.  But I don't yet know how to use usermod.  Can anyone enlighten me?  Or should I just get back to googling?

---

### Post by 23meg on 2007-02-13
> 
23meg, I know what you mean about being asked to create a user account, then using sudo. That was how things were on my last computer, when I did the auto install - I was asked to create a user account which then had super-user status, and there was no root by default.Your default user doesn't have superuser status; it's a *sudoer*, which means it can temporarily get superuser status with *sudo* and *gksudo*.
> 
But that is not what happened this time, with the manual install. The computer asked me to give a password for root, then told me to create a user account for my own use. I was pretty surprised when it happened, in my experience Ubuntu never had a password for root by default. But with the manual install it asked me to give the root account a password. And I can log in as root on a command line.I don't know what you mean by "manual install", but if you wanted to perform administrative tasks with graphical apps, the best way to do it is to use *gksudo* as a normal user. For example ```
gksudo nautilus
```will give you an instance of Nautilus running as root.

Can you run the default set of administrative apps in System / Administration? Does a prompt come up asking you for your user password?

---

### Post by Crooksey on 2007-02-13
1) Logging in as root is very dangerous.

2)To fine out about the command "man usermod"

The method i posted is the way to do it ideally, logging in as root is very bad practice.

---

### Post by gr0kzer0 on 2007-02-13
Thanks again Crooksey.  How embarrassing: forgetting about the MAN pages...

---

### Post by Brunellus on 2007-02-13
1) For help on permissions, including root and sudo, visit [RootSudo](http://help.ubuntu.com/community/RootSudo).  

2) For help on installing to low-memory systems and older hardware generally, look at [Installation/LowMemorySystems](http://help.ubuntu.com/community/Installation/LowMemorySystems)

On a personal note:

Being root in the GUI is almost a stupendously bad idea.  It's too easy to make mistakes in the GUI, and as root, you will have no-one to blame but yourself for any damage you do to a running system.  UNIX and UNIX-like operating systems use limited-permission user accounts for a good reason.

Ubuntu, by the way, does NOT enable the root account by default, preferring to use 'sudo' (and its graphical equivalents, gksudo in GNOME and kdesu in KDE).  For most administration tasks accessible in the menus in GNOME and KDE, a popup should appear asking for your USER password.  This gives you root privileges for a limited time, and logs your actions in /var/log/auth.log.  This is the recommended way to run;  for details, see RootSudo, above.

While it is possible to do many things in the GUI, you will find with older hardware that it will be faster and more efficient to work in the shell.  [linuxcommand.org](http://www.linuxcommand.org/) is a good resource for learning the shell.  You will also learn the shell by osmosis if you copy & paste commands from places like [ubuntuguide.org](http://ubuntuguide.org).  

If that seems like a lot to digest at once, don't worry--it is.  It took me a few weeks to adapt to Linux when I first migrated.  The impoortant thing, then as now, was to focus on learning *new* things, rather than wonder how my *old* habits were going to work in the new environment.

---

