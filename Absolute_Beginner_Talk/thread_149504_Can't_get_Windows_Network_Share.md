---
title: "Can't get Windows Network Share"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by Jose Catre-Vandis on 2006-03-24
Home LAN Netgear ADSL router - all wired

OK what I can get:

Sharing windows partitions on same PC
Sharing partitions on a networked NASLite box
All machines can ping each other
When going Places>Network Server I get
"Windows Network", then "WorkGroup" then "Server"

What I don't get:

If I double click on "Server" I get either a blank screen or am asked for username and password. None of the combinations I try get me anywhere, I just go round in a loop.

Under Windows I can set up shares with "Server" using \\Server\C$ (C$ for the drive C:\) and then type in username and password (this has to be the administrator user and pass, which is the same for all machines on the lan) Once set, these are transparent mappings

Server is running XP and IIS and not using simple file sharing, because of IIS lockdown tools and other security practices.

Also gettting this after the latest update of Samba (wans't getting this before but having the same problems

```
user@ubuntu:~$ /etc/init.d/samba restart
 * Stopping Samba daemons... start-stop-daemon: warning: failed to kill 6671: Operation not permitted
start-stop-daemon: warning: failed to kill 6673: Operation not permitted
                                                                         [ ok ]
 * Starting Samba daemons... /usr/share/samba/panic-action: line 51: mail: command not found
/etc/init.d/samba: line 24:  7788 Aborted                 start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/smbd -- -D
 
```

All any help much appreciated

---

### Post by kenweill on 2006-03-24
I was having the same problem before.
I installed Samba because I wanted to share a folder from Ubuntu to the Windows Network, to no avail.
After installing Samba, I can't browse to the Windows Network anymore. Keeps on prompting for a username and a password.

Removing Samba Completely solves the problem.
I can browse again to Windows Network. Of course, removing Samba prevents me from sharing Linux folder to Windows Network. But anyway, it doesn't work. So I remove it completely.

I guess theres a bug in the new update of Samba. It didn't happen before, only after updating my Ubuntu machine, which includes updating Samba.

And I have no idea how to solve this problem.

---

### Post by Jose Catre-Vandis on 2006-03-25
Its got worse

All I get now is Windows Network. when I click on that I get a dialog with message:

"smb:///" is not a valid location.

How do I test for samba and smbfs to be working correctly?

---

### Post by darf681 on 2006-03-25
I have this problem every so often.

make sure in your smb.conf file you have the following:

security = share

also, there is a line where you set up your workgroup name, make sure that it is correct..

skim through the rest, and you should be able to make a few minor adjustments according to what you desire..

also, when all is done...reboot all machines concerned...i know, i know..:-D

---

### Post by darf681 on 2006-03-25
Here is some good info too:
[http://ubuntuforums.org/showthread.php?t=26438](http://ubuntuforums.org/showthread.php?t=26438)

good luck!

---

### Post by Jose Catre-Vandis on 2006-03-25
[QUOTE=darf681]I have this problem every so often.

make sure in your smb.conf file you have the following:

security = share

[/QUOTE]

Thnaks, but am more confused now. :)  Had already read the link you kindly posted, which says

```
Make sure "security" is set to "user".
```

---

### Post by darf681 on 2006-03-25
if you set security to share, it will not ask you for passwords.  The link is for actually setting up a secure sharing setup.  If you set security = share, it will just let you access the share.

---

### Post by Jose Catre-Vandis on 2006-03-25
Still get the same message

---

### Post by Jose Catre-Vandis on 2006-03-27
Anyone? cannot access any network shares through Nautilus or command line, but can ping, and can telnet to the Naslite box. Am now officially hacked off with Samba :-P

---

### Post by Zimmer on 2006-03-27
user security is the best option I have found. You need to add a Samba user.
see:
[http://ubuntuforums.org/showthread.php?t=108950](http://ubuntuforums.org/showthread.php?t=108950)    post#5

---

### Post by Jose Catre-Vandis on 2006-03-27
Great, Zimmer. This gives me access to my Ubuntu shares from my Windows Box. Many thanks, I understand better now.

The important line in your link is:

myname = "network username" as opposed to system_username = myname in smbusers file.

However I am no further forward in seeing my windows box and Naslite box from Ubuntu still the same message?

---

### Post by Zimmer on 2006-03-28
[QUOTE=Jose Catre-Vandis]Great, Zimmer. This gives me access to my Ubuntu shares from my Windows Box. Many thanks, I understand better now.

The important line in your link is:

myname = "network username" as opposed to system_username = myname in smbusers file.

However I am no further forward in seeing my windows box and Naslite box from Ubuntu still the same message?[/QUOTE]

Quick guess  (have to dash out now) add a valid Windows user and password on the Ubuntu box as a user and as a Samba user, see if that makes a difference, or, a simpler test, add the Samba user you have already created as a user account on the Windows box....

---

### Post by Jose Catre-Vandis on 2006-03-28
Hmmm
Yes, I tried this, but still I should be able to see the boxes in File Browser even if the passworded shares are not set up. Thanks for your help.

---

### Post by Jose Catre-Vandis on 2006-03-28
Here is the answer:

[http://www.ubuntuforums.org/showthread.php?t=151758](http://www.ubuntuforums.org/showthread.php?t=151758)

Dependency needed:

```
apt-get install libgnomevfs2-extra
```

now to get the mp3's to play across the server!

---

