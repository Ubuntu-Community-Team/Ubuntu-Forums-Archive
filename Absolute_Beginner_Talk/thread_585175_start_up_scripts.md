---
title: "start up scripts?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2007-10-21
So... refresh my memory. Where do I put start up scripts?

/etc/init.d doesn't seem to be working.

---

### Post by bodhi.zazen on 2007-10-21
/etc/rc.local

---

### Post by ant2ne on 2007-10-21
```
antsvr@antubuntu:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
antsvr@antubuntu:~$ 
```

I was thinking more of a directory whos contents are executed at start up. I could have swore there was such a directory.

---

### Post by aktiwers on 2007-10-21
Just put your command in the end of that file, and it will be run on startup

---

### Post by bodhi.zazen on 2007-10-21
Not sure what you are trying to do exactly.

This thread may help : [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

Or are you trying to set up a service ?

---

### Post by ant2ne on 2007-10-21
> **bodhi.zazen said:**
> Not sure what you are trying to do exactly.

This thread may help : [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

Or are you trying to set up a service ?

Basically, I just want to execute a script on start up that is located in my personal script location such as "~/scr/startscr" Then I just need to modify my startscr.

so I just need to...
```
sudo echo ~/scr/startscr >> /etc/rc.local
```?? of course, you can's sudo echo grrr...

---

### Post by bodhi.zazen on 2007-10-21
Well, you shoule edit the file directly as your command will add after "exit 0" :(

so : ```
gksu gedit /etc/rc.local
```

use the full path /home/....) and NOT ~

FYI for that sudo to work :

```
sudo -c sh "echo /home/<user_name>/scr/startscr >> /etc/rc.local"
```

for security you should make  ~/scr/startscr owned by root without writ access by your user ;)

---

### Post by ant2ne on 2007-10-21
> **bodhi.zazen said:**
> Well, you shoule edit the file directly as your command will add after "exit 0" :(

so : ```
gksu gedit /etc/rc.local
```

use the full path /home/....) and NOT ~

FYI for that sudo to work :

```
sudo -c sh "echo /home/<user_name>/scr/startscr >> /etc/rc.local"
```

for security you should make  ~/scr/startscr owned by root without writ access by your user ;)

my /etc/rc.local
```
#!/bin/sh -e
/home/antsvr/scr/antstart
exit 0
```This doesn't execute the script antstart. =(   All that is in there is the command to begin folding at home. I do see the security flaw, and will chown it. I like to keep all of my personal scripts in one place for easy back up and editing.

---

### Post by jpkotta on 2007-10-23
[https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome)

---

### Post by ant2ne on 2007-10-23
> **jpkotta said:**
> [https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome)

right, that script wouldn't work either. Maybe something is wrong with my init.d

---

