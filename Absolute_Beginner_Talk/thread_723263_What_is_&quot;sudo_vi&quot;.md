---
title: "What is &quot;sudo vi&quot;?"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by DaddyUnit on 2008-03-13
I'm trying to follow instruction on how to setup cvs ([http://sanatio.blogspot.com/2005/12/cvs-server-on-ubuntu.html](http://sanatio.blogspot.com/2005/12/cvs-server-on-ubuntu.html)) and I'm supposed to enter a command "sudo vi". What does this do? It messes up the terminal and I have to close and reopen another terminal instance.

---

### Post by perlluver on 2008-03-13
That opens up a config file, you can also use sudo gedit, it is much easier.  Make sure you enter that whole line.

Edit: sudo gedit //var/lib/cvsd/cvsrepo/CVSROOT/config

---

### Post by Oldsoldier2003 on 2008-03-13
> **DaddyUnit said:**
> I'm trying to follow instruction on how to setup cvs ([http://sanatio.blogspot.com/2005/12/cvs-server-on-ubuntu.html](http://sanatio.blogspot.com/2005/12/cvs-server-on-ubuntu.html)) and I'm supposed to enter a command "sudo vi". What does this do? It messes up the terminal and I have to close and reopen another terminal instance.

vi is an advanced text editor that takes a lot of effort to learn how to use. using sudo runs vi under superuser do, meaning it acts as if it were being run by Root.

---

### Post by wieman01 on 2008-03-13
'sudo' prompts you to enter your use password and lets you run terminal commands as 'root' or 'administrator' to use a Windows term.

'vi' is a popular text editor which is command line based. An option would be:
> sudo nano
Or:
> sudo gedit

---

### Post by DaddyUnit on 2008-03-13
Thanks!

---

### Post by taurus on 2008-03-13
Wouldn't it be better to use gksudo with gedit instead of sudo?

```
gksudo gedit *filename*
```

---

### Post by wieman01 on 2008-03-13
Well, Taurus, I have had the discussion with others... I don't see why it would make a difference. I have read Aysiu's explanation on his website, but still I don't really get it. What's worse, 'sudo' sometimes work when 'gksudo' doesn't. I had a case recently. 

Don't ask me what's correct, I don't really know...

---

### Post by jimcooncat on 2008-03-13
> **taurus said:**
> Wouldn't it be better to use gksudo with gedit instead of sudo?

```
gksudo gedit *filename*
```

If you're at the command line, working on one thing at a time, sudo is just fine. It rolls off the fingers so fast now you don't even realize you're doing it. 

If you go sticking that into some gui launcher, though, you'll have a mess. For instance, if you want to make a new Gnome menu command to open up a editor with root privileges, "gksudo gedit" will get you what you want. "sudo gedit" won't work, as "sudo" needs the command line to work properly when it asks for your password.

---

### Post by FuturePilot on 2008-03-13
The thing with running graphical apps with sudo is that it launches the application as root with your config files, which could end up changing the ownership of those files to root which would render that app useless as a regular user since you wouldn't be able to read those config files anymore. Whereas gksudo launches the app as root with root's config files where's there's no chance that it will change the ownership of your files.

---

### Post by forrestcupp on 2008-03-13
I never use gksudo with gedit, and I've never had any trouble.  The only difference I've seen is that if I use sudo and close the terminal, it closes gedit.  But if I use gksudo and close the terminal, gedit stays open.

I've never had any problem with permission screw ups, and I've used sudo gedit a lot.  If someone has actually recently had that kind of trouble, I'd like to hear about it.

---

### Post by jimcooncat on 2008-03-13
I've had that happen to me before! That is, when one of my .dot files ended up getting owned by root. I don't think it I was running an editor when that happened, though; more than likely it was nautilus.

---

### Post by forrestcupp on 2008-03-13
> **jimcooncat said:**
> I've had that happen to me before! That is, when one of my .dot files ended up getting owned by root. I don't think it I was running an editor when that happened, though; more than likely it was nautilus.

Well, I guess with nautilus maybe you could run into trouble.  It's probably safer to just get in the habit of using gksudo with graphical stuff.

---

