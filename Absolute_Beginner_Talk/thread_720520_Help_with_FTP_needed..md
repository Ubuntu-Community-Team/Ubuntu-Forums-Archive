---
title: "Help with FTP needed."
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by crumble6 on 2008-03-10
Hi guys!

I'm pretty new to all this linux stuff so you will have to bare with me...

I have been using linux on my laptop for about a year now, but I use package managers to install things, and the gnome desktop means that operation isn't all that different to windows.

Anyway, I have recently got a cheap dedicated server to use as a web and file server. I chose Ubuntu 7.10 server edition as the OS. I can SSH into the server, and I have set up the user accounts, apache2, php, mysql, etc. My only problem is FTP.

I have been using VSFTPD, which is fine for the user accounts, as it FTPs directly to the users home directory. The problem comes when I need to upload files to the apache directory (/var/www if i remember correctly). I have absolutely no way of getting to that directory. I have tried editing the VSFTPD config file, but can't find an option to change the FTP directory. Is there any way I can set up and FTP account to the root (/) directory so I can manage files anywhere on the server???

I also tried PROFTPD but couldn't seem to find the config file for that, even though the guide I followed said it should have been at /etc/proftpd.conf

Any help greatly appreciated, thanks in advance!

---

### Post by lloyd_b on 2008-03-10
Creating an FTP user with a home of "/" is a VERY dangerous idea.  

An alternate suggestion:  "bind" the "/var/www" (or whatever that directory is) directory to a subdirectory under your home directory.  "ssh" to that machine, and:
```
mkdir www
sudo mount -bind /var/www www
```

Note that the permissions on that directory still apply - if your user doesn't have write permissions to /var/www, you won't be able to write to /home/username/www...

To make this mount permanent,  you'll need to add a line to the file "/etc/fstab":
```
/var/www   /home/username/www   bind   bind   0
```

Lloyd B.

---

### Post by bodhi.zazen on 2008-03-10
Since you have both ssh and root access, I advise you either use scp or after you upload a file (ftp) ssh into the server and move the files to www.

---

### Post by crumble6 on 2008-03-10
Thanks very much, that will do the job nicely!

---

### Post by Dr Small on 2008-03-10
SFTP would alternately work too.

---

### Post by Oldsoldier2003 on 2008-03-10
> **Dr Small said:**
> SFTP would alternately work too.

thats my favorite answer. FTP and telnet are bad news and any hosting company that allows them is  flirting with disaster.

---

### Post by Oldsoldier2003 on 2008-03-10
> **lloyd_b said:**
> Creating an FTP user with a home of "/" is a VERY dangerous idea.  


To make this mount permanent,  you'll need to add a line to the file "/etc/fstab":
```
/var/www   /home/username/www   bind   bind   0
```

Lloyd B.

nice info, is the syntax  set for ubuntu/debian? because i was considering doing the same on one of my machines but only was only familiar with the way I used to do it in gentoo

```
/var/www /home/user/www none bind
```

but didnt want to break the server on its next reboot....

---

### Post by lloyd_b on 2008-03-10
> **Oldsoldier2003 said:**
> nice info, is the syntax  set for ubuntu/debian? because i was considering doing the same on one of my machines but only was only familiar with the way I used to do it in gentoo

```
/var/www /home/user/www none bind
```

but didnt want to break the server on its next reboot....

I cut-n-pasted that line from another thread I was involved in, but since you asked I did a little testing.

The third parameter ("none" in your example, "bind" in mine) is completely ignored.  Just for the heck of it, I changed it to "crashme", and then mounted that directory - it worked fine.  Some further testing shows that if the mount command sees "-bind" or "-o bind", it doesn't care about the file system type, even if it's explicitly declared via a "-t" option.

The fifth parameter (null in your example, "0" in mine) is actually unnecessary in my example.  From the "fstab" man page:
```
 If the  fifth  field  is not present, a value of zero is returned 
```
meaning that in your example the value of 0 is assumed, rather than explicit as in mine.

So either form will work in 'buntu.  I suspect the same will be true of Red Hat, Gentoo, and every other Linux variant - it's a function of the "mount" command, which should be the same for all current distros (though what would happen if you tried it on an older kernel without "-bind" support I don't know).

Lloyd B.

---

### Post by Oldsoldier2003 on 2008-03-10
Thanks Lloyd,your post confirmed my gut feeling on the issue but i was referring to a remote "headless" server so its always nice to get some verification from another source

---

