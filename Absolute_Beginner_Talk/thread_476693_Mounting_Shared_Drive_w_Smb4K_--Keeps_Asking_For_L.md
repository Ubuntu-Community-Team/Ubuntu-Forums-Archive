---
title: "Mounting Shared Drive w/ Smb4K --Keeps Asking For Login --Help"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by anthonylitz on 2007-06-17
Hey all,

I am an Absolute Beginner, so I know this forum is for me!  I have researched this problem all weekend and can not find a solution, so I hope someone here has an easy fix :) 

So I gather I need to mount my shared windows drives that holds my media if I want many programs in Ubuntu to be able to access it. Such as Amarok or VLC Player.  Correct?

I have no experience with the Terminal and haven´t used a command line in about 10 years.  So I found Smb4k mounts shared drives through a GUI and seems pretty straight forward.  But when I try to mount a drive I am prompted for a login and password.  I have tried the login for my Ubuntu box and my windows box...they are the same....something seems to work.  I just repeatedly get asked for my password.

Can someone PLEASE help me mount a shared drive?

Thanks so much,
Anthony

---

### Post by anthonylitz on 2007-06-19
::bump::

Still need help with this, anyone?  Please, I am a lonely newbie big time with Linux and Ubuntu.

Thanks!
Anthony

---

### Post by warcriminal on 2007-06-19
If you are trying to mount a Windows Share on your linux box read this article;

[http://www.goitexpert.com/entry.cfm?entry=Make-Your-Windows-Share-ReadWriteable-From-Linux](http://www.goitexpert.com/entry.cfm?entry=Make-Your-Windows-Share-ReadWriteable-From-Linux)

If  it's the other way around read this article;

[http://www.goitexpert.com/entry.cfm?entry=Linux-Share-With-Windows-Vista](http://www.goitexpert.com/entry.cfm?entry=Linux-Share-With-Windows-Vista)

It sounds as though you have gotten fairly close to having a complete setup, but it seems what you are missing is the smbpasswd.  It isn't enough to merely have a "logon" username and password, you have to link the smbpasswd to usernames that you are already using.  Meaning change the smbpasswd (assuming samba is configured correctly) to the same password as you network share.

---

### Post by anthonylitz on 2007-06-20
Thanks for the support and feedback.  I am going to start pouring over these links right now.  I know I can figure this out! ;)

Anthony

---

