---
title: "Write to my iDisk"
date: 2007-10-20
forum: Apple PPC Users
---

### Post by phalkone on 2007-10-20
I installed davfs2 with apt-get and used dpkg-reconfigure to allow regular users to mount my iDisk. I then added my regular user profile to the davfs2 group and added the following line to my fstab file:

```
http://idisk.mac.com/usersname /media/idisk davfs      rw,user 0       0
```

Everything goes fine when I mount my iDisk. The problem is that I can't seem to write to my iDisk. When I copy a file to my iDisk it doesn't give an error, but the file is not copied to the iDisk (when I synchronise with my mac the added files are not there).

Does anyone recognize this problem? Is there an easy way to set up rsync to set up a local mirror of my iDisk and synchronize this with my real iDisk at a certain interval?

---

### Post by Twiggy003 on 2008-02-01
Have you tried doing this:  [http://mindbat.com/?p=29](http://mindbat.com/?p=29)

which sets the connection using the connect to server option, it remembers it after shut down etc.

---

### Post by andrewculver on 2008-04-26
> **phalkone said:**
> Does anyone recognize this problem?

Yeah.  I'm having this same problem right now.  If I create a directory on the iDisk, there is no problem and it persists.  But any files that I copy to the iDisk or any files I try to create on the iDisk simply do not persist.

My /etc/fstab entry looks like this:

```
https://idisk.mac.com/usernameremoved /media/idisk davfs rw,user,noauto 0 0
```

Can anyone confirm that they're able to write files to their iDisk, unmount and remount the iDisk, and still access the files they wrote?

---

### Post by freedom&lt;3 on 2008-04-27
Does it require that you provide any sort of login information in the URL string ?

Also, I noticed your using http, you might check that it doesn't use https. 

Just a thought.

---

