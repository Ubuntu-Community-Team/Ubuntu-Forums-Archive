---
title: "Mounting a Windows Share from SSH access"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by broth420 on 2007-06-23
I have a large windows server that I would like to access in 7.04 server.  I am very new to Ubuntu, so I am sorry if this has been answered somewhere else

I am using Putty to access the Ubuntu 7.03 terminal.
The share I need to access in the Windows world is \\192.168.0.11\flac
It does have a user name and password to access it, but not much else in the way of security.
any idea how I can do this?  Thanks in advance for your help

---

### Post by tagra123 on 2007-06-23
gftp (ubuntu) or WINSCP (windows) can access these files using a gui

you can also do it from the command line

scp username@192.168.011\flac\filename pathtocopyto

---

### Post by scxtt on 2007-06-23
hmm, i wasn't aware there was any tie-in for samba and ssh - there might be, but my gut tells me you can't "secure copy" from a samba share ...

but you can mount samba shares in Linux ... check out smbmount ...

---

### Post by broth420 on 2007-06-23
OK, say I am local on the machine.  I want to copy files from that windows  machine.  What do I need to do?  I have no x windows installed, so everything is going to be command line.  and there are a lot of files.  it is my .flac directory, with 22,000 different songs.  organized by artist\album

---

### Post by scxtt on 2007-06-24
well, if you can sit in front of the windows machine (i know, no fun - i avoid it at all costs :p) - just make a samba share on your linux box, then "map network drive" from windows ... you should be able to drag-n-drop after that ...

i'm not sure if you can do:
smbget -u $USER -w $WORKGROUP smb://192.168.1.100/smb_share/flac/*

to get them all [ folders + files], it might be as simple as that, or maybe you can **smbmount** the windows share and just **cp** everything in it ... i'm sure there are a few options ...

---

