---
title: "server 7.04 cd install questions"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by boonefly on 2007-05-11
LINUX newby  here...

As an IT professional by trade (MS products/IBM compats...) I thought I would just drop the disk in the drive and see how far I could get, my far superior and smarter co-workers who love linux suggested I install this as a means to my needs.  They are always trying to get a windows user away from the norm - so I felt it sounded like fun.  I did not get too far apparently.

On my day off,  I decided to upgrade an older system not being used AMD Athlon circa 2000 with plenty of ram and other updates over the years to the Ubuntu server 7.04.

I kind of wished I had just read the install pages listed on this site as I would have stopped dead in my tracks since the first screen was not what I was presented with.

The boot from CD menu does not have the run from disk option - only install to the hd, check cd for defects, rescue..., memory.. and boot from first hd.    

I tried to muttle through the install (rather old dos type install prompts - sorry since I have NO linux experience ever - I have no other basis as to what to call it).  Regardless - when all was said and done - it boots to a dos like login prompt.  That is it.  No GUI windows like interface which is shown on all the ubuntu.com pages.  What on earth happened?

Since this was an inconsequential pc - no damage done but I sure would like a GUI interface - not a dos / command like system.  Is it because it is the server edition? 

Basically just looking to setup a file/print server and backup repository so I just felt I might as well take the server plunge vs the desktop.

I like what I see on this site but can't really work with what I have at the moment.  Any help appreciated.


Signed - inside on a sunny day 'cause the pc is calling me!

---

### Post by Terl on 2007-05-11
Sounds like you got the server (or as they call it too, the alternate cd).

As a newcomer to Linux, I would advise you to try the regular desktop version.  This will run as a live cd so you can test drive with no changes to the pc.  If you like it, there is an install icon on the desktop with easy to follow directions.  I think this would be a great way to take your first steps into Linux.

---

### Post by boonefly on 2007-05-11
So I guess that answers my question about the install then.  The server version is apparently nothing similar to the desktop install.

Well - I had a feeling that was to be the case.  Regardless - I will venture forward with the desktop install next.

Thanks.

---

### Post by UbuntuniX on 2007-05-11
Best get a desktop for starting out, eh?

If your internet connection is already working on the server install, run this command:
```
sudo apt-get ubuntu-desktop
```

If not, download the Desktop or Alternate CD.

---

### Post by Terl on 2007-05-11
> **boonefly said:**
> So I guess that answers my question about the install then.  The server version is apparently nothing similar to the desktop install.

Well - I had a feeling that was to be the case.  Regardless - I will venture forward with the desktop install next.

Thanks.

You can use the desktop version as a server also.  It would just have a graphical desktop.  Once you are more familiar you can easily reinstall later and run everything from the command line thus ditching any desktop overhead..

---

### Post by dca on 2007-05-11
The alternate/sever still gives you the ability to install LAMP on the fly, set-up RAID or LVM, etc...  Once installed to your liking, then do the 'sudo apt-get install ubuntu-desktop' command...  
 
I love the 606LTS server ed.  Talk about rapid deployment of a server.  LAMP or FTP/SAMBA...  The thing moves.  The same thing w/o GUI as far as CentOS5/RH takes three times as along.  Not just installation, but reconfiguring after install.

---

### Post by boonefly on 2007-05-11
I appreciate all the responses.  I have the desktop downloading now.

Thanks much and have a great day!

---

