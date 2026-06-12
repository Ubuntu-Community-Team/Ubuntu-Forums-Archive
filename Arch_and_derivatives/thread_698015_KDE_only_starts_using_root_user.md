---
title: "KDE only starts using root user"
date: 2008-02-15
forum: Arch and derivatives
---

### Post by cprofitt on 2008-02-15
Having a little issue with my Arch installation...
 
I just re-did my install of Arch and I have gone over and over the instructions (I am sure I am missing some small item)... but the only way I can get KDE to start (from KDM) is if I login as root.
 
If I start as another user I get a message:
 
> 
Call to lnusertemp failed (temporary directories full?). Check your installation.

 
Does anyone know what this is before I pull out more hair trying to find the thing I missed?
 
Thanks.

---

### Post by fwojciec on 2008-02-15
check the permissions on the /tmp folder.  I've seen a number of people having similar problems and fixing permissions on the /tmp folder was the solution...  The correct permissions are 1777.

---

### Post by K.Mandla on 2008-02-16
That happens to me too. I end up changing the permissions on /tmp every time, because yaourt can't get to it either.

---

### Post by bwtranch on 2008-02-16
I haven't had this issue. I usually boot into Gnome, but I tried KDE boot and it worked fine. Are you using the kdemod package?

---

### Post by andbia on 2008-02-17
as root:
chmod -R 777 /tmp

then reboot and login with normal user

---

### Post by Crooksey on 2008-02-17
```

vi /etc/rc.d/perms

```

Make it look like

```

chmod -R 1777 /tmp
```

Make it executable

```

chmod +x /etc/rc.d/perms
```

Then in the deamons array of rc.conf add a new deamon called perms

---

### Post by Prinny_SoFaRo on 2008-03-27
Hmm...I'm having the same issue as the TC, but on Kubuntu...I tried solving the problem with chmod like everyone said, but it still doesn't work :/ First off, is the correct permission setting "1777" or just "777"? Because I tried the former...it didn't work...and I think it's already set to the latter.

Is there anything else that could cause this? I looked on the KDE site and tried making the directories it said lnusertemp exists to simulate, but no dice.

Although, it said they were to be named "tmp-HOSTNAME" and "socket-HOSTNAME" or something similar. The hostname of the computer is the string after the "@" at a terminal, right?

I just hope I don't have to reinstall...for whatever reason, I can't get the installer to come up from the CD! Seriously... o_O

---

