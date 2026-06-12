---
title: "How do I get the authority to change files?"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Sarah13 on 2006-10-23
I am the only user on my system, and I have set up an authorization password. However, when I try to add a folder or make any changes to my two largest partitions, it says that I don't have the authority to make the changes.

The permissions are 'root'. How do I set myself up to modify/add files?

---

### Post by jorn on 2006-10-23
What kind of partitions are they.windows?
What is the output of:
> sudo fdisk -l
and:
> sudo gedit /etc/fstab

---

### Post by aysiu on 2006-10-23
One of these links should help:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Sarah13 on 2006-10-23
Nope, no windows on this computer - it's solely linux.

Using 'gksudo nautilus' in a run application window works wonderfully, thank you so much!

I love the forums here, I think it would be real easy to give up on linux (as I'm an advanced windows user and I know exactly what to do and why to do it in order to get the result I want) if I didn't have these forums and all you wonderful guys to help me.

One quick question - if my two main linux partitions are set up as root only - does this mean only root can modify those files or only root can use them? For example, if I put music there, can I play it as a normal user? Or do I need to repartition?

Thanks again!

---

### Post by jorn on 2006-10-23
If their permissions are set to owned by root no user can access them.
 Change ownership to use them:
[http://ubuntuguide.org/wiki/Dapper#How_to_change_files.2Ffolders_permissions](http://ubuntuguide.org/wiki/Dapper#How_to_change_files.2Ffolders_permissions)

---

### Post by randiroo76073 on 2006-10-23
Thanks from me also,'gksudo nautilus' is what I was looking for too :)

---

### Post by Ben Sprinkle on 2006-10-23
If you type:
```
sudo su
```
Then type password, you can use regular commands without typing sudo before every one of them.

---

### Post by aysiu on 2006-10-23
[quote=sarah13]One quick question - if my two main linux partitions are set up as root only - does this mean only root can modify those files or only root can use them? For example, if I put music there, can I play it as a normal user? Or do I need to repartition?[/quote] If root owns a file, that doesn't mean you can't play it or read it. It all depends on the permissions.

For example, 700 means that the owner (in this case, root) can (7) read, write, and execute the file; and others can (0) do nothing. If the file were owned by root but was 755, it would mean that root could (7) read, write, and execute the file but others could (5) read and execute it.

---

