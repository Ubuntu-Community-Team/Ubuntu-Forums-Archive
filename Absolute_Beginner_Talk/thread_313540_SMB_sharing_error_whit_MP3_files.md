---
title: "SMB sharing error whit MP3 files"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by Roman78 on 2006-12-06
Hello there,

I have installed Ubuntu as a workstation. Now i still have a windhose machine where is stored some MP3 files. I can perfectly connect to the machine and browse to the directories. But when i want to play a MP3 file it won't play. When i copy the file to the machine it will play. So codecs are ok. What could be the problem? I also mounted the directory as a volume and tried it, but also no success.

Tnx

---

### Post by sonny on 2006-12-06
Well I surely need some more info about this... let me see if I understood correctly... in your windows machine you have a folder with mp3 files which you want to access from within your Ubuntu box, but files won't play through the network... you have mounted the folder in your ubuntu box... could you please paste the command you used to mount the folder?... There might be a problem there... also I've played mp3 files from my friend's machines without copying to my laptop... but I have to use totem in order to listen to them... perhaps you might want to try that... first you have to open totem, then drag and drop the files from the remote machine to totem's sidebar, totem will cache the files and then play them, the speed will depend on you networks performance.

---

### Post by Roman78 on 2006-12-06
Right. I also just tested video-files and that are also not playing.

I have mounted it with the Network Servers utility.

Totem says: 
```

Totem could not play 'smb://lindsay2/Beheer/DVD/Over The Hedge 2006/VIDEO_TS/VTS_01_1.VOB'. 

Could not read from resource.

```

Other programs does not give an error message. They just don't play it.

---

### Post by pete on 2006-12-06
You'll need to mount the remote Windows directory containing the files in the local filesystem on your Ubuntu machine.

This can be done on a one-time basis with the "mount" command, or you can add the remote dir to /etc/fstab if you want it to automatically mount on boot.

---

### Post by kelbizzle on 2006-12-06
I solved this following the directions **[here]("https://wiki.ubuntu.com/MountWindowsSharesPermanently")**. 

installed smbfs: 
```
sudo apt-get install smbfs
```

created a directory to mount it too:
```
sudo mkdir /media/mountname
```
then edit /etc/fstab:

```
mount //servername/sharename  /media/mountname  smbfs  username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

```
notice how I have "username-guest, password=" instead of just "guest". I wasn't working until I changed the line.

---

### Post by Roman78 on 2006-12-11
It wont mount. Is sais:

```

Usage: mount -V                 : print version
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

```

Is this an other version?

---

### Post by nerips on 2006-12-24
You're absolutely right. I'd be happy if someone could tell me how he managed to play mp3's on a  freshly installed ubuntu 6.10 from a read/write share (my files are located on an infrant readynas nv). Default access is read/write.
The mount command indicated as a solution gave an error.

---

