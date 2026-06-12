---
title: "lost administrator access"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by celticbhoy on 2007-11-01
While following a how-to in a Linux magazine I have somehow lost my adminstrator access. Mine is the only account on the PC and was set-up as an administrator, but that has somehow gone. When I go into System-->Administration, I no longer have Synaptic, or ability to enter users & groups.

Can anyone Please help.

Using Gutsy.

Oh suppose I should say that the how to was to install VirtualBox, and I had just entered a command to add my account to the vboxusers group.

---

### Post by Bliepo32 on 2007-11-01
You could enter recovery mode, and from there, make your account an administrator again.

---

### Post by zvacet on 2007-11-01
Boot in recovery mode and type 

```
adduser your_username admin
```

---

### Post by aysiu on 2007-11-01
This will help you:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by celticbhoy on 2007-11-01
Cheers folks give it a go in the morning on mobile just now

---

### Post by celticbhoy on 2007-11-02
For some reason Recovery mode wont boot - just got a blank screen.
Could this be connected, and can I fix privelidges from live disk.

---

### Post by ev5unleash1 on 2007-11-02
This may be a problem is Gutsy. You should report this to a thread, or you could have installed some 3rd party software.

---

### Post by celticbhoy on 2007-11-02
As I say was following a magazine how-to for VirtualBox.

The command I used before loosing admin rights was :-

'usermod -G vboxusers gary' - (my username) as root followed by :-

'/opt/VirtualBox-1.3.6/VBox.sh'

at that point it said I was not in user group so I ran first instruction again, and it all went wrong.

---

### Post by celticbhoy on 2007-11-02
Is there any way to update my sudoers list using a live CD, and also check what is wrong with my recovery boot ?????????

---

### Post by celticbhoy on 2007-11-04
bmp

---

### Post by celticbhoy on 2007-11-04
Is it possible that the root account has been deleted or corupted? 

If so how can I repair from a live CD

---

### Post by celticbhoy on 2007-11-07
Really need some help on this - cant install, un-install or update !!!

---

### Post by celticbhoy on 2007-11-07
Just had a thought, my system is set with a seperate home partition. If I re-install, will it fix the problem? or as I have the home partition will it remain ???

---

### Post by TeaSwigger on 2007-11-07
> **celticbhoy said:**
> Just had a thought, my system is set with a seperate home partition. If I re-install, will it fix the problem? or as I have the home partition will it remain ???

Hello,

Wow sounds like that really messed things up. I've no idea why recovery mode wouldn't boot.

If you have a separate home partition, yes you may reinstall retaining the home partition; specify the mount point of that partition as home and take care not to reformat that home partition of course.

---

### Post by celticbhoy on 2007-11-07
Just tried entering 'groups' from terminal and got this :-

gary@Ubuntu:~$ groups
gary vboxusers
gary@Ubuntu:~$ 

As there is no admin, does this mean that the root user has been deleted somehow ????

---

