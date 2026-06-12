---
title: "How to use startup scripts"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-21
Hi there, i've got a question as to how i can get a bash script to run at startup.
Currently i've place a file in my .gnome folder, but i can't get it to run on startup.  This is what i've tried.  The file is called mailip.

kristie@Sparktop:~$ cd .gnome
[email]kristie@Sparktop:~/.gnom[/email]e$ chmod +x mailip
[email]kristie@Sparktop:~/.gnom[/email]e$ sudo ln -s /home/kristie/.gnome/mailip /etc/init.d/mailip
[sudo] password for kristie:
ln: creating symbolic link `/etc/init.d/mailip' to `/home/kristie/.gnome/mailip': File exists
[email]kristie@Sparktop:~/.gnom[/email]e$ update-rc.d mailip defaults
update-rc.d: /etc/init.d/mailip: file does not exist

what's the problem here?

Thanks, and sorry that this overflows from my last thread, but it's a different topic.

---

### Post by jordanmthomas on 2007-11-21
I don't know much about creating services for debian, but if I had a script to run at boot, I'd put it in /etc/rc.local

Just put the path to your executable in there.
```
/home/kristie/.gnome/mailip
```

---

### Post by PointyWombat on 2007-11-21
ok, typically you put the script into /etc/init.d and link to it from whatever run level you wish it to execute from during startup.

Example:
Your script lives in /etc/init.d/script.sh
Link it within a run level:
ln -s /etc/init.d/script.sh /etc/rc3.d/S99script
which will give you
ls -l /etc/rc3.d/S99script
lrwxrwxrwx 1 root root 16 2007-11-21 01:35 /etc/rc3.d/S99script -> /etc/init.d/script.sh

You must prefix the name in the rc3.d directory with a capitol S followed by a number... which tells it to run on startup and at what sequence. 

You'll need to use sudo

---

### Post by jordank on 2007-11-21
i dont really follow what you're saying wombat, but i did try the other method mentioned.  I added the directory to the rc.local file, but nothing happened.
what am i missing?

sudo gedit /etc/rc.local
and added the line:
/home/kristie/.gnome/mailip

does this maybe need a # sign infront of it?
Or why does this not execute on startup?

---

### Post by jordanmthomas on 2007-11-21
No, you don't need a hash mark.
Are you sure it doesn't execute?  Try putting this in your script at the end or something
```
touch /home/kristie/Desktop/IDIDINFACTRUN
```
If after you reboot, there is a file called IDIDINFACTRUN on your desktop, then it did, in fact, run.

---

### Post by jordank on 2007-11-21
after adding that line of code, it still doesnt run.
What could the problem be?

sudo gedit /etc/rc.local
gives


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
/home/jordan/.gnome/mailip
exit 0


obviously the /home/jordan/.gnome/mailip is what i added, in attempts to run my script that is located in the gnome folder.
(the machine i'm on right now is under jordan, not kristie, so that's not the problem)

suggestions?  do i need to make mailip executable somehow? i thought i already did this.

---

