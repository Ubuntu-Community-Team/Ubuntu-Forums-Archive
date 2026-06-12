---
title: "you have to see this error message"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by gsb005 on 2007-03-01
Ok guys-

So I am fairly new to ubuntu- and need step by step directions...

Basically, i was messing with the services & turned off some that I thought i didn't need in Ubuntu.

Now upon bootup.. I get this error message:

Internal Error
Failed to Initalize HAL.

I don't know what it means or how to fix it-

Also, how can I create a root account- even though my credentials were used to insteall the system, it, denies me rights to say, "users and groups" or "services" because of the above mentioned problem.

Please advice...:confused:

---

### Post by userundefine on 2007-03-01
For root, there's no reason to enable a root account unless you really know what you're doing.

To get root privileges, you preface all your commands with the sudo command.  For example, if you want to change the name of the /etc/apt/sources.list file, owned by root, you would type **sudo mv /etc/apt/sources.list /etc/apt/sources.list.moved**.  Sudo will ask your pw before the command runs.

To use a graphical program with root, in Gnome type **gksudo [program]**.

---

### Post by gsb005 on 2007-03-01
> **userundefine said:**
> For root, there's no reason to enable a root account unless you really know what you're doing.

To get root privileges, you preface all your commands with the sudo command.  For example, if you want to change the name of the /etc/apt/sources.list file, owned by root, you would type **sudo mv /etc/apt/sources.list /etc/apt/sources.list.moved**.  Sudo will ask your pw before the command runs.

To use a graphical program with root, in Gnome type **gksudo [program]**.

So, for example, when I goto "users and groups" it says...
"the configuration could not be loaded"

If I goto services, it says,
"the configuration could not be loaded"

Is this normal? 

If not?

How do I fix it?:(

---

### Post by userundefine on 2007-03-01
That's not normal and I haven't experienced it.  But a quick search brought me to [this thread]("http://ubuntuforums.org/showthread.php?t=286260") and apparently that's an Edgy bug that I would imagine *should* be resolved by now, and reading through the thread there are solutions in there.  It should help you.

---

