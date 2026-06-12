---
title: "hfsplus can no longer execute binaries"
date: 2011-10-28
forum: Apple Hardware Users
---

### Post by mac_mcmacmac on 2011-10-28
Hey guys, having some problems with my macbook 6,1 (mactel)
I'm dual booting Snow Leopard and Lucid Lynx and have been frustrated that I have had to change permissions on my media-storing partition accessible to both every time I want to switch between the OSs. They don't seem happy to share.

That isn't the problem though.

Since about the time I installed wine and other things to get Deus Ex working in Ubuntu, I've no longer been able to execute on this partition (read/write fine, though).  This is a big problem since I have all my research code on there too, and have to copy to the home folder on the root partition in order to execute binaries.

It comes up with the error:
bash: <executable>: Permission denied
or, with root permissions:
sudo: unable to execute <executable>: Permission denied

I've done obvious things, like:
$sudo chown -R <username> <partition>
or
$sudo chmod -R 775 <partition>

It's hfs+ formatted, but has journalling disabled.  I was able to execute these files on this partition before just a couple of days ago.


I've even tried adding a line into /etc/fstab:

/dev/sda4 /media/data_bank hfsplus exec,rw,user,auto 0 2

to have the partition automounting with read/write and executable permission, but this hasn't changed anything.


Saying it was around the time of installing wine may be a red herring, but I can't think of any other causal link.
Please help me, thanks!

---

### Post by mac_mcmacmac on 2011-10-30
new info:

disk utility in Snow Leopard shows that the partition has ownership disabled, and using the command (whilst in a terminal in mac):
vsdbutil -a <partition>
did not change it.

I would have thought that no ownership would have meant that there would be no permission restrictions, such as for executing binaries... but I don't know

---

