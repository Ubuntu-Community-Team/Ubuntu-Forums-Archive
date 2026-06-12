---
title: "Problems with ubuntu 6.06"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by Sniper99 on 2006-08-07
i have installed the newest version of ubuntu on a gateway with 640mb of ram a 20 gb hard drive and no other network connections..ever since i have installed ubuntu i cannot log in on a regular session...i have to go through a fail safe GNOME..which is extremely annoying. when i go through the failsafe GNOME it gives me an error message that has to deal with a power option..i have tried to correct this in the power options section of the menu...but cant seem to figure out to do from there:(

---

### Post by jimbren on 2006-08-07
What's the error message you're getting?

---

### Post by muep on 2006-08-07
Have you installed the basic Ubuntu with the Gnome desktop or is it a more specialized install? Can you access the command line?

If the problem is just with the session, you could first try creating a user to see if the problem is just with the old user's settings.

Are there any error messages, if there are, please post them here, so that we can understand the problem and help better.

Good luck :)

---

### Post by Sniper99 on 2006-08-07
the error messages say long lines of script dealing with the X session....i will copy the lines   it is the basic version, i have a gnome desktop, but will the failsafe allow me to create a new user with admin permissions, or will i have to do that some other way....hold on i have to run home to see the messages again.....i will repost in 15 min

---

### Post by Sniper99 on 2006-08-07
the error message is      

your session only lasted less than 10 seconds. If you have not loggged out yourself,this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem  (then there is a check box) (~/.xsession-errors file)


(if box is checked this appears)

/etc/gdm/PreSession Default:registering your session with wtmp and utmp

/etc/gdm/PreSession Default: running /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0" "spencer"

/etc/gdm Xsession:Beginning session setup...

Inconsistency detected by ld.so: ../sysdefs/i386/di-machine.h657:elf_machine_rel_relative : Assertion ` ((reloc->r_info) & 0xff) == 8`failed!

damn that was long...that is the exact line that is displayed...

---

### Post by kebes on 2006-08-07
Well it mentions disk space might be a problem. Are you out of diskspace? On a terminal you can type:
df

This will show you the free space on your disks/partitions. Make sure that's okay first.


You can make another user from the terminal command-line, so that is worth trying at some point. ("useradd" to add a user, "usermod" to change an account)

---

### Post by Sniper99 on 2006-08-07
i am not out of disk space, the bar at the bottom of the file browser says that i have 18.26 gigs left.....when i create a new user account can i edit the password and priveleges in the terminal or will it just have no password

---

### Post by zxee on 2006-08-07
> **Sniper99 said:**
> the error message is      

your session only lasted less than 10 seconds. If you have not loggged out yourself,this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem  (then there is a check box) (~/.xsession-errors file)


(if box is checked this appears)

/etc/gdm/PreSession Default:registering your session with wtmp and utmp

/etc/gdm/PreSession Default: running /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0" "spencer"

/etc/gdm Xsession:Beginning session setup...

Inconsistency detected by ld.so: ../sysdefs/i386/di-machine.h657:elf_machine_rel_relative : Assertion ` ((reloc->r_info) & 0xff) == 8`failed!

damn that was long...that is the exact line that is displayed...

Those "session only lasted..." errors usually are about permissions being set incorrectly on one or more of the users home directory. You can do a search on the error to verify that.
One possible solution is to > cd /home
 sudo chmod 700 "yourusername"
 sudo chown "yourusername" "yourusername"
 sudo chgrp "yourusername" "yourusername" Where I've typed "yourusername" you would of course enter the username for the install.
I don't know for sure that the above suggestion will work but it has gotten me out of that error.

---

### Post by Sniper99 on 2006-08-07
thanks...i will try it as soon as i get off work

---

### Post by Sniper99 on 2006-08-07
i have another question...if that doesn't work...can i just reinstall ubuntu...i mean if that would work out all the bugs i currently have i will do that...i have nothing important on there yet....if i can do it...how do i?

---

### Post by jason.b.c on 2006-08-07
Your session only lasted 10 seconds....

[http://ubuntuforums.org/showthread.php?t=134400]("http://ubuntuforums.org/showthread.php?t=134400")

---

### Post by kebes on 2006-08-07
Reinstalling Ubuntu would certainly fix your problem. If you have nothing important on that installation then this is certainly an option. To do so, just put in the install CD (if you don't have one you can download the ISO file from the Ubuntu webpage and burn it to a blank CD) and reboot your computer, and then follow the install steps.

---

