---
title: "XAMPP problem"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Onyx_47 on 2007-02-19
I downloaded and installed XAMPP. When I try to run it:

```
onyx@onyx-desktop:~$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.6...
/opt/lampp/share/lampp/phpstatus: line 4: /opt/lampp/bin/php: No such file or directory
XAMPP: Starting Apache with SSL ...
XAMPP: Error 127! Couldn't start Apache!
XAMPP: Starting diagnose...
XAMPP: Sorry, I've no idea what's going wrong.
XAMPP: Please contact our forum http://www.apachefriends.org/f/
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP: /opt/lampp/lampp: line 302: /opt/lampp/sbin/proftpd: No such file or directory
XAMPP: Error 127! Couln't start ProFTPD!
XAMPP for Linux started.

```

Anyone else had that problem?

---

### Post by annda on 2007-02-19
why not install apache2 php and mysql through synaptic? it is easier...

---

### Post by Onyx_47 on 2007-02-19
> **annda said:**
> why not install apache2 php and mysql through synaptic? it is easier...

Bandwidth limit :( I hate my ISP...

I downloaded XAMPP at college, so...

---

### Post by n8bounds on 2007-02-19
I've only ever used XAMPP on windows because of how ridiculously easy it is to set it up "for real" on linux, as annda mentioned...

you could trace down all the dependencies and download the .debs individualls at college or whatever and bring those home....

---

### Post by vuurst on 2007-03-11
> **Onyx_47 said:**
> I downloaded and installed XAMPP. When I try to run it:

```
onyx@onyx-desktop:~$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 1.6...
/opt/lampp/share/lampp/phpstatus: line 4: /opt/lampp/bin/php: No such file or directory
XAMPP: Starting Apache with SSL ...
XAMPP: Error 127! Couldn't start Apache!
XAMPP: Starting diagnose...
XAMPP: Sorry, I've no idea what's going wrong.
XAMPP: Please contact our forum http://www.apachefriends.org/f/
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP: /opt/lampp/lampp: line 302: /opt/lampp/sbin/proftpd: No such file or directory
XAMPP: Error 127! Couln't start ProFTPD!
XAMPP for Linux started.

```

Anyone else had that problem?

HI,

Yes I do have the same problem.
On my machine an AMD64, running Fedora Core 6 (sorry, no Ubuntu (yet)), I installed XAMPP version 1.6. It gives me the problem as you described above.
The weird thing is that on that same machine, but running Fedora Core 5, I've ran Xampp 1.5.5a without any problem. BUt if I try to re-install that version the same errormessage pops up. :mad: 

I've searched the internet, and saw some other people who experienced the same problem, but nowhere a solution is described.

The weird thing is that you can see the file /opt/lampp/bin/php (a symlink to /opt/lampp/bin/php-5.2.1, which you can also just list).
I've checked all the rights both on the files and on the directories. And tried it both as root and user.

The only explenation I can come up with is that I am running fedora core 6 in pure 64 bit mode now, and not mixed with 32. While xampp is compiled as 32bit application.

```
[COLOR="Blue"][root@linux1 bin]# file php-5.2.1
php-5.2.1: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.0.0, stripped[/COLOR]
```

But I do not know if this would also be a reason to give the errormessage "No such file or directory"? :confused: 

If someone has the solution for these problems post them to this and other forums, or mail me at [email]john@johnvandervuurst.nl[/email]

Greetings,

John van der Vuurst
Uithoorn, The Netherlands
[http://www.johnvandervuurst.nl/wiki]("http://www.johnvandervuurst.nl/wiki")

---

### Post by vuurst on 2007-03-11
> **vuurst said:**
> HI,

Yes I do have the same problem.
On my machine an AMD64, running Fedora Core 6 (sorry, no Ubuntu (yet)), I installed XAMPP version 1.6. It gives me the problem as you described above.
The weird thing is that on that same machine, but running Fedora Core 5, I've ran Xampp 1.5.5a without any problem. BUt if I try to re-install that version the same errormessage pops up. :mad: 

I've searched the internet, and saw some other people who experienced the same problem, but nowhere a solution is described.

The weird thing is that you can see the file /opt/lampp/bin/php (a symlink to /opt/lampp/bin/php-5.2.1, which you can also just list).
I've checked all the rights both on the files and on the directories. And tried it both as root and user.

The only explenation I can come up with is that I am running fedora core 6 in pure 64 bit mode now, and not mixed with 32. While xampp is compiled as 32bit application.

```
[COLOR="Blue"][root@linux1 bin]# file php-5.2.1
php-5.2.1: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.0.0, stripped[/COLOR]
```

But I do not know if this would also be a reason to give the errormessage "No such file or directory"? :confused: 

If someone has the solution for these problems post them to this and other forums, or mail me at [email]john@johnvandervuurst.nl[/email]

Greetings,

John van der Vuurst
Uithoorn, The Netherlands
[http://www.johnvandervuurst.nl/wiki]("http://www.johnvandervuurst.nl/wiki")


Yes!!! Success!

On a different forum I found a topic not XAMPP related, but with about the same problems.

The solution was a bit cryptical to install ia-32 libraries.
(ia-32 = intel architecture 32bit).
I checked my system and I had as expected for a pure 64bit machine only ELF 64bit libraries.
I installed the ELF 32bit libraries and that solved the problem!!

But I still find it a weird error, I rather expected an more descriptive error as "Unsupported executable file format" or something like that...

But now I can start XAMPP 1.6

```
[root@linux1 synaptic-0.57]# /opt/lampp/lampp start
Starting XAMPP for Linux 1.6...
XAMPP: Starting Apache with SSL (and PHP5)...
[B]XAMPP: Error 1! Couldn't start Apache!
XAMPP: Starting diagnose...
XAMPP: Make the httpd.conf fit your system.[/B]
XAMPP: Next try...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Another FTP daemon is already running.
XAMPP for Linux started.
```

Good luck!

John van der Vuurst

---

### Post by noordung on 2008-01-02
I'm an Ubuntu (and Linux) newbie and I have the same problem: where can I find, how can I install and use the ELF 32bit library?:confused:

---

