---
title: "[SOLVED] Notification area lost."
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-07-02
Hi I have a problem with a dmrc error which I can deal with but!

```

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writeable by other users.
```

which I sorted using 
```

kevin@kevin-desktop:~$ sudo chown kevin /.dmrc
kevin@kevin-desktop:~$ sudo chmod 644 .dmrc
kevin@kevin-desktop:~$ sudo chown kevin .dmrc
kevin@kevin-desktop:~$ sudo chown kevin /home/kevin

```

Which clears the error - 

but when I log in I lose the notification area in the top panel - can't see the Network Manager - or amarok and gdesklets which I have in sessions startup.

Any ideas how to go about this?

TIA

---

### Post by bobbocanfly on 2007-07-02
Hopefully this will work. Right click on some blank space on your panel, then click add to panel. Look for notification area and double click it. You should now have you notification area back. It might be in the wrong place on the panel so left click the actual notification area then click move to shift it back to its place.

---

### Post by forestpixie on 2007-07-02
Erm... ah yes I forgot to say I'd tried that :oops: - and yes I get a notification area, but I don't get the Network Manager or either of the other two when I login.

---

### Post by forestpixie on 2007-07-03
bump

---

### Post by sailor2001 on 2007-07-03
check your "preferences/sessions" ?

---

### Post by forestpixie on 2007-07-03
since yesterday I'm back with the dmrc errror at login - have been studiously ignoring it.

If I now try the same commands as yesterday

kevin@kevin-desktop:~$ sudo chown kevin /.dmrc

gives me 

chown: cannot access `/.dmrc': No such file or directory

but at present I have my notification area with all I expect.

I had tried to add to panel and had checked sessions and it was showing but Network Manager (for instance) was starting but staying on the bottom panel

---

### Post by mcduck on 2007-07-03
> **forestpixie said:**
> since yesterday I'm back with the dmrc errror at login - have been studiously ignoring it.

If I now try the same commands as yesterday

kevin@kevin-desktop:~$ sudo chown kevin /.dmrc

gives me 

chown: cannot access `/.dmrc': No such file or directory



That command tries to chown .dmrc file in /, not in your home.

Either use 'sudo chown .dmrc' when you are in your home directory, or use 'sudo chown kevin ~/.dmrc' or 'sudo chown kevin /home/kevin/.dmrc'

By the way, are you using 'sudo' to start graphical applications? That seems to be the most common reson for permission/ownership problems of .dmrc file. You should always use 'gksudo' for graphical applications instead of 'sudo'.

---

### Post by forestpixie on 2007-07-03
Okay 'sudo chown kevin /home/kevin/.dmrc' didn't give me an error - logging out and in stiil get the dmrc error?

And I might have used sudo instead about 3 installs ago before I read the pyschocat page on gksudo/sudo - so I don't think it could be that.

On the last install - from a completely reformmated hdd - I had some issues with permissions for NTFS volume and other partitions - I mamaged to get it sorted but I guess I screwed something up in the process.


EDIT resolved with 

chmod 644 .dmrc

chmod 700 ~

---

