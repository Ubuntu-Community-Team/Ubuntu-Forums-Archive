---
title: "Networking two Ubuntu machines.  Samba?"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by KillrBuckeye on 2006-05-12
Hi, I now have Ubuntu installed on two machines, one of which is a dual-boot with Windows.  For clarification, let's refer to Ubuntu on my dual-boot machine as Ubuntu2, and Ubuntu on the other machine as Ubuntu1.  I have successfully set up Samba on Ubuntu1 such that I can access its folders/files from either of my 2 machines running Windows.  However, when I set up Samba on Ubuntu2, I have two problems:

1)  I can't see Ubuntu2 from Ubuntu1.  Shouldn't Ubuntu2 appear as a "Network Server" in my Ubuntu1 places?

2) I can't see Ubuntu2 from another Windows machine.  This Windows machine recognizes Ubuntu1 and the the Windows installation on the Ubuntu2 machine, so I'm wondering what the problem is.

Could it possibly be related to the Samba network names of the Ubuntu machines?  I don't think I changed them, so they might both have default names of "Ubuntu".  If this is the problem, how do I change the Samba name?  Thanks.

---

### Post by ProjectGod on 2006-05-15
so. after initialising samba on ubu2 (machine that is dual booting with windows)... you no longer can access its resources from neither ubu1 or another windows machine?

hmm :-k 

were you able to access ubu2 from another windows / ubu1 prior to installing samba on it? 

if you can't remember or didnt try dont worry. just check to see if all OSes are part of the same workgroup/domain. and that the network interfaces on each OS are all configured similarly...e.g. ip address mask, gateway etc.

and check you've properly set up samba on ubu2. make sure you've created a "network user account" that has access permissions set up on it.

or if everything fails again... try removing samba on ubu2 and reinstalling it. 

"sudo atp-get remove samba"
"sudo apt-get remove smbfs"

go to /etc/samba/ and remove manually the configuration files. with "rm". 

restart and reinstall samba.

check [http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver) if you get stuck.

---

### Post by KillrBuckeye on 2006-05-15
Ooops, sorry I had forgotten about this thread.  For some reason everything began working after both machines were rebooted.  Thanks for your reply though.  :)

---

