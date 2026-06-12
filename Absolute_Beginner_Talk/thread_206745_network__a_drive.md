---
title: "network  a drive"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by seanm on 2006-06-30
hi all - a complete beginner to Ubuntu - fed up with Windows so thought i would try something new. Any way can anyone tell me how to find a drive that is a networked backup drive that i could see before i changed to Ubuntu. I tried to "disk manager" but it hangs there for ever. What am i doing wrong? or is there something i should do before using disk manager. 

thanks

seanm:confused:

---

### Post by joshrobinson on 2006-06-30
[QUOTE=seanm]hi all - a complete beginner to Ubuntu - fed up with Windows so thought i would try something new. Any way can anyone tell me how to find a drive that is a networked backup drive that i could see before i changed to Ubuntu. I tried to "disk manager" but it hangs there for ever. What am i doing wrong? or is there something i should do before using disk manager. 

thanks

seanm:confused:[/QUOTE]

hmm ive never used a networked hard-drive before.. how exactally does it work? does it use samba/smb to share files? im guessing it should have its own ip also?
you could try installing all the files needed for samba, and clicking places > network servers to see if it pops up in there

---

### Post by fjm03 on 2006-06-30
Most, stand alone, inexpensive, networked, file servers are, in fact, Linux driven, using Samba to interpret inquiries from Windows operating systems.

If your network attached storage device is a linux box, Unbuntu, in it's standard configuration, should be able to see the server if your NAS was orginally provisioned as part of a work group rather than a domain.

As has been already mentioned, turn on the NAS and give it a moment to receive an assigned IP from your LAN router. Then, using the following Ubuntu menu path (Places  >> Network Servers ), if all is well, the NAS will be located. Enter the UserID and Pass for the NAS and you should be able to access and manipulate the shared folder.

Good luck.

---

### Post by seanm on 2006-07-03
hi fjm03,

thanks for the response - dumb question but how do you trun on NAS - the network hard drive is a netgear storage device - it has all my backup files from when i was running windows - will it still be able to "see the drive" even if i turn on the NAS?

many thanks

Seanm

---

### Post by grantquinn on 2006-07-06
netgear don't plan to provide a linux  driver for the SC101

---

### Post by magicfab on 2008-06-13
I know this thread is really old, but I now own one of these and it works fine in Hardy for me with the nbd module. That software is around since late 2007. See:
[http://ubuntuforums.org/showpost.php?p=4151832&postcount=15](http://ubuntuforums.org/showpost.php?p=4151832&postcount=15)

If you'd like to know if/when this makes it into Ubuntu, please subscribe to this bug:
[https://bugs.edge.launchpad.net/ubuntu/+bug/213744](https://bugs.edge.launchpad.net/ubuntu/+bug/213744)

Cheers,

---

