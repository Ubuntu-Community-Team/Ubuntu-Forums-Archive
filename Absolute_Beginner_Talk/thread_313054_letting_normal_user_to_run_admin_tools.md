---
title: "letting normal user to run admin tools"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by .::welemski::. on 2006-12-05
Hi,

Does anyone knows how to let normal user use admin tools like:

*network-admin - for dialup in dapper
*gnome-ppp -dialup for edgy

Tried search the net for solution but found none.

Also I read the "knichel" 's post but none of ubuntu users responded about this matter.

It is very hard to connect or use dialup or use any network-admin tool if you're a normal user. I just want to let normal user to connect to the internet using network-admin tool or gnome-ppp without giving him/her the admin password. I tried editing the /etc/sudoer file:

* normaluser ALL=NOPASSWD: /usr/bin/network-admin
or
* normaluser ALL=NOPASSWD: /usr/bin/gnome-ppp
even
* normaluser ALL=NOPASSWD: /usr/bin/gksu network-admin
or
* normaluser ALL=NOPASSWD: /usr/bin/sudo gnome-ppp


none of the statements above worked.

Does anyone knows how to stuff like these?


Thanks,

---

### Post by thk on 2006-12-05
Try adding them to the "dialout" user group and see if that works. If you are not too concerned about security, just add them to the "admin" group (allows root access, eg sudo -i).

---

### Post by lucky_chouhan on 2006-12-07
go to the system - administrator - users & groups.

select which your make you admin then click properties allow administrator rights and restarts.

i am also use as a normal user but i have a root power.

---

