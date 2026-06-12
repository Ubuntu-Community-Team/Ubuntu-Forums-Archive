---
title: "File sharing restrictions? (Program Files)"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by _Silhouette_ on 2008-04-17
Okay, I got my file sharing network up to a usable point. I do, however, notice that windows XP gave me no option to make the files C:\Windows or C:\Program Files sharable. Is there a way I can get these files shared so I can view them on my Ubuntu laptop?

---

### Post by bodhi.zazen on 2008-04-17
Go to My Computer

Navigate to the C drive

Right click "Program Files", select sharing and security

On the Sharing tab seledt "Share this folder"

Mount the share on Ubuntu

Places -> Networking -> Navigate to the share.

---

### Post by Hendrixski on 2008-04-17
Wait, why are you using Windows?  You probably *can* share your C:/ drive though it's probably even less safe.... and it's probably safer and easier to do so by sharing your Windows partition of windows THROUGH Linux.

---

### Post by _Silhouette_ on 2008-04-17
No, you misunderstand. I AM sharing my C:\ drive, it's just that Windows XP won't let me share the Program Files or Windows folders. Also, I can't access specific users' documents folders, just the "all users" ones. How do I work around this?

---

### Post by bodhi.zazen on 2008-04-17
Well what do you mean you can share the C drive but not Program Files or user files ?

You should be able to mount the C drive and navigate to Program Files. Do you get an error message ?

Also user files may be private or you may need to mount the share as a Windows user who has an administration (as opposed to a user) account. Try unmounting the samba share, to to places -> connect to a server. Enter your windows host name / ip address and (administration) windows user name and password.

Check the permissions on Windows.

---

### Post by _Silhouette_ on 2008-04-17
> **bodhi.zazen said:**
> Well what do you mean you can share the C drive but not Program Files or user files ?

You should be able to mount the C drive and navigate to Program Files. Do you get an error message ?

Also user files may be private or you may need to mount the share as a Windows user who has an administration (as opposed to a user) account. Try unmounting the samba share, to to places -> connect to a server. Enter your windows host name / ip address and (administration) windows user name and password.

Check the permissions on Windows.

There is no option in the sharing tab for Program Files or Windows. It will not let you do it share it through the sharing tab like the other folders. So when I try to access it from the network via Ubuntu, it gives me an error, saying that I don't have permission to view the file. I'm trying to figure out a way around this, if it's possible.
Also, I'm very new to networking, so step-by-step instructions are easiest, if it's not much of a hassle.

---

### Post by bodhi.zazen on 2008-04-17
You can look here :

[http://support.microsoft.com/kb/304040](http://support.microsoft.com/kb/304040)

My guess is you need to mount the share as an administrator.

---

### Post by bodhi.zazen on 2008-04-18
OK

To do this ...

On Windows XP go to my computer.

Go to Tools -> Folder options.

Go to the View tab

Scroll down and all the way at the bottom un-check the box "Use simple file sharing (Recommended)"

No navigate to the C drive, click on Program Files -> Sharing and security ...
Share this folder as Program Files.

===========

Ubuntu Client

First unmount any shares you have mounted.

Go to Places -> Network

Navigate to the share "Program Files". Double click. Enter your windows user name and password. I think your window user must be an admin account.

---

