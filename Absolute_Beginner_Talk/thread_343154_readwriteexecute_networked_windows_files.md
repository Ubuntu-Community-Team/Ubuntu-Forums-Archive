---
title: "read/write/execute networked windows files"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Shamus57 on 2007-01-21
Hello,

I am very new to *nix, and my experience with Ubuntu (Dapper Drake) has been very positive.  

However, I am having difficulty writing/executing files over my LAN with my windows 2k computers.  I have three computers (2 win 2k and 1 ubuntu) hooked up to a lynksis router, which is connected to my cable modem.  DHCP is enabled and dynamic IPs are assigned.

Computer #1 (win 2k) IP address: 192.168.1.128 (Drive E is shared) 
Computer #2 (win 2k) IP address: 192.168.1.101 (Drive D is shared)
Computer #3 (Ubuntu) IP address: 192.168.1.121

Windows network name = WORKGROUP

When I use Places--> Network Servers (I guess the program it is using is called Nautilus 2.14.3) allows me to see both computer #1 and #2 and see/read the shared drives.  However, when I try to copy or modify the shared drives from Ubuntu, it says I don't have permission.

How do I change the permissions for the shared drives? 

First of all, I ASSUME I am using Samba to connect through the network to the windows computers, but I'm not sure.  Does Nautalus use Samba to browse the network?  

I tried chmod 777 /smb/Computer #1/#2 (and variants with the shared drive names), but that didn't work.

I also tried gedit /etc/samba/smb.conf and changed the write expressions to "yes", but that didn't work either.

Any help would be appreciated.

Thanks,

-S 

P.S.  Sorry if this is a double post, I thought I hit submit only once.

---

### Post by riven0 on 2007-01-22
Well, [this post]("http://ubuntuforums.org/showthread.php?t=202605&highlight=windows+files+permissions") says to do **sudo chmod 0777 /smb/Computer**  <-- replace with your computer names.

Then try restarting samba:

> sudo /etc/init.d/samba stop && sudo /etc/init.d/samba start

Otherwise, how about doing gksudo nautilus and editing the file from there? Does that work?

---

### Post by Shamus57 on 2007-01-22
Thanks for the reply.  I tried the following command, substituting the computer name for "Computer." 

> sudo chmod 0777 /smb/Computer

Unfortunatly, it gave me the following reply:

[B]chmod: cannot access `/smb/Computer1': No such file or directory
[/B]

As samaba appears to be in the /etc directory, I attempted:

sudo chmod 0777 /etc/samba/computer1

but that also resulted in the above reply.
I went into Nautilus and looked at the properties for computer #1.  it says:

Name: Computer1
Size: unknown
Location: smb://workgroup
MIME type: ap"plication/x-desktop

In the "Link" tabl of the Nautilus properties for computer 1, it says:
URL:  smb://computer1/

Any other suggestions are greatly appreciated.

Thanks!

---

### Post by Shamus57 on 2007-01-24
/bump!

---

### Post by Shamus57 on 2007-01-25
wow.  I found the answer.  I can't believe it.  I'm totally stoked.

The problem was I needed to mount the windows shared folder/drive.  

I tried the command:

smbmount //computer1/DriveE /home/ubuntu/mp3 -o username=computer1,password=admin

where, //computer1/driveE is the shared folder on my win2k machine, and /home/ubuntu/mp3 is the place where I want to mount the shared folder. In this case, it is the home folder under my login for my ubuntu box.  I know, not very creative having a login of "ubuntu" but I'm new.  Also, in windows 2k, I turned on users/passwords and created a login and password of computer 1 and admin (as reflected above in the portion of the command "username=computer1,password=admin).

Unfortunatly, I was getting the following error:

smbmnt must be installed suid root for direct user mounts (1000,1000)

OMGWTF does that mean?!?!

I really don't know for sure, but I think it had to do with the permissions set for the mount point, in this case, /home/ubuntu/mp3     I think the permissions needed to be altered. 

I found the following command to change the permissions on the /home/ubuntu/mp3 folder.  I used:

chmod u+s /home/ubuntu/mp3

When I typed it in, ubuntu didn't freak out with a #%$%load of errors, so I was encouraged.

When I tried the smbmount //computer1/DriveE /home/ubuntu/mp3 -o username=computer1,password=admin

command again, it worked.  No errors or anything.  I could use Nautalus and read/write/execute the files.

I hope this helps someone.

---

