---
title: "groups?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by supersonicdarky on 2007-05-02
virtual box tells me to add myself to the vboxusers group. i had done so (user settings > manage groups > vboxusers properties > groupmembers). It still says the error. How do i fix?

```
kernel@laptop:~/downloaded$ VBoxManage 
WARNING: You are not a member of the "vboxusers" group.  Please add yourself
         to this group before starting VirtualBox.

         You will not be able to start VMs until this problem is fixed.
/opt/VirtualBox-1.3.8/VBoxManage: error while loading shared libraries: VBoxDD.so: cannot open shared object file: No such file or directory

```

---

### Post by jwbaker on 2007-05-02
You can show what groups to which a user belongs by typing "groups" at the command line.  If you don't see "vboxusers" you can add a user to that group with this command: usermod -a -G vboxusers joeblow.  Replace joeblow with the desired user.  Only root can issue this command, so you will need to use "sudo" or login as root to do so.

More information: man usermod.

---

### Post by supersonicdarky on 2007-05-02
nothing happens

```
kernel@laptop:~$ groups
kernel adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
kernel@laptop:~$ sudo usermod -a -G vboxusers kernel
Password:
kernel@laptop:~$ groups
kernel adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
kernel@laptop:~$ 

```

---

### Post by Seisen on 2007-05-02
Go to User Groups and select groups and then scroll down till you see vbox or something like that. It was the last one on the list. Then select the user that you use and then logout and log  back in.

---

### Post by jwbaker on 2007-05-02
Log out, log back in.

---

### Post by supersonicdarky on 2007-05-02
yay! worked. thnx.

but now i have another problem

```
kernel@laptop:~$ VBoxManage 
/opt/VirtualBox-1.3.8/VBoxManage: error while loading shared libraries: libuuid.so.1: cannot open shared object file: No such file or directory
kernel@laptop:~$ cd /lib/
kernel@laptop:/lib$ sudo cp libuuid.so.1 /opt/VirtualBox-1.3.8/
kernel@laptop:/lib$ VBoxManage 
/opt/VirtualBox-1.3.8/VBoxManage: error while loading shared libraries: libuuid.so.1: wrong ELF class: ELFCLASS64
kernel@laptop:/lib$ 

```
the file was missing, i copied it into folder, now some other error

amd64. forced architecture for vbox

---

now that i actually read the class (ELFCLASS**64**), it seems it wants a 32 bit version. can anyone send me theirs?

---

