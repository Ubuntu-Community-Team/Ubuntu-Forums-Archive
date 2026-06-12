---
title: "networking 2 + comps to router?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-09-04
I have three computers connected to a linksys router. 
Comp 1 - XP only
Comp 2 - Edgy + Win98
Comp 3 - Ubuntu Studio + XP
All three connect to the internet fine with the router.
What I want to do is be able to share files with each other & backup files from one to another etc. I assume it can be done but Is this something that is simple or complicated?
Any one have any recommendations for someone who has absolutely no clue where to begin?

---

### Post by southernman on 2007-09-04
To get you started, look into samba.

[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto") is a nice start, but take some time to do a little of your own research to make sure it will best suit your needs.

HTH's

---

### Post by VraiChevalier on 2007-09-04
A related question:

I am on the east coast and I want to set up some folder shares with my son in Denver, CO.
Is SAMBA the best way to go or are there other options I should investigate?

I have done it using Microsoft Windows XP but I would much, much rather do it using Ubuntu.

I too have several computers (4 to be precise) accessing the internet through one router (Linksys WRT54GL) so I will be watching this thread closely.

---

### Post by dwhitney67 on 2007-09-04
> **VraiChevalier said:**
> A related question:

I am on the east coast and I want to set up some folder shares with my son in Denver, CO.
Is SAMBA the best way to go or are there other options I should investigate?

I have done it using Microsoft Windows XP but I would much, much rather do it using Ubuntu.

I too have several computers (4 to be precise) accessing the internet through one router (Linksys WRT54GL) so I will be watching this thread closely.
Install (if you have not done already) the SSHD (secure shell daemon) to run on your Ubuntu system.  Then you son can connect remotely to your Linux box.  Mount any shared folders that you have on you Windoze boxes onto your Linux box using Samba.

You will need to configure your Linksys router to allow SSH traffic to pass from your router to your Linux box.  The default port used by SSH is 22, but that can be changed.

---

### Post by jombeewoof on 2007-09-04
> **VraiChevalier said:**
> A related question:

I am on the east coast and I want to set up some folder shares with my son in Denver, CO.
Is SAMBA the best way to go or are there other options I should investigate?

I have done it using Microsoft Windows XP but I would much, much rather do it using Ubuntu.

I too have several computers (4 to be precise) accessing the internet through one router (Linksys WRT54GL) so I will be watching this thread closely.

I would use FTP. fairly simple config with either linux or windows clients and servers. 
set up the ports to forward correctly, and the accounts to map to the correct folders and you're all set.

---

### Post by VraiChevalier on 2007-09-04
Thank you dwhitney67!

If I move the files/folders to my Linux box would it still be the same basic procedure? Son uses Windows, I try to not!  (I foretell some study in my near future)

---

### Post by dwhitney67 on 2007-09-05
> **jombeewoof said:**
> I would use FTP. fairly simple config with either linux or windows clients and servers. 
set up the ports to forward correctly, and the accounts to map to the correct folders and you're all set.
FTP is a poor choice.  It is not secure.  A "man in the middle" could easily see the data streaming by.  Now if you are referring to SFTP (SSH FTP) then that is ok.  But regular FTP... that's a no-no.

---

### Post by dwhitney67 on 2007-09-05
> **VraiChevalier said:**
> Thank you dwhitney67!

If I move the files/folders to my Linux box would it still be the same basic procedure? Son uses Windows, I try to not!  (I foretell some study in my near future)

SSH is your best option.  Whether you put all of the files on your Linux box or leave them on a Windows box, that is up to you.  Like I stated earlier, you can use Samba to mount Windows folders onto your Linux box.  Your son wouldn't know the difference.

Anyhow, your son, being that he runs Windows, would need to install an SSH-client application.  When I used to run Windows, I obtained my SSH-client (for free!) from [SSH Comm Sec]("http://www.ssh.com/").  I do not know if they still offer that non-commercial version.

---

### Post by morningboat on 2007-09-05
I would recommend FTP over SSH and Samba. 
SSH is a good choice but it suffers from: 1, free client support is not very good in windows. 2, not sophisticated in dealing with ASCII files due to different line endings. 3, file name encoding nightmare if you are using CJK system. 4, suffer from execution attack.
FTP/TLS has same level of security as SSH while has better clients support. Hence suggested.
Samba is of much worse performance and security than FTP, harder to configure, and not as reliable. It can suffer similar problems as SSH client as well. Not recommended.

For configuring the FTP clients and servers in linux or windows, you can refer to the following two threads:
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)
[http://ubuntuforums.org/showthread.php?t=473013](http://ubuntuforums.org/showthread.php?t=473013)

---

### Post by dwhitney67 on 2007-09-05
> **morningboat said:**
> I would recommend FTP over SSH and Samba. 
SSH is a good choice but it suffers from: 1, free client support is not very good in windows. 2, not sophisticated in dealing with ASCII files due to different line endings. 3, file name encoding nightmare if you are using CJK system. 4, suffer from execution attack.
FTP/TLS has same level of security as SSH while has better clients support. Hence suggested.
Samba is of much worse performance and security than FTP, harder to configure, and not as reliable. It can suffer similar problems as SSH client as well. Not recommended.

For configuring the FTP clients and servers in linux or windows, you can refer to the following two threads:
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)
[http://ubuntuforums.org/showthread.php?t=473013](http://ubuntuforums.org/showthread.php?t=473013)

Complete rubbish.

Who uses SSH?.... well for starters, NSA, FBI, DHS, DISA, etc.

Clients are available for Windows.  I have one... it is available from [http://www.SSH.com](http://www.SSH.com)

Here's some more support for SSH:

[I]Security problems

The original FTP specification is an inherently insecure method of transferring files because there is no method specified for transferring data in an encrypted fashion. This means that under most network configurations, user names, passwords, FTP commands and transferred files can be "sniffed" or viewed by anyone on the same network using a packet sniffer. This is a problem common to many Internet protocol specifications written prior to the creation of SSL such as HTTP, SMTP and Telnet. The common solution to this problem is to use either SFTP (SSH File Transfer Protocol), or FTPS (FTP over SSL), which adds SSL or TLS encryption to FTP as specified in RFC 4217.  -- source: [wikipedia]("http://en.wikipedia.org/wiki/File_Transfer_Protocol")[/I]

[edit]

---

### Post by morningboat on 2007-09-06
Please mind your words...  Nice reference from wiki, and you should read my recommends more carefully. It actually mentioned the wiki point on security issues. 
> FTP/TLS has same level of security as SSH while has better clients support. Hence suggested.
I have confidence that I have better understanding for these protocols, hence I made some suggestion. You can choose your preference anyway.

---

### Post by str8line on 2007-09-06
For sharing over the internet like you suggested using a VPN (Virtual Private Network) is the most secure way to do that.  A product that is free and not dependent upon any OS is Hamachi from Logmeinrescue.com.  There is a fine linux port of the original software in the ubuntu repos or you can compile it directly from the source at [www.logmeinrescue.com]("http://www.logmeinrescue.com").  There is a free and a pro version available and both work splendidly for file transfer and direct connections.  I use it to work on remote pcs regardless of the OS that the remote pc is running and it works beautifully.

As for the original question posted in this thread, the mixture of OSes and file systems would be the biggest challenge.  What I would suggest is setup one of the three machines to act as a host computer running FAT32 (ie the Win98 machine) and drop all of your networked files onto that pc for all others to access.  That way all would be able to share equally without issue as the Win98 OS will not read NTFS drives on your XP machines at all.

---

