---
title: "/usr/share/acpi-support/power-funcs: No such file or directory"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by guarriman on 2006-07-18
Hi. 

Working with Ubuntu 5.04, I tried to restart my PC and it doesn't start
with Gnome, but with the shell.

System shows this message:
----
/etc/rc5.d/S99acpi-support: line 7:
/usr/share/acpi-support/power-funcs: No such file or directory
----

If I 'startx', I get this message whithin Gnome:
-----
Can't access ACPI events un /var/run/acpid.socket
-----

Does anybody know what's happening?

Thank you very much.

---

### Post by geco on 2006-07-18
> **guarriman said:**
> Hi. 

Working with Ubuntu 5.04, I tried to restart my PC and it doesn't start
with Gnome, but with the shell.

System shows this message:
----
/etc/rc5.d/S99acpi-support: line 7:
/usr/share/acpi-support/power-funcs: No such file or directory
----

If I 'startx', I get this message whithin Gnome:
-----
Can't access ACPI events un /var/run/acpid.socket
-----

Does anybody know what's happening?

Thank you very much.
I don't know why, but a script for acpi daemon to work is missing, if you have a laptop I think it's better to have acpi...
try this to check if acpi is installed:
```

sudo dpkg -l *acpi*

```
if not, install it with
```

sudo apt-get update
sudo apt-get install acpi acpi-support acpid

```
if acpi is installed try this:
```

sudo dpkg-reconfigure acpi-support

```
or
```

apt-get --reinstall install acpi acpi-support acpid

```
you also have to check out your boot scripts, you should have something as /etc/rc2.d/S99gdm in yout /etc/rc2.d folder

bye

---

### Post by guarriman on 2006-07-18
Hi geco.

Efectively, I use a laptop (Packard Bell EasyNote D5710), and I've just
found out that there are some problems with ACPI and Ubuntu:
[http://www-zeuthen.desy.de/~alorca/linux2onlaptop.html](http://www-zeuthen.desy.de/~alorca/linux2onlaptop.html)
"After having upgraded the X11 fglrx drivers Ubuntu does not resume properly from hibernating, so it may happen that is a graphical problem since everything gets frozen at the very end, nearly when done."

In addition, my networking setup is unable, so I can't 'apt-get install'.

Yesterday it worked ok. Problems started when trying to reboot my laptop.

---

### Post by geco on 2006-07-18
> **guarriman said:**
> Hi geco.

Efectively, I use a laptop (Packard Bell EasyNote D5710), and I've just
found out that there are some problems with ACPI and Ubuntu:
[http://www-zeuthen.desy.de/~alorca/linux2onlaptop.html](http://www-zeuthen.desy.de/~alorca/linux2onlaptop.html)
"After having upgraded the X11 fglrx drivers Ubuntu does not resume properly from hibernating, so it may happen that is a graphical problem since everything gets frozen at the very end, nearly when done."

In addition, my networking setup is unable, so I can't 'apt-get install'.

Yesterday it worked ok. Problems started when trying to reboot my laptop.

Ok, you have problems with boot scripts, but maybe you're still able to set up your network manually.
if you have a direct network connection, try
```

sudo dhclient eth0

```
where "eth0" is your network device.
if you connect via ppp (dialup-modem) or ADSL, sorry I can't help you!
Anyway you can try to "downgrade" your xserver 
```

sudo dpkg-reconfigure xserver-xorg

```
but backup your /etc/X11/xorg.conf file
to restore graphics... even if I think thath will not resolve your boot problems...

---

