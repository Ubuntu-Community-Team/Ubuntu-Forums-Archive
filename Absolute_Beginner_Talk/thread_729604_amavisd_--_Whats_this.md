---
title: "amavisd -- Whats this??"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-03-20
Each time I install a package, it tells me that amavisd-new and amavisd-new-milter is unconfigured. It tries to configure it, but fails. I could not post the output of it here since I don't seem to be able to post long messages (thats too is a serious problm :D)

---

### Post by Peter09 on 2008-03-20
Well this is what it is

[http://www.ijs.si/software/amavisd/](http://www.ijs.si/software/amavisd/)

but what your problem is I do not know.

PC

---

### Post by sayakb on 2008-03-20
I am thinking of removing it.. Might be a metapackage that ClamAV installed..

---

### Post by zvacet on 2008-03-20
```
sudo dpkg --configure -a
```

---

### Post by sayakb on 2008-03-20
I dont seem to be able to post the output.. What do I do?

---

### Post by sayakb on 2008-03-20
glade@Muzic-Jukebox:~$ sudo dpkg --configure -a
Setting up amavisd-new (1:2.4.2-6.2ubuntu1) ...
Creating/updating amavis user account...
Starting amavisd: head: cannot open `/etc/mailname' for reading: No such file or directory
  The value of variable $myhostname is "Muzic-Jukebox", but should have been
  a fully qualified domain name; perhaps uname(3) did not provide such.
  You must explicitly assign a FQDN of this host to variable $myhostname
  in /etc/amavis/conf.d/05-node_id, or fix what uname(3) provides as a host's 
  network name!
(failed).
invoke-rc.d: initscript amavis, action "start" failed.
dpkg: error processing amavisd-new (--configure):

---

### Post by sayakb on 2008-03-20
subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of amavisd-new-milter:
 amavisd-new-milter depends on amavisd-new (= 1:2.4.2-6.2ubuntu1); however:
  Package amavisd-new is not configured yet.
dpkg: error processing amavisd-new-milter (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amavisd-new
 amavisd-new-milter
glade@Muzic-Jukebox:~$

This seems to be the max size I can post.. anyway, post #7 is a continuation of #6

---

### Post by zvacet on 2008-03-21
You can try with 

```
sudo apt-get -f install
```

Did you try to install it from synaptic?

> The value of variable $myhostname is "Muzic-Jukebox", but should have been
a fully qualified domain name; perhaps uname(3) did not provide such.
You must explicitly assign a FQDN of this host to variable $myhostname
in /etc/amavis/conf.d/05-node_id, or fix what uname(3) provides as a host's 
network name!

This look like problem.Can you change that?

---

### Post by sayakb on 2008-03-21
I actually removed clamAV including this package. Now a new problem I have. It's the package havp. Same error. I can't even remove it, it says that Error processing package havp. Package may be corrupted. How can I get rid of it?

---

### Post by sayakb on 2008-03-21
Since I cant post long outputs here, here is a screenshot..

[[IMG]http://img211.imageshack.us/img211/6825/atgaaaduno85exotwvekxznju8.th.jpg[/IMG]]("http://img211.imageshack.us/my.php?image=atgaaaduno85exotwvekxznju8.jpg")

---

### Post by zvacet on 2008-03-21
One line say that device is busy,meaning it is runing.That is whay you can not remove it.Stop it first and then remove.

---

