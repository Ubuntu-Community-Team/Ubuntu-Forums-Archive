---
title: "VMware Server install fails"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by BiggoCharley on 2006-11-22
Tried to install VMware server and all seemed to be going ok-- downloaded the tar.gz file, unpacked it ok but when I tried to run the install script I got this message:

"root@ubuntu3:~/vmware-server-distrib# ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

root@ubuntu3:~/vmware-server-distrib#"

I had installed the VMware player with Synaptic and subsequently removed it, and that was and is the only VMware product that was ever installed on this system.

Any ideas would be appreciated.

---

### Post by ginkhao on 2006-11-22
Blatant guess here but when you removed VMware player with Synaptic did you choose "mark for complete removal"?

The software may not be installed but if the configuration settings have been left behind that might be what is tripping up the installer.

---

### Post by janstedehouder on 2006-11-23
I had the issue before. There is a hidden .vmware folder in you /home/user folder. Make it visible in Nautilus with Crtl-H and either rename or remove the .vmware folder. That should do the trick.

---

### Post by BiggoCharley on 2006-11-23
Followed both of the above -- went back to Synaptic and marked the VMware player for complete removal and removed it.(again). 
I also found the ./vmware folder and move it to trash. Then rebooted and tried the install again with the same results as before.  Any more ideas?:confused:

---

### Post by Bachstelze on 2006-11-23
VMware Serve has an uninstall script, try to run it (it's somewhere in the bin folder) and then try reinstalling.

---

### Post by NetworkGuy on 2006-11-23
From a terminal type ```
 sudo updatedb 
```
then ```
 sudo locate vmw* 
```
then remove every file that comes up. (There should be about 10 to a dozen)

This is what ended up working for me.  The installer is looking for something, and if it finds it, it will not install.

---

### Post by BiggoCharley on 2006-11-23
It seems if i were to remove all the vmw* files I find (which are considerable) I will have no installer available. What next?  Start over?

---

### Post by BiggoCharley on 2006-11-23
Btw --I ran the uninstaller script with the following results:

charley@ubuntu3:~$ sudo /root/vmware-server-distrib/bin/vmware-uninstall.pl
Uninstalling the tar installation of VMware Server.

Stopping internet superserver: xinetd.
Starting internet superserver: xinetd.
This program previously created the file /etc/vmware/vmnet8/nat/nat.conf, and
was about to remove it.  Somebody else apparently did it already.

This program previously created the file /etc/vmware/vmnet1/dhcpd/dhcpd.leases,
and was about to remove it.  Somebody else apparently did it already.

This program previously created the file
/etc/vmware/vmnet8/dhcpd/dhcpd.leases~, and was about to remove it.  Somebody
else apparently did it already.

This program previously created the file /dev/vmnet7, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet5, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet2, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /etc/vmware/config, and was about to
remove it.  Somebody else apparently did it already.

This program previously created the file /etc/vmware/vmnet8/dhcpd/dhcpd.conf,
and was about to remove it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet0, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file
/etc/vmware/vmnet1/dhcpd/dhcpd.leases~, and was about to remove it.  Somebody
else apparently did it already.

This program previously created the file /dev/vmnet6, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet4, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet9, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet3, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet8, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /etc/vmware/vmnet8/dhcpd/dhcpd.leases,
and was about to remove it.  Somebody else apparently did it already.

This program previously created the file /etc/vmware/vmnet1/dhcpd/dhcpd.conf,
and was about to remove it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet1, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the directory /etc/vmware/vmnet1/dhcpd, and was
about to remove it. Somebody else apparently did it already.

This program previously created the directory /etc/vmware/vmnet8/dhcpd, and was
about to remove it. Somebody else apparently did it already.

This program previously created the directory /etc/vmware/vmnet8/nat, and was
about to remove it. Somebody else apparently did it already.

This program previously created the directory /etc/vmware/vmnet1, and was about
to remove it. Somebody else apparently did it already.

This program previously created the directory /etc/vmware/vmnet8, and was about
to remove it. Somebody else apparently did it already.

The removal of VMware Server 1.0.1 build-29996 for Linux completed
successfully. Thank you for having tried this software.

After doing this I tried the installer again but still wasn't able to install.

Thank all of you for trying to help.

Charley

---

### Post by djsroknrol on 2006-11-23
Try using this guide using your D/L'ed file and see what happens...

[LINK]("http://ubuntuforums.org/showthread.php?t=183209")

---

### Post by nickburns on 2006-11-23
I would really recommend using the following to install server.  I have done it successfully several times.

[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware)

---

### Post by BiggoCharley on 2006-11-23
I started out to install VMware Server using the tutorial on this webpage.

<http://www.howtoforge.com/ubuntu_vmware_server>

I don't know where I went wrong but by the time I found the pages you mentioned above, the damage was apparently done. Now I guess I need to clean up and start over or I'm stuck in never-never land.  Some how I need to purge the VMware dregs.  I'm not sure how to do this.

---

