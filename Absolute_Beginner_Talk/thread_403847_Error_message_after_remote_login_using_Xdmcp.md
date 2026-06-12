---
title: "Error message after remote login using Xdmcp"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by hec1979 on 2007-04-07
When I login to my ubuntu machine which is using the gnome desktop i see the background of my desktop but it never fully loads. I cannot see any of the options on the top of the desk top or the bottom I can only right click and see or use those options.  After being logged in for a while to see if anything would happen I was presented with a dialog box with the following error message.

There was an error starting the GNOME settings Daemon
some things such as themes sounds or background settings
may not work correctly

The settings daemon started to many times

the last error message was

System ExceptionL IDL:Bonobo/GeneralError:1.0: Child process
did not give an error message, unknown failure occured

GNOME will still try to restart the settings dameon the next time you log 

Has anyone experienced the before any suggestions on solving this would be great.

By the way when I log into my kde desktop on the same machine every thing is fine, if that helps any.


Hec1979

---

### Post by hec1979 on 2007-04-07
The following link is a Bug report dealing with the issue I was having, some people may have similar issues but under different circumstances.

[https://launchpad.net/ubuntu/+source/control-center/+bug/61381](https://launchpad.net/ubuntu/+source/control-center/+bug/61381)

In my scenarios I installed the latest and greates version of Kubuntu and then when ahead and installed gnome over it.  After i configured gnome to accept xdmcp connections it was taking very long to login and the eventually failing with the error message in my previous post.  The solution is to comment out all of the IPv6 entries in the /etc/hosts file and disable the windows firewall everything was fine after that.

---

