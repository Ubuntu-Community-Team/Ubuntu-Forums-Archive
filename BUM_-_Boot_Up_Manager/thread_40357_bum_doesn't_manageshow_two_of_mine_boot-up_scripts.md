---
title: "bum doesn't manage/show two of mine boot-up scripts?"
date: 2005-06-08
forum: BUM - Boot Up Manager
---

### Post by spda on 2005-06-08
Hi,

I have installed bum 1.2.7 but I can't find (or manage) two of my boot-up scripts in bum, they just doesn't show. Their names are:

spda@miura:/etc/init.d $ ls -l
total 215
**** FILES DELETED HERE ****
-rwxr-xr-x  1 root root  3295 2005-05-28 17:03 Win4LinPro
-rwxr-xr-x  1 root root  2961 2005-06-09 00:28 vpnclient_init
**** FILES DELETED HERE ****

As far as I can see they have the same rights as other boot-up scripts. I have tried to "Add a new script at bootup" amd bum says that it has been added and that I should check the box to enable it, but it still doesn't show.

Hmm, i just figured out the problem :-), I renamed the the scripts to:

-rwxr-xr-x  1 root root  3295 2005-06-09 00:48 win4linpro
-rwxr-xr-x  1 root root  2961 2005-06-09 00:48 vpnclient-init

and voilá, no problem, I restarted bum and there they were!

I guess CAPITAL characters and underscore _ confuses bum, can  you please look in to that for an upcoming release? 

Best Regards
Patrik

---

### Post by saltydog on 2005-06-10
[QUOTE=spda]Hi,

I have installed bum 1.2.7 but I can't find (or manage) two of my boot-up scripts in bum, they just doesn't show. Their names are:

spda@miura:/etc/init.d $ ls -l
total 215
**** FILES DELETED HERE ****
-rwxr-xr-x  1 root root  3295 2005-05-28 17:03 Win4LinPro
-rwxr-xr-x  1 root root  2961 2005-06-09 00:28 vpnclient_init
**** FILES DELETED HERE ****

As far as I can see they have the same rights as other boot-up scripts. I have tried to "Add a new script at bootup" amd bum says that it has been added and that I should check the box to enable it, but it still doesn't show.

Hmm, i just figured out the problem :-), I renamed the the scripts to:

-rwxr-xr-x  1 root root  3295 2005-06-09 00:48 win4linpro
-rwxr-xr-x  1 root root  2961 2005-06-09 00:48 vpnclient-init

and voilá, no problem, I restarted bum and there they were!

I guess CAPITAL characters and underscore _ confuses bum, can  you please look in to that for an upcoming release? 

Best Regards
Patrik[/QUOTE]


No, it is not a matter of capital or underscore. Maybe those script has some missing synlinks in standard runlevels, so BUM has not considered them as valid. I mean, when parsing /etc/init.d/ directory BUM checks if the script has the same link in runlevel 2-3-4-5. In this case it is valid. It is also valid if the script has no symlinks in any rcX.d directory (that's the case when you have renamed them). So, check the links of Win4linpro in all the rcX.d directories, and you will find something strange...
Let me know.

---

### Post by spda on 2005-06-14
Hi,

I can find traces (broken links) of boot vpncliet_init and Win4LinPro in /etc/rc[2-6].d

ls /etc/init.d/rc?.d
S77Win4LinPro  (color is red indicating broken link)
S85vpnclient_init  (color is red indicating broken link)

And I know that Win4LinPro atleast started on boot, the vpnclient should have started but I always has been force to manually start it (again?) to make it work.

What I still think is fishy are that bum at first didn't correctly discover the scripts and that I couldn't add them (Add New Script at boot) either, and after a rename everything worked at instant??? 

Well, the problem is fixed maybe it was something local to my machine and thanx to bum I don't have to start the vpn client_init manually everytime :-) 

//PDa

---

### Post by mozkill on 2007-12-07
Im having the same problem.

I installed nxserver (from precompiled binaries at FreeNX site) service, which does start automatically on reboot of the system but it doesn't show up in the BUM init-level editor.  

Does anyone know why it wouldn't show up in BUM even though the S99nxserver script actually exists in the /etc/rc5.d directory.   Since its there, i dont see why BUM doesnt display it to me.   There are 6 scripts in that rc5.d  and rc3.d directories that start with S99 and the nxserver scripts are one of them.

There are no bad symbolic links anywhere.  The first script that starts with S99 does show up in the BUM editor.  Do you think that it is because there are more than one script starting at the same number?  Any other ideas?

---

### Post by saltydog on 2007-12-07
> **mozkill said:**
> Im having the same problem.

I installed nxserver (from precompiled binaries at FreeNX site) service, which does start automatically on reboot of the system but it doesn't show up in the BUM init-level editor.  

Does anyone know why it wouldn't show up in BUM even though the S99nxserver script actually exists in the /etc/rc5.d directory.   Since its there, i dont see why BUM doesnt display it to me.   There are 6 scripts in that rc5.d  and rc3.d directories that start with S99 and the nxserver scripts are one of them.

There are no bad symbolic links anywhere.  The first script that starts with S99 does show up in the BUM editor.  Do you think that it is because there are more than one script starting at the same number?  Any other ideas?

BUM lists only applications which install "valid" init scripts, and this is not the case for nxserver.
For valid I mean an application that strictly follows recommendations for sysv-init systems.
More on BUM docs here: [http://www.marzocca.net/linux/bumdocs.html#how](http://www.marzocca.net/linux/bumdocs.html#how)

---

