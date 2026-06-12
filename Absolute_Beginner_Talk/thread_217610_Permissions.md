---
title: "Permissions"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by trebizond on 2006-07-17
Afternoon all,

I've just installed Kubuntu on my laptop, having no experience whatsoever of Linux. I remember the evil days of DOS though, so command line holds no fear.

The one major problem I'm having is with my hard drive. I can't access it. I can get to everything in the Home Folder, no problem.

However, whenever I try to alter anything on my hard drive, it says I don't have permission to alter it.

I've looked at the permissions, and it is User:root, group:root. My user is richard and my group is now root too - still happens.

It won't even let me change it in permissions to 'Group - can view & modify content'. I've had a look in System Settings, but no change there either.

I can't log in as root either. What is going on? I suppose what I really want is to be a 'Superuser' - how would I go about that?

Thanks for your help.

---

### Post by agurk on 2006-07-17
edit: wrong post

---

### Post by Rumor on 2006-07-17
It is set up that way on purpose. There is very little that you really need to do as root. If you are trying to modify one of your config files, you can edit it as superuser by typing ```
sudo gedit /path/filename 
``` It will ask for your password and then you can edit and save your changes to the file.

sudo (command) will allow you to temporarily enter superuser mode. It's handy for compiling and installing new programs, but there is really very little that you need to do on a regular basis as superuser. At least in my very limited experience.

---

### Post by uzi09 on 2006-07-17
may also want to take a look at this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by trebizond on 2006-07-17
Blimey - that was quick :) I must say, I placed a query on the OpenSUSE forums (it just wouldn't install) and I still haven't got a reply. Looks like (K)ubuntu was the right choice :)

I've changed myself into a root login :) There was plenty of warnings against doing it, but;

a) I'm a bit stupid

and

b) I have an inbuilt dislike of computers that tell me I can't do certain things, even if it is for my own benefit. If I want to overclock my P-M to 6 GHz and destroy an entire city block in the process, so be it. :)

Thanks again - I'm looking forward to getting to the point where I can help people so quickly :)

Richard

---

