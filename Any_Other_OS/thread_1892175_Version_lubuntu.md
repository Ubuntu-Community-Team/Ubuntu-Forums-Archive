---
title: "Version lubuntu"
date: 2011-12-07
forum: Any Other OS
---

### Post by ridero63 on 2011-12-07
Dear users,

What is the command in the terminal to see what version of lubuntu  i use ?

Thank you

r

---

### Post by 2F4U on 2011-12-07
I would suggest 

cat /etc/lsb-release

---

### Post by boydrice on 2011-12-07
uname -a

---

### Post by ridero63 on 2011-12-10
Gives differents results

Thank you


~$ uname -a 

Linux rinke-Lubuntu 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 i686 i386 GNU/Linux

$ cat /etc/lsb-release 

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

---

### Post by wolfen69 on 2011-12-10
You are using the 32bit version.

---

### Post by screaminj3sus on 2011-12-10
You are running the latest version of lubuntu (11.10) and the 32-bit (i686) version.

---

### Post by Kevin McCready on 2012-02-23
uname -a
gives me

3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i686 i386 GNU/Linux

but I have no idea what these numbers and date mean. And why it doesn't tell me Ubuntu 11.10 or Lubuntu or LXDE.

Is there a way to get it all with one command?

---

### Post by Theredbaron1834 on 2012-02-23
Lubuntu is just Ubuntu core, with different DE. Thus, it says "DISTRIB_DESCRIPTION="Ubuntu 11.10"" So, it would be Lubuntu 11.10.

cat /etc/lsb-release  is your general distro info

"DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10" 	"

DISTRIB_ID is the name of your distro, so Ubuntu. Release is the version of your distor. Codename is, well, the codename. And the description is just a description of it.


Uname -a gives you all kindsa kernel info. 
so 
"Linux rinke-Lubuntu 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 i686 i386 GNU/Linux"

Translates to you using Linux kernel version 3.0.0-13, the date is when it was made, and the i*** are the cpu's it can work on.


Hope that is informative at least.

---

### Post by Kevin McCready on 2012-02-23
ta
don't know how to mark this thread to get further updates of the thread. The email giving me your response said I had to visit the page to get further updates.

---

