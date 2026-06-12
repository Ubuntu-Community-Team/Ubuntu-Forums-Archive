---
title: "Guide for mounting an XP networked share from Ubuntu"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by frogtools on 2006-02-15
Hello,

Despite my best efforts, and trying everything I could find I can not mount a network share folder on my windows box from my ubuntu box.

I'm a newbie to Linux and need a step by step instruction guide for this.

I have a windows XP box (workgroup MSHOME, pc name COMP1). 
I have a ubuntubox. 

Both boxes are connected through my router - both can access the internet, but I can't see either box thorugh the other.

From ubuntu I want to mount a share folder on my xp box. Can anyone give me a step by step of how to do this? Help on configuring the windows box and the ubuntu system would be great.

Thanks.

---

### Post by terje on 2006-03-05
You need to install smbfs from synaptic or run:
sudo apt-get install smbfs

When you have smbfs installed edit your fstab file and add the following line at the end:

//windowsservername/sharename /ubuntumountdir smbfs username=windowsusername,password=windowspassword 0 0


If you don't need a password to access the windowsshare just substitute that section(username=windowsusername,password=windowspassword) with the word *defaults*.

Save the file and run:
sudo mount -a

The share should now be mounted and will stay mounted after reboot.

---

### Post by dodge78 on 2006-03-05
hi there,
i tried the instruction but it didnt work, when i tried to mount it i got a message under the command line stating "Could not resolve mount point /ubuntumountdir". also what if any do i need to do with Windows XP Pro to get it to work?:confused:

---

### Post by adamkane on 2006-03-05
There are good HOWTOs and WIKIs on this subject. 
[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

But you need to create a folder to mount the share and then make the folder accessible. (This isn't usually explained in the HOWTOs.)

```

sudo mkdir /media/sharename
sudo  chmod a+rw /media/sharename

```

Substitute "sharename" with something more descriptive.

---

