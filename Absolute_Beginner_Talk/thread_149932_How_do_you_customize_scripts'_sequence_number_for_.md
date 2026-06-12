---
title: "How do you customize scripts' sequence number for different runlevels?"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-03-25
1) I have a start/stop script in /etc/init.d/myscript and I would like the script to start at sequence number 60 at runlevel 2 and 99 for the rest of the runlevels. That is,

/etc/rc1.d/S99myscript
/etc/rc2.d/S60myscript
/etc/rc3.d/S99myscript
/etc/rc4.d/S99myscript
/etc/rc5.d/S99myscript
/etc/rc6.d/S99myscript

Can this be accomplished through update-rc.d command?

2) I have a start/stop script in /etc/init.d/myscript and the script starts at sequence number 99 on all runlevels. How do I edit with 'update-rc.d' to change the sequence number at runlevel 2 from 99 to 50?

3) How do I remove a script from running at runlevel 2 without affecting the start/stop sequence of the script for the rest of the runlevels?


Thanks !

---

### Post by Pragmatist on 2006-03-25
The files in the rcN.d directories are just links to the actual programs in the /etc/init.d directory.  So you should be able to delete whichever ones you want.  I would BACKUP the directory just so I remembered what was there and what was its order.  As far as what happens if your not starting say S01 and yet the shutdown runlevel tries to stop it...it would exit with exit status 1 unless you use the --oknodo option.  Read this manpage for more:
```
man start-stop-daemon
```

Also there seem to be a couple of useful tools in the repositories to help you with your goal. Type this to run synaptic and then do a search using keyword: **runlevel**:
```
sudo synaptic
```

---

