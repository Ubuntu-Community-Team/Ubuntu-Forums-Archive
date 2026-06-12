---
title: "Mount Windows Share at Boot"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by kklingerman on 2007-08-13
Hi,

  I would like to mount a windows share automatically when Ubuntu boots.  I've been able to mount the share manually, but as a newbie, I have no clue how to make it mount at boot.

   Ant insight would be appreciated.

---

### Post by felicity on 2007-08-13
The Ubuntu guide has directions for mounting a network share automatically on boot:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")
or
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access")

---

### Post by Alterax on 2007-08-13
Nothing to it, really.  First, install SMB/CIFS, which will cover the compatibility issues with newer versions of Windows.  This will get you what you need:

sudo apt-get install samba samba-common samba-client smbfs

create a mount point for the network share:

cd /media
sudo mkdir win-share
(Use whatever name you'd prefer for win-share, just be consistent as we go).

Next, you'll need to get the ip address of the windows box, the name of the share, and the username and password of a windows user that is allowed access to the share.

Now, edit the file system table (/etc/fstab) file to include it:

sudo gedit /etc/fstab

add the following lines, just making the changes for your particular setup.  In this case, I am using 192.168.0.5 for the windows server, the share name is myshare, the username is alterax and the password is 12345:

//192.168.0.5/myshare /media/win-share cifs username=alterax,password=12345,users,rw 0 0

---

### Post by kklingerman on 2007-08-13
Thanks.  I'll give this a try.  The share I am using seems to have an issue.  I can write new files to it, but trying to edit a file is causing an error.  Is there anything special I have to do in Ubuntu in relation to rights?  Here is the command I used to mount it:

mount -t cifs //server/share -o username=username,domain=domain,password=password /mnt/mydrive

Thanks for any additional insight.

---

