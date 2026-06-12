---
title: "VMware uninstall"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by fossmule on 2006-12-22
Hi, 

I'm pretty new with Ubuntu. I'm running Ubuntu dapper Drake. I tried to install VMWare server so i could run Windows (XP), but i had trouble with the installation.

the download from the vmware has been extracted and is on my desktop in the following folder (vmware-server-distrib)

there is also a folder in my user directory called (vmware) - it is locked and I can't figure out how to remove this so i can do another installation- i think i need to be root, but i don't understand how to remove that

to do another installation i typed the following command in the terminal

sudo ./Desktop/vmware-server-distrib/vmware-install.pl

and i got the following response:

A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Server.

Unable to find the answer INITSCRIPTSDIR in the installer database
(/etc/vmware/locations). You may want to re-install VMware Server.

Execution aborted.

Failure

Execution aborted.


--- can someone help me with this please!!! i would really appreciate some help.

thanks so much,

fossmule

---

### Post by Stew2 on 2006-12-22
I recently removed VMware server from my computer as well. The command I used was "/usr/bin/vmware-uninstall.pl". I cant remember though if I had to put a sudo in front of that. If you try it and it doesn't work the first time put "sudo" and a space first and then the rest of the command. I hope this helps you. Good luck with it.

Regards,
Stew2

---

### Post by viper on 2006-12-22
After you remove vmware, you could possibly use automatix to install it, just a thought.....

---

### Post by hanzomon4 on 2006-12-22
> **Stew2 said:**
> I recently removed VMware server from my computer as well. The command I used was "/usr/bin/vmware-uninstall.pl". I cant remember though if I had to put a sudo in front of that. If you try it and it doesn't work the first time put "sudo" and a space first and then the rest of the command. I hope this helps you. Good luck with it.

Regards,
Stew2

What ^ said and add the sudo.....

---

### Post by fossmule on 2006-12-22
hi everyone, thanks for your help

i took your advice and here is what happened.

i typed the following in terminal and this is what i got:

fossmule@fossmule-laptop:~$ cd vmware
fossmule@fossmule-laptop:~/vmware$ sudo ./vmware-uninstall.pl
Uninstalling the tar installation of VMware Server.

Unable to find the answer INITSCRIPTSDIR in the installer database
(/etc/vmware/locations). You may want to re-install VMware Server.

Execution aborted.

fossmule@fossmule-laptop:~/vmware$ sudo ./vmware-uninstall.pl
Uninstalling the tar installation of VMware Server.

Unable to find the answer INITSCRIPTSDIR in the installer database
(/etc/vmware/locations). You may want to re-install VMware Server.

Execution aborted.

any ideas??

---

### Post by Stew2 on 2006-12-23
So you tried:
```

 sudo /usr/bin/vmware-uninstall.pl 

```
and it didn't work? Thats weird, it uninstalled it for me. Maybe you will have to try to fully reinstall it first and then try to uninstall it again. The above command should work as it was given to me during the VMware install procedure. Hope you get it fixed.

Regards,
Stew2

---

