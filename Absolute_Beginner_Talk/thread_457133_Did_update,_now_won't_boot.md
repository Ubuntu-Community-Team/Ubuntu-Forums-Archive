---
title: "Did update, now won't boot"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by stevelasvegas on 2007-05-28
Using Ubuntu Feisty 7.04 installed with WUBI.
Update manager checked for updates which I allowed to download and install.
Now, when I boot, the Ubuntu splash screen freezes. I do a ctrl+alt+f1 and it says "Loading, please wait" and stays there.
Can't boot.
Please help.

---

### Post by Hobo Joe on 2007-05-28
A lot of people have this, it's a new kernel, so I would recommend using envy and re-installing your drivers.

If you can get into the command line, do this:
(If you already have Envy skip this step)
```

sudo aptitude install Envy

```
Then run it:
```

Envy -t

```
Then follow the instructions to uninstall and then re-install your drivers with respect to your manufacturer.(ATi, nVidia)

---

### Post by stevelasvegas on 2007-05-28
Can't get to command line.

---

### Post by Hobo Joe on 2007-05-28
> **stevelasvegas said:**
> Can't get to command line.

Not even to recovery mode?

---

### Post by stevelasvegas on 2007-05-28
Although I have a backup from a couple of days ago. Only problem is, it's a backup done in windows so I only have backups of the 3 virtual disks in the wubi folder.

---

### Post by leebrent on 2007-05-28
Can you boot to the Ubuntu CD and get the recovery console this way?

---

### Post by stevelasvegas on 2007-05-28
Will try that now, thanks. Will report back soon. I am very new but I really enjoy Ubuntu, migrating from many years of windows. Going to try your suggestion now.

---

### Post by stevelasvegas on 2007-05-28
I don't have Envy. I can get to a grub> prompt using the Ubuntu live CD. Remember, I installed Feisty through WUBI if that makes a difference. (sorry so new; a little ignorant, I'm learning through mistakes, hard way).

---

### Post by stevelasvegas on 2007-05-28
I see where it stops booting;
Loading Please Wait....
[43.675877] ATA1.00: SET of native returned 0, expected 195371568
[43.691836] ATA1.00: SET of native returned 0, expected 195371568

---

### Post by Hobo Joe on 2007-05-28
> **stevelasvegas said:**
> I don't have Envy. I can get to a grub> prompt using the Ubuntu live CD. Remember, I installed Feisty through WUBI if that makes a difference. (sorry so new; a little ignorant, I'm learning through mistakes, hard way).

Go ahead and try what I said in my previous post for installing Envy, post the results.

---

### Post by stevelasvegas on 2007-05-28
Frustration level = 2 (taking deep breathe)
OK, I rebooted and I think I hit esc 2 times and was prsented with a list (I wish I wrote it down) of kernels to boot from. I chose "original". Now I'm in Ubuntu. I will proceed with Envy now, right?

---

### Post by stevelasvegas on 2007-05-28
I get this.
steven@ubuntu:~$ sudo aptitude install Envy
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Couldn't find any package matching "Envy".  However, the following
packages contain "Envy" in their description:
  alsa-tools-gui 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
steven@ubuntu:~$

---

### Post by stevelasvegas on 2007-05-28
OK, I downloaded Envy and ran it uninstalling the ATI driver. Then tried to install the ATI driver and received this:
python pulse.py ati
root@ubuntu:/usr/share/envy# python pulse.py ati
ENVY ERROR: ATI card not found

---

### Post by stevelasvegas on 2007-05-28
In device manager, I don't see an ATI device. The only graphic thing I see is Intel Mobile 915GM/GMS/910GML Express Graphics Controller

---

### Post by Hobo Joe on 2007-05-28
Are you sure you have an ATi card?

Also, try uninstalling before installing.

EDIT:

I see that your using an Intel. I hate to break it to you, but Envy doesn't work for intel.

[http://support.intel.com/support/graphics/sb/CS-010512.htm](http://support.intel.com/support/graphics/sb/CS-010512.htm)
This is the Intel driver website, Install the appropriate driver.

You will probably have to compile some code to....

---

### Post by stevelasvegas on 2007-05-28
Compile? Now I am going to have to read how to do that. A precompiled driver would be nice. Anyway, when I boot with the new kernel (I guess that's what you call it), I hit esc, select Ubuntu and when presented with the "kernel menu" I can not get it to boot using 2.6.20-16 but I can using 2.6.20-15.
Based on the information so far, do you still think it's my graphics card driver causing the problem? Should I just continue to use the older kernel? Is this a potential problem every time a new kernel is produced?
Suggestions please.
By the way, thanks for all the help up to this point. The Ubuntu community has come to my rescue a few times in this migration process. I just hope I can last through the learning curve.
Thanks again.

---

### Post by stevelasvegas on 2007-05-28
One other thing. I recently installed Beryl Manager. Would this be a factor?

---

### Post by Lucifiel on 2007-05-28
Errr... if you ever want to compile something like a driver(basically something that could break your Ubuntu installation), try booting into the livecd and give compiling a shot from there.

That way, if anything breaks, you're safe. I've messed up my system trying to compile something and everything broke.

---

### Post by Seti on 2007-05-28
I had a similar problem after today's update. Ubuntu won't boot at all. Plus, I use lilo because the iinitial install didn't like XFS and couldn't install grub.
Good thing I have Zenwalk on another partition, otherwise i'd be reinstalling now. I guess I'm just going to wait a few days, reinstall ubuntu and give it yet another chance. They really REALLY need to fix this issue; having your system break every time there is a kernel update really sucks.

---

### Post by Hobo Joe on 2007-05-28
> **Seti said:**
> I had a similar problem after today's update. Ubuntu won't boot at all. Plus, I use lilo because the iinitial install didn't like XFS and couldn't install grub.
Good thing I have Zenwalk on another partition, otherwise i'd be reinstalling now. I guess I'm just going to wait a few days, reinstall ubuntu and give it yet another chance. They really REALLY need to fix this issue; having your system break every time there is a kernel update really sucks.

Have you re-installed your graphics driver?

You shouldn't have to do a whole reinstall of Ubuntu.

---

### Post by Seti on 2007-05-28
Don't get me wrong, I really like ubuntu. However, it would be nice to see my desktop still working after an update.

---

### Post by Hobo Joe on 2007-05-28
> **Seti said:**
> Don't get me wrong, I really like ubuntu. However, it would be nice to see my desktop still working after an update.

*Ahem*

like I said, you should try to re-install your graphics driver before you give up.

---

### Post by stevelasvegas on 2007-05-28
How do I reinstall the graphics driver? I am Googleing and copy and pasting anything that looks good and I am sure I will make it worse, so I am stopping. Time for mood elevators. Here's the newest command I tried sudo dpkg-reconfigure xserver-xorg, although my driver wasn't listed.
If I have this right, the new kernel, 2.6.20-16 will not work with my present video driver and I have to find the Intel driver for Mobile 915GM/GMS/910GML Express Graphics Controller (as is being reported by device manager).
Is that correct?

---

### Post by Repent on 2007-05-28
I had the same thing happen, I don't have time to mess with it now so I just went back to the last  kernel. you can do this by rebooting  and clicking on the Esc key when it says press Esc to enter Menu, scroll to Kernel 2.6.20-15-generic and click on it. It's not a fix but it will get you up and running. 

Hope it helps some.

---

### Post by stevelasvegas on 2007-05-28
But what can one do to always boot to a previous kernel without having to enter the grub menu?

---

### Post by notquitemichael on 2007-05-28
i'm not sure envy will help, judgeing by what returned it sounds like something to do with your hard drive (ATA) although that's about as much help as I can be.

---

### Post by stevelasvegas on 2007-05-30
Here's what displays on the screen when booting using the new kernel.
[http://www.flickr.com/photos/7610778@N03/520973259/]("http://www.flickr.com/photos/7610778@N03/520973259/")

---

