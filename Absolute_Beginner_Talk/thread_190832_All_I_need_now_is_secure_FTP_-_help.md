---
title: "All I need now is secure FTP - help"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by millsy on 2006-06-06
I'm still fairly new to linux/ubuntu but I love it.  My goal is to set up a combined media server / web server / ftp server so that I can access all my stuff from anywhere and I've nearly got there. :p 

I've got my base ubuntu install with apache / PHP / MySQL, samba to share media content with my Windows XP box (sorry), vnc working fine at home and Twonky Media server.

At the moment, I'm using ProFTPD as my FTP server to allow me to access my website root and my media from remote locations (mainly from work).  The only extra thing I require now is SECURE FTP access.  My work wont open port 5900 for VNC connections or I would use that. :( 

I've read a little about OpenSSH and think this (or rather sftp) is what I probably need but I don't want to start messing about with my currently working box without really understanding what I'm doing. :confused: 

The questions I have are ...

1. Is anyone running a secure FTP server (or alternative) and could explain how to do it?
2. Is it as simple as installing OpenSSH through synaptics and configuring sftp and if so is there a howto on this?
3.  I get the feeling that sftp works through port 22 - is that correct?  If so, there could be problems getting work to open port 22 (21 is open already).

If I can get this working I will truly be in 'ubuntu heaven'

Looking forward to your replies.
Mark

---

### Post by graigsmith on 2006-06-06
> 2. Is it as simple as installing OpenSSH through synaptics and configuring sftp and if so is there a howto on this?

this was all i did and it worked.

---

### Post by millsy on 2006-06-06
great - thanks for the quick response.  Do you access the sftp server with a different protocol i.e. sftp://www....? Also, which port does it run on - 21 or 22?  (This is important as only port 21 is open through work).

Thanks

---

### Post by omirix on 2006-06-06
I just signed up on the Ubuntu forums to help you out here.

OpenSSH + sftp work together... I believe it doesn't even spawn a new port. All you will have to do is sftp in, and I believe it uses port 22 (default for SSH).

---

### Post by millsy on 2006-06-07
thanks very much!  I'll give it a try and speak to work about opening port 22.
Mark

---

### Post by millsy on 2006-06-07
Right - I've installed OpenSSH and I can sFTP in from the command line via loopback from my Ubuntu box by using the 'sftp' command - excellent.

It asks me for a password for my login and i presume that this is sent encrypted.  Is the actual transfer encrypted too?

Can you tell me where the configuration file is for sFTP / openssh.  I've tried searching my filesystem and I can't find it.  I just want to have a little play ...

Does the installation of OpenSSH install anything else useful apart from sftp support?

Which graphical FTP clients can I use?  Do all standard FTP clients support secure FTP transfers??

Nearly there ....

---

### Post by millsy on 2006-06-07
An update ...

[QUOTE=millsy]Which graphical FTP clients can I use?  Do all standard FTP clients support secure FTP transfers??[/QUOTE]

I've used Nautilus to log in from my ubuntu box via my external IP (via loopback) and tried using sftp://<username>@www.<website>.com.  It asks me for a password - fine, but instead of locking my access to the <username> home directory, it gave me access to my root filesystem.

Is this something to do with the fact that I use the root login to work on my box? (yes, I know I shouldn't but I'm a control freak)

If I sftp://<username>@www.<website>.com from the command line, it locks me to the home directory.

Thanks for your help

---

