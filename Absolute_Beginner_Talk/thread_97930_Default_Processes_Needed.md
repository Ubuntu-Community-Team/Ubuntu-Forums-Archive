---
title: "Default Processes Needed?"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by echokilo on 2005-12-02
I was wondering what these processes are and if they are needed. I am not using the x-windows very much, but want to be able to if needed:

dhclient3 -pf /
hald
python /usr/sbi
/usr/sbin/hpiod
udevd --daemon
/usr/sbin/sdpd

Thanks!

---

### Post by Murgle on 2005-12-02
You want hald if you are using hardware abstraction lair as I assume that that is the deamon for that.  Python is also almost always a must as many things use it.  Not sure about the others but why bother removing them?  It shouldn't give you much of a benifit.

---

### Post by doclivingston on 2005-12-02
[QUOTE=echokilo]dhclient3 -pf /
hald
python /usr/sbi
/usr/sbin/hpiod
udevd --daemon
/usr/sbin/sdpd

Thanks![/QUOTE]

The processes are:
dhclient3: DHCP client, you'll need this if you use DHCP on your network (if you don't have a network or use static addresses, you can get rid of it.
hald: the HAL daemon, which notified programing about hardware or removable media changes.
udevd: udev daemon, which makes /dev work. Keep this.

I'm not sure about the others.

---

