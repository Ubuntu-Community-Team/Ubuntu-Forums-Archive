---
title: "Help!  VMWare Server Quit Working after Update"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by indy107 on 2006-09-20
Hi, newbie here.  I've been running Ubuntu on 2 of my work machine for about a month so far, just love it.  This morning I turned on my main counter computer (I run a business) and had some updates.  One was a Flash Update that errored, but I didn't think anything about it, I'm not sure what the other update was.  I clicked on my VMWare Console (I run XP in VMWare due to my cash register program) and it doesn't do anything?  I get the 'hourglass' and then it just disappears and nothing happens?  What do I do?

chuck

---

### Post by Kilz on 2006-09-20
I just reinstall after a kernel upgrade. The virtual machines wont change.

---

### Post by andypaxo on 2006-09-20
Yep, I get this problem all the time. You could reinstall VMWare as Kilz suggests, or...

Download the new kernel-headers package through apt/synaptic (This problem always occurs after a kernel update)

Then run VMWare from the command line (vmplayer on my machine, probably vmserver on yours, and follow the instructions)

Hope this helps

---

### Post by indy107 on 2006-09-20
I did the Synaptic Kernel Header packages, (2 of them) and got the same error for installing the Flash Plugin (non-free) and ignored the error.  But when I type vmplayer or vmserver I get a command not found error?

thanks

chuck

---

### Post by indy107 on 2006-09-20
I see the vmware shell script in /usr/bin but if I try to run it in a terminal window the terminal window pops up for a second and then disappears
????

chuck

---

### Post by indy107 on 2006-09-20
ok if I run vmware from a terminal I get this error..

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

and if I paste that into a terminal windows I get no such file or directory

chuck

---

### Post by charles.g.moore on 2006-09-20
> **indy107 said:**
> Hi, newbie here.  I've been running Ubuntu on 2 of my work machine for about a month so far, just love it.  This morning I turned on my main counter computer (I run a business) and had some updates.  One was a Flash Update that errored, but I didn't think anything about it, I'm not sure what the other update was.  I clicked on my VMWare Console (I run XP in VMWare due to my cash register program) and it doesn't do anything?  I get the 'hourglass' and then it just disappears and nothing happens?  What do I do?

chuck
I dont know how to fix your vmware but it sounds as if your having the same problem I did, I was asked to update the flash player nonfree-plugins this morning and when I did I got an error during install see if this helps your plugin problem..

[http://www.ubuntuforums.org/showthread.php?t=261287](http://www.ubuntuforums.org/showthread.php?t=261287)

---

### Post by andypaxo on 2006-09-20
Not being able to find that config script sounds most unusual, here are a couple of things to try:

[LIST]
[*]Firstly, this is a perl script - so you will need perl installed, or it won't work
[*]Secondly, try this command to find out if the file exists at all:
```
locate vmware-config.pl
```
(On my system this shows /usr/bin/vmware-config.pl)
[/LIST]

I hesitate to suggest this - but if all else fails, reinstalling vmware from scratch should work.

---

### Post by indy107 on 2006-09-20
I found the file

/home/shuttle/.Trash/vmware-server-distrib/bin/vmware-config.pl
/usr/bin/vmware-config.pl


Why is it in the trash?  And can I just put it back?

chuck

---

### Post by indy107 on 2006-09-20
Oh, ok.. never mind, its also in usr/bin/  so it is there.

I guess I can reinstall....problem is I installed it a month or so ago....and I'm not really sure I remember how!  But I can look it up.  

Once I re-install it, will my exising virtual XP still be there?  My data files are stored on there and no...I don't have that recent of a backup.
Shame on me.

chuck

---

### Post by andypaxo on 2006-09-20
Okay, running /usr/bin/vmware-config.pl should let you reconfigure VMWare to make it run again.

If the configure program asks you where your kernel headers are installed, you can select the package into Synaptic and go to the 'Installed Files' tab to find out where it put them.

----

If you do decide to go down the extreme route - re-installing should not have any effect on your virtual machine - if you really want to be extra mega sure, just make a copy of your vmx, vmdk and vmss files.

You can either install VMWare Player from apt, or go onto vmware.com for other options (heheh, I sound like a VMWare salesman)

---

### Post by indy107 on 2006-09-20
Ok....all done.  It's working again halleluja!
Thanks you thank you thank you.....

I gotta admit, I love Ubuntu, but when I get these kernel problems (and I've had 2 now) they make a Windows guy like me want to scream....I simply didn't know what else to do except cry for help.  I appreciated the help, I'll be more careful which updates I do, and I think I'm gonna back up my database now before something else happens.

Ubuntu Community is awesome.

chuck

---

