---
title: "Administration tools not running"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by norbird88 on 2007-09-19
Well, I install Ubuntu 2 days ago, First, everthing seems to be very good, But to day,  suddently  i can't run **Synaptic**, the **users and groups**, and my update manager can't install anythings.

More, I install stardict  yesterday, now i want to add some dictionaries, but i can modify anything in the File System, they report that i don't have the permission.

well, i am the one who install this computer, so i must be the admin, right?:confused:


Somebody please help, it's driving me mad](*,)](*,)

---

### Post by deadgobby on 2007-09-19
Are you logged into your root user account? Are you using a different user name than what you set up to?
Gobby

---

### Post by mikewhatever on 2007-09-19
Do you get any error messages when trying to run those things? What happens if you open the terminal and type > sudo synaptic

You do not have permission to modify system directories and files because although you belong to the admin group, you do not have admon rights all the time. It is very easy to get those permission, see the link for more --> [http://psychocats.net/ubuntu/permissions](http://psychocats.net/ubuntu/permissions)

---

### Post by norbird88 on 2007-09-19
thanks , it seem that my computer now has no admin group, i log into root, edit the ect/group and got that:
[HTML]root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
www-data:x:33:
backup:x:34:
list:x:38:
irc:x:39:
gnats:x:41:
games:x:60:
nogroup:x:65534:
dhcp:x:101:
syslog:x:103:
klog:x:104:
messagebus:x:107:
lpadmin:x:109:blacky
avahi-autoipd:x:112:
avahi:x:113:
haldaemon:x:114:
gdm:x:116:
blacky:x:1000:
ntp:x:120:[/HTML]


see, no admin group, show how can i creat an admin group now, i can't us user GUI tools, plz help

---

### Post by norbird88 on 2007-09-19
Well, thanks everybody, i solved the prob,

# addgroup --system admin
and gedit /etc/group
then next to admin, i added my username,

Hope people who have the same prob will find that helpful

---

### Post by norbird88 on 2007-09-19
oh, now i still have s&#417;me prob, if i add any user with admin priviledge, the system crash and the admin group will be automatically remove, What happened????

---

