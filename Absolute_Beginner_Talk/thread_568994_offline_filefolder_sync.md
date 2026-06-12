---
title: "offline file/folder sync"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by tdmoore on 2007-10-06
I have read many posts here regarding syncing files and folders - some suggest Unison, Conduit, rsync and Grsync.

Have looked at some of the screenshots and screencasts (wish they all had more shots with more detail)...and now confused more and more.  Unison has now become Harmony according to their site and no longer in active development.

As a beginner just in the process of migrating from Windows and used to a GUI world, is there one particular app that would work best?  

Looking forward to a reply.

---

### Post by talby on 2007-10-06
Rsync is a great one-way sync tool, although I can't say I have seen a gui for it.  I use it on the job for legacy server backups (so one-way sync is just fine)

Unison, on the other hand, is a two-way sync meaning it will take files updated on both sides on the source / target and update both accordingly so it is perfect for a multiuser folder that is shared.

There is a GUI tool called unison-gtk so just "sudo apt-get install unison-gtk" and it will install the latest stable version 2.13.16.  I tried it (by running "unison-gtk" in a terminal) an it asked me for the local source directory, then the target dir with additional options for ssh and such along with the host name & user login.  I would not worry it is out of active development it should work fine - I use the command line version on my laptop it works well.  The only caveat is make sure you have the same version installed on both the source and the target.  Harmony seems to be for xml files only not for file / folder sync.

Sorry can't comment on the others I have only used rsync & unison, both of which are cross platform (I use the cygwin version for win32 applications).  Check out passphraseless ssh keys if you want automated rsync / unison or if you tire of typing your password.

cheers

---

### Post by tdmoore on 2007-10-06
Thanks for the reply and I will file it for future reference as I have only used the Live CD.

Not real confident on command line yet so please define ssh for me

Appreciate it talby....

---

### Post by talby on 2007-10-06
Sure, no problem...

[quote="[Wikipedia](http://en.wikipedia.org/wiki/Secure_Shell)"]"Secure Shell or SSH is a network protocol that allows data to be exchanged over a secure channel between two computers. Encryption provides confidentiality and integrity of data. SSH uses public-key cryptography to authenticate the remote computer and allow the remote computer to authenticate the user, if necessary.

SSH is typically used to log into a remote machine and execute commands, but it also supports tunneling, forwarding arbitrary TCP ports and X11 connections; it can transfer files using the associated SFTP or SCP protocols."[/quote]

So it is similar to a "remote desktop" session on windows, without the windows :) you only get to run commands in a terminal.  The ability to tunnel and port-forward gives it the flexibility we need, once you set up the server (with "sudo apt-get install openssh-server") then you can use rsync or unison to sync a folder on that host.

---

