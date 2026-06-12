---
title: "Printing through VMware *PRIZE*"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by nuclearj on 2006-11-25
i am trying to access my LPT1 printer port through VMWare.  I can print to the printer in Dapper but when I power up my VM i get this error.
```
Cannot open /dev/parport0: Permission denied
Virtual device parallel0 will start disconnected.
```
I've bumped around the internet looking for a fix but to no avail.

I am in so dire need for this to work.  *PRIZE* Whoever helps me solve this issue will get a designer t-shirt.  (Designed by me and made possilbe because I can use the printer in my Virtual Machine.)

And I'm 90% sure that I would have to print through the virtual machine and not use it as a shared printer.  So that option is out.  Unless you know something I do not.  Thanks in advance. :)

---

### Post by kdawg on 2006-11-25
Not much experience with vmware yet, but did you install vmtools??  When I used it, the only problem I had printing was that I didn't have vmtools installed.

---

### Post by kdawg on 2006-11-25
Quick search yielded these results....

[https://linux.wordpress.com/2006/05/29/running-vmware-workstation-55-on-suse-101/]("https://linux.wordpress.com/2006/05/29/running-vmware-workstation-55-on-suse-101/")

This is on Suse but it may work for you....
more specifically.....

```
As root: rmmod lp
modprobe ppdev
You will then need to give the vmware user rw access /dev/parport0
ex: chgrp vmprint /dev/parport0
chmod g+rw /dev/parport0
or insecurely
chmod 777 /dev/parport0
```

So basically what its saying is that your vmware user doesn;t have access to the /dev/parport0....  give it access and try that out!

---

### Post by Spano on 2006-11-25
How about running VMware as root?  That should give you permissions to /dev/parport0.

---

### Post by nuclearj on 2006-11-25
> **Spano said:**
> How about running VMware as root?  That should give you permissions to /dev/parport0.

I tried "sudo vmware" but I still got he error.  Was that running vmware as root?

---

### Post by Spano on 2006-11-25
> Was that running vmware as root?
Pretty much.  Also you could try 
```
~$ sudo su vmware
```
However,I think kdawgs info is the way to go.

---

### Post by nuclearj on 2006-11-25
> **kdawg said:**
> Quick search yielded these results....

[https://linux.wordpress.com/2006/05/29/running-vmware-workstation-55-on-suse-101/]("https://linux.wordpress.com/2006/05/29/running-vmware-workstation-55-on-suse-101/")

This is on Suse but it may work for you....
more specifically.....

```
As root: rmmod lp
modprobe ppdev
You will then need to give the vmware user rw access /dev/parport0
ex: chgrp vmprint /dev/parport0
chmod g+rw /dev/parport0
or insecurely
chmod 777 /dev/parport0
```

So basically what its saying is that your vmware user doesn;t have access to the /dev/parport0....  give it access and try that out!


Okay so this is wat i did and I still got the error;

```
nuclearj@Venice-610:~$ sudo rmmod lp
nuclearj@Venice-610:~$ modprobe ppdev
nuclearj@Venice-610:~$ chgrp vmprint /dev/parport0
chgrp: invalid group `vmprint'
nuclearj@Venice-610:~$ chmod g+rw /dev/parport0
chmod: changing permissions of `/dev/parport0': Operation not permitted
nuclearj@Venice-610:~$ sudo chmod g+rw /dev/parport0
nuclearj@Venice-610:~$

```

I have no idea what any of that means (I'm kind like a parrot, i just repeat what i see and hope for the best)

---

### Post by Spano on 2006-11-25
Looks like the chmod part worked. Now try.
```
~$ sudo chgrp nuclearj /dev/parport0
```

---

### Post by nuclearj on 2006-11-25
> **Spano said:**
> Looks like the chmod part worked. Now try.
```
~$ sudo chgrp nuclearj /dev/parport0
```

Awwwww Yeaaahhhhh It worked.  Since it was a joint effort, both of yous get a shirt.  PM me with your mailing address.  And I'll get these shirts out to you two.

---

### Post by nuclearj on 2006-11-26
Okay so the stuff I got worked.  But if i retsart my computer, it goes away.  I would I make the changes permanent?

---

### Post by ondeugd on 2006-12-02
Some services are started when you use vmware.
If you change the startup script to include the commands to change permissions/ownership of /dev/parport0, permissions should always be right when vmware is started.

Startup script is /etc/init.d/vmware, open this in an editor (for example by running): sudo gedit /etc/init.d/vmware

Find the case statement that looks like this (around line 854)

# See how we were called.
case "$1" in
start)

Add the commands to change permissions/ownership of /dev/parport0 on new lines directly after start)

(not my findings btw, check [http://www.vmware.com/community/thread.jspa?messageID=328911](http://www.vmware.com/community/thread.jspa?messageID=328911))

succes!

---

### Post by peterx14 on 2006-12-15
Dunno how I missed this thread when I was having problems a couple of weeks back! Anyways, for the benefit of anyone else, all you need to do is:

Add your user to the "lp" group
sudo modprobe ppdev
sudo rmmod lp

My thread was/is here:
[http://www.ubuntuforums.org/showthread.php?t=308340#td_post_1891074](http://www.ubuntuforums.org/showthread.php?t=308340#td_post_1891074)

---

