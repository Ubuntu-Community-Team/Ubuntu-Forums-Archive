---
title: "[SOLVED] Pidgin will not connect to AIM"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-11-01
Recently I have been having a very hard time connecting to my AIM screen names in Pidgin. When I start Pidgin, it attempts to connect for 5 minutes or so, and then gives the following error: ```
Could not connect to authentication server:
Connection timed out
``` With the debug window open, I get this:```
(23:36:43) oscar: unable to connect FLAP server of type 0x0017
(23:36:46) oscar: unable to connect FLAP server of type 0x0017

```

I am fairly certain that my firewall is not the problem, since I am able to connect to AIM using AYTTM (available in the repos), and I have attempted removing Pidgin using ```
sudo aptitude remove pidgin --purge
``` and re-installing without any success. Anyone have any ideas at all?? Thanks for your help!

::EDIT:: Here is a logfile with a little bit more information which may be useful...

---

### Post by brennydoogles on 2007-11-02
::bump::

---

### Post by brennydoogles on 2007-11-03
:::bump:::

---

### Post by johncudd on 2007-11-05
I have the same exact problem. I got up this morning and it couldn't connect to my AIM accounts. I didn't touch any settings. It works perfect the day before. I went to the AIM website and logged into their web-based messenger without a hitch. Maybe the people at AIM changed their server address, or port. I have never had a problem with connecting to AIM like this before.

I went over to pidgin.im and apparently there are some security problems with 2.2.1. I haven't compiled the 2.2.2 version yet. Maybe it's a problem with 2.2.1. I hope someone finds a solution to this soon, I feel so disconnected. HAHA

---

### Post by powertower on 2007-11-05
I have recently been expieriencing problems with pidgin authenciation through AIM. It might be an AIM server related issue also. Sometimes it works - sometimes it fails. I know others who use windows distribution of pidgin also have problems recently. Wonder what AOL's up to now....
-POWERTOWER-

---

### Post by johncudd on 2007-11-05
Yea the problem is also on the windows version of pidgin. Must be a change at AIM.

---

### Post by brennydoogles on 2007-11-05
> **powertower said:**
> I have recently been expieriencing problems with pidgin authenciation through AIM. It might be an AIM server related issue also. Sometimes it works - sometimes it fails. I know others who use windows distribution of pidgin also have problems recently. Wonder what AOL's up to now....
-POWERTOWER-

as of last night it is working again (without any new configuration.....). Is there a good way to report bugs on Pidgin?

---

### Post by por100pre1 on 2007-11-05
Sometimes AOL blocks third party messengers, sometimes to wait is the best solution. If a change in AOL protocol breaks Pidgin functionality, it will likely be reflected in a Pidgin update.

---

### Post by johncudd on 2007-11-05
I found the solution to this problem. Seems there is a problem with the 5190 port, at least for now. I just switched the port to 443 and it worked perfectly. Try that, I hope it works for you, it did for me.

---

### Post by ridetheteapot on 2007-11-08
thanks johnc. fixed mine up like there was never a problem

hey but whats the big idea with 2.2.1?? i had 2.2.2 installed in fiesty.... whats with the regression? 
(meanwhile ubuntu must have changed something to supress the update notification security warning that should be popping up)
there is something to be said for not having to install the ton of libs that pidgin needs to compile, so i hope that the update comes soon

---

### Post by lord.toan on 2007-11-11
Thank you!  THis problem has been driving me insane as well.  Port change to 443 fixed it.  AIM must be messing with their ports.

---

### Post by mtlhd on 2008-02-07
you guys rock!  443 port works great!:guitar:

---

### Post by chrlywtrfall on 2008-02-14
OK total newbie question here, but I never feel safe doing anything without consulting the forums. 

I have the problem where it takes me like 5 minutes to connect to AIM through Pidgin, even though my Gchat works instantly. I went to Preferences>Network and under ports there is a range of ports to listen on. Mine is start 1024 and end 2048...now this thread said they switched their port to 448. Does that mean I just switch my range to include that port?

---

### Post by pythonusr on 2008-03-08
@chrlywtrfall:

Not sure if you still need this, but it's in Accounts > Yourname > Edit Account > Advanced

EDIT: FIX:

sudo chmod -x /usr/sbin/NetworkManager

!!!! =D

---

