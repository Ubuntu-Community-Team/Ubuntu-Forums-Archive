---
title: "VMware Fusion 2.0: Getting Linux from another partition as a virtual machine"
date: 2009-06-18
forum: Apple Hardware Users
---

### Post by micbelue425 on 2009-06-18
Hi, I recently modified my Macbook 5.1 (unibody aluminum) so that it can triple boot Mac OSX, Windows XP, and Linux 9.04 Jaunty Jackalope.

  I have VMware Fusion 2.04 installed on my Mac and it loads XP from the Bootcamp partition just fine.


 I was wondering if it is possible to load my Linux partition into VMware Fusion similar to how it does it with XP so that I can run Linux side-by-side with XP and OSX. 



I have read both: 

[http://fearandloath.us/vmware-fusion-bootcamp-partition.html](http://fearandloath.us/vmware-fusion-bootcamp-partition.html)
and
[http://taylorbanks.com/blog/ubuntu-on-the-macbook-pro-physical-virtual-or-both/](http://taylorbanks.com/blog/ubuntu-on-the-macbook-pro-physical-virtual-or-both/)


but both tell me to go to a directory/file in the VMware Fusion application support folder that doesn't exist in my version (./vmware-rawdiskCreator print /dev/disk0).


I'm new to the commands in terminal, but I believe the ./ means to go to a specific file in the directory.


 
 
 Thank you, any help is appreciated. [IMG]http://communities.vmware.com/images/emoticons/grin.gif[/IMG]

---

### Post by Ocxic on 2009-06-19
you can, and the manual to vbox describes how to do this, however it warns that once you do, to NOT boot into the partition normally, as it will mess-up the "virtual" virtual disk that is created.

---

### Post by robertbub on 2010-04-20
> **Ocxic said:**
> you can, and the manual to vbox describes how to do this, however it warns that once you do, to NOT boot into the partition normally, as it will mess-up the "virtual" virtual disk that is created.I was considering doing this, but I would precisely like the ability to either run in a virtual machine from MacOSX or boot into the partition.  (HFS has messed up my files too many times and I do not trust it -- I only trust ext2/ext3/ext4 .)

Is there a virtualization option which would not get messed up if I boot into the partition alone or run it in a vm?

Thanks.

---

