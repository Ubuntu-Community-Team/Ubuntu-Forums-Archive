---
title: "SOLVED:  USB Drive Won't Connect Under OSX and Fusion"
date: 2012-02-16
forum: Apple Hardware Users
---

### Post by iInventStuff on 2012-02-16
I've had a situation where I installed Ubuntu 11 under OSX Lion running VMWare Fusion 3 and I could not get my USB drives to connect to Ubuntu.  There have been quite a few threads on this with people perplexed at why lsusb would show the drive as connected, but fdisk never showed the drive.

After a bunch of searching, I found the solution and I wanted to pass it along.  This time configuring and re-configuring Ubuntu won't help.  It's a VMWare / OSX issue.

Problem:  Installing OSX Lion causes the permissions of the root directory ( / ) to be set incorrectly.

Fix:  reset the permissions of ( / ) by running these commands:

chown root:wheel /
chmod 755/

Now restart your Mac.  With any luck, USB drives will now mount.

Here are the official details from VMWare ([http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&docTypeID=DT_KB_1_1&externalId=2004687](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&docTypeID=DT_KB_1_1&externalId=2004687)) 
or 
([http://tinyurl.com/77kfk2l](http://tinyurl.com/77kfk2l))

Good Luck!

Steve

---

