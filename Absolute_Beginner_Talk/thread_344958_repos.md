---
title: "repos"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by asef on 2007-01-23
I have trouble with activating the components Universe and multiverse, 
when i click reload the disaster comes. Do I have to do something before I activate them?
thanks

---

### Post by jvc26 on 2007-01-23
Please can you clarify your problem beyond 'disaster comes' what happens? What did you do before it went wrong if anything? Are you getting error messages? Are you on edgy or dapper?
Thanks,
Il

---

### Post by 23meg on 2007-01-23
What exactly is "the disaster"? What errors are you getting?

---

### Post by asef on 2007-01-23
First message

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

Second message

Error

The following problems where found on your system:

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

---

### Post by lamego on 2007-01-23
Close Synaptic.
Open the terminal and type:
```
sudo apt-get update
```
Post here the output.

---

### Post by jvc26 on 2007-01-23
The lock is because you have another program open (like synaptic package manager, update manager, another terminal window etc) using the same stuff and hence it cannot access it while that one is using the directory. You can only have one of them working at once. 
Once all are closed, open terminal and type:
```

sudo apt-get update

```
If that works, all's good, if not:

Can you post up your /etc/apt/sources.list?:
```

gksudo gedit /etc/apt/sources.list

```
and copy and paste it onto here
Thanks,
Il

---

### Post by asef on 2007-01-23
To Lamego

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

---

### Post by jvc26 on 2007-01-23
(As above) You cannot have SPM/terminal sudo apt-get/update manager running at the same time. You usually get that error when more than one of them are open. If you close them bar the terminal and type again that should be ok.
Il

---

### Post by asef on 2007-01-23
Ti Il I did what you said and the output is

28% [Connecting to gr.archive.ubuntu.com (32.1.6.72)] [Connecting to security.ubuntu.com (1.0.0.0)] [Connecting to [www.getautomatix.com](www.getautomatix.com) (1.0.0.0)] [Connecti^

---

### Post by jvc26 on 2007-01-23
Can you possibly post up the /etc/apt/sources.list:
```

gedit etc/apt/sources.list

```
Then copy and paste from that window :) Just want to have a quick cursory scan over it :)

EDIT:: Am just having to clock off now its far too late at night - if someone hasnt got back to you by tomorrow morning I'll pop back on and take a look, apologise for that am knackered :)
Il

---

### Post by iver2435 on 2007-01-23
From your last post it looks like you tried to install Automatix and something either went wrong during the install, or maybe something was modified incorrectly.

Run:

```
ls -la /etc/apt/
```

and you should see a file called sources.list and hopefully one called sources.backup (or something similar, use your own judgement).

To restore your backup file to be the active one, use the following command:

```
sudo mv /etc/apt/sources.backup /etc/apt/sources.list
```

Then try running Synaptic again and see what happens....

Automatix is great, but you'll be better off learning how to install stuff on your own, trust me!

---

### Post by asef on 2007-01-23
To Il, here is it

(gedit:8156): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gedit:8156): Gdk-WARNING **: locale not supported by C library

(gedit:8156): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

Thanks

---

### Post by asef on 2007-01-24
The problem continues, and I can't still activate the repos. Can someone help :)

---

### Post by jvc26 on 2007-01-24
Thats really odd - do you get that error in the terminal when you try top open up the /etc/apt/sources.list from the terminal? Or is that the contents of that file??? I presume thats the error you're getting in the terminal - which is one I've never seen before, I'm afraid I can't push this further I hope that there are some other guys here who can help :) Sorry about that,
Il

---

### Post by asef on 2007-01-24
Thanks, anyway:)

---

### Post by MkfIbK7a on 2007-01-24
try the third  link in my signature

---

### Post by TehMark on 2007-01-24
> **wert613 said:**
> try the third  link in my signature

Your sig is a newbies dream

---

