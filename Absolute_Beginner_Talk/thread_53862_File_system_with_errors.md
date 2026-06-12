---
title: "File system with errors"
date: 2005-08-02
forum: Absolute Beginner Talk
---

### Post by nic2 on 2005-08-02
When starting Ubuntu I get the following error messages:

	Starting Ubuntu
	* Mounting a tmpfs over /dev …
	*Creating initial device nodes …
	* Setting disc parameters …
	/dev/hdb : no such file or directory
	* checking root file system …
	/contains a file system with errors, check forced
	/:
	Entry ‘.clean’ in /tmp (2076705) is a link to’.’

	/:UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
	*		(i.e., without –a or –p options)			[fail]
	* fsck failed. Please repair manually and reboot

I read a little on ‘Checking and Repairing Filesystems’ and tried the following command and just ended up getting yet another error message:	

fsck –t ext2 /dev/hdb 

I am not sure what might be the cause of this; I made some changes to the /etc/hdparm.conf file to enable DMA for /dev/hdb at start-up but booted without any problems several times after that.

Can someone please help with some suggestion as to how solve this problem (it would be greatly appreciated)

---

### Post by amohanty on 2005-08-02
What kind of drive is /dev/hdb?

AM

---

### Post by nic2 on 2005-08-02
My HP Compaq nx6110 notebook only has the one hard drive and a CD-RW/DVD Combo.

The fact that I am getting the error on /dev/hdb is the thing that puzzles me.

---

### Post by amohanty on 2005-08-02
If you can post the changes you made and the fsck error message that would help a  lot, or else your best bet is to boot via live cd and undo the hdparm.conf changes. You might have to run fsck to be able to mount the drive though so the error messages would help.

AM

---

### Post by nic2 on 2005-08-03
[QUOTE=amohanty]If you can post the changes you made and the fsck error message that would help a  lot, or else your best bet is to boot via live cd and undo the hdparm.conf changes. You might have to run fsck to be able to mount the drive though so the error messages would help.

AM[/QUOTE]
I used the wrong type of filesystem to repair with the fsck command.  After correcting my mistake all errors were found and corrected.

I am grateful for your assistance as this made me go back and double check my initial command - thank you!

---

### Post by amohanty on 2005-08-03
you are welcome!.

AM

---

