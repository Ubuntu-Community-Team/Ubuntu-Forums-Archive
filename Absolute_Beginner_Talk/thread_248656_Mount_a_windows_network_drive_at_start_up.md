---
title: "Mount a windows network drive at start up"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Traiger on 2006-09-01
I'm trying to get this Linux box to mount a windows network drive at start up and so far I have failed.  Can anyone tell me how to do this please?

---

### Post by jorn on 2006-09-01
Take a look at this and come back for further instructions:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by benfindlay on 2006-09-01
Mine seem to do it if you browse via networks for the drive in question, then right click on it and choose "Make Link". It puts an icon on your desktop which is there until I chhose to unmount it. If anyone knows the code behind it could they post it please? Would be ace to know for distros that arent as user friendly as ubuntu is!

Hope this helps

---

### Post by john_markh on 2006-09-01
1.First of all, you will need to install SAMBA to access windows network drives.
2. Create mount directory
```
sudo mkdir /media/sharename
```
3. Create smbcredentials
```
gksudo gedit /root/.smbcredentials
```
4. Insert the following lines into the new file 
```
username=myusername
password=mypassword
```
Replace myusername and mypassword network computer's username and password
5. Save the edited file
6. Change access premitions to the smbcredentials
```
sudo chmod 700 /root/.smbcredentials
```
7. Add mount to fstab
```
gksudo gedit /etc/fstab
```
8. Append the following line at the end of file 
```
//192.168.0.1/linux    /media/sharename smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0
```
Replace "192.168.0.1" with network computer's IP address and "linux" with shared folder's name
9. Save the file and remount /etc/fstab
```
sudo mount -a
```

---

### Post by jorn on 2006-09-01
Forget it, I'm not aware of what I am doing.

---

### Post by benfindlay on 2006-09-01
do you need samba server installed to do it? Doesn't the client take care of it for you?

---

### Post by benfindlay on 2006-09-01
Sorry, just realised, its not Make link, but "Connect to this Server"

Apologies for the mistake!

---

### Post by Traiger on 2006-09-04
John_Markh:

I can mount the drive with 

sudo mount //172.16.1.2/COMPANYDATA -o username=paul.hodgson,password=MyP455W0rD 

and I basically just need to ensure that this line is run when ever this box is booted.

I'm assuming that there is a bootup script somewhere for me to edit, any idea where?

---

### Post by Traiger on 2006-09-04
sudo crontab -e
* * * * 1 mount //172.16.1.2/COMPANYDATA -o username=john.smith,password=m1n3

works like a charm.  Although I feel like I'm cheating somewhat.

---

