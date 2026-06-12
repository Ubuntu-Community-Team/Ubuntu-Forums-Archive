---
title: "Going down for the third time..."
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Mallette on 2007-06-16
I finally DID find a reference to the "mode" business that is preventing me from doing anything on this system:

These rules tell udev what device nodes to create for aoe support.
2	# They may be installed along the following lines (adjusted to what
3	# you see on your system).
4	# 
5	#   ecashin@makki ~$ su
6	#   Password:
7	#   bash# find /etc -type f -name udev.conf
8	#   /etc/udev/udev.conf
9	#   bash# grep udev_rules= /etc/udev/udev.conf
10	#   udev_rules="/etc/udev/rules.d/"
11	#   bash# ls /etc/udev/rules.d/
12	#   10-wacom.rules  50-udev.rules
13	#   bash# cp /path/to/linux-2.6.xx/Documentation/aoe/udev.txt \
14	#           /etc/udev/rules.d/60-aoe.rules
15	#  
16	
17	# aoe char devices
18	SUBSYSTEM="aoe", KERNEL="discover",	NAME="etherd/%k", GROUP="disk", MODE="0220"
19	SUBSYSTEM="aoe", KERNEL="err",		NAME="etherd/%k", GROUP="disk", MODE="0440"
20	SUBSYSTEM="aoe", KERNEL="interfaces",	NAME="etherd/%k", GROUP="disk", MODE="0220"
21	SUBSYSTEM="aoe", KERNEL="revalidate",	NAME="etherd/%k", GROUP="disk", MODE="0220"
22	
23	# aoe block devices     
24	KERNEL="etherd*",       NAME="%k", GROUP="disk"

I suspect this is somehow related to the "mode is 446, should be mode 0440" that is the only return I get from sudo or su.  

If ANYBODY can shed light here I'd appreciate it.  I really hate giving up on something, but when you cannot even issue a command you can't get very far.

Regards,
Dave

---

### Post by machoo02 on 2007-06-16
> **Mallette said:**
> I finally DID find a reference to the "mode" business that is preventing me from doing anything on this system:

These rules tell udev what device nodes to create for aoe support.
2	# They may be installed along the following lines (adjusted to what
3	# you see on your system).
4	# 
5	#   ecashin@makki ~$ su
6	#   Password:
7	#   bash# find /etc -type f -name udev.conf
8	#   /etc/udev/udev.conf
9	#   bash# grep udev_rules= /etc/udev/udev.conf
10	#   udev_rules="/etc/udev/rules.d/"
11	#   bash# ls /etc/udev/rules.d/
12	#   10-wacom.rules  50-udev.rules
13	#   bash# cp /path/to/linux-2.6.xx/Documentation/aoe/udev.txt \
14	#           /etc/udev/rules.d/60-aoe.rules
15	#  
16	
17	# aoe char devices
18	SUBSYSTEM="aoe", KERNEL="discover",	NAME="etherd/%k", GROUP="disk", MODE="0220"
19	SUBSYSTEM="aoe", KERNEL="err",		NAME="etherd/%k", GROUP="disk", MODE="0440"
20	SUBSYSTEM="aoe", KERNEL="interfaces",	NAME="etherd/%k", GROUP="disk", MODE="0220"
21	SUBSYSTEM="aoe", KERNEL="revalidate",	NAME="etherd/%k", GROUP="disk", MODE="0220"
22	
23	# aoe block devices     
24	KERNEL="etherd*",       NAME="%k", GROUP="disk"

I suspect this is somehow related to the "mode is 446, should be mode 0440" that is the only return I get from sudo or su.  

If ANYBODY can shed light here I'd appreciate it.  I really hate giving up on something, but when you cannot even issue a command you can't get very far.

Regards,
Dave

I think I know what is the problem.  something happened where the /etc/sudoers file where the permissions are set wrong.  To fix it, log into the root account (easiest way is to reboot, and at the GRUB selection screen select recovery mode).  At the command prompt, enter```
chmod 0440 /etc/sudoers
```
Hopefully that will set you straight.

---

### Post by Mallette on 2007-06-16
You sir, are an angel...

Now I can at least get back to my regularly scheduled problems!!!

Trust me to find myself somewhere nobodies ever been...

Kind regards,
Dave

---

### Post by Mallette on 2007-06-16
Thank you again, machoo2!

The fact I am responding on the computer in question means I've made it.

OTOH, I am connected via a neighbors unsecured net as it did not accept my password to get onto my own.  Not sure what the deal is there, but I'll figure that out.

Now, if I can just get sound going...

Dave

---

