---
title: "How to install pine in Ubuntu"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-02-15
I am new to Ubuntu but have been using unix/linux for about a year now.  I am big fan of the program pine and am very shocked that Ubuntu does not include it. I would greatly appreciate if you could tell me how I can get Pine and go through the steps how to install it etc. 

Thank you

:popcorn:

---

### Post by IYY on 2007-02-15
```
sudo apt-get install pine
```

should do it. 

For configuration, I think it has help files, and a website.

---

### Post by taurus on 2007-02-15
You have two options:

1.  Download the .rpm and use alien to convert it to .deb and install it

```
sudo aptitude update
sudo aptitude install alien
alien **filename.rpm**
sudo dpkg -i **filename.deb**
```

[http://www.washington.edu/pine/getpine/linux.html](http://www.washington.edu/pine/getpine/linux.html)

2.  Download the source and install it by hand.

```
sudo aptitude update
sudo aptitude install build-essential
```

[http://www.washington.edu/pine/getpine/unix.html](http://www.washington.edu/pine/getpine/unix.html)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by jprb85 on 2007-02-15
I did exactly what you said but cannot get pine to install. This is the message I get.  

sudo apt-get install gnome-system-monitor
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-system-monitor is already the newest version.
The following packages were automatically installed and are no longer required:
  libwww-ssl0 librasqal0 libraptor1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jprblinux@jprblinux-desktop:~$ sudo apt-get install pine
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package pine is not available, but is referred to by another package.


I would greatly appreciate if you could tell me what I need to do now. Thank you. 
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package pine has no installation candidate
jprblinux@jprblinux-desktop:~$ pine
bash: pine: command not found

---

### Post by sardion on 2007-02-16
Pine cannot be distributed in binary form.  UW doesn't allow it with the license they put on it, so it cannot be legally included in ubuntu.

[http://www.washington.edu/pine/getpine/linux.html](http://www.washington.edu/pine/getpine/linux.html)

and download the .deb file there.
Then do
sudo dpkg -i pine_4.64_i386.deb

---

### Post by rushcamera on 2007-03-09
When I try to install pine, dpkg complains that:

 pine depends on libssl0.9.7; however:
  Package libssl0.9.7 is not installed.

However, dpkg also says that libssl0.9.8 is installed:

ii  libssl0.9.8        0.9.8a-7ubuntu0.3  SSL shared libraries

My questions are:

Does pine really need libssl0.9.7, shouldn't libssl0.9.8 suffice?

If so, how do I force - install pine.

---

### Post by diana.artemis on 2007-03-22
Rushcamera >>> These instructions work (I just did it, after having same problem as you)

> **Aberrix said:**
> first download the package.

```
wget ftp://ftp.cac.washington.edu/pine/pine_4.64_i386.deb
```

download/install the additional packages needed.

```
sudo apt-get install libssl0.9.7
```

then install the pine .deb

```
dpkg -i pine_4.64_i386.deb
```

and viola! pine is now installed.


Best wishes: Diana

---

### Post by jprb85 on 2007-03-22
Thank you so much.

---

### Post by jprb85 on 2007-03-22
I seems that Pine installed well but it did not create a /usr/bin/sendmail. I would greatly appreciate if you could tell me how to set that up. It will not allow me to send any emails because of that. It always says PIpe can't access /usr/bin/sendmail no such file or directory. Now I checked and it doesn't exist. When I tried to create a new file or folder in /usr/bin it wouldn't let me. I would greatly appreciate if you could tell me what I need to do so that Pine will finally work for me. Thank you.

:popcorn:

---

### Post by diana.artemis on 2007-03-23
> **jprb85 said:**
> ...When I tried to create a new file or folder in /usr/bin it wouldn't let me...

Wouldn't let you?  Permissions issue?  Use sudo... ?

---

### Post by jprb85 on 2007-03-23
It seems that the folder or file it is looking for doesn't exist. It refuses to allow me to send emails.
I do not think it is a permission error. I would appreciate any help to get Pine working. Thanks. :popcorn: 
:-?

---

### Post by wmcbrine on 2007-04-18
Pine is being replaced by Alpine -- essentially the same program, but under a Free license. Alpine is available in (at least) the Feisty repositories. I'd suggest using that if/when you're on Feisty.

Sendmail is a mailer program, which you could install separately. Pine doesn't install it. You could, alternatively, set up pine to use postfix, which I think is already included in the distro; or (my choice) set it up to use your ISP's outgoing mail server, just as you would with any mail client. Setup, Config, smtp-server.

The main reason to prefer a sendmail setup would be if you wanted to send mail locally, to other users on the same box, as well as to the wider Internet. This is traditional Unix stuff, but probably not what you want. The second reason to prefer a sendmail setup would be to avoid having to type the password in pine, which it will make you do unless you set up a password file.

For retrieving mail, on the other hand, I prefer to use fetchmail, which transfers it to your local mailbox. Reason being, pine's POP3 support is poor. But if you have IMAP access to your email, that works well.

---

### Post by andrew.46 on 2007-06-15
Hi,

 Read your post:

> **jprb85 said:**
> I seems that Pine installed well but it did not create a /usr/bin/sendmail. I would greatly appreciate if you could tell me how to set that up. It will not allow me to send any emails because of that. It always says PIpe can't access /usr/bin/sendmail no such file or directory. Now I checked and it doesn't exist. When I tried to create a new file or folder in /usr/bin it wouldn't let me. I would greatly appreciate if you could tell me what I need to do so that Pine will finally work for me. Thank you.

:popcorn:

 Have you thought of using ssmtp to send your mail? Depends on where your email server is: local or are you using your ISP / Gmal etc?

               Andrew

---

### Post by igpf on 2008-03-14
I was able to download and save the latest pine 4.64  however, i wasn't able to isntall libssl0.9.7

it kept saying :


```
Package lissl0.9.7 is not avaliable, but is referred to by another package. 
This may mean that the package is missing, has been obsolete, or
is only available from another source.
E: Package libssl0.9.7 has not installation candidate

```

any ideas here?

---

### Post by igpf on 2008-03-14
by the way, i found out that there's a pine clone of sorts.. called alpine

```
sudo apt-get install alpine
```

works and looks just like pine. ;)

---

### Post by alexisbellido on 2008-04-18
It's not a clone but Pine's evolution, this is the [story about Alpine]("http://www.washington.edu/alpine/overview/story.html").

---

### Post by foxmajik on 2008-07-02
Use alpine.

sudo apt-get install alpine

---

