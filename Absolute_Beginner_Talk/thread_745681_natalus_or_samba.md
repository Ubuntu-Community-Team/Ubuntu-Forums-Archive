---
title: "natalus or samba"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by love2learn on 2008-04-04
I am a little confussed. What is the difference between natalus and samba? I am getting different answers for the same functions.

Scenario:

I have a ubuntu laptop (7.10 and connected by wireless ) and an xp file storage desktop computer (cat5 to the router ).  I just want to have read /write  access to the server. I dont care if the server see's the ubuntu laptop. 

Questions:

should i use natalus or samba? Is there an easier method? Should I be able to atleast see the xp server right now? 

I just need a little bit of light shed on the subject. Thanks

*edited for clarity (hopefully)*

---

### Post by nick_h on 2008-04-04
Nautilus is the Gnome file manager.

What you need is samba.   Have a look at - [SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba).  Read the bit about the smbfs plugin.

---

### Post by Hospadar on 2008-04-04
Nautilus is a graphical file browser, samba is just a protocol, if you mounted a samba drive from the command line, or through nautilus, it would be doing the same thing on the backend.

Samba is probably the easiest way to get at a machine, although you may need to do some research into windows network shares to figure out how to get it set up properly.  A much nicer solution I think would be to have your fileserver run linux and use ssh to connect to it, since this gives you remote control and file transfer in a very secure way.  Obviously though, if your xp machine is already set up, that might not be an (easy) option.

---

### Post by bt224 on 2008-04-04
I've been using Samba for a couple of years to link to my Windows machine as well as other Ubuntu machines. Been working flawlessly. Here's a link to get you started.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Remember, the forum, Google, and the wiki are your friends!

---

### Post by love2learn on 2008-04-04
excellent links guys. I have decided to go with the smbf*s package as* [this]("https://help.ubuntu.com/community/SettingUpSamba")
link says: 

**Do you need Samba?**

  Samba is not necessary to:[LIST]
[*] Access shared folders, drives and printers on a Windows computer (that is, act as a client with Windows servers), you only need a **smbfs** plugin. See [MountWindowsSharesPermanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")[/LIST]so I followed [this]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")

which led me to a confusing statement: 
Add a line at the bottom of your /etc/fstab file that specifies: 
 //$SERVER/$SHARE $MOUNTPOINT $FS_TYPE credentials=$SMB_CREDENTIALS,uid=$UID,gid=$GID 
  # e.g.
SERVER=apollo
SHARE=install_files
MOUNTPOINT=/path/to/mnt
FS_TYPE=smbfs
SMB_CREDENTIALS=/path/to/.smbcredentials
UID=1000

a couple of questions about the above. he states " share=install_files
and mountpoint=/path/to/mnt"

but what if i want to share whole drives on my windows server? I have f: g: and h:
I want to share with multiple folders in each f=movies g=pictures h=music
and many many subfolders. how would i create that in the fstab?

thanks

*edited for clarity*

---

### Post by love2learn on 2008-04-05
okay, i have decided to just go for it and if i fubar something up i can just reload. I have edited the fstab to look something like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=eafe81a0-359c-4f9e-8289-a2bdc8d1b196 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ff38c1b7-89b0-4066-84d4-687e910a18e7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
//media/f/movies /home/lucana/desktop/mount smbfs credentials=/home/lucana/.smbcredentials,uid=1000 0 0

with that said i cant save it? ( this shows how new i am , or actually the title shows how new i am )

it states:
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

how do i sudo or change to root without losing my info ?

---

### Post by nick_h on 2008-04-05
Edit the file with:
```
gksudo gedit /etc/fstab
```

---

