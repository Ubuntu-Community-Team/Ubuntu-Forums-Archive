---
title: "Reading folders created in OS X? Permission problem?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by TonySmash on 2007-11-27
I have a few external hard drives that I formatted in OSX as HFS+ and that I had backed up my OSX system to. For example, I copied my "Documents" folder from OSX to the drive. Now, when I go to try to read the folder in Ubuntu, a message appears saying:

The folder contents could not be displayed. You do not have the necessary permissions to view the contents of "Documents".

How do I change the permissions of these folder? I also cannot write to the drive, how do I fix that? I know this is probably a really simple fix but I'm very new to this and would love some help...

---

### Post by ItsMitsHere on 2007-11-29
I think you can mount the drive but can not read-write right?

If that's the case, open terminal and type **sudo bash**, this will ask for your password. provide it. (caution! runnung Bash shell means you are using super user previlages. don't mess up anything except what you want to do) Now navigate to the mounted external drive by **cd** command (alternatively u can type cd and drag-drop the drive icon into the terminal and hit enter) this is how you can navigate and read-write to the whole drive. you can copy things to and from by using **cp ** command and so on. I don't really know how to set the permissions but you can certainly access your data with this procedure.

Hope it helps,
Mits.

---

### Post by Matthew Bartram on 2007-11-29
chmod is the command for changing permissions, and man chmod if you want to find out how to use it. I think using Nautilus (the standard file browser) is the easiest. If in a terminal you type sudo nautilus, you can then change all the file permissions by right-clicking on the file, selecting properties, and changing the permissions tab. You want to make your user the owner, and give yourself read/write privileges.

As for the drive, you might be able to set the mount options in nautilus, again under properties. But I thought Ubuntu automatically mounted external drives so they were read/writable by the user who mounted them. So maybe something odd's going on here.

A note on using sudo: it's generally better to use sudo for each command, rather than starting a new bash shell with sudo. Or if you want to do a lot of admin without typing sudo each time, then use su (or that might need to be sudo su) which will put you as root in your terminal until you type exit.

---

### Post by Fisslefink on 2008-03-30
I have this same problem.   I think it might be a bug in the hfsplus driver.  Can anyone confirm?  Did you find a workaround?

Here is the line from my /etc/fstab:
```
/dev/sda2	/media/MacintoshHD	hfsplus		ro,uid=1000,gid=1000,umask=000		0	0
```

Mounting produces this message in dmesg, but proceeds OK:
```
[ 2709.220235] hfs: write access to a jounaled filesystem is not supported, use the force option at your own risk, mounting read-only.
```

Navigating to /Users/[myname]/Documents in Nautilus produces an error:
```
You do not have the permissions necessary to view the contents of "Documents"
```

The directory listing of my home folder on OS X (viewed from Ubuntu) is:
```
drwx------ 1  501     501   12 2008-03-28 15:08 Desktop
-rw-r--r-- 1 root     501 5120 2008-02-14 19:25 Desktop DB
-rw-r--r-- 1 root     501    2 2008-01-28 17:03 Desktop DF
drwx------ 1  501     501   12 2008-03-13 09:27 Documents
drwxrwxrwx 1  501     501  111 2008-03-29 19:10 Downloads
drwx------ 1  501     501   60 2008-03-19 10:55 Library
drwx------ 1   99      99    7 2008-03-11 22:53 Movies
drwx---r-x 1   99      99  708 2008-03-18 21:34 Music
drwx------ 1  501     501   18 2008-01-02 12:37 Pictures
drwxr-xr-x 1  501     501    6 2008-02-21 14:45 Public
drwxr-xr-x 1  501     501    6 2007-08-08 09:39 Sites

```
...as you might guess, I can view Downloads, Music, Public, and Sites, but not Desktop, Documents, Library, Movies or Pictures.

If I navigate to these folders as super-user, I can see everything.  It's a permissions thing, but uid=1000 should override this, shouldn't it???

Very frustrating!

---

