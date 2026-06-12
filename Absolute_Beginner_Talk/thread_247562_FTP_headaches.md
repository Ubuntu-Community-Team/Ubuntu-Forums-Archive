---
title: "FTP headaches"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by George_S on 2006-08-30
I've been trying to connect to our FTP server (Windows 2003) for the past couple of days, but without any luck.

I tried using KFTPGrabber, as well as Nautilus to access the server, but in both cases got the same message back:

"The folder contents could not be displayed."

I tired both passive and active modes. No luck.

Then, thinking that perhaps the port is closed, I fired up the terminal and got this result:

```
george@george-desktop:~$ telnet 66.223.111.114 21
Trying 66.223.111.114...
Connected to 66.223.111.114.
Escape character is '^]'.
220 Microsoft FTP Service
```

This confirms that the server works okay. Also, since my system is dual boot, if I am in Windows XP Pro, and use WS_FTP client, I can access my server without any problems.

Any suggestions on this?

Thanks,
The Confused One

---

### Post by Abstract on 2006-08-30
I am not too sure on how exactly FTP works but could it be because the filesystem is formatted to NTFS and by default Ubuntu cannot read that?

---

### Post by George_S on 2006-08-30
I am not sure if that is the reason or not. If it is, then I definitely have a problem #-o

---

### Post by Abstract on 2006-08-30
Well it is quite possibly the reason. Is the windows partition/drive formatted to NTFS or a FAT32 system?

If its NTFS I don't see that a FTP server would make it readable somehow and I'd bet it is a problem.

---

### Post by dlmmsu on 2006-08-30
From what I've read Unbuntu can only read an NTFS filesystem. Only FAT16, and FAT32 can be read/written to. Given that even if an NTFS filesystem is read only, you should still see it if is mounted properly.

Dennis

---

### Post by Abstract on 2006-08-30
Ah, you are infact right and I am wrong it would seem. There is still the issue that FTP isn't that good if you can't write.

---

### Post by George_S on 2006-08-30
That makes sense - at least read only should be possible.

However, I find it hard to believe that I am the first person trying to access Windows 2003 server from Ubuntu.

---

### Post by cwaldbieser on 2006-08-30
> **George_S said:**
> That makes sense - at least read only should be possible.

However, I find it hard to believe that I am the first person trying to access Windows 2003 server from Ubuntu.

I can FTP to Win2K and Win2K3 boxes from Ubuntu.  The FTP server is IIS 5 or 6.  I usually use command line FTP, but don't normally have a problem with any other graphical clients.

To clear up some points-- the FTP server provides the file information to the client and performs all the reading and writing, so it doesn't matter what the underlying filesystems are.

Remember that FTP uses 2 ports-- 20 and 21, so make sure both are open from Ubuntu (unless you installed a firewall, they should be).

Are you using anonymous FTP or are you using some sort of authentication?

---

### Post by George_S on 2006-08-30
I am using an FTP address in a form of an IP address, username,and password. I double and triple checked this, but it still doesn't work.

Also, I did not install any firewalls in Ubuntu.

---

### Post by djf on 2006-08-30
Here comes my wild guess:

I had problems with connections that timed out shortly after I had logged into an FTP server. Try switching extended passive off (epsv4 off). 

Don't ask me where that setting is in nautilus. I usually use command line clients. For testing you could use ftp in the terminal, after you've logged in type epsv4 off.

---

### Post by cwaldbieser on 2006-08-30
> **George_S said:**
> I am using an FTP address in a form of an IP address, username,and password. I double and triple checked this, but it still doesn't work.

Also, I did not install any firewalls in Ubuntu.

Do you mean something like
```

ftp://user:pwd@192.168.0.2

```

Are you able to connect from the interactive command line ftp client (when it prompts for a password)?

Can you connect if anonymous access is enabled on the server?

---

### Post by George_S on 2006-08-31
> **cwaldbieser said:**
> Do you mean something like
```

ftp://user:pwd@192.168.0.2

```

Are you able to connect from the interactive command line ftp client (when it prompts for a password)?

Can you connect if anonymous access is enabled on the server?
Yes, that's what I mean. However, I just tried to use the domain name instead of the IP address and it worked. So, it appears that the domain name works, yet the IP address for the same domain doesn't. Is this possible?

I did not try to enable an anonymous access.

---

### Post by cwaldbieser on 2006-08-31
> **George_S said:**
> Yes, that's what I mean. However, I just tried to use the domain name instead of the IP address and it worked. So, it appears that the domain name works, yet the IP address for the same domain doesn't. Is this possible?

I did not try to enable an anonymous access.

I would guess that nautilus is just not resolving the address correctly for some reason.

---

### Post by George_S on 2006-08-31
> **cwaldbieser said:**
> I would guess that nautilus is just not resolving the address correctly for some reason.
That must be the case. It drove me nuts.:confused: :-k :D 

Thanks for the input everyone.

---

