---
title: "log in as root"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by mikeee6562 on 2007-12-18
please show me how to log in as root

thanks mike

---

### Post by kellemes on 2007-12-18
> **mikeee6562 said:**
> please show me how to log in as root

thanks mike

You can't by default..
There is no need to..
When you think you need it.. you're dead wrong. :popcorn:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by bumanie on 2007-12-18
You only need to have root privileges when you are changing something in the OS itself or adding packages etc. That is what the command sudo stands for (root). For general usage you don't need root privileges and thus there is no need to log in as root.

---

### Post by aysiu on 2007-12-18
You don't need to log in as root.

Why don't you explain what you're trying to accomplish, and then we'll explain the best way to accomplish it by *not* logging in as root?

---

### Post by lswest on 2007-12-18
well, might as well just answer the question so you know how.  go (in your normal user account) to system--->administration--->login and under the security tab check the "allow local administrator login" box, and then you can login at the login screen with "root" and your password for the root account.  However, it's a security risk, and just doing stuff with sudo is both faster and more efficient

---

### Post by psusi on 2007-12-18
There is no root password by default; the account is locked.

---

### Post by aysiu on 2007-12-18
> **lswest said:**
>  just doing stuff with sudo is both faster and more efficient That's the bottom line, which is why I try to find out what people want to accomplish rather than telling them inefficient ways to accomplish those tasks.

---

### Post by stchman on 2007-12-18
> **mikeee6562 said:**
> please show me how to log in as root

thanks mike

The root account is locked.

There is never a need to and if someone tells you otherwise they are completely wrong.

You can sudo things like nautilus or firefox but it is not recommended.

---

### Post by aysiu on 2007-12-18
> **stchman said:**
> 
You can sudo things like nautilus or firefox but it is not recommended. Or *gksudo* them.

---

### Post by stchman on 2007-12-18
> **aysiu said:**
> Or *gksudo* them.

My bad, gksudo should be used for graphical apps and sudo for CLI apps.

---

### Post by Lord DarkPat on 2007-12-18
just use "sudo"
It is safer than su (I guess)
I've done lots of crazy stuff with su you wouldn't wanna ask about:lolflag:
The root account is locked, anyways:popcorn:

---

### Post by Presto123 on 2007-12-18
Yeah..."sudo" can burn your house down or kill the Wicked Witch of the West depending on how you use it. :P

Sorry, had to be goofy on this...

---

### Post by ryharv on 2007-12-18
I'm trying to browse around the directory structure (ie, with the mouse and "windows," rather than on the command line).  Is there a "sudo" way to do this?  I found "drag and drop sudo" on [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo), but that only addresses how to run a program using sudo so you get root privileges.  All I want to do is move files around using sudo without using the command line.  Anybody know how?

Thanks for your help!

  Ryan Harvey

---

### Post by jken146 on 2007-12-18
> **ryharv said:**
> I'm trying to browse around the directory structure (ie, with the mouse and "windows," rather than on the command line).  Is there a "sudo" way to do this?  I found "drag and drop sudo" on [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo), but that only addresses how to run a program using sudo so you get root privileges.  All I want to do is move files around using sudo without using the command line.  Anybody know how?

Thanks for your help!

  Ryan Harvey

```
gksu nautilus
```

---

### Post by ryharv on 2007-12-18
Beautiful.  Thank you!

---

### Post by stanz on 2007-12-18
Hi All....
Just hours into my fresh Gutsy install and I'm trying to get familiar with the changes. One difference is in the panal icon launcher properties {nautilus being the focus here} are now pointing to the file to open: file:///home/stanz. 
I used to and now still need a quick click access to 'root' nautilus which was: 'gksu nautilus' and I was in {so to say}.
Does anyone know if there's a tweak to have this in Gutsy?
Thanks in advance, as I go reading on....:)

---

### Post by stanz on 2007-12-18
A quick find soon after posting.
I've often dragged the 'Home Folder' out of the main panel (Places) and modified the command.
Gutsy' Launcher Properties GUI has changed abit, but when adding a 'Custom Application Launcher', the 'Create Launcher' GUI has the familiar input for 'Command:' where I can place and create my 'gksudo nautilus'.
Ahhh, I'm just another satisfied user!

---

