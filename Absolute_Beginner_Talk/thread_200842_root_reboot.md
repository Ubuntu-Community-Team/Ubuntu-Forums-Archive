---
title: "root reboot"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by mbgb14 on 2006-06-20
Hi,

Can someone tell me (asap) how to make it so *only* root can reboot the machine?
Yet again, my sister just was upstairs, and rebooted into Windows, meanwhile I'm downstairs remoting in with SSH and VNC and all of a sudden. Wammo. 

How can I make this change please? Thanks.

---

### Post by Thirsteh on 2006-06-20
This might not be very helpful, but I do believe there's a usergroup that allows users to reboot, if you remove your normal user from that group, they shouldn't be able to, unless they sudo.

I might be wrong, but better than nothing anywho :)

---

### Post by mbgb14 on 2006-06-20
[QUOTE=Thirsteh]This might not be very helpful, but I do believe there's a usergroup that allows users to reboot, if you remove your normal user from that group, they shouldn't be able to, unless they sudo.

I might be wrong, but better than nothing anywho :)[/QUOTE]
Suspected something like that - but I can't seem to find an obvious group. 
#-o Any ideas?

---

### Post by aysiu on 2006-06-20
How about just creating a keyboard shortcut for locking the session? That way, she can't reboot... well, unless she just unplugs the computer...

---

### Post by mbgb14 on 2006-06-20
[QUOTE=aysiu]How about just creating a keyboard shortcut for locking the session? That way, she can't reboot... well, unless she just unplugs the computer...[/QUOTE]
She has her own account, I always keep mine locked no problem there. The problem is she logs in as her and just reboots it cuz she thinks Windows is leet.

---

### Post by %hMa@?b&lt;C on 2006-06-20
well if you have a power button, your screwed either way eh?
Just delete the windows partition, we'll see who's 1337 then!:roll:

---

### Post by aysiu on 2006-06-20
```
lrwxrwxrwx  1 root root        4 2006-05-31 22:44 reboot -> halt
``` Looks as if just about anyone can reboot, if I'm looking in the right place (/sbin/reboot). You could try *chmod*ing this file, but I don't know if that'll solve the problem.

The weird thing is that anyone can reboot graphically, but if you try to reboot from the command-line, only root can do it.

I think you can use KDM (instead of GDM) and limit who has the ability to shutdown.

---

### Post by mbgb14 on 2006-06-20
Yeah I could try chmodding that, but I doubt that would be such a wise idea without more information. 

Hehe. If I delete my windows partition, my dad will kill me.

---

### Post by aysiu on 2006-06-20
What about KDM?

---

### Post by mbgb14 on 2006-06-21
[QUOTE=aysiu]What about KDM?[/QUOTE]
That wouldn't be Ubuntu now then would it.. I think they call that Kubuntu ;) ;)

---

### Post by aysiu on 2006-06-21
You can use KDM with Ubuntu.

---

### Post by mbgb14 on 2006-06-21
[QUOTE=aysiu]You can use KDM with Ubuntu.[/QUOTE]
Isn't KDM a KDE based program though?

---

### Post by aysiu on 2006-06-21
KDM basically manages the login and logout. It accompanies KDE, yes, but you can install KDM without installing KDE. ```
sudo aptitude update
sudo aptitude install kdm
```

---

### Post by mbgb14 on 2006-06-21
[QUOTE=aysiu]KDM basically manages the login and logout. It accompanies KDE, yes, but you can install KDM without installing KDE. ```
sudo aptitude update
sudo aptitude install kdm
```[/QUOTE]
Thanks, I'll try that. One question, once I install KDM, how do I 

1) Pick which one I want to use
2) Configure KDM (I know in KDE you use the control center, but there is none if I don't install KDE!)
3) Go back to GDM/switch back and forth

?

---

### Post by aysiu on 2006-06-21
Well, when you install KDM, you'll be given an option which you want to use.

I would imagine that the Control Center would be one of the dependencies of KDM, but if it isn't, there's a config file for it somewhere where you can edit stuff.

The file you want to modify is /etc/X11/default-display-manager

It'll basically say either ```
/usr/sbin/gdm
``` or ```
/usr/bin/kdm
```

---

### Post by mbgb14 on 2006-06-21
[QUOTE=aysiu]Well, when you install KDM, you'll be given an option which you want to use.

I would imagine that the Control Center would be one of the dependencies of KDM, but if it isn't, there's a config file for it somewhere where you can edit stuff.

The file you want to modify is /etc/X11/default-display-manager

It'll basically say either ```
/usr/sbin/gdm
``` or ```
/usr/bin/kdm
```[/QUOTE]
Thanks... I'll check it out -- I just wish there was a way to make GDM do this :-/
There surely *must* be.

---

### Post by aysiu on 2006-06-21
If KDM doesn't install Control Center, you can edit the config file /etc/kde3/kdm/kdmrc

Here's an excerpt: ```
#AuthNames=
# Need to reset the X-server to make it read initial Xauth file.
# Default is false
#ResetForAuth=true
# See above
AllowNullPasswd=true
# See above
**AllowShutdown=All**
# Enable password-less logins on this display. USE WITH EXTREME CARE!
# Default is false
#NoPassEnable=true
# The users that do not need to provide a password to log in. NEVER list root!
# "*" means all non-root users. @<group> means all users in that group.
# Default is ""
#NoPassUsers=fred,ethel
```

---

### Post by mbgb14 on 2006-06-21
[QUOTE=aysiu]If KDM doesn't install Control Center, you can edit the config file /etc/kde3/kdm/kdmrc

Here's an excerpt: ```
#AuthNames=
# Need to reset the X-server to make it read initial Xauth file.
# Default is false
#ResetForAuth=true
# See above
AllowNullPasswd=true
# See above
**AllowShutdown=All**
# Enable password-less logins on this display. USE WITH EXTREME CARE!
# Default is false
#NoPassEnable=true
# The users that do not need to provide a password to log in. NEVER list root!
# "*" means all non-root users. @<group> means all users in that group.
# Default is ""
#NoPassUsers=fred,ethel
```[/QUOTE]

Sweet. Thanks again. 
*Now to find out about Gdm :-/*

---

### Post by tonyr on 2006-06-21
Just to throw a spanner in the works, the **gdm** configuration file, **/etc/X11/gdm/gdm.conf**
contains this:
> 
# Reboot, Halt and suspend commands, you can add different commands separated
# by a semicolon.  GDM will use the first one it can find.
RebootCommand=/sbin/shutdown -r now "Rebooted from gdm menu."
HaltCommand=/sbin/shutdown -h now "Halted from gdm menu."
SuspendCommand=/usr/sbin/pmi action sleep
HibernateCommand=/usr/sbin/pmi action hibernate


I read this to mean you can substitute a command of your own, say, for example, a script
that checks who is actually invoking the command, and allowing the shutdown command
to be run only for certain users.

There are some things I don't know about this.  Is the logged in username actually
available by the time the RebootCommand is called, and if so where/how?

You shouldn't modify the file **gdm.conf** directly, but it's overriding companion,
**gdm.conf-custom**, by redefining RebootCommand in the appropriate section.

---

### Post by dmizer on 2006-06-21
[QUOTE=tonyr]Just to throw a spanner in the works, the **gdm** configuration file, **/etc/X11/gdm/gdm.conf**
contains this:
```
# Reboot, Halt and suspend commands, you can add different commands separated
# by a semicolon. GDM will use the first one it can find.
RebootCommand=/sbin/shutdown -r now "Rebooted from gdm menu."
HaltCommand=/sbin/shutdown -h now "Halted from gdm menu."
SuspendCommand=/usr/sbin/pmi action sleep
HibernateCommand=/usr/sbin/pmi action hibernate
```

I read this to mean you can substitute a command of your own, say, for example, a script
that checks who is actually invoking the command, and allowing the shutdown command
to be run only for certain users.

There are some things I don't know about this.  Is the logged in username actually
available by the time the RebootCommand is called, and if so where/how?

You shouldn't modify the file **gdm.conf** directly, but it's overriding companion,
**gdm.conf-custom**, by redefining RebootCommand in the appropriate section.[/QUOTE]
i like this solution.  just comment out the two lines:
RebootCommand=/sbin/shutdown -r now "Rebooted from gdm menu."
HaltCommand=/sbin/shutdown -h now "Halted from gdm menu."

that way, the only way to reboot or halt the machine would be from the cli ... as root, and if you ever need to change that just take the coment off.

---

### Post by tonyr on 2006-06-21
[QUOTE=dmizer]i like this solution.  just comment out the two lines:
RebootCommand=/sbin/shutdown -r now "Rebooted from gdm menu."
HaltCommand=/sbin/shutdown -h now "Halted from gdm menu."

that way, the only way to reboot or halt the machine would be from the cli ... as root, and if you ever need to change that just take the coment off.[/QUOTE]

It doesn't seem to be that easy.   Without those lines, selecting Restart results in
gdm exiting to the cli console with no shutdown, almost the same behavior as
CTL-ALT-F1.  I tried substituting **/bin/false** and **/bin/true** for the
**shutdown** commands, and I tried simply removing the **shutdown** 
commands (leaving a NULL definitions for RebootCommand and HaltCommand), 
but Restart happened anyway.   This may not be such a good idea after all.

---

### Post by glotz on 2006-06-21
But this discussion is all purely academic. She can always hit teh power button or if that's disabled in BIOS, pull the plug. You've just have to spank her into Linux!

---

### Post by dmizer on 2006-06-21
[QUOTE=glotz]But this discussion is all purely academic. She can always hit teh power button or if that's disabled in BIOS, pull the plug. You've just have to spank her into Linux![/QUOTE]
maybe ... but then she should get a sharp scolding for potentially damaging the computer.  Not that it makes such a huge difference anymore (compared to win95 days anyway), but the prevailing common belief is that manually powering off a running machine is a bad idea.

course spanking her into linux might be more rewarding in the long run ... lol

lol, there has to be some way to completely remove the reboot/shutdown options from the gdm.

---

### Post by glotz on 2006-06-21
One overly complicated solution would be to install **bastille** and have it set only roots can reboot.

---

### Post by tonyr on 2006-06-21
I found a brute force method out on the net.  You can turn off the **Quit** display,
the one that shows you the buttons for choosing Restart, Logout, Hibernate, etc.
altogether.  A bit drastic, and not very clean.  The event associated with System->Quit
is apparently stored forever, or until you re-activate the **Quit** display, even
across boots.  It feels kind of like things are not being managed very well,
gdm-configuration-wise.

**System->Administration->Login Window** has a checkbox labeled 
**Show Actions menu**, which, when unchecked, prevents **System->Quit**
from showing anything.  It also prevents the GDM login window **Options** menu
from showing halt and restart selections.

---

### Post by mbgb14 on 2006-06-21
[QUOTE=tonyr]I found a brute force method out on the net.  You can turn off the **Quit** display,
the one that shows you the buttons for choosing Restart, Logout, Hibernate, etc.
altogether.  A bit drastic, and not very clean.  The event associated with System->Quit
is apparently stored forever, or until you re-activate the **Quit** display, even
across boots.  It feels kind of like things are not being managed very well,
gdm-configuration-wise.

**System->Administration->Login Window** has a checkbox labeled 
**Show Actions menu**, which, when unchecked, prevents **System->Quit**
from showing anything.  It also prevents the GDM login window **Options** menu
from showing halt and restart selections.[/QUOTE]
How do users logoff when I do that?

---

### Post by steve.horsley on 2006-06-21
Whatever you do, I think you'll have trouble stopping the sequence Alt-Ctrl-F1 Alt-Ctrl-Del. 

Give her a spanking or threaten to format windows.

---

### Post by tonyr on 2006-06-21
[QUOTE=mbgb14]How do users logoff when I do that?[/QUOTE]

I don't know.  I said it was brute force.:(  There may still be some way to do
it with **gdm** configuration; I just haven't looked deep enough.

---

### Post by tonyr on 2006-06-22
I revisited this, and came up with some almost satisfactory results.

I added these lines to **/etc/gdm/gdm.conf-custom** under **[daemon]**
```

RebootCommand=""
HaltCommand=""

```

I'm attaching the revised file.

After restarting **gdm**, I selected **System->Quit** and waited. After
about two minutes (I think), the Actions display appeared without the Restart
and Shutdown buttons, but the other buttons were still there: Logout, Switch user,
Hibernate, Lock Screen.

Subsequent selections of **System->Quit ** suffered only a couple of seconds
delay.  I guess there is some kind of wholesale reconstruction of the Desktop/Menu
World going on the first time?

The Options button at the bottom of the GDM Login screen shows Hibernate and
Suspend, but not Halt or Restart.

---

### Post by jpepin on 2006-06-23
Just edit your grub menu.lst file to make ubuntu the default OS on boot, and give her about 2 seconds to change her selection.  It'll take that long to read the menu, unless you know what you're looking at.  Or you could always set the grub menu to be hidden, unless a certain key combo is pushed.  

Either way, rebooting on her part would be futile :)

---

### Post by e_james on 2006-06-23
Suggestion. Edit or replace bootloader in such a way that only you can start Windows (I'm not sure how). It won't help the first time, but then she'll have to ask.

Sorry. I hadn't read the preceding message before I wrote this.

---

