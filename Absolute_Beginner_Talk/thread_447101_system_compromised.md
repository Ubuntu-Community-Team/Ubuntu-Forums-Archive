---
title: "system compromised?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-05-17
After startup of 6.10 and before I began using any applications, I saw quite a load of sent traffic on System Monitor. I opened that and checked the Processes panel and found nothing unusual, then realized too late that default shows only 'my processes'. Have changed that to 'active processes' for next time.

Installed and ran rkhunter. Got this, which elsewhere is said to be a normal false positive for Ubuntu:

++++
* Filesystem checks
   Checking /dev for suspicious files... -e                      [ OK ]
   Scanning for hidden files...-e                                [ Warning! ]
---------------
 /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools /etc/.pwd.lock
/etc/.java
---------------
Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory)  /etc/.java (directory) 
++++

Firewall interface in Guarddog, email is Claws, main browser is Opera, & occassional browser is Firefox. System is kept updated, and I believe configured correctly & in a fairly paranoid manner.

SSH is occasionally opened to one other system, which has few permissions restricted to its own home dir. SSH is blocked in Guarddog when not actually in use, and was blocked this morning.

For a few weeks, Gmail has been rejecting mail from my system as "Our system has detected an unusual amount of unsolicited mail originating from your IP address." Until now, I've been figuring that's a screwup on their end.

That's all I can think of. Question is what's up, and what to do about it?

---

### Post by userundefine on 2007-05-17
Start by checking out /var/log/auth.log to see if there has been any logins that aren't you.

---

### Post by ofb on 2007-05-17
Log starts 11 May and shows only myself logging in.

---

### Post by ofb on 2007-05-19
Is there a log I can check to see what application was accessing the network at that time? Or see where network traffic was going?

---

### Post by colinleroy on 2007-05-24
> **ofb said:**
> Is there a log I can check to see what application was accessing the network at that time? Or see where network traffic was going?

Not after the fact. But next time you see suspicious activity, try

$ sudo netstat -nap --inet

You'll see listening services and established connections.

---

