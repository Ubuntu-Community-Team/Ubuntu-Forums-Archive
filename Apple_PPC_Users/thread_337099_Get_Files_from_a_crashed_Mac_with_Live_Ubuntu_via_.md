---
title: "Get Files from a crashed Mac with Live Ubuntu via Samba"
date: 2007-01-12
forum: Apple PPC Users
---

### Post by antron on 2007-01-12
Boot the Ubuntu Live 6.1 disc by holding down c while booting.
You will need internet access to install samba
Test the internet with firefox (test google)

Now mount the drive.  You need to create a directory to mount it to
open Applications->Utilities->Terminal , type:
```
sudo mkdir /mnt/macos
```
Find the partition to mount, type:
```
sudo parted
```
then type
```
print
```
it will list all partitions with sizes
note down the number of the one you want, lets say it is 5
type:
```
quit
```
Then type:
```
sudo mount -t hfsplus /dev/hda5 /mnt/macos/
```
now:
```
sudo gedit /etc/samba/smb.conf
```
this will open an editor, scroll down to workgroup and change it to your windows workgroup
scroll down to 'invalid users = root' and comment it out by putting a # or ; on front of that line.
save and exit
type:
```
sudo smbpasswd -a root
```
enter a password

then type:
```
sudo passwd root
```
enter the same password, this step may not be neccessary

go to System -> Administration -> Shared Folders
turn off NFS and continue with samba on.  It will go get samba.  When it is done Add a Share in the opened window.  Click back to the root and choose the directory /mnt/macos , then close.

The mac harddrive will now show up in your windows workgroup.
When prompted for a user and password; enter 'root' and the password you used.

Don't try to copy too many files at once (thousands worked, hundreds of thousands crashed)
Now that you have your important files, you can install Ubuntu with the icon on the desktop!

---

