---
title: "Starting without administrative privileges"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Megabuntu on 2007-02-08
I don't know what I did that might have changed things, but when I start up I get a window that says

Starting without administrative privileges

You will not be able to apply any any changes. But you can still export the marked changes or create a download script for them.

There's also something at the end which says something about my changes not being applied. I am the admin user and I can do sudo, etc., but I have no idea what this is talking about.???

---

### Post by banditti on 2007-02-10
when and where are you seeing this?

---

### Post by nickoli_02 on 2007-02-10
You're not the root (administrative) user, root is the root user. When you use sudo you're executing a command as root. This is one of the differences between windows and linux, and one of the main reasons linux (and unix in general) is much more secure: the default user does not have root privileges.

---

### Post by Megabuntu on 2007-02-12
The message comes up every time I start the computer.

---

### Post by Megabuntu on 2007-02-14
Anyone have an idea?
when I click on the close button, synaptic manager opens up with the startup box that explains what synaptic manager is, and it's important to reload so I don't miss stuff, etc.:confused: :confused: :confused:

---

### Post by Amarsingh0793 on 2007-10-31
I had that problem too. I also couldn't do any administrative jobs but I found a solution. 
After logging in as root via terminal (su --login) , type the following
usermod -a -G admin yourusername

After that the problem should be fixed. :)

---

### Post by rampage355 on 2007-11-30
I got the same thing on xubuntu, I tried the fix you stated with no luck. I am also get a dkpg error and no top or bottom panel. Anyone have any suggestions?

Thanks
Greg

---

### Post by jken146 on 2007-11-30
It sounds like you have a program that normally requires sudo configured to start when you log in (like starting Synaptic with 'synaptic' instead of 'gksudo synaptic').  Have a look in System > Preferences > Sessions and see which programs are trying to start up.

---

### Post by rampage355 on 2007-11-30
can't get there, the top menu bar and bottom task bar is gone.
the one error is 
Starting without admin privileges. You will not be able to apply any any changes. But you can still export the marked changes or creat a downoad script for them.

The other one is 
e: dkpg was intrupted you must manual run dpkg -configure -a! to e:
cache -. -> open (failed) please report.

---

### Post by rampage355 on 2007-11-30
I also did the dpkg --configure -a and nothing changed either

---

### Post by wormser on 2007-11-30
> **Amarsingh0793 said:**
> I had that problem too. I also couldn't do any administrative jobs but I found a solution. 
After logging in as root via terminal (su --login) , type the following
usermod -a -G admin yourusername

After that the problem should be fixed. :)

> **rampage355 said:**
> I also did the dpkg --configure -a and nothing changed either

Did you put sudo infront of both these commands?  That might not work because you might not be part of the Admin group.  The first command makes you an administrator and you might not be an administrator which could be the problem.  To check if you are an administrator run:

```
less /etc/group | grep -i admin
```

The output should be like this:  admin:x:110:YourUserName

If your user name is not there then that is the problem.  Reboot and log into recovery mode.  Run the first command then reboot.

---

### Post by rampage355 on 2007-12-05
Yea I was able to use the sudo for usermod -a -G admin yourusername and dpkg --configure -a
I also did the less /etc/group | grep -i admin and it returned admin:x:109:MyUserName.

Where do I go from here?

Grg

---

### Post by Amarsingh0793 on 2007-12-07
I don't know why the other one didn't work. Have you tried getting Remote Assistance from a friend? If you haven't, try that :). I will try and find a solution for you:confused:.

---

### Post by rampage355 on 2007-12-10
How do you do Remote Assistance from a friend? I don't see it anywhere sorry pretty new to this.

Greg

---

### Post by Amarsingh0793 on 2008-01-17
Remote Assistance should be somewhere in the System Menu. If you can't see it, right click the menu and click edit menus. Then look for Remote Assistance and check the box next to it.

Hope this helps!

---

### Post by Amarsingh0793 on 2008-01-17
If that doesn't work out, try launchpad. That is where I get all of my problems fixed! Here is the link: 
[URL="https://launchpad.net/ubuntu"]
https://launchpad.net/ubuntu[/URL]

There was a similar bug posted in the site somewhere but I've forgotten where.

---

### Post by notadog on 2008-04-07
After a reinstall (of mythbuntu) I was getting the same message.  I managed to get rid of it by looking for startup settings as mentioned earlier in this thread.  Turning off "Launch Gnome Services..." in the advanced settings eliminated this message for me.  I haven't noticed any issues resulting from turning off those services.

---

