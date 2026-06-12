---
title: "VMware Help!!"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-08-10
I have installed Vmware Server following all instructions. I am trying to run XP home under Ubuntu. XP is found by Vmware and everything works but then when I go to start the XP partition I get the error 

Cannot open the disk '/home/jason/windows.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file.

How do I fix the permissions to allow Windows XP to boot under Ubuntu??:confused:

---

### Post by iAndrew on 2007-08-10
I'm pretty sure you have to chmod, but I'm pretty new to linux. So wait for a elder's help.

---

### Post by Wake Rider on 2007-08-10
What are the commands to change the permissions of the files to read and write for Owner and the group with no access to others??:confused:

---

### Post by Wake Rider on 2007-08-10
OK I managed to boot the system, but then it came up with GRUB and it wouldn't let me move down to Windows XP and so VMware booted into Ubuntu so now I have Ubuntu running in Ubuntu. I am such a n00b! How embarrassing!:oops:

How do I make the necessary changes so I can use the keyboard in VMware to select Windows??:confused:

---

### Post by Bachstelze on 2007-08-10
Hold on a sec. Why did it show GRUB ? Are you trying to run your *physical* Windows under vmware ?

---

### Post by anewguy on 2007-08-10
Well, before we even go back to any of the Windows things, you MUST shut down your virtual machine NOW.  Running your Ubuntu in a virtual machine when Ubuntu is booted can corrupt your physical partition.

Next, be sure you have added yourself to the vmware group using system/administration/users and groups.  You then need to do the following in a terminal window:

pwd   - make sure it shows /home/jason

ls -al windows.v*  - this will list  the windows virtual machine files and their attributes.  Check your windows.v* files to see what they say up front -  something like -rwx -r--r-- will be at the front.  If those files don't say something similar to  -rwxrwx-r-  you can do the following  and it will  set the permissions on the file so you should be able to access them:

sudo chmod  YourFileName 765

Do this for each of the windows.v* files that show in your directory.

After that, I would have to agree with the previous post - you must be trying to run off the physical partition.  This is allowed, but it comes with some warnings:

- you MUST select your Windows installation when GRUB comes up in your VM window.  Many people change the time out time to a higher value in the menu.lst (?) file for grub so they get more time to choose.  Others will make Windows the default, so if no reply is given it will just start Windows.  Remember this change effects ANY boot, not just the boot in the VM, so it can get tiring remembering to move up/down to the Ubuntu one when you boot normally.

- as mentioned above, a slip up, just letting your machine boot normally for example inside the VM can cause the physical partition to become corrupted resulting in data loss and a clean install being needed.

- it's supported, but still what you might call "experimental" the last I heard

- once you boot your physical partition in a VM, you will have to activate Windows again.  Then next time you do a dual-boot normal boot of Windows, you'll have to activate again (that's been my experience).  Microsoft starts asking questions after a couple of these, and there is a big gray area on what they mean in their EULA.  From what I've read on this forum and on the net, it sounds like Microsoft does their best not to let you run in a VM and boot both, even though it is a single installation of Windows on a single PC.

That being said, either way around be sure to install the VMWare Tools to the virtual machine.

If you need additional help, please post back!:)

---

### Post by anewguy on 2007-08-11
BTW - for the "not able to move down to the Windows" option, you have to click your mouse in the VM window first, then you can use the keys.:)

---

