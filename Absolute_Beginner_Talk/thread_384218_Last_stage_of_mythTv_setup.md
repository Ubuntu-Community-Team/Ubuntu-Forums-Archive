---
title: "Last stage of mythTv setup"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by arnabbiswas on 2007-03-14
I am so close that I can almost touch it..

I have finally been able to run mythtv setup after numerous problems with mysql connectivity. 

After starting the mythbackend when I run mythfrontend and I try to watch TV, I get the following error:

pom@pom-desktop:~$ mythfrontend
2007-03-14 07:33:35.329 Using runtime prefix = /usr
2007-03-14 07:33:35.387 Gnome-Screensaver support enabled
2007-03-14 07:33:35.388 DPMS is not supported.
2007-03-14 07:33:35.485 New DB connection, total: 1
2007-03-14 07:33:35.530 Connected to database 'mythconverg' at host: localhost
2007-03-14 07:33:35.533 Total desktop dim: 1274x738, with 1 screen[s].
2007-03-14 07:33:35.538 Using screen 0, 1274x738 at 0,0
2007-03-14 07:33:35.754 Current Schema Version: 1160
2007-03-14 07:33:35.755 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-03-14 07:33:35.755 Enabled verbose msgs:  important general
2007-03-14 07:33:36.301 Total desktop dim: 1274x738, with 1 screen[s].
2007-03-14 07:33:36.303 Using screen 0, 1274x738 at 0,0
2007-03-14 07:33:36.304 Switching to square mode (G.A.N.T.)
2007-03-14 07:33:36.320 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-03-14 07:33:36.918 Joystick disabled.
2007-03-14 07:33:37.845 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2007-03-14 07:33:37.988 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-03-14 07:33:38.052 Registering Internal as a media playback plugin.
2007-03-14 07:33:50.639 New DB connection, total: 2
2007-03-14 07:33:50.641 Connected to database 'mythconverg' at host: localhost
2007-03-14 07:33:50.698 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-03-14 07:33:50.698 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.
2007-03-14 07:33:52.082 TV: Attempting to change from None to None
2007-03-14 07:33:54.361 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-03-14 07:33:54.361 Connection timed out.          
                        You probably should modify the Master Server 
                        settings in the setup program and set the    
                        proper IP address.

Any ideas on how to modify the Master Server settings in the setup program and set the proper IP address?

---

### Post by omockler on 2007-03-14
I've had myth tv set up for a few weeks now and I was getting that same message when I tried to run mythfrontend on a different computer.

You might looking at this page:
[http://mythtv.org/docs/mythtv-HOWTO-6.html#ss6.2]("http://mythtv.org/docs/mythtv-HOWTO-6.html#ss6.2")

---

### Post by ifross on 2007-03-14
Do you have the frontend on a different machine to the backend you are trying to connect to?

If so, the frontend is trying to connect to the local mysql server (localhost) when it should be connecting to the remote host...

I have set up a backend server with a front end separately so if this is the case I will be able to help... The poster above's website is very good but not very secure... I can outline how I did it which is probably more secure, if you need it.

---

### Post by ifross on 2007-03-14
Well I think that you need to do a few things before it will be done.
First, you need static IP addresses for the frontand and backend if you have not already done this...

edit the /etc/network/interfaces file on both machines(frontend and backend):
```
sudo nano /etc/network/interfaces
```
Then comment out the lines than refer to auto eth0 and add different ones...
```
#auto eth0
#iface eth0 inet dhcp

auto eth0
iface eth0 inet static
     address 192.168.0.55
     netmask 255.255.255.0
     network 192.168.0.0
     broadcast 192.168.0.255
     gateway 192.168.0.1


```

Note: change the "192.168.0.55" to the IP you want for each machine (make sure they are different!!)

Then add lines to your /etc/hosts file on both machines.
```
sudo nano /etc/hosts
```
add these lines to both (remember to change the IP address for the actual IPs and you can change the hostnames to what you want!)
```
192.168.0.101   mythtv-backend
192.168.0.55   mythtv-frontend

```


THEN, on your **backend**, you need to add the frontend so it can access the mysql database:
```
mysql -uroot -p mythconverg
[enter mysql root password (default blank)]
>grant all privileges on mythconverg.* to mythtv@mythtv-frontend identified by "password";
>flush privileges;
>exit;

```

Note: change password to something else and make sure you use semi-colons at the end of each line!

Then on your frontend, you need to edit your ~/.mythtv/mysql.txt
```

gedit ~/mythtv/mysql.txt

```

Then edit the first few lines to look like this:
```

DBHostName=mythtv-backend
DBUserName=mythtv
DBPassword=password
DBName=mythconverg
DBType=QMYSQL3

```

Then fire up the frontend and fingers crossed it will work.

If this doesn't work, post the errors and I'll try and help, I've never tried to help anyone on anything computer related before so I will have probably made loads of errors! 

Good luck :) mythtv is great when set up properly, even if it is dificult to set up.

---

