---
title: "how to orgenaize files?"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by natanel on 2008-03-07
Hi

I am used to XP files folders

how do you organizes your files in ubuntu

to where you download programs to where to install them (examples,workspace,templates,public,...)?

for what is it home folder and the folder inside it?
all the bit,lib,boot,dev etc in the file system

any important folders to know?

thanks

---

### Post by indytim on 2008-03-07
It is recommended to keep you personal files in the /home.  You have complete access to it.  A lot of the other directories are specific to the ops.  In most cases, you will need to super user priv's to write to these folders (by design).

Other than the /home partition, space permitting, you could set up a separate partition to house your data... whatever works for you.

IndyTim

---

### Post by mcduck on 2008-03-07
Keep all your files inside your home directory, actually that's all you can as users only have write access in their own homes. You can create what ever directories you want in there to organize your files the way you want.

You don't need to worry about where programs go, the package management will handle everything for you automatically. (Actually programs don't even go into one place, instead their files go to different places depending on their purpose. For example executable files usually go to /usr/bin, all documentation goes to /usr/share/doc, libraries to /usr/lib and so on.)

Directories other than your home that are worth knowing about are /etc, where most system settings are, /media where you can find all your disks and removable drives, /mnt which is alternative place to mount your drives (for example to prevent them from appearing on your desktop) and /boot where the kernel image and Grub configuration files are. In /var/log you'll find some system log files.

edit: here are some of the system directories explained: [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html")

---

