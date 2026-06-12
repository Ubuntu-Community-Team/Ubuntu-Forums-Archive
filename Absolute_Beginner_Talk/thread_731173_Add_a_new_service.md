---
title: "Add a new service"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by jmitch18 on 2008-03-21
Hi,

I'm completely new to Ubuntu and I'm trying to set it up so develop PHP scripts and that's working alright however Apache and MySQL don't automatically start up.  I went to Sessions to try and add the command but it requires you to be signed as root to run it.  Is there any way to get around this?

It's a bit annoying to have to sign into root user to start it up every time.

Any help is greatly appreciated.

---

### Post by compiledkernel on 2008-03-21
BE CAREFUL , then do.....

sudo apt-get install sysv-rc-conf 

then 

sudo sysv-rc-conf 

you can then use the application to modify runlevels. Be careful it can damage your install if you turn off the wrong items. Id really just look for apache2 and mysql and set them to I think 2, 3, 4, 5, and then reboot.

---

### Post by jmitch18 on 2008-03-21
Neither apache nor mysql is listed in the services list from that command.  Is there a command I can use to add it?

---

### Post by compiledkernel on 2008-03-21
uninstall apache and mysql and reinstall them. 

Its unusual to see that install NOT create init scripts, properly.

---

### Post by maddog39 on 2008-03-21
Another approach you might want to try is manually launching apache and mysql in your rc.local which is run every time you boot up. Although I dont have specific commands for launching those daemons.

---

### Post by compiledkernel on 2008-03-21
for rc.local 

I think you can get away with 

/etc/init.d/apache2 start 
/etc/init.d/mysqld start

---

### Post by jmitch18 on 2008-03-21
Could the reason for them not appearing in the list be because I used an installation kit?  I've always used an installation kit just for the handiness.  I have no intention of running my own server.  Would I maybe be better off setting up and configuring the individual software?

---

### Post by compiledkernel on 2008-03-21
hmmm, which installation kit did you use? 

Honestly, if you want to install Apache, look here, Its not hard, and only requires a few commands to be run. 

[https://help.ubuntu.com/7.10/server/C/](https://help.ubuntu.com/7.10/server/C/)

---

### Post by jmitch18 on 2008-03-21
I used XAMPP to set it all up.  Just used it because it was what I always used on my Windows system.

I might just set up Apache and MySQL myself.  Could be the best way to go.

---

### Post by jmitch18 on 2008-03-21
Setting it all up myself has been so much easier in Ubuntu than Windows.  Thanks a lot for your help!

---

