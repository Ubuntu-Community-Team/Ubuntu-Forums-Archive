---
title: "vmware - how to increase allocated disk space ..."
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-06-22
I really like vmware and the virtual Windows XP I am running.  When I installed XP, I took the default disk size and went with 8GB.  Now I would like to increase it to 16GB -- how can I increase the disk space for a virtual machine without destroying what I already have configured?

Thanks

Carl

---

### Post by Bachstelze on 2007-06-22
Did you pre-allocate the disk space ? If you did, you can't resize it.

EDIT : But you could crearte a second virtual disk and add it to your VM, virtually achieving the same thing.

---

### Post by RedRover1 on 2007-06-22
Take a look at this thread if you running Vmware server

[http://www.vmware.com/community/thread.jspa?messageID=659054&#659054](http://www.vmware.com/community/thread.jspa?messageID=659054&#659054)

---

### Post by Jupp on 2007-06-26
Hi, 
I had the same problem some days ago. What I found was, that vmmanager (Sourceforge) is working quite well, but only under windows. So I opened a Samba shared folder, copied the image and the vmx file into the virtual machine with installed windows 2000, installed the vmmanager, resized the image and made some corrections with this tool. Then I copied it back  to my kubuntu host, renamed it and restarted my virtual machine with the vmplayer again. After that, I had to install a partion manager (paragon) into the image and resized the virtual machine. Half an hour later, my usable size had increased from 4GB to 20GB. Could be one solution to increase vmplayer images.

bye

---

### Post by sefs on 2008-03-10
How to increase disk size of a vmware image with a norton ghost bootdisk

[http://www.vmware.com/support/reference/common/virtual_disks.html](http://www.vmware.com/support/reference/common/virtual_disks.html)

---

