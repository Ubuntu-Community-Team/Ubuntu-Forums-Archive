---
title: "how to remove vmware"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by sn0m on 2007-01-31
hi can anyone show me  how to remove vmware.
i have tried synaptic, sudi apt-get autoremove/remove, no luck so far.
ta
koli

---

### Post by yabbadabbadont on 2007-02-01
How did you install it?

---

### Post by sn0m on 2007-02-01
i installed it using a guide here, but i decided it was too buggy. Anyway, i managed to do it but cant get rid of a file.
this is the output frm terminal

sn0m@sn0m-laptop:~$ cd /
sn0m@sn0m-laptop:/$ ls
bin    dev   initrd      lost+found  opt   sbin  tmp  vmlinuz
boot   etc   initrd.img  media       proc  srv   usr  Windows 2000 Professional
cdrom  home  lib         mnt         root  sys   var
sn0m@sn0m-laptop:/$ rm Windows 2000 Professional
rm: cannot remove `Windows': No such file or directory
rm: cannot remove `2000': No such file or directory
rm: cannot remove `Professional': No such file or directory
sn0m@sn0m-laptop:/$ sudo mv  Windows 2000 Professional ~/Desktop
mv: cannot stat `Windows': No such file or directory
mv: cannot stat `2000': No such file or directory
mv: cannot stat `Professional': No such file or directory
sn0m@sn0m-laptop:/$ sudo rmdir  Windows 2000 Professional
rmdir: Windows: No such file or directory
rmdir: 2000: No such file or directory
rmdir: Professional: No such file or directory
sn0m@sn0m-laptop:/$ 

how can i get rid of it

thanks

koli

---

### Post by yabbadabbadont on 2007-02-01
Pretty much the same way you would when using the command prompt in win2k...  :D

rm "Windows 2000 Professional"

---

### Post by sn0m on 2007-02-01
](*,) ](*,) 
this is what i get

sn0m@sn0m-laptop:~$ cd /
sn0m@sn0m-laptop:/$ rm rm "Windows 2000 Professional"
rm: cannot remove `rm': No such file or directory
rm: cannot remove directory `Windows 2000 Professional': Is a directory
sn0m@sn0m-laptop:/$ sudo rmdir "Windows 2000 Professional"
rmdir: Windows 2000 Professional: Directory not empty
sn0m@sn0m-laptop:/$ sudo rm "Windows 2000 Professional"
rm: cannot remove `Windows 2000 Professional': Is a directory
sn0m@sn0m-laptop:/$ sudo rmdir "Windows 2000 Professional"
rmdir: Windows 2000 Professional: Directory not empty
sn0m@sn0m-laptop:/$

---

### Post by rovernaut on 2007-02-01
are you using WMware or VMWARE SERVER?
these are the command for removing vmware server in konsole form the installation tutorial.

"/usr/bin/vmware-uninstall.pl". 
might work for vmware also?

---

### Post by yabbadabbadont on 2007-02-01
DO NOT MAKE ANY TYPO'S!  (or very bad things may happen)

sudo rm -rf "Windows 2000 Professional"

---

### Post by glabouni on 2007-02-01
seems there's some confusion here.

do you want to remove a virtual machine inside vmware?
-> run vmware and look for "delete from disk" in menus

do you want to remove vmware ? 
-> look for uninstall script "vmware-uninstall.pl" somewhere on your disk

do you want to remove a non-empty directory ?
-> man rm to learn about the options to rm command

---

### Post by yabbadabbadont on 2007-02-01
> **glabouni said:**
> seems there's some confusion here.

do you want to remove a virtual machine inside vmware?
-> run vmware and look for "delete from disk" in menus

do you want to remove vmware ? 
-> look for uninstall script "vmware-uninstall.pl" somewhere on your disk

do you want to remove a non-empty directory ?
-> man rm to learn about the options to rm command

They way I have read his posts is that he has already uninstalled vmware (through whatever means).  Uninstalling vmware doesn't remove the VM related files though, and I think that is what he is trying to remove now.  (He just doesn't know how to handle spaces in file and directory names)

---

### Post by aribezas on 2008-04-14
Hello(sorry for my English)
I removed vmware server from synaptic but i am still see disc space 28G used from vmware. What can i do?

---

### Post by OMan on 2008-05-21
same thing happened to me. if you create a partition using vmserver and then "delete disk" then the whole partition goes into Trash and you cant use that disk space until you empty your trash.

run this command 
sudo du -h --max-depth=1
and look for the really big file/directory. 
If its in a directory then cd into that directory and run the command again until you get to the location of the really big file (probably in your Trash). 
then remove it using rm.

---

