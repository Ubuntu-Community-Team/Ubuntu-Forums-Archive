---
title: "What is a good ftp server/manager?"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Stomstedt on 2006-10-15
I'm just looking for a simple, good ftp server that isn't too hard to understand.  Right now I have pure-ftp and I hate it very much because I have no clue what is going on and it doesn't give me any choices.  Besides.. the GUI doesn't even work with it.  (Let alone the fact that you can connect to it with root, how easy to become hijacked) :mad:

---

### Post by nix4me on 2006-10-15
Well ftp servers on linux are different animals than on windows.  Servers are supposed to serv, not look pretty.

I've been using proftpd for years with no problems.  Its very configurable and very stable.  Again, its a service so no fancy gui.

I think there is an addon gui for it but i've never needed or used it.

The top 3 ftp servers for linux are:
proftpd
vsftpd
pureftpd

nix4me

---

### Post by taurus on 2006-10-15
I have both proftpd and vsftpd running on my machines so either one is good.  However, I think you might want to go with vsftpd...

---

### Post by equal on 2006-10-15
A simple useable one is gFTP

```
sudo apt-get install gftp
```

---

### Post by taurus on 2006-10-15
> **equal said:**
> A simple useable one is gFTP

```
sudo apt-get install gftp
```
That is a client and he is talking about a server!!!

---

### Post by chalex on 2006-10-15
I've only ever used proftpd.  You install it, you edit the single configuration file, then you make sure permissions are the way you want them on the directories that the ftp server is using.

Here's a guide: [http://www.debian-administration.org/articles/228](http://www.debian-administration.org/articles/228)

Edit: of course, it's 2006, so you shouldn't be using unsecure FTP at all.  You probably want sftp.

---

### Post by Stomstedt on 2006-10-15
OK so i installed proftpd...  How do I start and stop the server?  And also, how do I manage the Root directories?  I really don't like people messing around with my root directory.. Thank you.

---

### Post by nix4me on 2006-10-15
You start and stop it from the System/Administration/Services applet.

As far as configuring it....you really need to read the documentation at the proftpd website.

Or at least read some howto's on these forums.  There is a very good one in the Howto forum.

Proftpd is very configurable.

nix4me

---

### Post by chewbunny on 2006-10-15
Have you tried:
/etc/init.d/proftpd start
/etc/init.d/proftpd stop

---

