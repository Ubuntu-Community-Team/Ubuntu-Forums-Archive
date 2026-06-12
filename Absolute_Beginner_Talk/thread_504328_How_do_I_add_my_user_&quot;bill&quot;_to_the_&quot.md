---
title: "How do I add my user &quot;bill&quot; to the &quot;vboxusers&quot; group?"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-07-19
How do I add my user "bill" to the "vboxusers" group?
I already tried 
System > Admin > Users and Groups
Then selecting Groups tab.

Then choosing the row with below properties and adding "bill" to the "Group members" column.
Group: vboxusers
GID: 1001

It didn't work how do I add "bill" to "vboxusers" group the right way?


> bill@Gates:~$ VirtualBox
WARNING: [B]You are not a member of the "vboxusers" group.  Please add yourself
         to this group before starting VirtualBox.[/B]

         You will not be able to start VMs until this problem is fixed.
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device


---

### Post by PaulFr on 2007-07-19
```
sudo adduser bill vboxusers
```

---

### Post by jingo811 on 2007-07-19
tnx,

---

### Post by sunilattri on 2007-09-09
Go to **System>Administration>User and Groups**

Window '**Users Setting**' will be displayed

Click on Button '**Manage Groups'**.

Window 'Group Setting' will be opened.

Select '**vboxusers**' and click on Button '**Properties**'

Window '**Group vboxusers Properties**' will be opened.

Select your **username**.

Click **OK** and now close **Group Settings** and **User Setting** Windows.

Restart your Ubuntu. 

I hope your problem will be solved now.

---

### Post by deserthowler on 2007-09-10
you can try:

sudo pico /etc/group

and edit the file adding your user to the vboxusers group

Earl

---

