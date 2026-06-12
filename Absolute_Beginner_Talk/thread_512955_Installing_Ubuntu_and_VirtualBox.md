---
title: "Installing Ubuntu and VirtualBox"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-07-29
Just curious, how do I install Ubuntu into the Virtual Machine in VirtualBox?
Of course when it boots in the VM it runs the LiveCD with the option
to install sitting on the Desktop.

Do I just click on the Install Icon on the LiveCD while running
it inside the VM?

Will this touch my real XP install.

This is my 1st time running a VM so forgive my ignorance.

---

### Post by felicity on 2007-07-29
I've not personally tested an Ubuntu install from a Windows XP host running VirtualBox, but I know that it won't harm your WIndows XP installation. You should be able to double-click the install icon like a normal install. It will install on the virtualdrive you made previously in VirtualBox, not conflicting with what you already have on your main drive with WinXP.

---

### Post by Dokatz on 2007-07-29
I've done it, It's no problem if you just click the install button. At least that was my experience. But if you really really question I would stop before I went any further and made sure that the partition it's writing too isn't your existing NTFS one obviously, So you don't clear it.

---

### Post by felicity on 2007-07-29
I don't believe it writes over any data, but creates a virtual file (.vdi) during the setup of the virtual machine, and that is written wherever you want it. But as far as I know there isn't a way to make that file overwrite anything. It can only be created if there is free room on the hard drive.

---

### Post by Orbital75 on 2007-07-30
Yeah, I've created a Virtual Hard Drive that's 8 gigs in size.
So I guess after clicking the Install icon from the LiveCD, it should
just install to the Virtual Hard Drive.  

While in The LiveCD in the Virtual Machine I looked 
Within My Computer and it didn't show any Drives
mounted so Ubuntu doesn't seem to be seeing out
of the VM. Under normal circumstances, it should auto mount
all drives Correct?

---

### Post by vexorian on 2007-07-30
If "normal circumstances" mean an usual live-cd execution on the machine itself , yes.

You may try the live-cd without installing it.

I had issues when I tried to run xubuntu live on virtualbox, dunno why everyone got it right. On Linux guest I found virtualbox really good.

---

### Post by Orbital75 on 2007-07-30
I tried installing ubuntu 7.04 from the LiveCD "install icon" on the 
Desktop but had no luck.

This is the Error message I received. 

[img]http://img404.imageshack.us/img404/9951/00screenshotki9.png[/img]

Here is some info that may help.
I gave my Limited User account Admin rights when I installed VirtualBox
then Took admin rights away to run it as a Limited User.
The LiveCD works great but I can't do an install.

I don't won't to run windows as an admin even while
using Virtual Box....  Could this be the issue, the LiveCD
work fine.

I'm thinking maybe trying to Right Click on the VirtualBox
Program Icon and selecting " Run As" 
then choosing Admin.

---

### Post by Orbital75 on 2007-07-31
Well, I am posting my finding to help others.....  It seems that you do have to be an Admin to
format the Virtual HardDrive to Ext3.  After you become an Admin it will Format the Virtual
HardDrive and create your Ext3 partition along with your Swap partition.

After I did all the Formating and Partitioning to the VirtualHard Disc the install continued
and did just fine.  After I had the OS set up to near what I wanted, I powered off the
VM and Took away my Admin rights.

So far so good running without the Admin rights.

I'll keep everyone posted so it will be beneficial to others if they may need these questions answered.

:KS

---

