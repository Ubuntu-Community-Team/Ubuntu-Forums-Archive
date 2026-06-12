---
title: "NXClient &amp; File Sharing - Help"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by pimpaulogy on 2007-05-31
I have been using nxclient for a while now and I am very happy with it.  The only issue I currently have is I can not figure out how to setup file sharing between the local and remote computer.

Both computers are Feisty.  The local computer is my laptop and the remote (server) is my workstation at home.  I have file sharing hooked up between my remote (server) computer and a Windows box that I have at home so I was able to setup Samba to work for those, but I can not get the file sharing working for my laptop and my workstation.

So far, I have been able to get as far as when I connect to my workstation, I get an error message saying:
"Cannot mount share 'paul'.
12775: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed"

Messing around with different config options on both the laptop's nxclient settings (Services tab on config window) and /usr/NX/etc/node.cfg on the workstation, I could get different error messages, but when those settings aren't like they are now, I get error messages that seem to come earlier in the connection process.  This particular message seems like it is later in the process so to this point, I think the settings are the best so far.  This message seems to refer to 'paul' which would be the share or directory on my laptop (local computer) that I am trying to mount to the remote (server: aka workstation).  However, when going through the Services tab on the configure screen for the nxclient, it only has a drop down menu where I get to pick what directory to share with two options: paul or Anonymous login s.  The 'paul' in the error message seems to come from this option.  I am guessing it wants a better path than just paul but more like /home/paul but I don't know how to add that as an option.  I also could be completely wrong.

Can somebody help me with this?  I still consider myself a n00b when it comes to Linux (about 8 months into it) so the more hand holding type instructions are preferred.

---

### Post by grahams on 2007-06-13
I use NXClient but I haven't tried the file sharing (didn't know it provided this), instead I use sshfs which is very simply to set up (lots of Howtos on this). You could also try NFS which is faster but harder to configure.

---

