---
title: "&quot;Samba Package Broken&quot; cant do updates"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by scotty32 on 2007-03-12
hi,

On my mums PC, it seems Evolution doesnt want to load up, you click on it you can see its "loading" (Cursor and HDD) but then nothing, it doesnt load.

so i decided to try a "Re-Install" of it, but the package manager complains of a broken package, samba.

i cant re-install samba, i cant remove samba, and i cant completely remove samba.
i cant do anything in the P.M with samba. so i cant do updates or try to fix Evo.

can anyone suggest the best way i can repair or remove Samba?
though its not really needed anyway.

---

### Post by useResa on 2007-03-12
Hi, normally broken packages can either be fixed in Synaptics or by issuing the following in a terminal```
sudo apt-get install -f
```.
Have you tried this command?
If so, could you please provide the result of this command?

---

### Post by juleshernandez on 2007-03-14
Good day!

Please see [https://answers.launchpad.net/ubuntu/+ticket/3583]("https://answers.launchpad.net/ubuntu/+ticket/3583/"). 

I'm also trying to reinstall Samba, but the solution in the above link didn't work for me :( . Maybe you'll be more lucky :) 

I posted a reply to another thread [http://ubuntuforums.org/showthread.php?t=245146]("http://ubuntuforums.org/showthread.php?t=245146/") that gives more specifics about a Samba install error.

---

### Post by scotty32 on 2007-03-28
thanks for the link to launchpad, but that didnt work.

it seems that the computer is using a newer version of samba-common

i saw the following error:

```
The following packages have unmet dependencies:
   samba: Depends: samba-common (= 3.0.22-1ubuntu3.1) but 3.0.22-1ubuntu3.2 is installed.
```

i cant seem to install or remove anything, because this Synaptic wants this fixed.

also terminal complains if you try to do any "apt"ing.

anyone know a commandline way to make it remove version (...)ubuntu3.2 and install (..)ubuntu3.1

---

### Post by scotty32 on 2007-03-28
correction, i went back and tried it again.

i had errors on this line:

```
  sudo dpkg -P samba samba-common smbclient
```

but i decided i'd risk continuing this time, and did the following line:
```
  sudo rm -f /etc/rc*.d/*samba /etc/init.d/samba
```

then i could reinstall samba, and now am able to do updates.

if your having problems.... and willing to risk your system (am a newbie, not sure HOW risky it is) then doing the "rm" line is worth a shot.


anyway, thanks for the help, now i can try and fix evolution

---

