---
title: "Multiple troubles after install"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by Slavus on 2006-05-09
I cant do a clean boot, I can only go through recovery mode and start gnome manually. I know this is not the real OS and im kinda pissed.

Just letting the system boot will bring me to the login screen, where I proceed to type in my username and notice my computer has completely frozen up. CTRL ALT F1 does nothing, and i am forced to hard restart.

I have only been able to let it boot normally once, the very first time-- I dont know what I did wrong, maybe restarting the system too fast?

Is there a diagnostic i can run to check for errors? its not Gnome but something else running at the same time as gnome, because using sudo /etc/init.d/gdm start in recovery mode produces no errors.

---

### Post by deadgobby on 2006-05-09
[QUOTE=Slavus]I cant do a clean boot, I can only go through recovery mode and start gnome manually. I know this is not the real OS and im kinda pissed.

Just letting the system boot will bring me to the login screen, where I proceed to type in my username and notice my computer has completely frozen up. CTRL ALT F1 does nothing, and i am forced to hard restart.

I have only been able to let it boot normally once, the very first time-- I dont know what I did wrong, maybe restarting the system too fast?

Is there a diagnostic i can run to check for errors? its not Gnome but something else running at the same time as gnome, because using sudo /etc/init.d/gdm start in recovery mode produces no errors.[/QUOTE]
 What Vid card do you hav installed on your system?

---

### Post by Sef on 2006-05-09
I'll answer the questions that I can.

> 4. Is having no desktop icons normal?

For Gnome, yes.  There is just the icons on the top tool bar and a couple on the bottom one.

If you want to add an icon to your top tool bar or desktop, go to Applications and highlight the application you want on the tool bar/desktop, then right click and select the option you want.

> now, i can log in, but... theres really nothing i can do without a mouse.

If you have no mouse, you can open, applications this way:

ALT + F2 will bring up run application.  Either type in a name or click on 'Show List of Known Applications'.  Find the one you want and click twice on it.  That will open the application.

If you have any more questions, please post them.

---

### Post by Slavus on 2006-05-09
a geforce 6800

I tried going through a HOWTO on installing the latest nvidia drivers, but with no  luck. The only driver that works is Vesa


------Thanks for clearing those up for me Sef.

---

### Post by Sef on 2006-05-09
You're welcome.  

HAL

> 
HAL (Hardware Abstraction Layer) is a specification and an implementation of a hardware abstraction layer. It encompasses a shared library for use in applications, a daemon, a hotplug tool, command line tools, and a set of stock device info files.

[http://freshmeat.net/projects/halayer/]("http://freshmeat.net/projects/halayer/")

---

