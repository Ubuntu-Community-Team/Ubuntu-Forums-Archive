---
title: "CUPS web-interface"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by mbgb14 on 2006-10-28
When I goto localhost:631 in hopes of configuring my printer (Xubuntu Dapper) I'm presented with a login box when I try and do any kind of adminstrative task. 

It won't take my login credentials :( I don't know why! 
I've even gone to the trouble to set a password for root, but to no avail. 

Please assist :)

---

### Post by Marsolin on 2006-10-29
I might have the same problem.  I didn't get an error after trying to login, but I was never able to get to the next page.  Is there a reason you want to use this interface and not an administration program?

[GNOME CUPS Manager]("http://linuxappfinder.com/package/gnome-cups-manager") and [Gtk Print Manager]("http://linuxappfinder.com/package/gtklp") are a couple you could try.

---

### Post by mbgb14 on 2006-10-29
Same here. I amusing Xubuntu, so there's no software installed out of the box. And, I'd like to be able to access the web interface remotely, which would make administration/job-management ALOT easier.

---

### Post by wastrel on 2006-10-29
The administrative web interface is disabled by default. (Supposedly for security reasons...)  

Try this:

[https://help.ubuntu.com/community/PrintingCupsWebInterface](https://help.ubuntu.com/community/PrintingCupsWebInterface)

---

### Post by mbgb14 on 2006-10-29
Thanks alot :) 
You rock!

---

### Post by wgpeters on 2006-11-02
That doesn't help.  The kde utility in "System settings" doesn't work either.  I have read all the threads and tried all the tricks, and I am not able to get my brother MFC printer working and share it with my other machines.  

I have been successful in getting the cups web interface to work one time only.  After its used to reconfig one time, it fails to work again, unless I restore the cupsd.conf to its defaults. 

Ubuntu is worthless to me unless I can get control of my printer and use it with Samba.  

Is it possible to download a version of cups that is not intentionally broken?

Is it possible to install the printer and share it without having to use cups?

Is there a way to fix this version?

---

