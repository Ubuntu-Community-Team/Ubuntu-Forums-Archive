---
title: "[SOLVED] Using the GUI to mount a hardrive"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Droidling on 2007-12-31
I installed Ubuntu 6.10 from a CD I got in the back of the book The Ubuntu Bible. I've been messing around with it over the last couple of weeks. I upgraded it to 7.04, and finally got the courage to try to install my Rocketraid 2220 controller. It made the system so unstable that I can't get my files off it. 

I rebooted to the CD (6.10) in the hope of copying files to another network computer or USB Drive. Unfortunately the C: drive on my computer dose not seem to have mounted. The instructions I have for mounting it say to open System>Administration>Disks, which does not exist on my system. What has replaced this feature?

Terry

---

### Post by spiderbatdad on 2007-12-31
you are probably not going to be able to do this graphically, if the partition isn't mounting. Do you see the partiotion if you run:```
sudo fdisk -l
```

---

### Post by spiderbatdad on 2007-12-31
also...if you get you're hands on a fiesty or gutsy cd then the partition should mount for you ...

---

### Post by spiderbatdad on 2007-12-31
here are a couple of links providing clear simple instructions for mounting the partition. The second one includes a program that will mount the partition at boot, and enable read write features...

[http://www.ubuntux.org/edit-fstab-to-mount-partition-at-startup](http://www.ubuntux.org/edit-fstab-to-mount-partition-at-startup)

[http://www.arsgeek.com/?p=585](http://www.arsgeek.com/?p=585)

---

### Post by Paqman on 2007-12-31
You can add a GUI "disk mounter" to any panel. It's only a right-click away! :)

---

### Post by spiderbatdad on 2007-12-31
He's using Dapper Drake.

---

### Post by dcstar on 2007-12-31
> **Droidling said:**
> 
..........
I rebooted to the CD (6.10) in the hope of copying files to another network computer or USB Drive. Unfortunately the C: drive on my computer dose not seem to have mounted. The instructions I have for mounting it say to open System>Administration>Disks, which does not exist on my system. What has replaced this feature?

Terry

Install the** pysdm** package, then System-Administration-Storage Device Manager.

---

### Post by Droidling on 2007-12-31
> **dcstar said:**
> Install the** pysdm** package, then System-Administration-Storage Device Manager.

This sounds promising. :) thanks! 

I'm sorry I didn't respond to everyone. I just popped off to get lunch and suddenly I had a half dozen replies. If this app fails to do the trick I'll be trying out the instructions for using the terminal.

Thank you all.

Terry

---

### Post by Droidling on 2007-12-31
I tried the synaptic package manager, selected all, but couldn't find pysdm listed there. Is the somewhere else I should be looking?

---

### Post by Droidling on 2007-12-31
> **Paqman said:**
> You can add a GUI "disk mounter" to any panel. It's only a right-click away! :)

Just tried this. It only lists the Floppy drive.

---

### Post by FuturePilot on 2007-12-31
Try this in a Terminal (Applications>Accessories>Terminal)
```
sudo apt-get install pysdm
```

---

### Post by Droidling on 2007-12-31
> **spiderbatdad said:**
> you are probably not going to be able to do this graphically, if the partition isn't mounting. Do you see the partiotion if you run:```
sudo fdisk -l
```

Yes. Here is the response

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       19080   153260068+  83  Linux
/dev/hdc2           19081       19457     3028252+   5  Extended
/dev/hdc5           19081       19457     3028221   82  Linux swap / Solaris

---

### Post by ayenack on 2007-12-31
Try this.

**sudo mount /dev/hdc1** (to mount hdc1 and so on) Entirely possible you'll get permission issues with the drives.

---

### Post by Droidling on 2007-12-31
> **FuturePilot said:**
> Try this in a Terminal (Applications>Accessories>Terminal)
```
sudo apt-get install pysdm
```

No Luck

ubuntu@ubuntu:~$ sudo apt-get install pysdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pysdm

---

### Post by Droidling on 2007-12-31
> **ayenack said:**
> Try this.

**sudo mount /dev/hdc1** (to mount hdc1 and so on) Entirely possible you'll get permission issues with the drives.

Still no luck. I'm not sure what fstab and mtab do.

ubuntu@ubuntu:~$ sudo mount /dev/hdc1
mount: can't find /dev/hdc1 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$

---

### Post by FuturePilot on 2007-12-31
> **Droidling said:**
> No Luck

ubuntu@ubuntu:~$ sudo apt-get install pysdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pysdm

Go to System>Administration>Software Sources and make sure the first 4 check boxes are checked. Uncheck the one for the CD-ROM if it's checked. Then go to the Updates tab and check the first 2 boxes and optionally the 4th one. Reload the sources when prompted, then try that command again,

---

### Post by ayenack on 2007-12-31
Did you type that in a terminal? Silly question just noticed you did.

---

### Post by dcstar on 2007-12-31
> **Droidling said:**
> No Luck

ubuntu@ubuntu:~$ sudo apt-get install pysdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pysdm

Enable the "**universe**" repository in Synaptic, **Reload** and try again.

---

### Post by Droidling on 2007-12-31
> **FuturePilot said:**
> Go to System>Administration>Software Sources and make sure the first 4 check boxes are checked. Uncheck the one for the CD-ROM if it's checked. Then go to the Updates tab and check the first 2 boxes and optionally the 4th one. Reload the sources when prompted, then try that command again,

Gentlemen we have a winner!!!:KS Once I set the right software sources. the package installed, and I am browsing my hardrive.

I am still curious why mounting hdc1 through the terminal failed.

You guys are great. I really didn't expect to get this kind of support. 

Terry

---

### Post by ayenack on 2007-12-31
Try this to add the discs to fstab. Might be an idea to write this down.

Make a backup of fstab.
[B]sudo cp /etc/fstab /etc/fstab_backup

gksudo gedit /etc/fstab
[/B]
Add these lines to it.

[B]/dev/hdc1 /mount/hdc1 ext3 defaults 0 0
/dev/hdc2 /mount/hdc2 ext3 defaults 0 0
/dev/hdc5 /mount/hdc5 ext3 defaults 0 0[/B]

Then reboot. If this does not work you can restore fstab by doing this.

**sudo cp /etc/fstab_backup /etc/fstab**

Edit:
To late solved already. Mark as solved so others can learn how you did it. Top of page Thread Tools Solved.;)

---

### Post by dcstar on 2007-12-31
> **Droidling said:**
> Gentlemen we have a winner!!!:KS Once I set the right software sources. the package installed, and I am browsing my hardrive.

I am still curious why mounting hdc1 through the terminal failed.
.........

Getting the mounting syntax 100% correct can be tricky, that is why (most) people should use the GUI tools available rather than muck around with arcane manual text editing.

Too many people have a bad experience with Linux because others insist of offering them "terminal" commands instead of a GUI alternative that "normal" users find much easier to use (and understand).

---

