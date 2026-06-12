---
title: "Ipconfig /release /renew equiv and mapping drive"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by marco916 on 2007-01-18
Hi All, what’s the equivalent in Ubuntu or should I say Linux of the ipconfig /release and the /renew commands in Windows OS. And also how do you map a drive in Ubuntu with SMB services turned on in Ubuntu. I want to map a Windows drive in my shared network.
:-k

---

### Post by john_spiral on 2007-01-18
I know ipconfig is ifconfig in linux,

would love to know what the others are?

---

### Post by spockrock on 2007-01-18
I believe its

ifconfig /down
and 
ifconfig /up


as per mapping a drive it does not quite work that way, but you can mount a network share to a folder.  Try mapping a network share to /media/<name_of_the_map>.....if you want...try that....if thats the desired affect.

---

### Post by JamieC on 2007-01-18
To renew your IP address (or rather to send a DHCP request) you can use the following (where <device> is the name of your network interface):
```

sudo dhclient <device>

```

---

### Post by marco916 on 2007-01-18
Thanks all, will try these commands tonight  :)

---

### Post by drlarsen on 2008-02-13
> **JamieC said:**
> To renew your IP address (or rather to send a DHCP request) you can use the following (where <device> is the name of your network interface):
```

sudo dhclient <device>

```

Thanks, this worked for me!

---

### Post by oedha on 2008-02-13
mapping windows drive :=> go to places - network - set to smb - fill the servername and folder
or
you can use smbfs to mount the shared folder

---

