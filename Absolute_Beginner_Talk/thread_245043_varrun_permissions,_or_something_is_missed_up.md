---
title: "/var/run permissions, or something is missed up"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by jelevin on 2006-08-27
In playing around with trying to get vsftp to work I seem to have goofed up the permissions for /var/run, or maybe I did something with the non-real user accounts.

Here are the symptoms:
> $ /etc/init.d/vsftpd start
 * Starting vsFTP server: vsftpd                                          mkdir: `/var/run/vsftpd': Permission denied

I tried another /init.d script, and, although samba had been working before I get:

> 
$ /etc/init.d/samba restart
 * Stopping Samba daemons...                                                    start-stop-daemon: open pidfile /var/run/samba/nmbd.pid: Permission denied (Permission denied)
start-stop-daemon: open pidfile /var/run/samba/smbd.pid: Permission denied (Permission denied)
                                                                         [ ok ]
 * Starting Samba daemons...                                                    install: `/var/run/samba': Permission denied
/etc/init.d/samba: line 25: 11135 Aborted                 start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/smbd -- -D
                                                                         [fail]


The permissions for /var/run are:
> $ sudo ls -ld  /var/run/
drwx------ 15 root root 560 Aug 27 07:51 /var/run/


Does anyone have any thoughts?  Thanks for any help.  Is there a good tutorial to how those init.d scripts work?

---

### Post by Klaidas on 2006-08-27
You should run it as root
Just add "sudo" to a command.
[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by jelevin on 2006-08-27
Oh, of course.  An embarrassing mistake.  Thanks Klaidas!

---

