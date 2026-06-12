---
title: "apache/php/mysql"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by rlynch on 2006-08-01
So I used WAMP when I was on XP, but now I gotta install them all seperately.

So I go to the ubuntuguide.org and setup apache, i see it's running in the process list. . .but it's not working. I have a testphp.php file in the /var/www folder, and still nothing. It just keeps trying to load it.

Also I see this
```

    * To test if php5 installed correctly 

sudo gedit /var/www/testphp.php

    * Insert the following line into the new file 

<?php phpinfo(); ?>

    * Save the edited file
    * http://localhost/testphp.php
    * Be sure to remove the file afterwards, as it may pose a security risk 

```


But even thought I can't go to localhost/testphp.php to view it, it doesnt let me edit it or delete it.

I try sudo gedit /var/www/testphp2.php, and the terminal just sits there at the new line I create when pressing enter


Thanks in advanced to anyone who can help with this issue.

---

### Post by louieb on 2006-08-01
[FONT=Arial Black][SIZE=3]Try [/SIZE][/FONT][FONT=Arial Black][SIZE=3][COLOR=DarkGreen]gksudo gedit /var/www/testphp2.php[/COLOR][/SIZE][/FONT][FONT=Arial Black][SIZE=3]   something to do with sudo and graphical stuff. I just go finished installing a web development server. check out this post it helped me a lot. [http://www.ubuntuforums.org/showthread.php?t=223410](http://www.ubuntuforums.org/showthread.php?t=223410)[/SIZE][/FONT]

---

### Post by rlynch on 2006-08-01
So I'd like to start from the beginning. I uninstalled everything(but still see apache2 running in the background. I went to Synaptic and uninstalled apache2, php, and mysql.

I figure if I uninstall everything, get things working one thing at a time instead of all at once it would be the ideal thing to do.

So if apache2 is uninstalled from Synaptic, why is it still running in the process list? If I kill them, they just respawn with new pid #'s. But that means it's installed and running. Why can't I go to [http://localhost](http://localhost) and view the demo index.html doc I have put into /var/www?

If I put /var/www/index.html into firefox, it views the html that way

Any ideas on things I can check to get this up and running? Thanks in advanced.

---

### Post by rlynch on 2006-08-01
oopps

---

### Post by rlynch on 2006-08-02
also, I thought it was odd, that when I restart, and go open the system monitor to view the processes running, theres anywhere from 4-8 apache2 processes/daemons running, any reason?

and on top of that, none 'work' since all my requests to [http://localhost](http://localhost) time out


i always thought it would be easier to setup a web server on *nix over Windows. . .But I can't seem to get it working on here.

---

### Post by rlynch on 2006-08-02
bump. . .so yea, anyone able to help me start this all over from scratch? I figure if I can get apache up and running at least I can see it works, and can build(add php and mysql) on from there. . .


thanks in advanced

---

### Post by az on 2006-08-02
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by rlynch on 2006-08-02
> **azz said:**
> [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I have bookmarked this page. How can I uninstall/wipe everything that's installed and setup now. I'd rather not just delete the folders and have services try to start when they can't. Plus I'd probably delete the wrong things.

Thanks in advanced.

---

### Post by rlynch on 2006-08-02
after re-booting, and seeing apache2 running, yet again(after an sudo apt-get --purge remove apache2 command). i try to stop it, and notice it's being run under root, while my account username is 'rlynch'

could this be an issue with me not being able to view html docs via [http://localhost?](http://localhost?)

when I shut the root process of apache2 down, and try to start apache under my account(rlynch), and I get this error
```
rlynch@laptop:/usr/sbin$ apache2 -k start apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

```

---

### Post by az on 2006-08-03
> **rlynch said:**
> after re-booting, and seeing apache2 running, yet again(after an sudo apt-get --purge remove apache2 command). i try to stop it, and notice it's being run under root, while my account username is 'rlynch'

could this be an issue with me not being able to view html docs via [http://localhost?](http://localhost?)]

No.

> **rlynch said:**
> 

when I shut the root process of apache2 down, and try to start apache under my account(rlynch), and I get this error
```
rlynch@laptop:/usr/sbin$ apache2 -k start apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

```

Something else is using port 80.  Apache (version 1.3) or skype?  You only want apache2 running.  Check to see if you have both apache and apache2 installed.  Remove apache if that is the case.

---

### Post by rlynch on 2006-08-03
Here is my ps -ef results.


```
rlynch@laptop:~$ ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Aug02 ?        00:00:01 init [2]
root         2     1  0 Aug02 ?        00:00:00 [ksoftirqd/0]
root         3     1  0 Aug02 ?        00:00:00 [watchdog/0]
root         4     1  0 Aug02 ?        00:00:00 [events/0]
root         5     1  0 Aug02 ?        00:00:00 [khelper]
root         6     1  0 Aug02 ?        00:00:00 [kthread]
root         8     6  0 Aug02 ?        00:00:00 [kblockd/0]
root         9     6  0 Aug02 ?        00:00:00 [kacpid]
root       125     6  0 Aug02 ?        00:00:00 [aio/0]
root       124     1  0 Aug02 ?        00:00:06 [kswapd0]
root       712     6  0 Aug02 ?        00:00:00 [kseriod]
root      1790     6  0 Aug02 ?        00:00:19 [kacpid-work-0]
root      1791     6  0 Aug02 ?        00:00:02 [kacpid-work-1]
root      1792     6  0 Aug02 ?        00:00:00 [kacpid-work-2]
root      1793     6  0 Aug02 ?        00:00:00 [kacpid-work-3]
root      1794     6  0 Aug02 ?        00:00:00 [kacpid-work-4]
root      1795     6  0 Aug02 ?        00:00:00 [kacpid-work-5]
root      1796     6  0 Aug02 ?        00:00:00 [kacpid-work-6]
root      1797     6  0 Aug02 ?        00:00:00 [kacpid-work-7]
root      1798     6  0 Aug02 ?        00:00:00 [kacpid-work-8]
root      1799     6  0 Aug02 ?        00:00:00 [kacpid-work-9]
root      1881     6  0 Aug02 ?        00:00:00 [khubd]
root      1889     1  0 Aug02 ?        00:00:00 [khpsbpkt]
root      1895     1  0 Aug02 ?        00:00:00 [knodemgrd_0]
root      1962     1  0 Aug02 ?        00:00:06 [kjournald]
root      2193     1  0 Aug02 ?        00:00:00 /sbin/udevd --daemon
root      2963     1  0 Aug02 ?        00:00:00 [shpchpd_event]
root      3132     1  0 Aug02 ?        00:00:00 [pccardd]
root      3517     6  0 Aug02 ?        00:00:25 [wrapper_wq]
dhcp      3548     1  0 Aug02 ?        00:00:00 dhclient3 -pf /var/run/dhclient.
root      3850     1  0 Aug02 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/eve
root      3962     1  0 Aug02 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /v
klog      3964     1  0 Aug02 ?        00:00:00 /sbin/klogd -P /var/run/klogd/km
root      4284     1  0 Aug02 ?        00:00:00 /usr/sbin/gdm
root      4313  4284  0 Aug02 ?        00:00:00 /usr/sbin/gdm
root      4318  4313  1 Aug02 tty7     00:23:36 /usr/bin/X :0 -br -audit 0 -auth
104       4423     1  0 Aug02 ?        00:00:01 /usr/bin/dbus-daemon --system
108       4438     1  0 Aug02 ?        00:00:01 /usr/sbin/hald
root      4439  4438  0 Aug02 ?        00:00:00 hald-runner
108       4444  4439  0 Aug02 ?        00:00:00 /usr/lib/hal/hald-addon-acpi
108       4498  4439  0 Aug02 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard
108       4508  4439  0 Aug02 ?        00:00:07 /usr/lib/hal/hald-addon-storage
108       4509  4439  0 Aug02 ?        00:00:06 /usr/lib/hal/hald-addon-storage
root      4722     1  0 Aug02 ?        00:00:01 /usr/sbin/powernowd -q
root      4743     1  0 Aug02 ?        00:00:00 /usr/sbin/sshd
root      4802     1  0 Aug02 ?        00:00:00 hcid: processing events
root      4806     1  0 Aug02 ?        00:00:00 /usr/sbin/sdpd
root      4821     1  0 Aug02 ?        00:00:00 [krfcommd]
root      4834     1  0 Aug02 ?        00:00:00 /sbin/mdadm -F -i /var/run/mdadm
daemon    4869     1  0 Aug02 ?        00:00:00 /usr/sbin/atd
root      4882     1  0 Aug02 ?        00:00:00 /usr/sbin/cron
root      4994     1  0 Aug02 tty1     00:00:00 /sbin/getty 38400 tty1
root      4995     1  0 Aug02 tty2     00:00:00 /sbin/getty 38400 tty2
root      4996     1  0 Aug02 tty3     00:00:00 /sbin/getty 38400 tty3
root      4997     1  0 Aug02 tty4     00:00:00 /sbin/getty 38400 tty4
root      4998     1  0 Aug02 tty5     00:00:00 /sbin/getty 38400 tty5
root      4999     1  0 Aug02 tty6     00:00:00 /sbin/getty 38400 tty6
rlynch    5010  4313  0 Aug02 ?        00:00:02 x-session-manager
rlynch    5052  5010  0 Aug02 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus
rlynch    5055     1  0 Aug02 ?        00:00:00 /usr/bin/dbus-launch --exit-with
rlynch    5056     1  0 Aug02 ?        00:00:02 dbus-daemon --fork --print-pid 8
rlynch    5058     1  0 Aug02 ?        00:00:02 /usr/lib/libgconf2-4/gconfd-2 5
rlynch    5061     1  0 Aug02 ?        00:00:00 /usr/bin/gnome-keyring-daemon
rlynch    5063     1  0 Aug02 ?        00:00:00 /usr/lib/bonobo-activation/bonob
rlynch    5065     1  0 Aug02 ?        00:00:13 /usr/lib/control-center/gnome-se
rlynch    5081     1  0 Aug02 ?        00:00:00 /usr/bin/esd -terminate -nobeeps
rlynch    5085     1  0 Aug02 ?        00:01:46 /usr/bin/metacity --sm-client-id
rlynch    5092     1  0 Aug02 ?        00:01:00 gnome-panel --sm-client-id defau
rlynch    5094     1  0 Aug02 ?        00:02:25 nautilus --no-default-window --s
rlynch    5097     1  0 Aug02 ?        00:00:02 gnome-volume-manager --sm-client
rlynch    5104     1  0 Aug02 ?        00:00:01 /usr/lib/gnome-vfs-2.0/gnome-vfs
rlynch    5106     1  0 Aug02 ?        00:00:06 update-notifier
rlynch    5110     1  0 Aug02 ?        00:00:09 /usr/lib/gnome-applets/trashappl
rlynch    5114     1  0 Aug02 ?        00:00:04 gnome-cups-icon --sm-client-id d
rlynch    5133     1  0 Aug02 ?        00:00:05 gnome-power-manager
rlynch    5141     1  0 Aug02 ?        00:00:00 /usr/lib/nautilus-cd-burner/mapp
rlynch    5144     1  0 Aug02 ?        00:00:05 /usr/lib/gnome-applets/mixer_app
rlynch    5146     1  0 Aug02 ?        00:00:02 /usr/lib/gnome-panel/clock-apple
rlynch    5148     1  0 Aug02 ?        00:00:06 /usr/lib/gnome-netstatus/gnome-n
rlynch    5165     1  0 Aug02 ?        00:01:01 gnome-screensaver
rlynch    5592     1  0 Aug02 ?        00:00:09 /usr/lib/notification-daemon/not
rlynch    6757     1  0 Aug02 ?        00:00:36 gaim
rlynch   16068     1  0 01:52 ?        00:00:01 /usr/bin/artsd -F 10 -S 4096 -s
root     19332     6  0 03:14 ?        00:00:00 [pdflush]
root     19421     6  0 03:16 ?        00:00:00 [pdflush]
cupsys   27203     1  0 07:43 ?        00:00:00 /usr/sbin/cupsd
syslog   27308     1  0 07:43 ?        00:00:00 /sbin/syslogd -u syslog
rlynch   12755     1  6 19:20 ?        00:03:04 /usr/lib/firefox/firefox-bin -a
rlynch   13860     1 17 20:04 ?        00:00:11 gnome-system-monitor
rlynch   13881     1  6 20:05 ?        00:00:01 gnome-terminal
rlynch   13883 13881  0 20:05 ?        00:00:00 gnome-pty-helper
rlynch   13884 13881  1 20:05 pts/0    00:00:00 bash
rlynch   13912 13884  0 20:05 pts/0    00:00:00 ps -ef

```


If apache or skype is installed, I am not aware of it.

When I go to synaptic. Search for 'skype'. It says it's not installed.
When I search for apache. The only thing installed is.

- libar0 - The apache Portable Runtime
- libcommons-cli-java - API for working the command line arguments
- libjaxp1.2-java - Java XML parser and transformer
- liblog4j1.2-java - Logging library for java
- libservlet2.3-java - Servlet 2.3 and JSP 1.2 Java classes
- libssl0.9.8 - SSK shared libraries
- libxalan2-java - XSL Transformations processor in Java
- libxerces2-java - Validating XML parser for Java with DOM level 3


But isn't that permission denied because I didn't put sudo in front of it?
Due to my rlynch account not having high enough permission level? I assume it's supposed to be that way, but I did that test just to see if my account could start apache2, and see if because it was ran at root level, that was the reason it wasn't working for my account(since it's not root), but you said no, it doesn't matter that it's being run as root.


I am normally pretty linux savy, with compiling, shell commands, etc. But this Ubuntu design, with having to do the sudo, and permissions things, have me confused. I normally run as root when using linux. I tried RH 7.2 back in the day, and even mandrake at one point. But due to it not seeing my wireless I had to go back to Windows.

Thanks for you taking the time to help. Let me know if there is anything else I can do. I would love to be able to start over from scratch, remove/delete etc everything involving apache, php, and mysql. I'm thinking that would be the way to go. But I don't know how, and don't want to mess the kernel up by deleting stuff that's supposed to be there.


I gotta know, why apache2 starts, and I'm able to turn it on and off, when I dont even have apache or apache2 installed. I even tried lampp and one point, but removed it since I couldn't get it to work either.

---

### Post by rlynch on 2006-08-03
and here is my /etc/hosts file. I hear that needs to be configured a certain way.

```
127.0.0.1 localhost laptop
127.0.1.1 laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```


EDIT, lol. and don't think im trying to use apache without it being installed. It's just at this time I removed everything trying to start from scratch. I had just noticed apache ran with the boot, and I was able to start and stop it without it showing it's installed via synaptic.

---

### Post by harisund on 2006-08-03
If you know want to know what is listening on port 80 do ```
sudo netstat -plant
```

---

### Post by harisund on 2006-08-03
So you want to start fresh? 

[http://ubuntuforums.org/showpost.php?p=1334336&postcount=6](http://ubuntuforums.org/showpost.php?p=1334336&postcount=6)

---

### Post by rlynch on 2006-08-03
> **harisund said:**
> If you know want to know what is listening on port 80 do ```
sudo netstat -plant
```


here's the output of that command
```
rlynch@laptop:/usr/sbin$ sudo netstat -plant
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.1.101:43249     205.188.210.74:5190     ESTABLISHED6757/gaim
tcp        0      0 192.168.1.101:47434     72.14.209.104:80        ESTABLISHED12755/firefox-bin
tcp        0      0 192.168.1.101:40920     64.12.31.226:5190       ESTABLISHED6757/gaim
tcp6       0      0 :::80                   :::*                    LISTEN     15148/apache2
tcp6       0      0 :::22                   :::*                    LISTEN     4743/sshd

```


this is after I do a sudo /usr/sbin/apache2 -k start. So apache2 is now running in the background. Yet nothing happens when I go to [http://localhost](http://localhost)

---

### Post by harisund on 2006-08-03
Looks like it would indeed be better if you could purge apache2 and its helper files first, and reinstall. 

That, and do not start apache2 with the command you used. Instead  use ```
sudo /etc/init.d/apache2 restart
```

---

### Post by rlynch on 2006-08-03
I have done this fully remove and reinstall commands you linked.

I redo the netstat and the output is
```
rlynch@laptop:/usr/sbin$ sudo netstat -plant
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN     17308/mysqld
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     17042/master
tcp        0      0 192.168.1.101:43249     205.188.210.74:5190     ESTABLISHED6757/gaim
tcp        0      0 192.168.1.101:36826     64.233.185.19:80        ESTABLISHED12755/firefox-bin
tcp        0      0 192.168.1.101:58764     64.233.185.83:80        ESTABLISHED12755/firefox-bin
tcp        0      0 192.168.1.101:36480     66.249.81.99:80         ESTABLISHED12755/firefox-bin
tcp        0      0 192.168.1.101:40920     64.12.31.226:5190       ESTABLISHED6757/gaim
tcp6       0      0 :::80                   :::*                    LISTEN     16802/apache2
tcp6       0      0 :::22                   :::*                    LISTEN     4743/sshd

```

But [http://localhost](http://localhost) still does nothing, and I have a index.html file there. I can do [http://localhost/blah.txt](http://localhost/blah.txt) which is a txt file of random characters. And nothing shows up.

---

### Post by harisund on 2006-08-03
Ok do one thing. 

First purge the files (remember to have the 'purge' word in the command. Otherwise you are not really doing anything). 

After purging, look at netstat again and make sure nothing is listening on port 80. 

Also make sure /etc/apache2 folder doesn't exist. If it does, delete it. 

If you don't mind, back up your /var/www folder and delete that as well. 

Then can you give it a shot?

---

### Post by rlynch on 2006-08-03
ok, I did

```
sudo /etc/sbin/apache2 -k stop
```

then did

```
sudo /etc/init.d/apache2 start
```

And still nothing comes up when going to localhost

---

### Post by harisund on 2006-08-03
Did you try what I said one post above? I am guessing some configuration file is really messed up. 

Another thing I would suggest you try is ```
sudo a2enmod userdir
```What this does is allows each user to have a public web site. 

Then create a directory in your home directory called public_html, something like mkdir ~/public_html

Then put everything you have in /var/www in that public_html directory. 

Then, after making sure apache2 is running type in [http://localhost/~rlynch](http://localhost/~rlynch) in your browser (substitute rlynch with your username on the machine) and you should see the contents there.

---

### Post by rlynch on 2006-08-03
ok, purged again. /etc/apache2 is gone
i did 'sudo mv /var/www /home/rlynch/www'

nothing is running on port 80, and did the reinstall again

did 'sudo nano /var/www/blah.txt' and added some text. still nothing happens when going ot [http://localhost/blah.txt](http://localhost/blah.txt)

here is the netstat command now
```
rlynch@laptop:/etc$ sudo netstat -plant Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN     20047/mysqld
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     17042/master
tcp        0      1 192.168.1.101:39419     127.0.0.1:80            SYN_SENT   12755/firefox-bin
tcp        0      0 192.168.1.101:43249     205.188.210.74:5190     ESTABLISHED6757/gaim
tcp        0      0 192.168.1.101:59041     64.233.185.19:80        ESTABLISHED12755/firefox-bin
tcp        0      0 192.168.1.101:60982     66.249.81.147:80        ESTABLISHED12755/firefox-bin
tcp        0      0 192.168.1.101:54206     64.233.185.83:80        ESTABLISHED12755/firefox-bin
tcp        0      0 192.168.1.101:40920     64.12.31.226:5190       ESTABLISHED6757/gaim
tcp6       0      0 :::80                   :::*                    LISTEN     19775/apache2
tcp6       0      0 :::22                   :::*                    LISTEN     4743/sshd
```

---

### Post by rlynch on 2006-08-03
i did that
```
rlynch@laptop:/etc$ sudo a2enmod userdir
This module is already enabled!

```

so I do 'sudo mkdir /home/rlynch/public_html' then i go into /var/www and do 'sudo mv * /home/rlynch/public_html'

i see everything in the public html directory when doing an ls. but going to [http://localhost/~rlynch/blah.txt](http://localhost/~rlynch/blah.txt), which is a file in there, and still nothing happens. . .or even localhost/~rlynch and nothing happens

---

### Post by harisund on 2006-08-03
This is most absurdly curiously strange.

Do you have a firewall? An iptables or firestarter or something?

---

### Post by benmoreassynt on 2006-08-03
I've not followed this entire thread, but just to throw in an idea - why not use XAMPP ([http://www.apachefriends.org/en/xampp.html)](http://www.apachefriends.org/en/xampp.html)).

It's a really easy way to install PHP 4 and 5, Apache and MySQL which does not require any prior knowledge.

It's perfect for developers. Not sure how it works as a server in the 'real world', but I doubt that is what you are looking for.

Good luck

Ben

---

### Post by rlynch on 2006-08-03
I have tried, and get the same issue with apache as I do here.

I don't have any firewall, that I am aware of. 

```
rlynch@laptop:/var/www$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```


I am told that means no firewall is on. I don't know what firestarter is.

I read that in apache2.conf there is a spot to configure user and group. That's supposed to be changed to whatever user and group I am in(from what I read). Right now the user and group is 'www-data' if that means anything I do not know. But yes, this is driving me crazy.

---

### Post by rlynch on 2006-08-03
Here is my netstat again. Shouldnt there be an ip address for the local address. Instead of :::80, shouldnt it be something like 127.0.0.1:80 for apache, and the same for mysqld, shouldnt it be 127.0.0.1:3306, and not 0.0.0.0:3306?

```
rlynch@laptop:/etc/apache2$ sudo netstat -plant
sudo: unable to lookup laptop via gethostbyname()
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN     20047/mysqld
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     17042/master
tcp        0      0 192.168.1.101:43249     205.188.210.74:5190     ESTABLISHED6757/gaim
tcp        0      0 192.168.1.101:38896     66.249.81.147:80        ESTABLISHED12755/firefox-bin
tcp        0      1 192.168.1.101:44258     127.0.0.1:80            SYN_SENT   12755/firefox-bin
tcp        0      1 192.168.1.101:44257     127.0.0.1:80            SYN_SENT   12755/firefox-bin
tcp        0      0 192.168.1.101:37140     216.239.51.181:80       ESTABLISHED12755/firefox-bin
tcp        0      0 192.168.1.101:40920     64.12.31.226:5190       ESTABLISHED6757/gaim
tcp6       0      0 :::80                   :::*                    LISTEN     25422/apache2
tcp6       0      0 :::22                   :::*                    LISTEN     4743/sshd

```


or maybe even 192.168.1.101:80/192.168.1.101:3306? like the others. . .

---

### Post by rlynch on 2006-08-04
I changed the ports.conf to 192.168.1.101, restarted apache, and [http://192.168.1.101](http://192.168.1.101) does not work. I change it to 127.0.0.1:80 and I get an error.


this is what it says with 192.etc
```
rlynch@laptop:/etc/apache2$ sudo /etc/init.d/apache2 stop
 * Stopping apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
^[[A^[[A^[[A^[[A                                                                                                      [ ok ]
rlynch@laptop:/etc/apache2$ sudo /etc/init.d/apache2 start
 * Starting apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                                                                      [ ok ]

```
and doesnt work

and this is set to 127.etc
```
rlynch@laptop:/etc/apache2$ sudo /etc/init.d/apache2 start
 * Starting apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(99)Cannot assign requested address: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs
                                                                                                                      [fail]
```

that really confuses me

---

### Post by rlynch on 2006-08-04
wow, so I turn on my eth0 network connection, and localhost works now!!!!!!!!!!!!!!!!!!!!!!!!


that is rather odd. before i only had wlan0 on(unless i go to copy something to the other computer via ftp, then i'll connect the ethernet to the desktop)

so that's rather odd. what i did was pull the ethernet cable from the cable modem to the router, plugged it into the laptop, and rebooted. i did get a LONG pause of reloading postfix something, but after booting back up, i enabled eth0, STILL didn't get internet. . .but localhost worked for apache. i unplug the cable from the laptop, hook the router and cable modem up, re-enable wlan0, keep eth0 enabled, even though the cable is disconnected. both internet works and so does localhost/apache!!!!!!!!!!

i see php works with it too!, and i should be able to configure mysql, add a user, and import my database. thanks a lot guys to all of you who helped.

once i get my home web server setup, and get my php script copied over(doing a digg.com clone), i will be sure to add all of you who helped into the readme

---

### Post by rlynch on 2006-08-04
when I go to phpmyadmin i see
The configuration file now needs a secret passphrase (blowfish_secret).

---

### Post by rlynch on 2006-08-04
I did this

[http://www.ubuntuforums.org/showpost.php?p=1203635&postcount=4](http://www.ubuntuforums.org/showpost.php?p=1203635&postcount=4)

and stopped/started mysql, i still get that error on phpmyadmin
??????
so close i can almost taste it

---

### Post by rlynch on 2006-08-04
after doing the link above, im supposed to reboot, and that fixes it.


now i get
 MySQL said: Documentation
#1045 - Access denied for user 'root'@'localhost' (using password: YES)

---

### Post by rlynch on 2006-08-04
So I fixed that. . .and TADA!!!!! everything is working well!

Thanks a LOT guys.

---

