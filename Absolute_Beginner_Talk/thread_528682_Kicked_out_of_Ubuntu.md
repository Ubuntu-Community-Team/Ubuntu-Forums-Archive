---
title: "Kicked out of Ubuntu"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by rubab on 2007-08-18
I needed to change the permission of /etc/sudoers to 0440. But i rebooted in the recovery mode and entered this in the terminal "sudo chmod -R 0440 /etc" and then the terminal showed something like there is an error opening bash file or something like that and instead of showing my username "rubab@dualboot07:~$" it started showing something like "i have no name!@dualboot07:~$.
And after restarting it only asks for a login. The same thing is asked in the Recovery Mode. My login is not working. Please Help.

---

### Post by apjone on 2007-08-18
> **rubab said:**
> I needed to change the permission of /etc/sudoers to 0440. But i rebooted in the recovery mode and entered this in the terminal "sudo chmod -R 0440 /etc" and then the terminal showed something like there is an error opening bash file or something like that and instead of showing my username "rubab@dualboot07:~$" it started showing something like "i have no name!@dualboot07:~$.
And after restarting it only asks for a login. The same thing is asked in the Recovery Mode. My login is not working. Please Help.

chmod'in /etc to 0400 is a nice way to break your system. 

I suggest a re-install. Sorry dude

---

### Post by rubab on 2007-08-18
> apjone  	
Re: Kicked out of Ubuntu
Quote:
Originally Posted by rubab View Post
I needed to change the permission of /etc/sudoers to 0440. But i rebooted in the recovery mode and entered this in the terminal "sudo chmod -R 0440 /etc" and then the terminal showed something like there is an error opening bash file or something like that and instead of showing my username "rubab@dualboot07:~$" it started showing something like "i have no name!@dualboot07:~$.
And after restarting it only asks for a login. The same thing is asked in the Recovery Mode. My login is not working. Please Help.
chmod'in /etc to 0400 is a nice way to break your system.

I suggest a re-install. Sorry dude

apjone you are in this Forum from Nov 2005 and you are telling me to re-install. I dont know if you are serious or are you joking but there was an easy method.

I just had to boot my PC with the live CD and enter
"chmod -R 0777 /media/Disk/etc" 
in the terminal and i was able to boot Ubuntu.
Man your suggestion freaked me out.

But thanks, atleast you replied.

---

### Post by rubab on 2007-08-18
.

---

### Post by nichipet on 2007-08-18
apjone was not wrong to suggest a reinstall. Fooling around with /etc is a great way to break your system. By the way, you said:

> I needed to change the permission of /etc/sudoers to 0440

yet:

> But i rebooted in the recovery mode and entered this in the terminal "sudo chmod -R 0440 /etc" 

Why mess with the entire /etc directory when only one file needed changing? Oh, and

```
sudo chmod -R 0440 /etc
```

not only changes the permissions of sudoers, but of every other file in /etc and every file in every directory in /etc, and so on. That may be why a reinstall was suggested; do you know the correct permissions of everything in /etc? I don't, so if I recursively changed the permission of everything in there I may be reinstalling as well.

---

### Post by steve.horsley on 2007-08-18
That has made your system horribly insecure, and you probably can't use sudo any more. A re-install is the only way to fix this properly, I'm afraid.

---

### Post by apjone on 2007-08-18
> **steve.horsley said:**
> That has made your system horribly insecure, and you probably can't use sudo any more. A re-install is the only way to fix this properly, I'm afraid.

That is why i suggested it in my first post. I dont think anyone has ever reset /etc back to correct permissions ever. Its just to much work and chmod'in every thing to 777 is insecure.

---

### Post by vexorian on 2007-08-18
well, think about this: you just need to keep your /home in a safe place, and reinstalling ubuntu would not take more than 1 hour, and you can still use the web  / things while installing from live-cd , so it is a good alternative imho

---

### Post by rubab on 2007-08-18
Guys read the post i have posted above. i solved the problem everything is working just fine. No re-installation required. I just had to use the Live CD and chmod etc back to 0777. I think you misunderstood my second Post. It was the way how i solved the problem. I posted it cause in the future may be it will be helpful for other users.

---

### Post by nichipet on 2007-08-18
And what did chmod -R 0777 /etc accomplish, besides appearing to fix your problem? Do you know what it did to your system?

It just made everything that has a path starting with /etc readable, writable, and executable by every user on your system. That's why we're all telling you that your system is insecure and needs reinstalling. We understand your post just fine.

As vexorian pointed out, copy your /home to somewhere safe and the reinstall takes 20-60 minutes.

---

### Post by p_quarles on 2007-08-18
> It just made everything that has a path starting with /etc readable, writable, and executable by every user on your system.
In other words: "Welcome scriptkiddies! You are now free to run startup programs on my computer! Feel free to mess around with the cronjobs!"

---

### Post by dmizer on 2007-08-18
no ... what you're missing here is that despite appearances ... everything is NOT fine.

/etc should NOT be 777 permissions.  this is very very bad, and breaks things that you do not immediately see.  the entire /etc directory has many different permission levels for specific situations and reasons.  making everything in /etc 777 rendered your system worthless.  it may appear to be working fine now.  but it's broken, and sooner or later you'll start to see the results of that.

here's just a small sample from my own /etc directory:
```
/etc$ ls -l
drwxr-xr-x  8 root   root      4096 2007-08-10 02:18 acpi
-rw-r--r--  1 root   root      2657 2007-08-10 01:50 adduser.conf
-rw-r--r--  1 root   root        45 2007-08-18 21:42 adjtime
-rw-r--r--  1 root   root        51 2007-08-10 02:35 aliases
drwxr-xr-x  2 root   root      4096 2007-08-14 23:32 alsa
drwxr-xr-x  2 root   root      4096 2007-08-17 18:30 alternatives
-rw-r--r--  1 root   root       395 2007-03-05 15:38 anacrontab
drwxr-xr-x  2 root   root      4096 2007-08-10 02:18 anthy
drwxr-xr-x  7 root   root      4096 2007-08-10 02:18 apm
drwxr-xr-x  4 root   root      4096 2007-08-10 01:55 apt
-rw-r-----  1 root   daemon     144 2007-02-20 22:41 at.deny
drwxr-xr-x  4 root   root      4096 2007-08-10 02:18 avahi
-rw-r--r--  1 root   root      1566 2007-04-11 08:32 bash.bashrc
-rw-r--r--  1 root   root       278 2007-04-10 16:34 bash_command_not_found
-rw-r--r--  1 root   root    215938 2007-04-11 08:32 bash_completion
drwxr-xr-x  2 root   root      4096 2007-08-14 23:32 bash_completion.d
drwxr-xr-x  2 root   root      4096 2007-08-10 01:49 belocs
-rw-r--r--  1 root   root       248 2007-08-10 02:35 blkid.tab
drwxr-xr-x  2 root   root      4096 2007-08-17 18:30 bonobo-activation
-rw-r--r--  1 root   root      4832 2007-08-10 02:32 ca-certificates.conf
drwxr-xr-x  2 root   root      4096 2007-08-10 02:17 calendar
drwxr-s---  2 root   dip       4096 2007-08-10 02:18 chatscripts
drwxr-xr-x  2 root   root      4096 2007-08-10 01:51 console-setup
drwxr-xr-x  2 root   root      4096 2007-08-10 01:51 console-tools
drwxr-xr-x  2 root   root      4096 2007-08-10 02:17 cron.d
drwxr-xr-x  2 root   root      4096 2007-08-10 02:20 cron.daily
drwxr-xr-x  2 root   root      4096 2007-08-10 02:17 cron.hourly
drwxr-xr-x  2 root   root      4096 2007-08-10 02:19 cron.monthly
-rw-r--r--  1 root   root       724 2006-12-20 23:46 crontab
drwxr-xr-x  2 root   root      4096 2007-08-10 02:18 cron.weekly
drwxr-sr-t  5 cupsys lp        4096 2007-08-10 02:21 cups
drwxr-xr-x  4 root   root      4096 2007-08-10 02:18 dbus-1
```

move your home directory to a separate partition and reinstall ubuntu.

and from here forward ... avoid changing permissions in directories outside of /home.

doom .... doooooooooom.

---

### Post by rubab on 2007-08-18
Ok i have downloaded Apton CD. Now if i backup my home directory and use apton CD to Backup the packages will it be OK if i format this partition on which Ubuntu is Installed and do a Clean Insatallation. Do i need to backup anything else. 
By the way please look at this thread [http://ubuntuforums.org/showthread.php?t=523479&goto=newpost]("http://ubuntuforums.org/showthread.php?t=523479&goto=newpost")
and help me solve this problem please because one of the things i liked about Ubuntu was Myth Tv and if i cannot get the TV card work on Ubuntu i would need to Dualboot Ubuntu with Windows XP for the rest of my life cause i like to record my favorite shows in my PC. Now i don't have enough budget for buying a New TV Card ,that is why i am seeking your advice and support on this matter.

---

### Post by stmiller on 2007-08-23
You can reinstall Ubuntu and retain your /home partition, if it's on another partition. Just tell the install to not reformat that /home partition.

But if it's not a different partition, yeah you'll have to backup and reinstall.

---

