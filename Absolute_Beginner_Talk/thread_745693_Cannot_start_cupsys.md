---
title: "Cannot start cupsys"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by dako on 2008-04-04
When I try to start cups (beacuse it doesn't come up in boot) I get this error:


sudo /etc/init.d/cupsys start
 * Starting Common Unix Printing System: cupsd            
   start-stop-daemon: Unable to start /usr/sbin/cupsd: Permission denied (Permission denied)

How can I fix this?

---

### Post by wormser on 2008-04-04
I am not sure what is going on but post the results of the command.

```
ls -la /etc/init.d/cupsys
```

Your results should look like this:

> -rwxr-xr-x 1 root root 1937 2007-10-15 04:11 [COLOR="Lime"]/etc/init.d/cupsys[/COLOR]

---

### Post by dako on 2008-04-04
OK here it is.

ls -la /etc/init.d/cupsys
-rwxr-xr-x+ 1 root root 2287 2008-03-17 20:21 /etc/init.d/cupsys

---

### Post by wormser on 2008-04-04
> **dako said:**
> OK here it is.

ls -la /etc/init.d/cupsys
-rwxr-xr-x**[COLOR="Red"]+[/COLOR]** 1 root root 2287 2008-03-17 20:21 /etc/init.d/cupsys

It appears the problem is with the [COLOR="Red"]**+**[/COLOR] at the end.  Searching the net leads me to believe it has something to do with ACL (Access Control Lists).  I have never worked with ACL.  [Here]("http://tlug.dnho.net/?q=node/171") is more on ACL.  I do not know how to correct it yet, but am researching it.

Update:

I found a [post]("http://ubuntuforums.org/showpost.php?p=832721&postcount=9") that might help.

> Just an important note in case anyone tries this -- to remove acl permissions, execute the following on the directory:
```
sudo setfacl -b /directory/to/remove/permissions/from
```
I tested this and everything under this directory inherits the default permissions. Works great for what I want!

You would want to run the following command.  I have never used ACL, so you might want somebody else to confirm.  BTW, did you install ACL for a reason?

```
sudo setfacl -b /etc/init.d
```

---

