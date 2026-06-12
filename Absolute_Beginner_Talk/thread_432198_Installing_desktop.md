---
title: "Installing desktop"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by BobLand on 2007-05-03
I have fiesty beta installed in about 46 gb,  Windows takes about 75 gb,  and I have 67 gb unallocated.  

1. Does the install overwrite any part of Windows?
2. Does the install partitioning software overwrite the beta?
3. I have Partition Magic.  Should I delete the Linux partitions?

I want to ensure that Windows is not overwritten in any way and I'd prefer that the beta is overwritten or upgraded.  Will all of this happen automagically?

Thanks,
bobland

---

### Post by aktiwers on 2007-05-03
1)Arent they on 2 different partitions? 
No they will not overwrite eachothers.
2) Are you talking about gparted? What are you trying to do?
Do you have beta, and now want to install the full from a CD, whipping your current install?
3) Again, why whould you want to do that? Do you want to get rid of Linux or upgrade til Feisty that is not in beta?

You must likely already have the full version, as the beta got upgraded from the updates when the final version got out.

I too had the beta, but the updates keep it up too date. So you should no longer be in beta. Sorry if I misunderstand your question.. please explain what you want to do :)

---

### Post by BobLand on 2007-05-03
Are you saying that there is no need to install from the "official release" CD, that the original beta installed on my hard disk is, in fact, the same as the new release?

I was hoping that there would be the correct drivers on the disk for my nVidia GeForce4 card.  I wrestled with the drivers for weeks and could not get them to work.

I'm not looking forward to going thru that procedure again.

Thanks,
bobland

---

### Post by aktiwers on 2007-05-03
Hmm I have a nVidia card too, and it works fine.

Try do a 
```
sudo apt-get  dist-upgrade
```Then..

EDIT:
That should give you the latest feisty.

---

### Post by BobLand on 2007-05-03
Just curious, when I run "sudo apt-get  dist-upgrade" does ubuntu get this driver from the internet or somewhere buried in the OS?

---

### Post by aktiwers on 2007-05-03
In System => Administration => Restricted Driver Manager
It finds it Automatically on my PC.

But the command should make your Ubuntu to the Latest. Maybe you need to reboot when it is done. Else if it doesnt work, I can maybe help you install those drivers.

---

### Post by Sef on 2007-05-03
> 3. I have Partition Magic.

Partition Magic is not recommended because it and GNU/Linux do not always get along.  If you do need a partioner get [GParted]("http://gparted.sourceforge.net").

---

### Post by BobLand on 2007-05-03
Sef, this is no longer an issue as aktiwers pointed out.  

However, I would most certainly appreciate any help with  installing the drivers.  My card is a GeForce4.  My last attempt may have screwed my system up because of the various drivers and commands I ran.  And got nowhere.

I'm trying to get a screen resolution of 1600x1200.  The screen defaults to 1024 regardless of what the resolution selector says.

---

### Post by BobLand on 2007-05-03
Just for the record, I ran 
sudo aptitude remove envy linux-restricted-modules
sudo apt-get install nvidia-glx-legacy
changed the device name from vesa to nvidia and restarted x
resolution displayed everything.  Selected 1600x1200 and boom!  There is was.  Finally.

Thanks for all the responses on this thread and thanks for all the responses on the nvidia threads.

bobland

---

