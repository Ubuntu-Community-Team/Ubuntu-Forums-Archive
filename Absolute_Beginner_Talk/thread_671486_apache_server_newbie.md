---
title: "apache server newbie"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Station on 2008-01-18
I have to configure apache 2.2.6 to my computer. It does not want to configure to my computer. I was wondering what program to use to read the config.log, so I can track down the issue. G edit seems to work fine.

Now I have to figure out how to make apache configure to my 64 bit computer...

configure:3119: result: x86_64-unknown-linux-gnu

I found a patch for 64 bit platforms, but having troubles making that work properly.
I have been told that this is the run command
patch -p1 < apr-util_2.2.6.patch

but I get this

patch:*** strip count 1 is not a number

So at the moment I am kinda stuck

---

### Post by peabody on 2008-01-19
Is there a reason you need to compile the apache server from source?  Apache2 is part of the Ubuntu repositories.  Just "sudo apt-get install apache2" from a terminal window.

---

### Post by Station on 2008-01-21
I see, this helps a lot. Thanks

now i am getting this

could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

---

### Post by peabody on 2008-01-22
either you already have an apache instance installed from source running on port 80 (which is what the error message is saying) or you're forgetting to run apache as root.  The method used to start apache on debian based systems (which includes Ubuntu) is:

sudo /etc/init.d/apache2 start

If you want the apache2 service to start automatically everytime you boot the machine, install the sysv-rc-conf package, run that as root from a terminal and turn the service on for run level 2.

---

### Post by Station on 2008-01-24
> **peabody said:**
> either you already have an apache instance installed from source running on port 80 (which is what the error message is saying) or you're forgetting to run apache as root.  The method used to start apache on debian based systems (which includes Ubuntu) is:

sudo /etc/init.d/apache2 start

If you want the apache2 service to start automatically everytime you boot the machine, install the sysv-rc-conf package, run that as root from a terminal and turn the service on for run level 2.


station@Homestation:/$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 5754) already running
                                                                         [ OK ]

yes I realize I may be taking a huge leap off a cliff!

---

### Post by peabody on 2008-01-24
> **Station said:**
> 
yes I realize I may be taking a huge leap off a cliff!

Not sure what you mean, but that message means apache is working.

---

### Post by Station on 2008-01-24
it means that I am really new at this. 

I have a friend, who has asked me to set up apache server to test the httpd files that I am supposed to download and backup. All in the attempts to learn how to navigate and teach myself Linux.

---

