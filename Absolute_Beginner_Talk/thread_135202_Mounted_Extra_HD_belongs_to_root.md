---
title: "Mounted Extra HD belongs to root?"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by TrevorNet on 2006-02-23
I've made my way through the process of adding and mounting a second hard drive. I can access it through the mount point of mango. The intended purpose for this drive is to act as a file dump for our local network. When I try to fit the folder from my XP computer, I find myself at a log-in prompt. Using my Ubuntu user/pass, nothing happens. When I check the permissions of the mango (mounted HD) folder, I see that it belongs to "root". I've tried transfering the ownership to myself through the following terminal commands.

sudo chown trevor:trevor mango
chown trevor mango
sudo chown trevor:trevor /mango
sudo chown -R trevor:trevor /mango

But nothing happens. The folder still belongs to root. Therefore, I have not been able to pass along "write" permissions to anyone as the check-boxes are disabled. Any suggestions?

The folder has been "Shared" as:
Path : /mango
Share With : SMB
Name: MangoDrop
Allow browsing folder is checked.
WINS are not being used.

I simply need a file server that can play host to WinXP, Mac OS X, and Ubuntu. (I may try to latch my PClinuxOS crap-top to the network as well, but that is neither here nor there.)

Cheers!

---

### Post by pbaehr on 2006-02-23
I can half help you. I'm sure someone will come along with the details soon after but I'm at work so I don't have access to my configuration files to give you examples.

You can't set the permissions of a mounted drive with chown or chmod. It has to be done when the drive is mounted (either using 'mount' or in '/etc/fstab').

Sorry I can't provide the proper config, but I think that's your problem.

---

### Post by patrick295767 on 2006-02-23
and, chmod 777 /dev/hdc working ?

---

### Post by Iowan on 2006-02-23
You may be able to change the ownership  via the share definition in Samba.

---

### Post by TrevorNet on 2006-02-23
Thanks all. I'm not sure when/how the mount changed permissions and ownership, but it has. \\:D/  I've been able to set it as the network storage facility using Samba as well.

This Ubuntu creature is fantastic!

---

### Post by Sutekh on 2006-02-23
You will need to paste the contents of your /etc/fstab here so we can see how you have mounted the shared HD.  

I believe it will come down to using the flags **uid** and **gid** in the mount option for the shared HD.

[Just Linux - Mounting smbfs Shares Permanently Help File]("http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html")

You should scroll down the section **Providing Security**

> Providing Read/Write Access to the Share

Another problem with mounting the Windows share as shown in the /etc/fstab file above is that only the root user would have read/write access to the share. All other users would have read only access to it. If you wanted read/write access to it for yourself, you need to specify your userid or groupid. That would change the line in /etc/fstab to look like this:

//servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/. smbpasswd,**uid=mylinuxusername,gid=mylinuxgroupname** 0 0

Whatever user and or group you specified in the line would have read/write access to the mounted share. You can use either the user or group name or the user or group numerical ID. Either should work.

If you had several users you wanted to have read/write access to it, create a group and add those users to the group. Then specify just that groupid in the /etc/fstab file. You wouldn't need to specify a userid. The line in etc/fstab would look like this:

//servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/. smbpasswd,**gid=sambausersgroup** 0 0


You would need to identify your user's **uid** using the command[CODE]id/[CODE] and substituting that value in.  Usually the first user of the system is uid=1000.

---

