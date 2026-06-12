---
title: "samba workgroup?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by ceeg on 2007-06-13
Okay I just finished setting up samba on my ubuntu server. From my windows XP box, I can only access the samba share if I access it directly.

Example:
\\ubuntuserver\myshare

I want to be able to access the samba share by clicking on "Workgroup Computers".
In smb.conf I have
workgroup = WORKGROUP

and the workgroup my XP machine is placed on is WORKGROUP.

After reloading the samba daemon I still can only access the share DIRECTLY. How can I fix this?

Thanks

---

### Post by captlogic on 2007-06-13
I'm not really sure if this is the problem, but I had all kinds of problems networking linux to xp via samba until I REMOVED zone alarm from the XP machine.  (I even tried to configure it to allow the network traffic through, but it just would'nt work till I removed it.)

Good Luck

---

### Post by ceeg on 2007-06-13
My XP machine isn't running Zone Alarm or any firewall software at the moment.

I can access my samba share by typing \\sambaserver\myshare in an address bar, but I can't access it through Workgroups.

Again, in smb.conf I have
workgroup=WORKGROUP

and my XP machine is assigned to WORKGROUP

---

### Post by tagra123 on 2007-06-13
What is your workgroup name on the XP Machine  -- Is it WORKGROUP or MSHOME ?

In your System-Administration-Networking try setting the domain as MSHOME or WORKGROUP.

POST your /etc/samba/smb.conf 

Someone will be able to help with this.

---

