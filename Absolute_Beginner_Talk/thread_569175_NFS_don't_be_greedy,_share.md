---
title: "NFS don't be greedy, share"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by gimpguy2000 on 2007-10-06
While I want to accomplish one thing... share a drive...I can't get NFS , at all. 

I have 3 drives, 

80gig WD, widnows xp pro

80 gig max, nothing, only ext 3

120 gig wd with ubuntu


Now, I only want to share the ext 3 drive over my home network so my son and I can both access the drive. I tried putting a folder in it and sharing it but only get the option to use SMB not NFS.  

Any suggestions? 

Thanks,

Paul

---

### Post by talby on 2007-10-06
HOWTO: NFS Server/Client
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

On your system, follow "Install NFS Server Support" and your son's system "Install NFS client support" as well as "Mounting manually" to test the share and "Mounting at boot using /etc/fstab" to make it run automatically at boot time - unless it is not accessible 24x7 maybe skip that step and mount manually when needed :)

---

### Post by louieb on 2007-10-06
Haven't tried NFS yet though I probably should.  If both you and your son are running Ubuntu then the easy Linux to Linux  way is to install openssh-server on the machine w/ the hard drive. and give the PC a static IP.  Then set your son up as a user on that PC that has access to the drive. Then he can go to Places>Connect to server> Service type>  ssh. Enter the IP and your machine will appear as  just another Place in the Places menu.

---

### Post by gimpguy2000 on 2007-10-07
Thanks, will give suggestions a try and see what works :)

Cheers,

Paul

---

