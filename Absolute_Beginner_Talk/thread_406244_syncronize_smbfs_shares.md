---
title: "syncronize smbfs shares?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Statik on 2007-04-10
Hi all,

I quickly installed smbfs and could see and read/write my shared directory on a windowsXP laptop. I'd like to synchronize a directory on my ubuntu box with this shared directory. Since smb:// is not a recognized protocol in unison, how do I go about doing this?

Statik

---

### Post by LaurelLynn on 2007-04-10
Dear Statik,

First I was just wondering if there was some underlying reason that you did not share the directory you wanted to be synced directly.

If there is a reason to keep them separate, then I would suggest reading the man page on rsync:

$ man rsync                  OR         $ rsync --help

There is also a GUI front end called grsync which is available through Synaptic or apt-get.

To automate the syncing, you would want to look at the man page for ¨cron¨ and ¨crontab¨. Cron is the background process which runs programs at specific times or intervals (say every 15minutes).

---

### Post by Statik on 2007-04-10
I'm not sure what you mean. I have a laptop that belongs to a soccer club that I have just become president of. I am using the laptop while away from home. I do most of my work on my desktop which is running Ubuntu. I have all the files on the laptop that pertain to the project in one directory that is shared with full access. I can browse to it in Ubuntu and mount it. I can copy and paste files to and from that directory. No access trouble at all. All I want is that instead of remembering which files I worked on, etc. to manually copy back and forth, I'd like to sync them. Is there some better way of arranging it?

I'll look at rsync as well.

Statik

---

### Post by LaurelLynn on 2007-04-10
I see,

rsync was designed for that purpose, the name is short for ¨Remote Syncronize¨. It´s big advantage over cp is that it copies only what has changed. 

$ rsync -rx  source-address  destination

You can just run the command anytime you plug the laptop into the network.  You could also add a Launcher to your Desktop so that all you have to do is double-click to sync up.

Cron would be for getting really fancy.  If you wanted to write a script that would check to see if the laptop was on the network, then automatically run the command.

---

### Post by Statik on 2007-04-10
so, can I use smb://blah/blah as one of the addresses? I couldn't use smb:// with unison.

Statik

---

### Post by LaurelLynn on 2007-04-11
Try thinking  of rsync as an enhanced version of cp.  For example:

$  cp  dirA/file  dirB/file   (copies file from dirA to dirB )

becomes:

$  rsync  dirA/file dirB/file         (same thing, but only if the file has changed)

To copy an entire directory tree:

$  rsync -rx dirRoot/.  dirTarget/ 

-r makes it recursively copy subdirectories.  -x keeps it from following links, so that it doesn´t go round in circles.

So, if you can reach a point where you can use the ls command to list the files on your windows laptop. Then you can replace ¨ls¨ with ¨rsync -rx¨ add ¨/.¨  then the folder you want to copy too.

If you can´t get ls to work because your having trouble with the Samba share, that is another problem.  I not familar with unison or what impact it would have.

Samba is an implementation of the Windows filesharing system. Since the share is comming from an XP system the filesystem should be NTFS or FAT, both of which Samba was designed to handle. That goes on at the filesystem level and is designed to be transparent to applications. The windows share should look just like another folder once it is mounted.

That mounting may be the step you are missing.  The format goes like this:

$ sudo mount -t smbfs  //servername/share  /mountpoint  [-o options]

Enter:  mount --help  for a listing of the options.

Hope I made that clear enough to follow. I´ll check back latter to see if you still have questions.

---

### Post by devnulljp on 2007-04-11
rsync

You want something like 

rsync -avz --recursive /source /destination/

---

### Post by LaurelLynn on 2007-04-11
Dear devnulljp,

-r is just short for --recursive.
-v  is a good addition for testing, but not something I would want everytime I synced up.
-z  yes, turning on compression should speed up the transmission.
-x  yes remove this, it is more of a linux safety feature, it stops at share boundries which probably aren´t nested in Windows.

Thanks for the input!

---

### Post by Statik on 2007-04-11
Yes, I think the mount is the step I am missing. I can browse to the share using the Places->Network Servers, and then I can right-click->connect to server, which makes it appear in my left-hand pane. However, it isn't a directory I can enter into cp, ls, or such. I'll try that mount tonight and let you know how it works out.

Statik

---

### Post by Statik on 2007-04-11
Well, it worked one way. Now, the mount point no longer reflects what is on the XP box. I can browse to it in places->network and the proper thing appears, but the mount point only shows a copy of the local folder.

I think there is something wrong with the mount, somehow.

Yeah, the mount isn't working for some reason.

 sudo mount -t smbfs //soccer/Porters_Lake_Soccer /home/statik/Laptop_Share

This doesn't seem to work. What am I doing wrong?

Statik

---

### Post by LaurelLynn on 2007-04-11
Dear Statik,

Try the command:

$  df -lh

The samba mount should be listed there. The mount command probably worked if it didn´t give you any error messages, and it shows up here.

There is always a possiblity that something is going wrong at the windows end.  SMB is a windows protocol and I have sometimes had a devil of a time setting this up on windows only boxes. Usually the problem is a firewall blocking the connection.

If you have another windows computer and it can´t read the share either, the laptops firewall is probably blocking the incoming connection.  (Windows Firewall defaults to doing just that).

I suspect a firewall, because they often result in failures with no error messages, just silence.

Just in case though double check all the file and computer names to look for typos, a single character, or the case can matter.

Lastly Ubuntu has a very good tool for debugging network problems (this is for Gnome not KDE):

System->Administration->Network Tools

There is a port scan tab.  You give it the ip number for the laptop ( the windows command should be ipconfig, though my memory is not what it once was).  Then hit the button.

What you are looking for is the Samba server on the laptop.  Should be 139 (possibly 445 I´ve seen that once before too).  If you get no open ports it either does not have sharing on, the network connection is not going through, or a firewall is standing in the way.

---

### Post by devnulljp on 2007-04-14
You might need your windos password in there:

mount -t smbfs //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword

---

### Post by LaurelLynn on 2007-04-14
Dear devnulljp,

In a network with Active Directory I would definitely agreed. With a basic peer to peer setup, Windows tends to be of the ¨Do you wanna expose this to anyone not blocked by a firewall or don´t you?¨ sort.  So I would be surprised if a password were required, I could be wrong though,  and it is certainly worth a try! (Windows tip - NEVER share ¨C:¨) ;)

Dear Statik,

Since the share appears under Network Servers, everything at the Windows end should be fine, and a firewall is not blocking it.

Having just an empty folder happens anytime a mount fails and a lack of an error message is not a sign of success. Mount is specifically designed to map the share **over** an empty folder.

I wish I had Samba setup on my network (but I don´t) so I could try a few things out on my system to see if I can reproduce the problem.

To find out what went wrong, all mounts should leave a log entry in the file /var/log/syslog. Just use any text editor (like ¨gedit /var/log/syslog¨). It is a long file, but right after running your mount command from the command prompt.  An entry should appear at the end of this file. If it list an error post what it says as that will help us figure out what is wrong.

Another log file which might log any errors is /var/log/samba/log.smbd.  So look at the end of that one too.

I would also ¨ls -l¨  the mountpoint, just on the off chance that  it is something like -r--r--r--  and root doesn´t have write access (which might block the mount).

I´ll try and check back again a couple of times a day. I´d really like to see you get your share!

---

