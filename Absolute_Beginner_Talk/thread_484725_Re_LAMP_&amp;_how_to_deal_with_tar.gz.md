---
title: "Re: LAMP &amp; how to deal with tar.gz"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by maddie2120 on 2007-06-26
Hi there, I'm a complete newbie to Linux and Ubuntu, however I have been able to install LAMP through Synaptic Package Manager.  The question is how do I use it and access it?  I'm used to using WAMP (Windows, Apache, MySQL and PHP) on windows which has a desktop interface, my guess is that I'm going to have to access it through the terminal (a complete newie on me!) can anyone point me in the right direction of how to upload web pages and manage LAMP?

On an associated topic how do you install 'tar.gz' packages?.... Help please as I'm really impressed with Ubuntu and would like to learn how to use it properly.

Many thanks
Maddie :confused:

---

### Post by mattg89 on 2007-06-26
.tar.gz is just a compressed file, like .zip or .rar
to untar, just do in the command line:
```
tar xvfz <filename>
```

---

### Post by maddie2120 on 2007-06-26
Many thanks Mattg, I will have to give that a go!

Maddie :)

---

### Post by lazyart on 2007-06-26
sudo apt-get install ubuntu-desktop

if you want a gui.  or use webmin to administer from another machine.

---

### Post by tom1g on 2007-06-26
I also have question about LAMP... The thing is I can't install it!

Here are some instructions:

[http://www.apachefriends.org/en/xampp-linux.html#377](http://www.apachefriends.org/en/xampp-linux.html#377)

I pasted this in console:

tar xvfz xampp-linux-1.6.2.tar.gz -C /opt

 and I got this as a reply:

lampp/
tar: lampp: Cannot mkdir: Permission denied
lampp/backup/
tar: lampp/backup: Cannot mkdir: No such file or directory
lampp/bin/
tar: lampp/bin: Cannot mkdir: No such file or directory
lampp/bin/CA
tar: lampp/bin/CA: Cannot create symlink to `CA.pl': No such file or directory
lampp/bin/captoinfo
tar: lampp/bin/captoinfo: Cannot create symlink to `tic': No such file or directory
lampp/bin/infotocap
tar: lampp/bin/infotocap: Cannot create symlink to `tic': No such file or directory
lampp/bin/ldapadd
tar: lampp/bin/ldapadd: Cannot create symlink to `ldapmodify': No such file or directory
lampp/bin/libpng-config
tar: lampp/bin/libpng-config: Cannot create symlink to `libpng12-config': No such file or directory
lampp/bin/php-5.2.1
tar: lampp/bin/php-5.2.1: Cannot open: No such file or directory
tar: Skipping to next header
tar: Error exit delayed from previous errors

Help please

---

### Post by az on 2007-06-26
There is no desktop GUI interface to apache2 on linux.  When you install apache, it runs in the background.  It starts whenever you boot the system.


[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

To write to parts of the filesystem, you need sudo priveledges:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tom1g on 2007-06-26
Well, I just want to install LAMPP, I've been using xampp for a quite a while on my Windows machine, and I want get Apache running on Ubuntu, but I can't install LAMPP.

I'll try with this priviledges thing and then I'll crawl back here :D

---

### Post by LaRoza on 2007-06-26
> **tom1g said:**
> I also have question about LAMP... The thing is I can't install it!

tar xvfz xampp-linux-1.6.2.tar.gz -C /opt

Help please
```

sudo tar -xvfz xampp-linux-1.6.2.tar.gz -C /opt

```

---

### Post by tom1g on 2007-06-26
> **tom1g said:**
> Well, I just want to install LAMPP, I've been using xampp for a quite a while on my Windows machine, and I want get Apache running on Ubuntu, but I can't install LAMPP.

I'll try with this priviledges thing and then I'll crawl back here :D
Don't understand a word from [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
:(:(

---

### Post by tom1g on 2007-06-26
> **LaRoza said:**
> ```

sudo tar -xvfz xampp-linux-1.6.2.tar.gz -C /opt

```tar: z: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

Do I have to place tar.gz file on some special place? It is currently located at my folder, the same where "Desktop" is.

Edit: Oh yees! It is working! I typed "xvfz" instead of "-xvfz". Thanks a lot ;)

Edit 2: Another problem:
After entering this: /opt/lampp/lampp start
this is outputted: You need to start XAMPP as root!

Edit 3: I chaned user to root, but now i have some other problem with running it. I will try to solve it by myself :D

---

### Post by LaRoza on 2007-06-26
```

sudo lampp start

```

I do not know the command for XAMPP, but I am assuming it is lampp start. To run something as root in the terminal, type "sudo" before it.

Unlike Windows, everything you do is not as an administrator. You have to tell the OS that you want to act as root (admin, super user).

---

### Post by tom1g on 2007-06-26
No idea what's going wrong. Yeah, Thanks a lot XAMPP!!

Starting XAMPP for Linux 1.6.2...
/opt/lampp/share/lampp/phpstatus: line 4: /opt/lampp/bin/php: No such file or directory
XAMPP: Starting Apache with SSL ...
XAMPP: Error 127! Couldn't start Apache!
XAMPP: Starting diagnose...
XAMPP: Sorry, I've no idea what's going wrong.
XAMPP: Please contact our forum [http://www.apachefriends.org/f/](http://www.apachefriends.org/f/)
/opt/lampp/bin/mysql.server: 228: /opt/lampp/bin/my_print_defaults: not found
/opt/lampp/bin/mysql.server: 231: /opt/lampp/bin/my_print_defaults: not found
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP: /opt/lampp/lampp: line 302: /opt/lampp/sbin/proftpd: No such file or directory
XAMPP: Error 127! Couln't start ProFTPD!
XAMPP for Linux started.

---

### Post by tom1g on 2007-06-26
Guys please :|

---

### Post by maddie2120 on 2007-06-27
Thanks for all the advice, unfortunately none of it has worked, I still can't install the xampp-linux-1.6.2 tar.gz file, it downloads to my desktop.  I keep getting the following error message when I try to untar it as per instructions through the Konsole:

xxxxxxxxx@xxxxxxxxx-desktop:~$ sudo tar xvfz xampp-linux-1.6.2.tar.gz
Password:
tar: xampp-linux-1.6.2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
xxxxxxxxx@xxxxxxxxx-desktop:~$

Any help would be greatly appreciated
Maddie

---

### Post by maddie2120 on 2007-06-28
I found out what the problem was, I was in the wrong directory! I got some tips from the mailing list - one of which was to check which directory you're in by using the 'ls' command, helped loads!  It was plain sailing after that.

Many thanks
Maddie

---

