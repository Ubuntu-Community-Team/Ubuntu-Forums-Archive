---
title: "HELP: system died!!!"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by tiris on 2006-02-03
Someone help, I don’t know what is going on.

I have had my system up for around two weeks installing various programs and have been using it fine until…
I was in FireFox and had just updated my bookmarks using the import function. The system seemed to be working fine for like 30 min then the mouse was not where to be found and focus would leave the FireFox window so I used ctrl+alt+F1 to login to the shell and reboot. When the system came back up and I logged in it said “You session only lasted less then 10 seconds…” and had this in the error details.

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "tiris"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/deskubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/deskubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/deskubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:6903): WARNING **: Unable to read ICE authority file: /home/tiris/.ICEauthority

```

I don’t have any idea what is wrong or even what could be tried other than reinstalling the system. I don’t really want to do that because I would like to learn how to fix things rather than wiping the system.

Any help or advice would be great.

Thanks,

---

### Post by tiris on 2006-02-03
After doing some digging I fixed the problem but I would still like to turn this into a learning experience. Here are my observations.

To fix the problem all I did was rename the file /home/tiris/.ICEauthority to /home/ tiris/.ICEauthority.bak

```
diff .ICEauthority .ICEauthority.bak |less
```

yields 
Binary files .ICEauthority and .ICEauthority.bak differ

so I am not sure how else to compare the difference between them.

I did notice that the owner is different and maybe this is the reason the session failed to start.
-rw-------   1 tiris tiris       165 2006-02-03 14:57 .ICEauthority
-rw-------   1 root  root        495 2006-02-02 10:20 .ICEauthority.bak

Okay time for learning.
How/why would the old file have become to be owned by root?
What is in this file that I can rename it and everything is okay? In other words how is the file important?

---

### Post by griz on 2006-02-03
Hi,
I had the same problem myself when I used K3B in Gnome.  Try typing:

sudo chown *username*:*username* .ICEauthority

Worked for me.

Griz.

---

### Post by krusbjorn on 2006-02-03
You need to have permission to write to the .ICEauthority file in your home folder. If you run (for example) K3b as root, it will create an .ICEauthority file that is owned by root, and therefore you wont be able to login next time you try.

As you said, you can either rename, delete or make yourself owner of the file to solve the problem.

---

### Post by tiris on 2006-02-06
What is in the .ICEauthority file?
What information am I loosing if I delete it and it is recreated?

---

### Post by GTvulse on 2006-02-06
[QUOTE=tiris]What is in the .ICEauthority file?
What information am I loosing if I delete it and it is recreated?[/QUOTE]

The ability to login to remote X displays using XDCMP credentials. As XDMCP is disabled by default in Ubuntu, you are not losing anything of value. Localhost credentials are recreated automatically.

---

