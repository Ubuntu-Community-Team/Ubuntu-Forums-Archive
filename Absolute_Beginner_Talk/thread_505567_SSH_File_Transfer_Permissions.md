---
title: "SSH File Transfer Permissions"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by d2843 on 2007-07-20
I'm using Ubuntu 7.04 trying to transfer files via SSH to an Ubuntu 6.10 virtual server. I am able to connect to the server in Nautilus, but I am unable to perform any file operations on the server. I cannot copy files in, rename files, or delete files. I changed the folder I'm working in to have read/write permissions for Owner, several of the Groups, and Others. It comes up with the following error:

Error "Operation not permitted" while copying "*filename*".

---

### Post by kngunn on 2007-07-20
Could you post a little transcript of what you're doing?  If we could see the from where you start with ssh until the error message occurs we might spot something.

---

### Post by d2843 on 2007-07-21
Its a simple copy and paste operation in Nautilus.

I had used "Connect to Server" in the Places menu to access the server via SSH. When I open the connection in Nautilus, it asks me for username and password, which I enter. After the successful login, It allows me to view all the files and folders on the server.

The error message I posted above was the result of copying a file (lets call it *filename*) from my hard drive and pasting it into the server. All of this is from within Nautilus.

Every operation I attempt results in a similar error message. I am able to perform many of these operations by using a remote desktop (vncviewer), but that does not allow copying and pasting.

---

### Post by kngunn on 2007-07-21
Sorry, I see what you're saying now.

OK, here's two things to try to help isolate the problem.

First, right click on any file on the remote system when you are connected via Nautilus.  Bring up the properties -- what are your permissions according to the properties panel?

Next try performing a secure copy via a terminal:

scp mytestfile mylogin@myserver:.

(that should drop the file into you home folder on your server).

Let me know what you see...

---

### Post by yvs on 2007-08-11
Hi, I have the same problem by transferring a file from my windows laptop, from c:\filename to the Ubuntu Server, into /etc/opt
I'm a new user of Ubuntu and Linux, which command let's me see the folder properties of /opt?

Oh, I found how to do it: 
sudo chown myusername.myusername /etc/opt

This solution might work for you too....

---

