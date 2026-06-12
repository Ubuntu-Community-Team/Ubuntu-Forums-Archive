---
title: "Networking"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by jtx472 on 2007-03-09
I can access shared files on my other computers from UBUNTU.  I cannot access UBUNTU shared files on my other computers.  When I map network drive in Windows XP Ubuntu shows up but none of the shared files that I have set up.  Thanks for any help.

---

### Post by tonyr1988 on 2007-03-09
Have you tried setting up your Ubuntu shared folders using Samba?

[https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba)

---

### Post by dstew on 2007-03-09
You may need to add a driver to windows in order for it to read ext3 (linux style) file systems. The driver system is called ext2ifs. Get it from this web site:
[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm]("http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm")

p.s. Actually, I think tonyr is right, because it is a networked share. My comment holds if windows and linux are on the same disk.

---

### Post by lamalex on 2007-03-09
this is a great howto

[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+peer+howto]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+peer+howto")

---

### Post by jtx472 on 2007-03-09
Thanks all for your help.  I did manage to install Samba but I don't really know how to use it.  And the last suggestion just lost me completely.  Since this is my first day using Ubuntu I think I'll just familiarize myself with it for a while before I worry about networking.  If I really need to access a file on another computer it''s just a matter of going down to the basement.:)

---

### Post by lamalex on 2007-03-09
the howto through you off? do you have aim? if youve got a minute I'd be happy to help you set up samba. if youve got more than one computer in the house its most def worth setting up.

---

### Post by Malac on 2007-03-09
Samba Server isn't installed automatically "out-of-the-box" but it will be installed if you right click on  a folder and choose "Share folder".

You need to make sure that in /etc/samba/smb.conf the network name is the same as your Windows machine. And it makes life easier if there is a username and password combination common to both machines.

---

### Post by dstew on 2007-03-10
One easy way to use Samba is to use the Samba client program (smbclient). It works like ftp. See the smbclient man pages to see how to use it. Briefly, you can connect to a shared folder by issuing the smbclient command in the terminal:

smbclient //server/share

You will be prompted for a password, but if the share is not password protected, just press enter. Then, you get the Samba client prompt 

smb: \>


To see files, enter dir at the prompt. It should work, if in fact Samba is installed correctly.

---

