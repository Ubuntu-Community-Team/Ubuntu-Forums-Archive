---
title: "VLC and Samba"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by IronLike Monkey on 2007-04-07
Good evening.  I am trying to figure out if I can use VLC media player to watch videos off of a shared folder on a diffrent computer on the same network.  The files are on a Windows Media Center PC, but it doesn't look like VLC will let me navigate to this folder through the network.  This is something I can do on a windows machine, so I am sure there has got to be a way in Ubuntu.  Can anyone help?

---

### Post by moffa on 2007-04-08
Unfortunately, the only way I've got that to work out is mounting a network share to a local point, using smbfs.

You have to install samba fs ```
 sudo apt-get install smbfs 
``` which installs a program to mount a network share to your computer (it looks like its actually a folder on your computer)

In a shell window you type ```
 sudo mount -t smbfs -o username=guest, password="",ip=192.168.1.100,workgroup=MSHOME //192.168.1.100/sharedname /home/user/foldertomounto 
```

Substituing the in the correct ip addres, sharedname and foldertomounto

If it seems too complicated, I'm sorry hopefully someone else will explain an easier way to overcome this.

---

### Post by IronLike Monkey on 2007-04-08
Thanks for the reply, the instructions are pretty clear.  I tried but I must be missing something. I get :
"Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount ."

So I know I did something wrong, just to clarify, the command is as follows, right?:

  sudo mount -t smbfs -o username=guest **(login on the windows PC?)**, password="**(is this without quotes}**",ip=192.168.1.100**(is the gateway ip address)**,workgroup=MSHOME //192.168.1.100**(ip address of the host pc?)**/sharedname /home/user/foldertomounto

Thanks again, and there is no GUI with Samba on regular ubuntu?

---

### Post by moffa on 2007-04-10
Did you install smbfs?

The password needs to be password="" as in no password thats why there is nothing in the quotes.  Both ip addresses need to be the address of the host pc.

Some samba GUIs are listed here: [http://www.samba.org/samba/GUI/]("http://www.samba.org/samba/GUI/")
although I have not used any of them myself.

---

### Post by IronLike Monkey on 2007-04-16
thanks for your help, but I never got the syntax down right, but I did find another way, instead of using the ip address I used the netbios name....

smbmount //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword

that worked great, and I added this to the fstab file to make it permanent


//servername/sharename /mountdirectory smbfs username=windowsuserename,password=windowspassword 0 0


slowly but surely I am making progress, thanks to this forums help.

---

