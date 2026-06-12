---
title: "Permissions Question"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2007-08-30
I am trying to create a backup server on Ubuntu. I want to allow writing of files, but I do not want to allow overwriting, deleting, or renaming. Only viewing. How can I do this?

Of course, I still want writing to be allowed in root mode.

---

### Post by kevdog on 2007-08-30
Are you sure you phrased your question appropriately?  Do you just want a folder and subfolders to have the same permissions?  You only want rw parameters??  If someone has write parameters, then they can rewrite -- there is no such thing as separate rewrite parameters.

---

### Post by splintercellguy on 2007-08-30
chmod/chown? Check their man pages for more info.

---

### Post by amitroy5 on 2007-08-30
Well, what I want is once a file gets copied.  I do not want any further modification allowed to the file. I need to back up photographs though Samba from Windows and I cannot afford to risk the loss of even one photo.

---

### Post by Hobo Joe on 2007-08-30
I'd recommend setting it to read only, and when you need to edit, give yourself root permissions in Nautilus.

---

### Post by amitroy5 on 2007-08-30
Is there any other way? This is for my father who refuses to use anything but Windows and he will not even touch the desktop. The best option I have is to have him copy the files though the mapped network drive on Windows.

---

### Post by Hobo Joe on 2007-08-30
It's not possible to have read only permissions, and to copy files. Similiarly, it's not possible to have write permissions, but not be able to edit anything.

---

### Post by amitroy5 on 2007-08-30
Do you know about any workarounds for this situation? Any other methods I can use to do this? He recently lost a lot of his work which I blame on Windows.

---

### Post by Hobo Joe on 2007-08-30
> **amitroy5 said:**
> Do you know about any workarounds for this situation? Any other methods I can use to do this? He recently lost a lot of his work which I blame on Windows.

What caused the data loss? Him or Windows?

---

### Post by aquavitae on 2007-08-30
Not sure exactly how you're copyint them, but you could write a two line script so change the permissions as soon as its copied. 
```
#!/bin/sh
cp $1 $2
chown root:root $2
chmod 0644 $2

```
This could be refined (e.g. handling executables), but its a start point.  I'm not that good at bash so I don't want to try writing a complete script which I won't be able to get to work.

---

### Post by mckryptyk on 2007-08-30
Perhaps the backup server can run an automated backup of a mounted folder on the windows desktop to the backup server which can then be mounted read only. That way windows cant delete anything but it will only be mounted read only on the samba process and not the actual server.

I have something similar to this already running and on the server I can move, modify,delete, etc. any file I need to, but windows cant touch the from it's client side.

I do this by having them copied to a read/write folder on the server from windows via samba.
Then moved by a backup script to a folder that is shared read-only back to the windows client.
So from the windows client I have two folders on the desktop. 
Let's call them "inbox" for storage to the server and "outbox" for read-only sharing to the windows client after they have been backed up.

They are moved out of the inbox to the outbox when backed up correctly. I then have automated backups to disk of the server over time.

---

### Post by amitroy5 on 2007-08-30
I have no idea what caused the loss, but I have no trust in Windows, especially for such data as photographs. I'm not good at programming, so I will have trouble writing a script. :(

However, I like mckryptyk's approach. Now if I can convince my dad of sharing his files. But I think such a method will work.

---

### Post by mckryptyk on 2007-08-30
Your dad will only be sharing/uploading them to the server thats it. "You can even specify upload from here only" / "download to here only".
He can actually even read them from the server and save them to his desktop with changes,etc. Then upload them back to the server for backup.

I'm actually only doing everything from the samba configuration found ate /etc/samba/smb.conf

Since you probably don't want to muck about the command line you might want to try using simple backup for the second part of the post I wrote. 

(The backing up of the server afterwards but use openbox or blackbox for desktop enviroment, a real server has no GUI or DE  :) )

You may be interested in trying SWAT -- the Samba Web Administration Tool
I've never used it but it's supposed to provide a point and click interface to samba configuring.

Let us know here at the forum which way you go with this and I'll try to help with this too.

You might want to consider writing a how-to for the forum afterward to help out otheers in your situation.

PM me if you are stuck and I will post it back to this a thread afterward about the technicals when you have it working so other people can follow it too.

---

### Post by amitroy5 on 2007-08-30
I was thinking about trying grsync. But one question I have about this program is how I can just allow the destination to copy from the source. But disallow the source from sending files back to the destination.

---

### Post by mckryptyk on 2007-08-30
read-only allows him to "read-only" to his client-side folder called "Outbox". He can't delete those but can open them up for viewing or to save a copy locally to the windows client.

He will not be able to modify the originals if they are copied to the server without intervention at the server-end by the admin.

"Inbox" will let him upload to the server only and the backup program, moves it to the outbox after he uploads it.

To him it will just be a case of "copy and paste" into the "Inbox" and watching them disappear out of the "Inbox" every hour and appearing in the "Outbox" permanently in "read-only" mode.

You can even restrict access to the server based on "IP address" and "Username/Password".
Also you can restrict access to the samba server by how many users can connect at the same time. 
So if he is connected no one else can connect to see his files.

You can also tell samba to encrypt the data as it travels over the wire between him and the server.

Another program then backs up the server including "Inbox" and "Outbox" in case of server failure.

These backup you would burn to some dvds or copy to an external drive to be put away in a safe place.



Cheers.

---

