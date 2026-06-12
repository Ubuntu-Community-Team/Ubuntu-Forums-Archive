---
title: "VMWare Player Problem"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by shannonbrown on 2007-03-11
Status: Ubuntu Newbie

Info:
X86 (Dell 8200)
Ubuntu 6.10


What I Did:
I used the Applications ... Add/Remove ... tool and inadvertently added VMWare-Player to my new Ubuntu install.  This has created a perpetual and annoying problem that I cannot resolve.

The Problem:
VMware-Player fails to install properly, and I cannot get it to uninstall.  All I want to do is to remove this application.  However, when I try to use Applications ... Add/Remove to uninstall, VMWare fails to uninstall returning a  error code (1) from the post-install script.  

What I have done:
I have trolled the online forums for similar issues.  I have tried using ap-get  etc. to remove the packages and all of these efforts fail with error codes.

What I want to do:
I simply want to cleanly and completely remove VMware-Player--from the tool bar, from my system, and from the Add/Remove Tool.  (Note:  Every time you try to add any other package, the VMWare issue arises and causes problems with the install.

I am not sure what else to do.  I am not familiar with Ubuntu or Debian to take further action.  Has anyone else had success removing this (annoying) package?

---

### Post by Icemanyurt on 2007-03-11
I am having this same problem and I am getting nowhere too, if I learn anything I will send it your way...

---

### Post by joriad on 2007-03-11
I also had this same problem. I tried sudo dpkg --configure -a and sudo apt-get clean to fix the problem but I eventually had to boot my system from the installation cd and select rescue a broken system. It only took a few minutes and then I was able to uninstall and reinstall vmware-player. If you do this, when it gets to rescue mode select reboot the system and everything should be fine. So far I haven't noticed any adverse effects of doing this, but then again I have a fairly recent fresh install of edgy. After your system has restarted you should then be able to run sudo apt-get remove vmware-player or sudo apt-get install vmware-player as needed.

---

### Post by shannonbrown on 2007-03-12
Thank you Joriad.

I found that I did not need the original install CD (actually, I could not get the install CD to boot into a safe or recovery mode????).

**VMWare-Player Uninstall/Install Problem **
As noted, the following may work (use at your own risk):
1) Save work, log-off, and select restart Ubuntu.
2) As the computer reboots, the GRUB loader appears and allows you to select the boot system.
3) Select the latest option noted (recovery mode) from the GRUB loader screen--you must use recovery mode.
4) Ubuntu loads in "text mode" and you should see the command line appear after several seconds/minutes.
5) When the command line appears type 'sudo apt-get remove vmware-player'. [Do not type the ' marks.]
6) Hit enter.  You should see text output indicating that VMWare Player was uninstalled.
7) When the command line returns, type 'exit'  and hit return.
8) At this point, the Ubuntu Graphical interface should load but you are still in recovery mode.
9) After the graphical interface loads, select RESTART.  The system reboots.
10) Restart the system and select the regular (NON recovery mode) option from GRUB.

This fixed the problem on my system.  I did not note any adverse effects from using this method.

---

### Post by joriad on 2007-03-14
I'm glad to hear that worked for you. I had to use the cd because my grub doesn't give me any options at all, it just boots the system in normal mode, no recovery mode at all.

---

### Post by jeremywhiting on 2007-03-14
I just ran into the same issue, if you actually want to use vmware-player all you have to do is run depmod as root or sudo depmod and that part of configuring vmware-player no longer has issues.

For some reason when the vmware-player modules are installed, depmod isn't run, so vmware-player doesn't know where to find them.  I'll file a bug if I can't find one that's already in the bug database somewhere.

---

