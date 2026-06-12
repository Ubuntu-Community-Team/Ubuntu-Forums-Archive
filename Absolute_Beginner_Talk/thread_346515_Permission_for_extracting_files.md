---
title: "Permission for extracting files"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by thepaul on 2007-01-25
Hi All


I attempted to extract some files into a directory and I received this error message

"You don't have the right permissions to extract archives in the folder "/usr/share/sword""

how do I gain the 'right permission'.  I am the only person using and accessing this machine.

this is my only problem, otherwise Ubuntu is working wonderfully for me.

thanks in advance

---

### Post by Tomosaur on 2007-01-25
You're supposed to use the 'sudo' command, like this:
```

sudo <command>

```

So if the files were of the tar.gz type, you'd type:
```

sudo tar zxvf file.tar.gz

```

The password it asks for is your own, but you won't see it being typed in (to stop people looking over your shoulder :))

A WORD OF WARNING: It may be a better idea to COPY the files to somewhere in your home directory before extracting them. Not for any particular security reason, just to keep the system tidy.

---

### Post by aysiu on 2007-01-25
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by thepaul on 2007-01-25
I was using the Archive Manager to extract the files to the directory.

It was a .zip file.

would it be better to use command line?

---

### Post by aysiu on 2007-01-25
> **thepaul said:**
> 
would it be better to use command line? No. For now, you're better off with point-and-click. Read the link I posted.

---

### Post by thepaul on 2007-01-25
Thanks for the link

---

### Post by thepaul on 2007-01-25
I found another method

sudo chown -R *login name*:*blogin name* /directory

---

### Post by aysiu on 2007-01-25
> **thepaul said:**
> I found another method

sudo chown -R *login name*:*blogin name* /directory
That's a quick way to break your system. Permissions and ownership are there for a reason.

---

### Post by thepaul on 2007-01-25
so use it very very sparingly then?

---

### Post by aysiu on 2007-01-25
> **thepaul said:**
> so use it very very sparingly then?
Or not at all.

The filesystem--for stability and security reasons--has certain ownership and permissions set by default. Root owns just about everything except /home/*username*

If you find yourself needing to make system-wide changes often, create a keyboard shortcut or icon launcher for the command *gksudo nautilus*.

---

### Post by thepaul on 2007-01-25
thanks

I will

---

