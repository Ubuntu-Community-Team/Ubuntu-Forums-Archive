---
title: "Linux Kernel change 2.6.33  / 2.6.32  NFS mount"
date: 2012-06-14
forum: Any Other OS
---

### Post by jeduffey on 2012-06-14
I have determined that some part of the changes between Linux kernel 2.6.32 and 2.6.33 effected mounting NFS shares. It is definitely a kernel issue as my testing has been included a dozen different distributions.

With any disto using a .32 kernel the command
  "mount ip:/NFS/server/share /mnt/localdir"
works automatically, without fuss. The same command used in a distro with   any kernel from .33 afterward returns the error
  "mount:nfs timed out, giving up"

When you modify the command, like this
  "mount -o proto=tcp ip:/NFS/server/share /mnt/localdir"
then the command works correctly.

I would like to know:
*What is the specific change between .32 and .33 that causes this change in the behavior of the mount command, so that UDP is now the automatic protocol instead of TCP?
*Why was it changed?
*Where/How do I make a change in the settings of Ubuntu or other systems so that they permanently revert back to a default of TCP?
*Where/How do I make a change in the settings of an NFS server, I am using NAS4Free/FreeNAS/BSD, to make the shares either UDP or TCP?

I have been working on this for quite awhile and your help is greatly appreciated.

---

### Post by jeduffey on 2012-06-19
Can anyone even point me in the right direction of a web site or forum that would have some answers about the Linux kernel? I have looked at kernel.org and I do not see any contact information or a forum to get such answers.

---

### Post by jeduffey on 2012-08-05
Anyone at all?

---

### Post by jeduffey on 2012-08-05
[http://kernelnewbies.org/Linux_2_6_32](http://kernelnewbies.org/Linux_2_6_32)

[http://kernelnewbies.org/Linux_2_6_33](http://kernelnewbies.org/Linux_2_6_33)

---

