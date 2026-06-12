---
title: "How to install update patch for Vmware"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by dcalvani on 2007-06-20
Hi, I'm following the directions given at
[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

and I have a couple of questions on the following part:

"As of right now VMware Server won't compile correctly on Feisty without patching the vmmon file http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz"

1) do I actually install this patch BEFORE or AFTER running the syntax to untar the Vmware-server pack?
2) in any case, how do I proceed after downloading + unpacking the patch? It's in a folder called "vmware-any-any-update109" that's sitting at /home/daniele

I read through the tutorial [http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0](http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0)
and my problem seems to be how to "enter that directory and run "./runme.pl" and "vmware-config.pl". 

Please help. Thank you.

---

### Post by Clay_Banger on 2007-06-20
with the anyany patch, you run through the normal setup until it fails, then you run the anyany setup and that will finish the entire setup for you.
however there is an easier way, vmware server is in the feisty repos, so a simple sudo aptitude install will install it without the hassles of patching it.

---

