---
title: "Accessing Vista shares with Ubuntu"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by bullet ballet on 2007-03-01
I'm fairly new to Ubuntu here.  I've basically just set up a second desktop in my place and have put Ubuntu on it.  I want to be able to view my shared folders of my Vista PC via this Ubuntu computer.

I've installed Samba and have toiled through some aggravating problems and now I can actually see my Vista box via Nautilus.  However, the first time I try and access the workgroup or the box or any folder it returns the message:

The location could not be displayed.

I have to try again or refresh to gain further access.  It's pretty annoying, but not a major concern.  The real problem is that when I try and access my Vista box I always get a login prompt even though I don't have Password Protected Sharing enabled.  I can access my roommate's computer just fine with no authentication necessary.  But mine pops up a box asking for User, Domain, and Pass.  I've tried authenticating with my windows account but that didn't work.  I created an account and tried that and it didn't work either.  I'm thinking it's a problem between Ubuntu and Vista as when I try to access XP shares there is no problem.  Can anyone point me in the right direction or provide a clue as to what the heck is going on?  :confused: 

I should add that I can access my Ubuntu shares from Vista with absolutely no problems.

---

### Post by z600 on 2007-03-03
You should be able to access the Vista share through a mount:

 sudo mount -t smbfs -o username=[your windows user name],password=[your windows user's password] [Windows share] [Ubuntu mount directory]

eg: sudo mount -t smbfs -o username=james,password=bond //FileServer/Files /home/james/shares/FileServer

Looks like Nautilus has a problem accessing Vista shares. Vista seems to have changed the way it shares files with non-windows clients! ;)

Hope this helps.

---

### Post by postalservice14 on 2007-03-22
That Worked!!!! Thank you so much, I have had so much trouble trying to access my Vista Box.

Thanks,

John

---

### Post by bharris on 2007-03-30
Worked for me as well.  What is the syntax to get it to automount in fstab?  Thanks!

---

### Post by dsula on 2007-04-11
This only workes partially for me. When I mount the vista share all of the files are shown to be owned by root. Therefore I can't write any of the files on the vista share with my ubuntu user login. I have to login as root (on ubuntu) to be able to change files on the vista share. Any thought?

---

### Post by caish5 on 2007-04-16
When i try this i get...

> 
caish5@GigaDuo:~$ sudo mount -t smbfs -o username=NetworkUser,password=network //quark/andy /media/APD
mount: wrong fs type, bad option, bad superblock on //quark/andy,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



Any ideas?

---

### Post by somafm on 2007-04-16
A note on how I mount my Windows shares via fstab (so they mount on startup):

```
sudo gedit /etc/fstab
```

Type this line at the bottom of the fstab, and save. *(Note my username and password are both 'defaults'. This is what you use when there is no username/password required, and the folder is available for all to see. If you have a username/password you can just change those to match)*:

```
//192.168.1.2/folder /mnt/folder smbfs username=defaults,password=defaults 0 0
```

- **//192.168.1.2/folder** is the lan IP and shared folder of the windows machine, you can also use a hostname instead of the IP address.
- **/mnt/folder** is where I decided to mount it on the Ubuntu machine
- **smbfs** is the file system (samba fs)

You can also set up samba credentials to hide your windows passwords, considering /etc/fstab is viewable by all users: _[Click to learn how]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")_

Now that you're done, you can mount the folder live so you don't have to reboot:
```
sudo mount -a
```

When mounted, there will be a mount icon on the desktop. You can remove these mount icons from the desktop if they are annoying:
```
gconf-editor
```
Then goto apps>nautilus>desktop, and uncheck Volumes Visible

---

### Post by TalioGladius on 2007-09-26
> **caish5 said:**
> When i try this i get...



Any ideas?I get the same thing...what am I missing?

---

### Post by TalioGladius on 2007-09-26
Nevermind.  Installing smbfs and smbclient would help.  duh....

---

### Post by sesquipedalian101 on 2007-11-05
> **dsula said:**
> This only workes partially for me. When I mount the vista share all of the files are shown to be owned by root. Therefore I can't write any of the files on the vista share with my ubuntu user login. I have to login as root (on ubuntu) to be able to change files on the vista share. Any thought?

Just went through this problem -- with help from this page -- so here is a possible solution:

Add a ',uid={your_user_id},gid={your_group_id}' right after the 'username={your_user_name}' and/or the ',password={your_password}' in the original mount command.   That way your non-privileged (id est: non-root) user will "own" the mount once it is complete and should have the same access that root currently has when you are mounting without the 'uid=' and/or 'gid=' parameters.  

To plagerize the original examples above:

sudo mount -t smbfs -o username={your_windows_user_name}[,password={your_windows_user's_password}][,uid={your_local_user_name}][,gid={your_local_group_ID}] [Windows share] [Ubuntu mount directory]

eg: sudo mount -t smbfs -o username=james,password=licensed-to-kill,uid=bond,gid=MI6 //FileServer/Files /home/james/shares/FileServer


Good Luck
-101-

---

### Post by goginot on 2007-12-14
> **caish5 said:**
> When i try this i get...



Any ideas?

you should try username and password that you use to log on to vista
in regular way and not "username=NetworkUser,password=network" 
(which you probably defined for shared folder accessing )

---

### Post by chudman on 2008-03-13
> **somafm said:**
> A note on how I mount my Windows shares via fstab (so they mount on startup):

You can also set up samba credentials to hide your windows passwords, considering /etc/fstab is viewable by all users: _[Click to learn how]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")_


I've just followed the directions from the ubuntuguide.org website quoted above exactly (except I like to have my mount point at /mnt/SHARE rather than /media/SHARE).  

The problem is that upon `mount -a` I get a prompt for the password.  Once I enter the password there is no problem.  However, I want this to happed automatically and when I reboot it does not get mounted automatically either.  

The share I'm trying to connect to is //192.168.x.x/d$ and that machine is running Vista Ultimate.  Is there some problem or change in Vista that causes this to not work properly?  I've checked the spelling in my /ect/fstab and /root/.smblogin file, but cannot find anything that suggests I screwed up.  Suggestions?  I would really like this share to get mounted without my intervention.

---

### Post by chudman on 2008-03-13
Please disregard my last post guys/gals.  I did in fact make an error in my /root/.smblogin file.  I had passwork=my_password instead of password=my_password.  DUH!!  That's what I get for trying to be productive at 3am.  It works great now!

---

