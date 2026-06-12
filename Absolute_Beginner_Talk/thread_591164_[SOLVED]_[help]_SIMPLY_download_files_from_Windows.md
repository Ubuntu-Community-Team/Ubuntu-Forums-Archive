---
title: "[SOLVED] [help] SIMPLY download files from Windows server to Ubuntu Server (Without S"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Bl4deRunner on 2007-10-25
Hi,
Is there a SIMPLE way to access a file on a Windows server(192.168.1.1) from Ubuntu server?

Like:

**cp \\192.168.1.1\c$\myDir\myFile.zip /~/myTempDir/myFile.zip**

It's only required once, and I don't want to install software I otherwise don't need.
:confused:

---

### Post by stump138 on 2007-10-25
Tyr using your regular network browser from the system menu.  IIRC Samba is already installed and all you should have to do is authenticate a user account on the server. 
I can connect to Windows servers with no extra software installs from my Gutsy box with no issues.

---

### Post by kvonb on 2007-10-25
Open your file manager and type:

smb://192.168.1.1

into the address bar, you should see your other system.

If you don't have the address bar, only the icon bar, click on the writing pad and pencil icon on the top left there.

---

### Post by Bl4deRunner on 2007-10-25
I'm using Ubuntu SERVER, so there's only a CLI.

---

### Post by Bl4deRunner on 2007-10-27
[BUMP] is there no simple way using CLI to copy something from a windows server?
something like WGET?

---

### Post by Bl4deRunner on 2007-10-31
[BUMP] no way to download a file from a windows server through CLI?

---

### Post by volksman on 2007-10-31
you don't need samba...you need smbfs....just apt-get install smbfs and apt-get remove smbfs if you don't want it after...

then run something like:

mount -t smbfs //IP/sharename /media/<mountpoint>

Then copy away....

---

### Post by ByteJuggler on 2007-10-31
Yes there's several ways:

1.) Windows networking on Windows + Samba client on Linux (use "smbmount" to mount the samba share so you can use normal filesystem commands e.g. "cp", or use "smbget" which is a wget like utility for Samba.)  Type "smb" in the command prompt and press tab a couple of times to get a list of all commands that start with "smb".  Use the "man" command to get more information about a particular command, e.g. "man smbget"
2.) IIS FTP server + ftp client on Linux.  
3.) IIS Web server + wget on linux
4.) SSH Client tools on Windows + SSH server on linux (use "scp" to copy from the windows box to the Linux box.)

There's possibly other options but I can't think of any others right now.  :-)

---

### Post by maybeway36 on 2007-10-31
Install WinSCP on Windows and your problems are pretty much solved.

---

### Post by psusi on 2007-10-31
man smbclient

sudo apt-get install smbclient if it isn't installed already.

---

### Post by Bl4deRunner on 2007-11-05
I found this the most useful, as I didn't want to install Samba (SMBClient is a Samba Client):

> Install WinSCP on Windows and your problems are pretty much solved.

;)

Thanks maybeway36 & ByteJuggler
This was the solution I was looking for!

---

### Post by Bl4deRunner on 2007-11-05
What I've found sofar:

Download and install:
[http://sshwindows.sourceforge.net/](http://sshwindows.sourceforge.net/)

to enable SSH server on your windows system.

then you SHOULD be able to use scp from linux to get the nessesary files.
Haven't quite found out how that works yet... But I'll post it here as soon as I do.

---

