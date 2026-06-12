---
title: "VMWARE config"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by neewby on 2006-08-04
Trying to use my internet

for vmware machine xp pro

how to detect proper connection for vmware machine xp pro???

---

### Post by djsroknrol on 2006-08-04
It would be easier to use your GUI connection in Ubuntu(security sake), but I'm sure you have your reason...check out this **[link]("http://ubuntuforums.org/showthread.php?t=183209")**...it should have set it all up for you upon install.

---

### Post by neewby on 2006-08-05
Yeh but how do I configure 

I get error message for trying vmserver connect internet for virtual machine XP :

Could not open /dev/vmnet8: No such file or directory
Failed to connect virtual device Ethernet0.





How can I change for right directory to connect eth0???

---

### Post by moma on 2006-08-05
Just an idea:
Can you change the virtual network interface to "nat" instead of "bridged" ?
Check the network settings in VMware.

---

### Post by neewby on 2006-08-05
Yes I can but I think problem is cannot find default Ubuntu default dev dsl etho

error:

"Could not open /dev/vmnet8: No such file or directory
Failed to connect virtual device Ethernet"

It says No such ......

---

### Post by moma on 2006-08-05
What about if you run the "vmware-config.pl" again?
$ sudo vmware-config.pl

---

### Post by neewby on 2006-08-05
What will this command issue

---

### Post by moma on 2006-08-05
Well, I had to reconfigure (re-install) vmware-player after installment of a new kernel.
vmware-config.pl did the trick.

---

### Post by neewby on 2006-08-05
Okay did terminal default select options success

now running up vmserver again 

3 warning
 while power on vmachine XP:

"Could not connect to floppy "/dev/fd0". Please correct your configuration and then re-attempt to connect the virtual floppy drive."

"Virtual device floppy0 will start disconnected."

"Could not open /dev/vmnet8: No such file or directory
Virtual device Ethernet0 will start disconnected."

????????????????????????????????????????????????????????????????????????

ok now what:idea:

---

### Post by Daremo on 2006-08-05
It sounds like you have your virtual machine set to use "host-only" network settings. Host-only only allows connectivity within the host computer VM's only.

Change this to "bridged". This lets the virtual machine have its own direct connection to the Internet. Use this setting if you have a router with DHCP capability. Otherwise you will need to use NAT to share your host computers IP address as bridged will alow the VM to aquire its own seperate IP address.

Also as moma reply stated, if you have upgraded the kernel you will need to re-install VMware. Hope this helps...

---

### Post by neewby on 2006-08-05
nah you just repeated what she said

---

### Post by neewby on 2006-08-05
Where is my default eth0 connect device located ?

---

