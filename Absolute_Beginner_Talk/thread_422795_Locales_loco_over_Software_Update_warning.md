---
title: "Locales loco over Software Update warning"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-04-25
The orange & white update icon appears when Dapper is fired-up.

Clicking the icon calls for a password, which once entered brings up the Software Updates window.

Clicking Install Updates starts the process.

The Software Updates window says:

locales

common files for locale support
New version 2.3.18.3 (size 3285K)

the Updater fetches the software, but when it tries to install it, I read in another window:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/langpack-locales/locales_2.3.18.3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/langpack-locales/locales_2.3.18.3_all.deb)
  Error reading from server. Remote end closed connection [IP: 130.239.18.158 80]

Anybody seen this before?

---

### Post by bapoumba on 2007-04-25
I can get the file. May be the server was not responding at the moment you tried.
Could you please open a terminal (> Applications > Terminal), and run:
```
sudo aptitude update
```
and paste in here any error you get.

---

### Post by Mark_in_Hollywood on 2007-04-25
no sir,

same problem as before

---

### Post by bapoumba on 2007-04-25
Okay, the mirrors may be too slow (did this happen before? Are you on dialup?). Try the main ubuntu repositories. Open a terminal, and:

1- save your sources.list file:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_070415
``` 

2- edit the file and change all the **us.archive**.ubuntu to **archive**.ubuntu
```
sudo nano /etc/apt/sources.list
```
Save the file with CTRL-O (same name, hit enter) and exit nano with CTRL-X.

2- reload the repos list:
```
sudo aptitude update
```

If you still have errors, continue to run the update (or if using synaptic, please check [this bug]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/29332")).

---

### Post by Mark_in_Hollywood on 2007-04-26
So, after 4 or 6 attempts to have the Update Manager install LOCALES, it did. 

As to whether I'm using dial-up. Yes, and maybe that was it.

Thanks for you time and support.

Dapper Rocks. All by itself.

---

### Post by bapoumba on 2007-04-27
Okay, so it did fail on big files, and you are on dialup.

One way to work around this would be to increase the timeout in apt-get process, ie have it wait longer before it dies. 
This is set up in apt.conf file, here is a tutorial about it:
[http://www.die.net/doc/linux/man/man5/apt.conf.5.html]("http://www.die.net/doc/linux/man/man5/apt.conf.5.html")
Look for the acquire group.

Look for the /etc/apt/apt.conf file. If you have one, save it:
```
sudo cp /etc/apt/apt.conf /etc/apt/apt.conf_bak
```
Then edit the file:
```
sudo nano /etc/apt/apt.conf
```
If the file does not exist, the last command will just create it.

Then add:
```
Acquire::http::Timeout "600";
```
**"** and **;** are mandatory. Time is in seconds, you may have to play around with it and find a more appropriate value.
Save the file and exit (CTRL-O, CTRL-X)

This file will be used on next update/upgrade, no need to reboot.

---

