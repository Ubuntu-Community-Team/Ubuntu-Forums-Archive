---
title: "Cant access services"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Blandust on 2007-03-14
I was configuring which apps would run at start up of ubuntu I guess i un-checked the wrong one now at startup I get a pop-up window, reading : "Failed to initialize HAL."
Also I cant access services anymore, it reads " The Configuration could not be loaded, you are not allowed to access system configuration."
How can I fix this? Thanks.

---

### Post by eljalill on 2007-03-14
I don't really know, how you can fix this, especially for I don't have any idea, which services you are talking about. 

But if this is a problem of accessing the .conf files, where the autostart programs are in (at least some... I have no clue which and why though), you could change the access to your .config directory so that you as a user can change it .

You can do this through chmod and chown in the terminal, the man pages will tell you, how the commands work (man chmod goives you the manual, q lets you leave again).

But remeber to change it back as well! After all these secured accesses are there for something!

I hope this somehow helps, it might at least be something to try.
But be careful when screwing around with these files, and keep a backup somewhere...:)

---

### Post by Blandust on 2007-03-14
?????????

---

### Post by eljalill on 2007-03-14
I you were doing, what I think you were doing, you edited the startup programs in system>preferences>sessions . As far as I know, these have something to do with the autostart in your .config folder. (You can find this folder when you open nautilus: the file browser, and type "Cntrl H" while you are in your home directory.)

In any case, the error message you get, when you try to "access services" (you might want to describe what you mean by this), seems to be about access restrictions.

Normally you are logged in as a user. This means, you do not have access to some system resources. As root (administrator) however, you do.

So, what you could try is changing the access of your configuration folder. 
However, before you do that, you might want to make sure, that this is actually what you want, since there is a reason for users to not have access to some resources.

That is what I was proposing above.

But maybe it would be good, if you explain a little more, what exactly you did, before you got the problems, and what exactly you are doing when you try to change everything back. This will help to see where the problem lies.

However, I am not sure at all, that I can actually help you. However, someone in this community most likely can. So posting more information might be the best.

OK?

---

### Post by deathbyswiftwind on 2007-03-14
Hey depeding apon what your kernel your running this can happen. Has nothing to do with the sessions. Hal starts up before your gnome session does. You may just need to make sure you have all updates and the latest kernel. Mine did that until I got an updated kernel from the repos

---

### Post by Blandust on 2007-03-14
i was in system/administration/services, I unchecked like  2 or 3 programs to not run at start up, then after i re-booted i recieved the " failed to initialize HAL" error window and now i cannot access services again to re-check what I unchecked , which I know is the root of the problem

---

### Post by eljalill on 2007-03-15
You open a terminal and type
sudo usp run-in-window

That way you open the system panel as root. 
Are you now able to change your services back?

---

### Post by jessika_kaos on 2007-04-13
I'm having the same issue. I disabled some startup services in System>Administration>Services, and now whenever I log in I get a warning that Hal failed to initialize and I am unable to open the the services dialog again. I unchecked the printing and speech synthesis services.

I tried sudo services-admin and get this:> (services-admin:4391): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
4391: arguments to dbus_connection_add_filter() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4379.
This is normally a bug in some application using the D-Bus library.
4391: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.

(services-admin:4391): Liboobs-CRITICAL **: run_message: assertion `oobs_session_get_connected (priv->session)' failed
4391: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.


---

