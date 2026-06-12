---
title: "System hangs @ root@(none)&quot;/# while reseting root password"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by fmansoor on 2007-07-26
Hello

I am trying to rest ubuntu root password by appending single init=/bin/bash to kernel command line as explained several place on the web like here

[http://ubuntuforums.org/showthread.php?t=490953&highlight=password+reset+grub](http://ubuntuforums.org/showthread.php?t=490953&highlight=password+reset+grub)

but my system hangs as soon as I get the root@(none):/# prompt any one has any idea about the problem

Thanks.

---

### Post by irish_flu on 2007-07-26
(this is just a guess) it sounds like your system might not know what its hostname is.  If you know what it is (which is probably set in the /etc/hosts file) you can run a command to set it for the session
```

sudo hostname <yourhostname>

```

then do the password change command.

I'm not sure if that's the ticket, but it's worth a shot.

---

### Post by fmansoor on 2007-07-26
actually i forgot the roots password and can't log into the system and therefore cannot issue any command.

---

### Post by FleetAdmiral74 on 2007-07-26
When you say forgot...did you reset it in the past? If not, then you never knew it in the first place cause its set to random.

---

