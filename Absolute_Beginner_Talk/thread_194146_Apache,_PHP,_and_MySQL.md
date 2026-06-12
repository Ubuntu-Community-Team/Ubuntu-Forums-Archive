---
title: "Apache, PHP, and MySQL"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by Ryan H on 2006-06-11
I am trying to install Apache, PHP, and MySQL on Ubuntu. I followed the steps [here]("https://wiki.ubuntu.com/ApacheMySQLPHP"), and Apache is working, I can look at files in my browser that are stored in /var/www, but when I try to excecute a .php file this error is allways returned:
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

I can't seem to figure it out?

-Ryan

---

### Post by Ahriman on 2006-06-11
[QUOTE=Ryan H]I am trying to install Apache, PHP, and MySQL on Ubuntu. I followed the steps [here]("https://wiki.ubuntu.com/ApacheMySQLPHP"), and Apache is working, I can look at files in my browser that are stored in /var/www, but when I try to excecute a .php file this error is allways returned:
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

I can't seem to figure it out?

-Ryan[/QUOTE]
It's a permission problem, basically: the server doesn't have the right permissions to look at or run the file.
if you right click on the file from in Nautilus, chosoe Properties, and in the permissions tab you can select Read for everyone, Write to Owner and Execute to everyone. That works for my server.
If you wanted to do it from the command line, the command is:
```
chmod 755 filename.php
```

---

### Post by Ryan H on 2006-06-11
That fixed it! But I thought I chmoded /var/www/ and all it subdirectories and files the same way, maybe not. Anyways how do I change the location of my htdocs file to something like /home/ryan/www ?

-Ryan

---

### Post by Ryan H on 2006-06-11
I've added > DocumentRoot /home/ryan/www to the apache2.conf file and still nothing is happening! Anyone know how to change this?

-Ryan

---

### Post by Ahriman on 2006-06-11
[QUOTE=Ryan H]I've added  to the apache2.conf file and still nothing is happening! Anyone know how to change this?

-Ryan[/QUOTE]
I'm pretty sure that if you create a folder in your home directory called public_html, you can access it normally by navigating too: [http://localhost/~username](http://localhost/~username)
BUT ... give this a try:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_map_URLs_to_folders_outside_.2Fvar.2Fwww.2F](http://easylinux.info/wiki/Ubuntu_dapper#How_to_map_URLs_to_folders_outside_.2Fvar.2Fwww.2F)

---

### Post by Ryan H on 2006-06-11
Thats exactly what I needed! But by default new files in that directory aren't chmoded so the browser can read them, how do I change this so all files and directories are set to a certain way?

-Ryan H

---

### Post by Ahriman on 2006-06-12
I have not yet found out how to make it do this automatically when you add a file in, I have gone into the terminal and run:
```
chmod -R 755 public_html
```
which sets the permissions recursively through the directory, but occasionally, like when I create a file from within PHP, the permissions are off and I have to set it manually.
I have set the public_html directory's permissions up as seen in the attachment, and I haven't noticed any problems since, although I don't know if setting the User and Group ID's does, in fact, do anything.

---

### Post by Randomskk on 2006-06-12
To change the document root, you need to change the DocumentRoot value in /etc/apache2/sites-available/default; this is your default virtual host and that's where the docroot is stored.
The command umask will set what permissions files are made with by default, however an easier way to do what you want is to add Apache to your group, or change your own group to Apache, so that apache can read the files.
(nb: for that to work, all files need to be made with group read access)

---

### Post by Ryan H on 2006-06-13
Alright, I'll try that. The final thing is when I click on a php file it asks what I want to do with it (Run in Terminal, Display, Cancel, Run) and I want it to allways be set to Display, so when I click on a php file it is automaticaly displayed.

-Ryan

---

### Post by Ryan H on 2006-06-15
Bump?

---

### Post by Ahriman on 2006-06-16
If you open Nautilus, go to Edit -> Preferences, and choose the Behavior Tab.

In the middle of that window, there is a section marked "Executable Text Files"

Make sure that "view executable files when clicked" is checked. and click Close

---

### Post by rootleafhmmm on 2006-06-16
[QUOTE=Ryan H]Bump?[/QUOTE]

Hi, I was wondering if anybody could show me how to limit access to an Apache2 web server. Something like that it would require a user to login. Is there such a way?

---

### Post by rootleafhmmm on 2006-06-16
Any idea how to make Apache authenticate such as it would ask for a username and password?

---

### Post by nitin_mz on 2006-06-16
[QUOTE=rootleafhmmm]Any idea how to make Apache authenticate such as it would ask for a username and password?[/QUOTE]

Create a .htaccess file in your document root.
[Wiki link](https://wiki.ubuntu.com/ApacheMySQLPHP#head-c353cd3c0a06dae032ab869150ffab7911ede57e)

---

### Post by indytim on 2006-06-16
Ryan,

Your're running a web server (Apache).  No longer in  the point-and-click world.    Open a browser and http://localhost/<foldername>/<file name>  ie 
[http://localhost/test/test.php](http://localhost/test/test.php)

Hope this helps.

IndyTim

---

### Post by Ryan H on 2006-06-17
I've been running Apache on Windows for the past 8 months before I got Linux. Thanks Ahriman, what you said worked! ^_^ Now I only have one more question: I have a static IP and I have port range forwarding for port 80 on my router, but when I try to connect to my IP address through port 80 it says it can't connect to the host. When I was on Windows I could do this, does anyone know how to fix it?

-Ryan

---

### Post by rootleafhmmm on 2006-06-17
thanks dude for the APache htaccess thing, it helped a lot. ;-)

---

### Post by Ahriman on 2006-06-19
[QUOTE=Ryan H]I've been running Apache on Windows for the past 8 months before I got Linux. Thanks Ahriman, what you said worked! ^_^ Now I only have one more question: I have a static IP and I have port range forwarding for port 80 on my router, but when I try to connect to my IP address through port 80 it says it can't connect to the host. When I was on Windows I could do this, does anyone know how to fix it?

-Ryan[/QUOTE]

Go to the terminal and type:
```
cat /etc/apache2/ports.conf
```
It should say something like:
Listen 80

If, instead, it says:

Listen 127.0.0.1:80

then open the file in a text editor (as sudo) and change it to be like the first one. You will have to restart Apache for the change to take effect
```
sudo /etc/init.d/apache2 restart
```

I have found that I can't access my server from within my local network from a domain address, because I keep getting forwarded to my router's configuration screen. If you are using your server's IP address, then that shouldn't be the problem, in which case, if the ports.conf file is OK, I don't know what the problem could be.

---

### Post by Ryan H on 2006-06-24
Sorry I haven't replied, I was away hiking. It says Listen 80 allready, anyone else have any ideas?

-Ryan

---

### Post by Ahriman on 2006-06-25
If you have Firestarter installed and running, you will most likely need to configure it to allow access to your system on port 80.
To do this:
Open the Firestarter screen, click on Policy. Make sure that in the "Editing" field the selected one is "Inbound traffic policy".
In the bottom box (Allow service for), right click and select "Add Rule".
In the window that appears next, select "HTTP" from the Name field, and leave the source as "Anyone".
Click Add, then up the top of the original Firestarter window, click "Apply Policy".

If you don't have a firewall running, or if that doesn't work, try this:
(assumes your IP address is 111.222.333.444)
```
telnet 111.222.333.444 80
GET /
```
If you see some HTML code, then your server is accessable on port 80. 

Also, can you connect to your server when you try: [http://localhost/](http://localhost/) ?

---

### Post by Ryan H on 2006-06-26
I can connect through [http://localhost/](http://localhost/) or [http://127.0.0.1/](http://127.0.0.1/), I don't have a Firewall, that I know of, unless Ubuntu comes with one. I typed in 
> ryan@ryan-linux:~$ telnet 205.147.111.213 80
Trying 205.147.111.213...
telnet: Unable to connect to remote host: Connection refused

But it didn't seem to work. . .

-Ryan

---

### Post by Ahriman on 2006-06-27
It might be a problem then with the port forwarding on your router. When I try and do this with my domain name and IP address, I get my router's login page. If I try it from, say, work, then I get my web server's index page.

If you have a look at [http://www.portforward.com/routers.htm](http://www.portforward.com/routers.htm) see if you can find your router listed there, it will tell you how to get port forwarding set up correctly.

---

### Post by Ryan H on 2006-06-27
I thought I had that working. I have a Linksys BEFSR41 v3.1. I attachted the screenshot which shows my current settings. When I enter my IP address [http://205.147.111.213/](http://205.147.111.213/) to try to access my web server it times out with saying
> The server at 205.147.111.213 is taking too long to respond.
But when I take out the port 80 on the Port Forwarding and enter my IP address it goes to my Router setup. I'm thinking maybe I don't have the right IP address set?

-Ryan

---

### Post by Ryan H on 2006-06-27
Bump

---

### Post by Ahriman on 2006-06-28
What do you get when you type this into the Terminal:

```
ifconfig
```

It will show up your IP address there (my result is below)
```
eth0      Link encap:Ethernet  HWaddr 00:50:8D:E1:3E:9D
          **inet addr:192.168.1.101**  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fee1:3e9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71472 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74838 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:34667324 (33.0 MiB)  TX bytes:5098660 (4.8 MiB)
          Interrupt:193 Base address:0x2000

```
so my IP address is 192.168.1.101.

Make sure that this IP matches the one in the router rule. Also, check to see if your IP is assigned by DHCP or is manually set. You can check by going System -> Administration -> Networking.

---

### Post by Ryan H on 2006-06-28
OMG! That works! Thank you so much! You all have been a big help! ^_^

-Ryan

---

### Post by alexohara1 on 2006-06-30
hi guys i followed the instructions on installing apache,php and mysql
im new to linux and ubuntu....
now what happened is that during setup i was setting the username and passwords and by accident i hit the enter key not setting everything up proberly...
now i cant access my sql .... so is there a way around this? i have tried re-installing over the installed version but the password and username are still set...and root is gone i have tried many combinations such as my new username and blank password or both even root and blank or root and my password...i muck up just after setting the username and during the password so i imagine the new username is set..but not the password...not sure...any ideas...
regards alex

---

