---
title: "Permissions problem - Complete Ubuntu newbie installing Xampp"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by undesign on 2007-04-21
HI I have installed Xampp on  OSX before but just installed Ubuntu desktop. Its working great but I am having problems extracting the tar archive of xampp to the opt folder. Its a permissions thing but when I issue the sudo or su command and log in as root I don't seem to be able to extract the archive.

First I am putting

sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt

at the shell prompt once I have logged in as root

I get the following error

tar: xampp-linux-1.5.3a.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I tried to do the same with the gui but it says that as admin I do not have permission to copy the xampp folder to opt. 

I tried to switch users and log in as root but it tells me that the root user cannot log in at the login screen. I understand that this is a security feature but I just want to copy the xampp folder to the right directory.

Any ideas?

---

### Post by heimo on 2007-04-21
```
 sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt
```

> **undesign said:**
> 
tar: xampp-linux-1.5.3a.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors



That's also exactly what I get when I run this command on a non-existent file.

---

### Post by Boreras on 2007-04-21
make sure root has the rights to read and write in the /opt map. You can allow this with chmod in shell, or your system's default file manager (Nautilus, Konqueror, Thunar, etc., but run it as root by typing "gksudo nautilus" or similar)
And you forgot the "-" in your command :) , and you must use "./" before a file
> sudo tar -xvfz ./xampp-linux-1.5.3a.tar.gz -C /opt

I hope it helped.

Boreras

*edit: I don't think the problem would be if the file exist. to make sure run "ls ./xampp*"

---

### Post by ArieT on 2007-04-21
I think you'd better not to install xampp but install apache etc. with synaptic.

Open system > administration > synaptic and go to something like 'mark packets with tasks' in the edit menu and select lamp. That's all :-) . 
I'm using the dutch version of Ubuntu so i had to do some translations. I hope i made it clear.

---

### Post by undesign on 2007-04-21
Managed to get xampp copied to opt using that nautilus command, Thanks.

It came up with a number of errors though and then opened a new file window as root.

Here are the errors that appeared in shell window

(nautilus:13643): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:13643): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.


I now have xampp running but there seem to be a few permissions problems still. Mysql isn't running for some reason even though xampp has started,

I try and open php myadmin and I get the following

The server is not responding (or the local MySQL server's socket is not correctly configured) 

this could also be down to permissions.

Perhaps I should reboot first.

---

### Post by undesign on 2007-04-22
Sorry didn't notice the reply from ArieT, thanks for that.

Now I am really stuck what to do.

Xampp was working fine but it seemed that there was either no MySQL or another version of it running. Wasn't sure how to test Mysql in the shell but thought it best to uninstall Xampp and see what I was left with.

Now I have no apache at all but typing [http://localhost](http://localhost)  redirects to [http://localhost/xampp](http://localhost/xampp) but with a nothing found error.

I also followed the advice of ArieT to install all manually or look in the package manager for Lamp, well it is not in there.

I really only need to use Xampp for my LAN development webserver anyway but can't seem to install it without problems.

Supposing I could use the command

sudo tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt

to copy the tar archive to opt (without the permissions problems) what actually happens?

Does this install Apache2, MySQL PHP and all the other modules to the correct folders in the file system or just redirect everything to the opt/lampp folder?

What should I do next?

---

### Post by undesign on 2007-04-22
Sorted it,

Found something on another forum about stopping other mysql services. I went into administration > services and stopped all mysql services I could see.

Restarted Xampp

And it all started correctly.

---

