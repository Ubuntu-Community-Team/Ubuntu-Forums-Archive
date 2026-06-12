---
title: "Why no ftp server?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by AcworthJack on 2007-08-15
OK, here is a newbie question from an oldie... :)

How come Ubuntu Feisty does not ship with an ftp server (ftpd)?

Back when most computers where as big as a microwave - they all had ftp.  

Since there is no ftpd – what is the most common way to occasionally move files between Linux systems?

Thanks,

John

---

### Post by shad0w_walker on 2007-08-15
There is no ftp server for a few reasons. Mostly security.

1. FTP servers normally do things in unencrypted channels which is amazingly insecure
2. This distro is geared more towards average desktop users who have little to no use for a FTP server on their system.
3. Its a program that is opening a port by default, the more open ports by default the bigger the potential for security problems
4. Theres are lots of better file transfer systems then FTP.

If you are looking for transferring files between Linux systems scp is a good tool, failing that most people just use a USB drive or similar. If you want to setup something a little more permanent or GUI based then a samba server (If sharing between windows pcs as well) or a NFS server would be a good way to go.

---

### Post by xpod on 2007-08-15
I find nfs is the best method for Linux machines...no having to copy files back and forward with a mounted share:)

This guide explains it pretty well.
[http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto)

---

### Post by AcworthJack on 2007-08-15
Thank you for the feedback - I had Apache on the boxes and shared the files via a web page.

I also agree ftp transport is not secure - but in this case I was moving files between 2 VMWare VM's on the same machine - so security was not an issue.

But funny enough - you suggested the old "sneaker net" as a better alternative to ftp.  :lolflag:

It seems to me Ubuntu may want to include ftpd - but leave it turned off.  Then the user could enable it via a gui if they needed an ftp server.  As it is now, I tried installing wu-ftp - and it will not work (probably configuration issue but I can't find any good documentation) so I will try another flavor of ftpd...

Thanks again,
John

---

### Post by shad0w_walker on 2007-08-15
Never underestimate the bandwidth of a truck full of hard drives. Not quite the same thing but when faced with various bandwidth restrictions (Especially on the internet) sneakernets or more physical methods can be far better.

---

### Post by Hospadar on 2007-08-15
Well if you want ftp you can always install it via repos.

---

### Post by AcworthJack on 2007-08-15
> **Hospadar said:**
> Well if you want ftp you can always install it via repos.

Repos?  Is that part of Ubuntu?  I would like to find an easy to configure ftpd - just something simple that works.

Thanks,
John

---

### Post by insane_alien on 2007-08-15
```
sudo aptitude install ftpd
```

that'll get you ftpd.

i preffer proftpd myself. and i tunnel it through SSH to make it secure.

---

### Post by nanotube on 2007-08-15
i use ssh and sftp. 
piece of cake to set up, as easy as ftp to use. 
```
sudo apt-get install openssh-server
```
will set up an ssh server on port 22 for you by default.
ssh and sftp clients come preinstalled already, so you can use them right away.

---

