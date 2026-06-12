---
title: "Cannot accedd certain admin functions using Xubuntu Edgy Eft"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by oleyeller on 2007-01-10
Hi - I am a complete newbie and just installed Xubuntu 6.10 on an old machine. I cannot access users and groups from the user interface.  

I get a message 

"The configuration could not be loaded.  You are not allowed to access the system configuration"

I am a member of admin and can create new users at the command line using sudo.... which is what I did, BUT I should be able to use the interface...

I also cannot adjust date and time with the same message.

Can someone give me a step-by-step procedure using xubuntu to correct these errors on Xubuntu?
Can that person also explain what the problem is?

(I have another machine using Ubuntu 6.10 and to date I haven't seen this problem).

---

### Post by taurus on 2007-01-10
What's the output of this command from a terminal?

```
groups
```

---

### Post by oleyeller on 2007-01-10
Sure - here&#347; the output of the groups command...

daniel1 adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

(daniel1 is my user name)

The problem started after a system update...

I KNOW I had access to these menus before the update ...because, for instance, I activated networking....so that I could connect to the internet with a USB network driver...

Here&#347; what I don have access to in the system menu:
networking
services
shared folders
time and date
users and groups

I have access to all other things in the system folder for xubuntu (Synaptic, update manager, etc.).  These all prompt for a password...which I supply....

Make sense?

(I found this information elsewhere on the forum - and I am wondering if this would help....)
I also found some information saying reinstall drivers with dbus, but I don't know what is meaningful and what isn't.

Re: Edgy: not allowed to access the system configuration 

--------------------------------------------------------------------------------

Hi, in Xubuntu, you can solve the problem manually editing the .desktop files that refer to the entries in the System sub-menu, which are in /usr/share/applcations

You have to do it with root permission. What you have to edit is the Exec entry, just adding 
Code:
gksubefore the application name


-------------------------------------------------------------------------------------
Also, sudo still works... For instance, I can add the user at a terminal window using the sudo adduser command (with the -m and -g switches)...

---

### Post by oleyeller on 2007-01-11
OK - I fixed the problem by editing the files as posted above.  The question that I have is WHY did this happen on a system upgrade?  Can someone explain how gksu was removed from the *.desktop files?

---

