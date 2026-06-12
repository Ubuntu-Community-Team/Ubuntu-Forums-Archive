---
title: "Guest Additions Won't Install in Virtualbox"
date: 2012-02-09
forum: Any Other OS
---

### Post by afz12 on 2012-02-09
I thought I'd take a peek at Fedora using Virtualbox on a Windows 7 machine. The main OS installed OK but the guest additions will not install. Is there a "fix" for this?

---

### Post by CharlesA on 2012-02-09
You need to install some other packages before you can compile the guest addition modules.

[http://fedoraunity.org/Members/realz/VB_Guest_Addition](http://fedoraunity.org/Members/realz/VB_Guest_Addition)

Same thing happens on CentOS.

---

### Post by afz12 on 2012-02-09
Thanks CharlesA - I'll give it a try :)

---

### Post by afz12 on 2012-02-10
I tried the reccomendations, first I logged in as a superuser 

su --login

this worked OK

then I typed in the terminal

yum install kernel-headers kernel-devel gcc

as suggested from the fedora site, this worked

I then tried to install guest additions from 'devices' but the s/w complained that I needed to unmount the disk!. I did this but the s/w then complained that the file /VB could not be found. Therefore still no guest additions!

I removed the virtual machine and started a new one. The same behavior occured expect now the VM wont start!

I think I'll give Fedora one last chance. This time I'll download a new Fedora version (16) and try the same, unless anyone has a better solution. If it works I might migrate an older notebook to Fedora, otherwise I'll give up on it as being a dud OS :)

---

### Post by CharlesA on 2012-02-10
Hrm. I always just mount the ISO manually and then run the guest additions manually.

Hope Fedora 16 is more cooperative. :)

---

### Post by leclerc65 on 2012-02-11
It looks like the instruction given in the links is not for Windows host.

---

### Post by afz12 on 2012-02-11
Hi CharlesA

Well I perservered and finally, guest additions installed in Fedora 16. It was a mission and I'm not exactly sure now which combinations did the trick! Certainly, the inbuilt commands in Virtualbox failed consistently. However the terminal finally worked with 

su --login (then password)
yum install kernel-headers kernel-devel gcc (this finally completed)

I then installed all available updates and rebooted, then in a terminal

su --login (then password)
cd /media/VBOXADDITIONS_4.1.8_75467
./VBoxLinuxAdditions.run

I'm not flaming Fedora but equally I'm not impressed! Ubuntu is far more user friendly in comparison. Still, I am curious to see what Fedora has to offer. Given such a shaky start, I am maintaining lowish expectations :) - perhaps others can present some comparitive analysis and suggest advantages offered by Fedora ?

---

### Post by CharlesA on 2012-02-13
Glad you were able to get them installed.

Fedora vs Ubuntu - they are just different distros with a different package management system. The base is pretty much the same but there are some differences between the two.

---

