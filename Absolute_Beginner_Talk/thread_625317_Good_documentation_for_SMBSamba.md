---
title: "Good documentation for SMB/Samba?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by FuzzyBob on 2007-11-27
Okay, I've gone through all the docs I can find and frankly I'm about ready to scream.  Depending on how I phrase my search I'm coming up with various things on how to set up SMB or Samba and it's all blurring together.

Here's the rundown:
I've got an Ubuntu desktop and a Ubuntu desktop install set up on another machine to be the file server, and a couple XP boxes too.  All I want to do is have network type drives where I can keep music/photos and stuff, without having to figure out which machine they're on. 

I've got Samba, smbfs, nfs, etc all installed but I can't reach the drives. I've used the Samba GUI and added the users, even used Fstab and changed the permissions so that anybody can read/write to them.  When I open the Network, I can see the linux boxes but I can't get into them to see the drives/files.  

So the long-winded question is this: Is there a recent online doc that can give me step-by-step instructions on how to do this? Is there a book someone can recommend?  Some of the docs online talk about things and don't really say what you should be seeing and if it's good or bad. Example: one I found says "Are smdb and nmdb running?" under troubleshooting, and then lists the commands to do it. It doesn't say what the results should be so you have no way of knowing if it's correct, only that it did *something*.

I know this is another "noob with file sharing issues", but there's gotta be an easier way than fighting with files and command line stuff for 3 days and not getting anywhere. :(

Thanks for reading my vent/question...

-Bob

---

### Post by JKyleOKC on 2007-11-27
I found the book "Using Samba" to be helpful when I was fighting my way through setting up the system, but I don't know whether it has been updated to cover the latest versions. My copy only goes to Samba version 2, and version 3 has been around for quite a while now.

There's also a quite good step-by-step procedure here, on the "networking" forum, that might fill your immediate need.

Have you customized your smb.conf file to set up permissions for the drives you want to reach? You can do this using "swat" by opening your browser (Firefox, Nautilus, Konqueror, etc) and havigating to "http://localhost:901" which will ask you to log in and then give you a GUI for setting up the shares...

---

### Post by vba_djs on 2007-12-18
When I was setting up my Samba a year ago I purchased The Official Samba-3 Howto and Reference guide [ISBN# 0131882228].  I believe that it is a collection of the HowTos that you can get from the Samba site, but I liked it because it put everything in one place.  It covers through 3.0.20

---

### Post by Alpinist on 2007-12-18
I could not get samba to work using the GUI tools. Seems to be a major weakness in Ubuntu as you see a lot of posts on it.

Did find this article on manually setting up samba and it worked for me.

[http://ubuntuforums.org/showthread.php?t=202605&highlight=set+up+samba+pee%20r-to-peer](http://ubuntuforums.org/showthread.php?t=202605&highlight=set+up+samba+pee%20r-to-peer)

---

