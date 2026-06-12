---
title: "Subversion Daemon"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by leemobile on 2006-01-28
Hello,

So I've followed the online wiki to install subversion and I created my repository.

Now I want to know how to have it so that the svnserver daemon is loaded whenever my computer is turned on, or restarted whenever it gets terminated.

I can't seem to find any user guides on how to get this done.

Thanks,

Lee

---

### Post by leemobile on 2006-01-28
Bump!

---

### Post by cwaldbieser on 2006-01-28
[QUOTE=leemobile]Bump![/QUOTE]
Did you install subversion from the repositories or from a tarball?  If you got it from the repositories, it should be configured to run as a service when it was installed.

If you installed it from scratch, the Subversion Book tells you how to do it.  It is pretty simple.  In /etc/inetd.conf, add a line like this:

```

svn	stream	tcp	nowait	svnowner	/usr/bin/svnserve svnserve -i

```
"svnowner" should be the name of the user you want to run the daemon as.  That user should have (filesystem) permissions to read and write to the repository.

---

### Post by leemobile on 2006-01-29
Hi, 

I did install Subversion from the repositories, but it didn't get setup as a service.

For some reason I don't have the /etc/inetd.conf file.  Is Ubuntu 5.10 supposed to have this file?  Or do I just create it?

Cheers,

Lee

---

### Post by cwaldbieser on 2006-01-29
[QUOTE=leemobile]Hi, 

I did install Subversion from the repositories, but it didn't get setup as a service.

For some reason I don't have the /etc/inetd.conf file.  Is Ubuntu 5.10 supposed to have this file?  Or do I just create it?

Cheers,

Lee[/QUOTE]
Well, make sure you have /usr/sbin/inetd.  It is part or the netkit-inetd package.  Then you can just create the file.  

I checked and my inetd.conf wasn't installed by apt-get, so I guess it was created later by some process since it has commented lines in it that I never added.  Mine has permissions like so:
```

-rw-r--r--  1 root root 1463 Oct 15 17:28 /etc/inetd.conf

```

---

