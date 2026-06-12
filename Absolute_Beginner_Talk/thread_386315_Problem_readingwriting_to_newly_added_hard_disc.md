---
title: "Problem reading/writing to newly added hard disc"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Rizlaw on 2007-03-16
I have read through most of the posts that talk about problems with adding new hard discs after Ubuntu has been installed, but they aren't helpful with my particular problem.

I am unable to read and write to a new SATA drive I added to my relatively new installation of Ubuntu 6.10.  After installing the new Seagate 750GB SATA drive, I did the following:

1. Opened a terminal window and ran "gparted" with the command "sudo gparted".
2. Created one massive 750GB partition and formatted it as an "ext3"  filesystem.
3. Checked to see what the new drive was called: "/dev/sdc".
4. Opened and edited "/etc/fstab" file (as 'sudo') and added the following line to the end of the file:

                      /dev/sdc1         /mnt/LinuxMusic         ext3         defaults         0         2

5. Performed a "mkdir" and added "/mnt/LinuxMusic" mount point folder to the file system.
6. Rebooted OS.

Inside the "LinuxMusic" folder there is a locked "lost+found" folder, which an error message tells me I do not have root permissions to view. In addition, when I try to copy files to this new drive, I get the error:

                            "Error while copying to '/mnt/LinuxMusic'
                            You do not have permssion to write to this folder."

Also, a right click inside "LinuxMusic" to create a text file, can not be done.

When I look at "Properties > Permissions" for "LinuxMusic" it shows, in light grey:

Owner: root,
     Folder access: "Create and delete files";
Group: root,
     Folder access:  "Access Files",
Others
     Folder access: "Access Files".

I can't change any of the above. Does anyone have any ideas what I did wrong? Thanks.

---

### Post by taurus on 2007-03-16
If you want to write to /mnt/LinuxMusic, you just need to change the ownership of it from root to whatever your login name is.  Assuming your login name is **john**, do

Applications -> Accessories -> Terminal
```
sudo chown -R **john**:**john** /mnt/LinuxMusic
ls -la /mnt
```

---

### Post by Rizlaw on 2007-03-16
> **taurus said:**
> If you want to write to /mnt/LinuxMusic, you just need to change the ownership of it from root to whatever your login name is.  Assuming your login name is **john**, do

Applications -> Accessories -> Terminal
```
sudo chown -R **john**:**john** /mnt/LinuxMusic
ls -la /mnt
```

I will try it, but I'm confused. Can you explain why, when adding a new drive, Linux isn't automatically setup to allow any user to read and write to the drive; or, at least the user who created the new drive using the "sudo" command? I thought that was what the line I added in "fstab" was supposed to accomplish with the "default" option.  Thanks again.

---

### Post by amd-64 on 2007-03-16
Basically, the default is that only the owner is allowed to mount and use the drive and the default owner is root. The chown command changes the ownership of the drive to another user. For more details, 
man fstab
man mount

---

### Post by JohnSilver on 2007-03-18
Hi, I have the exact same problem. I created an ext3 partition with gparted and added the line

```
UUID=d4370856-c4f1-4f9b-b3c5-5889364a066a /media/hda1	ext3	defaults	0	0
```

in /etc/fstab. I also did

```
sudo chown -R john:john /media/hda1
sudo chmod -R 777 /media/hda1 
```

to my mount point, but I still only have a lost+found folder in /media/hda1 and no write permissions.

Any ideas?

P.S. I've also tried using this line in /etc/fstab
```
/dev/hda1 /media/hda1	ext3	defaults	0	0
```

---

### Post by JohnSilver on 2007-03-18
Nevermind, the issue is resolved in my case.

The partition needs to be mounted when running 

```
sudo chown -R john:john /media/hda1
sudo chmod -R 777 /media/hda1
```

---

