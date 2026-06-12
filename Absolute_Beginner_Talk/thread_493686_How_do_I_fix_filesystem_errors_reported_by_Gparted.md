---
title: "How do I fix filesystem errors reported by Gparted?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by timzak on 2007-07-06
I'm using Psychcats tutorial to create a /home partition (it's currently in my /root).  When I get to the point of resizing my partition and creating a new one, Gparted errors out with the following:

check filesystem on /dev/sda2 for errors and (if possible) fix them.

How do I check for errors and how do I fix them?

FYI, these errors don't seem to be affecting my system in any way.  I can exit out of Gparted and the LIveCD, and reboot back into my Ubuntu install and everything works fine.

I'm using Feisty on a 74GB Raptor (68.77GB reported size in Gparted) with about 7GB total used and 61GB free.

Thanks.

---

### Post by logos34 on 2007-07-06
schedule a filesystem check for next boot


**sudo touch /forcefsck**

reboot

see if that turns up anyhting

---

### Post by timzak on 2007-07-06
Thanks.  I watched the filesystem check run all the way through, briefly saw something about 2% non-contiguous, then it booted to the login screen.  How do I check the results of the scan?  Is there a log somewhere?

Thanks again for your help.

---

### Post by timzak on 2007-07-06
bump...can anyone help?

Thanks.

---

### Post by timzak on 2007-07-06
Please help...I'm trying to create a separate /home directory, which I should've done in the first place but it's my first time using any Linux OS and I didn't know better.

I'm not sure where to check for fsck logs.  There was nothing obvious when the fsck check was done at bootup...no error messages popped up or anything.  Does that mean fsck didn't find any problems?

Thanks.

---

### Post by logos34 on 2007-07-06
/var/log/fsck/checkfs

it's probably ok

Try using the [Gparted Live Cd]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828&release_id=519163") instead of the version on the ubuntu install live cd...it's stronger.  Not sure why it won't resize that partition.  It's got plenty of room.

---

### Post by timzak on 2007-07-06
Hi, 

Here's the contents of checkfs:

> Log of fsck -C -R -A -a 
Fri Jul  6 19:27:31 2007

fsck 1.40-WIP (14-Nov-2006)

Fri Jul  6 19:27:31 2007
----------------

I downloaded the Gparted live cd and will try it out when I get a chance.  The log looks fine, no?

Thanks for your help.

---

