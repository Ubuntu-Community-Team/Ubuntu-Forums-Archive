---
title: "[SOLVED] VM Server Gutsy"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by jmeyer on 2007-10-24
I am running VM Ware server for XP on Fiesty and recently upgraded to Gutsy.  Now when I try to run the virtual machine it give me an error

> Unable to change virtual machine power state: The process exited with an error:
End of error message.

Did the path for the vmware change from fiesty to gutsy

> /var/lib/vmware-server/Virtual Machines/XPPro/XPPro.vmx

---

### Post by timcredible on 2007-10-24
probably need to re-install vmware.

---

### Post by jmeyer on 2007-10-24
Will that delete my current virtual machine?  i dont want to have to redo that unless it is absolutely necessary.

---

### Post by celsdogg on 2007-10-24
im having the same problem since upgrading to gutsy. i would take the VM files in the vmware-server directory and back them up elsewhere before upgrading. hopefully they will still be compatible with the new version of vmware.

im going to do it now and see what happens.

---

### Post by rlevini on 2007-10-24
I do not use the repo version of vmware, but I saw the same thing after upgrading to gutsy.

Running 

```
sudo /usr/bin/vmware-config.pl
```

fixed it for me. Hope this helps.

---

### Post by celsdogg on 2007-10-25
i dont have that script. i only have this one:

vmware-config-network.pl

when i run it it goes thru fine, but at the end it says this:

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

---

### Post by celsdogg on 2007-10-26
bump

---

### Post by jmeyer on 2007-10-26
I have the file vmware-install.pl
when i run that it says 
> A previous installation of VMware software has been detected.

Failure

Execution aborted.
I don't have any other installation of VM on the ubuntu box.  the only thing i have is the virtual machine saved from before the upgrade.

---

### Post by celsdogg on 2007-10-26
i found this:

[http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/](http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/)

i tried it but i get this error:
> A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.

man j, we are having the worst luck.

---

### Post by jmeyer on 2007-10-30
celsdogg,
I am getting that error also, except it has only this part
> 
A previous installation of VMware software has been detected.

Failure

Execution aborted.


it doesn't give me any code.  it would be helpful if I had a error number to look up.

---

### Post by celsdogg on 2007-11-02
this might help:

[http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html)

i had to do:

sudo find / -name vmware

after it found all the references to vmware, i renamed them all, and then the installer worked fine.

i do have a much bigger problem tho. after rebooting after i installed it, my video settings are all crazy. my xorg.conf is fine, but it seems to ignore it. it will not display higher than 800x600 @ 73hz. i cant figure this out and im not sure if it has anything to do with vmware.

---

