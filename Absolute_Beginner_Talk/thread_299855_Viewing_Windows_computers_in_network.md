---
title: "Viewing Windows computers in network"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Dual Cortex on 2006-11-14
Hey guys, 
So I try accessing my windows network/workgroup - I go to Places>Network Servers>"Windows Network"> and this is what I see ("home" workgroup):

[[IMG]http://img205.imageshack.us/img205/4953/untitledjv3.th.png[/IMG]](http://img205.imageshack.us/my.php?image=untitledjv3.png)

Double clicking on it gives me the following error:
> Couldn't display "smb:///home",
The location is not a folder

Pressing F5 various times until the correct icon appears and then double clicking on that Icon allows me to see the computers on the network... but the same problem happens with the computers... same white icon appears and after F5'ing several times, the correct icon appears and double clicking on it allows me to see their shared folders (which I don't have to F5 my way through them).

Has anyone else experienced the same problem? How'd you fix it? (if you were able to do so)

Thanks in advance.

---

### Post by hollaburoo on 2006-11-14
well that just looks wierd.... there should never be 3 slashes like that "smb///home/"  Anyway, see if you can access the computer at all.  Open up firefox and just type smb://ip-Adress-Of-Your-Windows-Computer/, so something like smb://192.168.1.109/, if your computer is connected right you should see all shared Windows folders.

---

### Post by dbott67 on 2006-11-14
A few things to verify:

1. Make sure you have samba, smbfs and smbclient installed

Run the command smbtree and post the output here:
```
dbott@thedrake:~$ smbtree
Password:
MSHOME
        \\THEDRAKE                      thedrake server (Samba, Ubuntu)
                \\THEDRAKE\print$               Printer Drivers
                \\THEDRAKE\dbott-P4
                \\THEDRAKE\IPC$                 IPC Service (thedrake server (Samba, Ubuntu))
                \\THEDRAKE\ADMIN$               IPC Service (thedrake server (Samba, Ubuntu))
        \\DAPPER                        dapper server (Samba, Ubuntu)
                \\DAPPER\print$                 Printer Drivers
                \\DAPPER\ndis
                \\DAPPER\IPC$                   IPC Service (dapper server (Samba, Ubuntu))
                \\DAPPER\ADMIN$                 IPC Service (dapper server (Samba, Ubuntu))

```

Also, some issues arise because of the way SMB shares "announce" themselves to the network.  Generally, connecting via IP address works properly, but browsing by 'computer name' can occasionally fail.  Windows uses WINS service to allow users to browse by computer name (also known in Windows-speak as Netbios name).  WINS binds the computer name to the IP address.  For the most part, this has been superceded by DNS, which binds the fully-qualified domain name to the IP address. The problem is that DNS resolution requires that:

a) You're running a DNS server
b) Each client is registered in the DNS server

The problem here is that most people don't run their own DNS server and if you have any Windows computers on the network (or Samba shares), you really should have a WINS server or 'winbind' installed.

There is a package in the repositories called 'winbind' that will allow you to browse by computer name.

This info is provided by 'featherking' from [this thread]("http://www.ubuntuforums.org/showthread.php?t=288022"): 

```
sudo gedit /etc/nsswitch.conf
```

find this line (it may not be exactly that)

```
hosts:          files dns mdns
```

and add wins, so now it looks like

```
hosts:          files dns mdns wins
```

then install winbind
```

sudo apt-get install winbind
```

Now trying connecting to "Places->Network Servers".

-Dave

---

### Post by la3875 on 2006-11-20
I have a similar question. I have kubuntu running as master in a dual-boot set up with XP as the slave. I followed the grub set up and at boot I hit escape to access the Linux side. This has kept harmony in the household with the other users and only added about 15 extra second to their windows boot time. 

My newbie question is, how can I or is it possible view and read the windows shared folders from the other drive in the same computer? I have already installed the NTFS reader so I can see my windows files.

Thanks in advance!

---

### Post by la3875 on 2006-11-20
OK. Showing my newbie stripes now... I installed samba, smbfs and smbclient and now I can access the shares on the XP drive. 

If this success keeps up I'll dump M$ for good!!!:p

---

### Post by rccharles on 2006-11-21
> **la3875 said:**
> I have a similar question. I have kubuntu running as master in a dual-boot set up with XP as the slave. I followed the grub set up and at boot I hit escape to access the Linux side. This has kept harmony in the household with the other users and only added about 15 extra second to their windows boot time. 

My newbie question is, how can I or is it possible view and read the windows shared folders from the other drive in the same computer? I have already installed the NTFS reader so I can see my windows files.

Thanks in advance!

This is really a different question: howto mount a NTFS or FAT partition

Here is one write-up:

[http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/)

To see the list of partitions on a second HD, try:

sudo fdisk -l /dev/hdb

where /dev/hdb is the name of the disk.

Robert

---

### Post by la3875 on 2006-11-21
Robert, Thanks for the link. As I mentioned I am operating in a dual-boot set up with Ubuntu and Windows on separate IDE drives and it works beautifully. All the best!

---

### Post by rccharles on 2006-11-23
> **la3875 said:**
> Robert, Thanks for the link. As I mentioned I am operating in a dual-boot set up with Ubuntu and Windows on separate IDE drives and it works beautifully. All the best!
Thanks for your comment.

You can make the mount happen at boot time by:


Here is a quick rundown on mounting a NTFS partition.

Start a terminal session, by:
Applications > Accessories > Terminal


To find the name of the partition, do:
sudo fdisk -l
# note, the l is the lower case letter l.

You need to make a directory used in mounting the partition or use one you have
sudo mkdir /media/windows

Here is one way of editing,
sudo nano /etc/fstab

You need to edit /etc/fstab
and add or change the line
/dev/hda5 /media/windows ntfs nls=utf8,umask=0222 0 0

Change /dev/hda5 as needed. If you already have a mount, insert or change nls and umask.


now, either reboot or issue the command

sudo mount -a

---------

This web site will show you how to make the NTFS partition read/read. It will also give you more info on the commands I used above. I do not know if this is the best way to make the NTFS partition read/write and all the read/write drivers are in BETA.

[http://www.arsgeek.com/?p=675](http://www.arsgeek.com/?p=675)


Remember, this is BETA software!!!

Robert

---

### Post by BLTicklemonster on 2007-01-09
Weeeee!!!!!


```
bill@bill-desktop:~$ smbtree
Password: 
Error connecting to 172.16.24.1 (Connection refused)
cli_start_connection: failed to connect to 172.16.24.1<20> (172.16.24.1)
Error connecting to 172.16.24.1 (Connection refused)
cli_start_connection: failed to connect to BILL-DESKTOP<20> (172.16.24.1)
```


now what?

---

### Post by dbott67 on 2007-01-09
Are you running a firewall on the computer?

Depending on the OS, you can try the following:

Ubuntu:
```
dbott@thedrake:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

If 172.16.24.1 is a Windows machine, open the Network Connections and see if the Windows firewall is enabled (or if you have Sygate, ZoneAlarm, Norton, etc. installed).

-Dave

---

### Post by BLTicklemonster on 2007-01-09
I have no idea what that ip address is. It's not windows, and it's not my linux box!

I haven't even set up networking yet, as it's always a mystery to me how it's done in linux. 

I swear, look at all the threads on how to do it. They're all different.

---

### Post by carib909 on 2008-06-23
I am having a similar issue: Here are the results of smbtree command.

evan@ubuntu:~$ smbtree
Password: 
WORKGROUP
	\\UBUNTU         		ubuntu server (Samba, Ubuntu)
Error connecting to 63.251.179.13 (Connection refused)
cli_start_connection: failed to connect to UBUNTU<20> (63.251.179.13). Error NT_STATUS_CONNECTION_REFUSED
CHORDS
	\\STUDIOTWO      		
Error connecting to 8.15.7.117 (Connection refused)
cli_start_connection: failed to connect to STUDIOTWO<20> (8.15.7.117). Error NT_STATUS_CONNECTION_REFUSED
	\\GATEWAYLAPTOP  		
Error connecting to 8.15.7.117 (Connection refused)
cli_start_connection: failed to connect to GATEWAYLAPTOP<20> (8.15.7.117). Error NT_STATUS_CONNECTION_REFUSED
	\\BADMAN-PC      		
Error connecting to 8.15.7.117 (Connection refused)
cli_start_connection: failed to connect to BADMAN-PC<20> (8.15.7.117). Error NT_STATUS_CONNECTION_REFUSED
evan@ubuntu:~$ 







I> **hollaburoo said:**
> well that just looks wierd.... there should never be 3 slashes like that "smb///home/"  Anyway, see if you can access the computer at all.  Open up firefox and just type smb://ip-Adress-Of-Your-Windows-Computer/, so something like smb://192.168.1.109/, if your computer is connected right you should see all shared Windows folders.

---

