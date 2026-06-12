---
title: "Problem Editing Files"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by IndyBob on 2007-04-04
I just reinstalled 6.10 on a new hard drive and am a real noob to Ubuntu.  I am having problems editing files to try to fix mplayer so it will work with everything.  I have searched the forums for answers and I think I have found the solutions to my issues, but everytime I try to use gedit I get the following response from the terminal.

bob@ubuntu:~$ sudo gedit /usr/lib/firefox/plugins
Password:

(gedit:4584): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
bob@ubuntu:~$ gedit /usr/lib/firefox/plugins
bob@ubuntu:~$ gksudo gedit /usr/lib/firefox/plugins

(gedit:4732): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
bob@ubuntu:~$ 


What am I doing wrong or what don't I have set up to do this?<br /><br />
----------------------------------------<br />

----------------------------------------<br />

---

### Post by dbbolton on 2007-04-04
/usr/lib/firefox/plugins is a directory, not a file. thus, you can't open it with gedit.

do ```
gksudo nautilus /usr/lib/firefox/plugins
``` then you can edit the contained files you want as root.

---

### Post by IndyBob on 2007-04-04
Thanks, being a noob it's going to take time for me to learn everything.  I tried your command and got the following error, but the file opened.  What would be causing these error messages??

gksudo nautilus /usr/lib/firefox/plugins
(nautilus:5861): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:5861): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

---

### Post by dbbolton on 2007-04-04
that always happens. i really don't know why, but it's harmless.

---

