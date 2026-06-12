---
title: "Driver help"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Bofur on 2007-06-13
I was wondering if anyone could tell me where to get the right drivers for my card, a Intel Wireless WiFi Link 4965AGN and how to install them. Thanks!

---

### Post by skymera on 2007-06-13
you can get NDISwrapper.
its windows wirelless driver installer

and your card... shouldnt it have a disc?
is fo, you need the .INF, and  .SYS
not sure bout the .CAT

---

### Post by Bofur on 2007-06-13
I tried that before, and used the dell driver from their website and I still didn't have any luck. Is there another way?

---

### Post by Bofur on 2007-06-13
Bump for help!

---

### Post by Bofur on 2007-06-13
Anyone, please?

---

### Post by w4ett on 2007-06-13
I found this link: [http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi) For and open source  driver solution

and this:  [http://support.intel.com/support/notebook/sb/CS-006408.htm](http://support.intel.com/support/notebook/sb/CS-006408.htm)  for the Intel drivers.

---

### Post by Bofur on 2007-06-13
I'm on this part:
Download, build, and install from snapshots [Recommended]
From this site: [http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi) which is the installation process.

Anyways, heres the output when I try to use the 'make' command in terminal:
```
justin@ubuntu:~/.drivers/iwlwifi-0.0.25$ make
Makefile:19: 
Makefile:20: WARNING: $SHELL not set to bash.
Makefile:21: If you experience build errors, try
Makefile:22: 'make SHELL=/bin/bash'.
Makefile:23: 
Kernel Makefile not found at '/lib/modules/2.6.17-10-generic/source'
make: *** [compatible/kversion] Error 1

```

Any ideas on what the problem is? I cded to the correct location..

---

### Post by w4ett on 2007-06-13
> **Bofur said:**
> I'm on this part:
Download, build, and install from snapshots [Recommended]
From this site: [http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi) which is the installation process.

Anyways, heres the output when I try to use the 'make' command in terminal:
```
justin@ubuntu:~/.drivers/iwlwifi-0.0.25$ make
Makefile:19: 
Makefile:20: WARNING: $SHELL not set to bash.
Makefile:21: If you experience build errors, try
Makefile:22: 'make SHELL=/bin/bash'.
Makefile:23: 
Kernel Makefile not found at '/lib/modules/2.6.17-10-generic/source'
make: *** [compatible/kversion] Error 1

```

Any ideas on what the problem is? I cded to the correct location..
 Did you "sudo make shell"? You need root permission for this I believe.

---

### Post by Bofur on 2007-06-13
```
root@ubuntu:/home/justin# cd /home/justin/.drivers/iwlwifi-0.0.25
root@ubuntu:/home/justin/.drivers/iwlwifi-0.0.25# sudo make shell
Makefile:19: 
Makefile:20: WARNING: $SHELL not set to bash.
Makefile:21: If you experience build errors, try
Makefile:22: 'make SHELL=/bin/bash'.
Makefile:23: 
make: *** No rule to make target `shell'.  Stop.
root@ubuntu:/home/justin/.drivers/iwlwifi-0.0.25# 


```

---

### Post by skymera on 2007-06-13
and make sure its turned on ;)
i thought i had problems, but my card wasnt activated oops.

good luck

---

### Post by wreti on 2007-06-13
> **Bofur said:**
> ```

Makefile:20: WARNING: $SHELL not set to bash.
Makefile:21: If you experience build errors, try
Makefile:22: 'make SHELL=/bin/bash'.



```
I know I wasn't much help earlier, but did you try following the advice of the above lines? Just a shot in the dark. I know how frustrating this can be!

---

### Post by Bofur on 2007-06-13
Yeah, I tried it before: 
```
root@ubuntu:/home/justin# cd /home/justin/.drivers/iwlwifi-0.0.25
root@ubuntu:/home/justin/.drivers/iwlwifi-0.0.25# make SHELL=/bin/bash
Kernel Makefile not found at '/lib/modules/2.6.17-10-generic/source'
make: *** [compatible/kversion] Error 1
root@ubuntu:/home/justin/.drivers/iwlwifi-0.0.25# 

```

---

### Post by wreti on 2007-06-13
Maybe try *sudo make SHELL=/bin/bash*?

---

### Post by Bofur on 2007-06-13
Same error :(

---

### Post by Bofur on 2007-06-13
Anyone else have any ideas on how to get the shell thing working?

---

### Post by Bofur on 2007-06-13
Bump.

---

### Post by renerey on 2007-06-13
Kernel Makefile not found at '/lib/modules/2.6.17-10-generic/source

just a thought, the Makefile isn't located in that folder. i believe it is in /lib/modules/2.6.17-10-generic/build. 

here's a link for an explanation and credit for the poster...
[http://ubuntuforums.org/showthread.php?t=360514&highlight=iwlwifi](http://ubuntuforums.org/showthread.php?t=360514&highlight=iwlwifi)

hope it helps,

---

### Post by JoePits on 2007-06-14
> **Bofur said:**
> I'm on this part:
Download, build, and install from snapshots [Recommended]
From this site: [http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi) which is the installation process.

Anyways, heres the output when I try to use the 'make' command in terminal:
```
justin@ubuntu:~/.drivers/iwlwifi-0.0.25$ make
Makefile:19: 
Makefile:20: WARNING: $SHELL not set to bash.
Makefile:21: If you experience build errors, try
Makefile:22: 'make SHELL=/bin/bash'.
Makefile:23: 
Kernel Makefile not found at '/lib/modules/2.6.17-10-generic/source'
make: *** [compatible/kversion] Error 1

```

Any ideas on what the problem is? I cded to the correct location..

bump because i have the same problem and i really want this driver!!!

---

