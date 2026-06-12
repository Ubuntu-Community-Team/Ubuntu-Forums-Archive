---
title: "Access Universal Repositories ?"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-08-15
Hi,

I wanted to try and install "netatalk" -- but I think I need to enable my universal repository from the command line.  (I have the server version installed).  I don't see netatalk in the regular apt-get offerings.

One: how do I get access to the universals from the command line ?

Two: any info on how to setup netatalk ?

Thanks,
Damon

---

### Post by aysiu on 2006-08-15
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) will give you the universe and beyond.

---

### Post by thornomad on 2006-08-15
Thank you!  That's perfect.  

Is there anyway to list what "packages" are available to see if the one I want is there ?  

And, where do they get installed ?  that is, after I install, where do I look for the README or whatever ?

Thanks,
D

---

### Post by aysiu on 2006-08-15
System > Administration > Synaptic Package Manager is the easiest way to browse them.

You can also search online at [http://packages.ubuntu.com](http://packages.ubuntu.com)

Read this, though:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

That'll explain a bit more about software installation.

---

### Post by thornomad on 2006-08-15
Thanks for all your help.  For people finding this in a search, here is what I did (from all your suggestions):

First: edited my sources list to let me get at the universal packages

```
:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
:~$ sudo nano /etc/apt/sources.list
```

Then I removed the # marks from these two lines:

```
# deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe
```

Ctrl-O to write changes; Ctrl-X to exit.  Then updated aptitude and installed netatalk:

```
$ sudo aptitude update
$ sudo aptitude install netatalk
```

After the prompts, I could access my home folder form my Mac flawlessly (simple Apple-K from the finder and entered my IP address).  But I wanted to see everything (since I am learning about Linux still), so I edited which directories were available to me when I connect by doing this (first the backup then the changes):

```
$ sudo cp /etc/netatalk/AppleVolumes.default /etc/netatalk/AppleVolumes.default-dtbackup
$ sudo nano AppleVolumes.default
```

Then, at the very bottom of the document, I added my root directory by adding this line after what is already there (shown here):

```
~/ "Home Directory"
/ "Root"
```

Now, when I connect, I can either hook into my home directory or the root.  I am not sure if these is a safety concern, but I currently don't have my server hooked up to the internet.  When I do, I will probably remove the root access.

Thanks everyone!
D

---

