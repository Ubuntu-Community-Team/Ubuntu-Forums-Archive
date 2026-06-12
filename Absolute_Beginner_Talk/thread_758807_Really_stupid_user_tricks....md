---
title: "Really stupid user tricks..."
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Exgbear on 2008-04-18
Ok, let's say I went and did something really stupid like uninstall tar.  Well I've been trying to reinstall it without any luck.

stupid@ubuntu:~$ sudo apt-get install tar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ncompress
The following NEW packages will be installed:
  tar
0 upgraded, 1 newly installed, 0 to remove and 29 not upgraded.
Need to get 340kB of archives.
After unpacking 2171kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main tar 1.18-2ubuntu1 [340kB]
Fetched 340kB in 3s (111kB/s)
dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/tar_1.18-2ubuntu1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/tar_1.18-2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

What the hell am I supposed to do?

---

### Post by indiecast on 2008-04-18
r u using synaptic package manager or strictly doing it through the terminal?

---

### Post by tnl2k7 on 2008-04-18
indiecast, are you having an off day or something?

At the top of the code output is:
```
stupid@ubuntu:~$ sudo apt-get install tar
```

So he's clearly using the terminal.

It seems that you, outrageously, need the tar package already installed to install the tar package, catch 22 situation if you catch my drift.

I don't know what you need to do to resolve this, but you might need to just do a reinstall of Ubuntu from scratch......wait and see what other community members say though, there'll be someone who can help you better.

---

### Post by lespaul_rentals on 2008-04-18
Does anyone know the URL for the FTP server for all the .debs?  He could download the .deb from there and install it that way.

Wow, this is a tricky situation, haha!

---

### Post by fs3rp4 on 2008-04-18
> **Exgbear said:**
> Ok, let's say I went and did something really stupid like uninstall tar.  Well I've been trying to reinstall it without any luck.

stupid@ubuntu:~$ sudo apt-get install tar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ncompress
The following NEW packages will be installed:
  tar
0 upgraded, 1 newly installed, 0 to remove and 29 not upgraded.
Need to get 340kB of archives.
After unpacking 2171kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main tar 1.18-2ubuntu1 [340kB]
Fetched 340kB in 3s (111kB/s)
dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/tar_1.18-2ubuntu1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/tar_1.18-2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

What the hell am I supposed to do?

Hi!

Try this:


Close synaptic, update-mananger, etc...

First, clean the cache:

sudo apt-get clean

Now fix the issue:

sudo dpkg --configure -a


Try to install the tar package.

---

### Post by Exgbear on 2008-04-18
stupid@ubuntu:~$ sudo apt-get clean
[sudo] password for stupid:
stupid@ubuntu:~$ sudo dpkg --configure -a
stupid@ubuntu:~$ sudo apt-get install tar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ncompress
The following NEW packages will be installed:
  tar
0 upgraded, 1 newly installed, 0 to remove and 29 not upgraded.
Need to get 340kB of archives.
After unpacking 2171kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main tar 1.18-2ubuntu1 [340kB]
Fetched 340kB in 5s (63.1kB/s)
dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/tar_1.18-2ubuntu1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/tar_1.18-2ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sdennie on 2008-04-18
If you've previously installed 7zip (type "man 7z" to see if you have), that can directly extract data out of a .deb file.  You could try to install the .deb with apt-get again, then look in /var/cache/apt/archives for the tar .deb, copy it to a temp location, "undeb" using it 7z then manually copy the tar binary to /bin.  You should then be able to properly install the tar .deb and it will just clobber the binary you put in /bin.

---

### Post by Exgbear on 2008-04-18
Unfortunately it doesn't look like I have 7z, and I can't install it because i don't have tar.

---

### Post by erlyrisa on 2008-04-18
[http://packages.ubuntu.com/gutsy/tar]("http://packages.ubuntu.com/gutsy/tar")

---

### Post by erlyrisa on 2008-04-18
[http://www.gnu.org/software/tar/#downloading]("http://www.gnu.org/software/tar/#downloading")

.... google search tar...

it won't be easy - but not that difficult either

---

### Post by Irony on 2008-04-18
Download the deb package to your cache drag it to an external drive and then untar it with the live cd, drag the untarred version back to the external drive.

Then go back to ubuntu and install it from there... I don't know what the install instructions would be though.

---

### Post by sdennie on 2008-04-18
The other thing you could do would be to stick in your Ubuntu install disk, mount the live base image and steal tar from there.  Something like this might work:

```

mkdir tmp_install
sudo mount -o loop /media/cdrom0/casper/filesystem.squashfs tmp_install
sudo cp tmp_install/bin/tar /bin
sudo umount tmp_install
rmdir tmp_install
sudo apt-get install tar

```

Hopefully the filesystem.squashfs exists on the install CD you have for Ubuntu.  I just tried mounting it on Hardy and it worked fine.

---

### Post by Exgbear on 2008-04-18
> **vor said:**
> The other thing you could do would be to stick in your Ubuntu install disk, mount the live base image and steal tar from there.  Something like this might work:

```

mkdir tmp_install
sudo mount -o loop /media/cdrom0/casper/filesystem.squashfs tmp_install
sudo cp tmp_install/bin/tar /bin
sudo umount tmp_install
rmdir tmp_install
sudo apt-get install tar

```

Hopefully the filesystem.squashfs exists on the install CD you have for Ubuntu.  I just tried mounting it on Hardy and it worked fine.

Getting this error:
mount: you must specify the filesystem type

---

### Post by sdennie on 2008-04-18
You could try this as the mount command instead:

```

mount -t squashfs -o loop /media/cdrom0/casper/filesystem.squashfs tmp_install

```

I would make sure that /media/cdrom0/casper/filesystem.squashfs actually exists on your install CD as well.

---

### Post by erlyrisa on 2008-04-18
why don't yoy just download the latest version from the gnu website....

it comes gzipped - no need for tar

---

### Post by Exgbear on 2008-04-18
> **vor said:**
> You could try this as the mount command instead:

```

mount -t squashfs -o loop /media/cdrom0/casper/filesystem.squashfs tmp_install

```

I would make sure that /media/cdrom0/casper/filesystem.squashfs actually exists on your install CD as well.

Vor........

I just want to tell you.....

In a very manly way.....

That I love you very much.

Thanks to everyone for all of their help.  I promise I'll never uninstall tar again.
stupid@ubuntu:~$ which tar
/bin/tar

---

### Post by Rinzwind on 2008-04-18
Now all you need to do is make a bug report so no-one else falls into this trap :)
Consider that the price for getting helped >:)\

lol

I saw what you did and went: wtf is wrong with deleting tar!? and then: duh, obvious!! :D

---

### Post by sdennie on 2008-04-18
I'm glad it worked.  It's actually surprising that packages like dpkg and apt-get don't depend on the tar package (sounds like a dependency bug).  I'm always very hesitant to uninstall something after apt-get informs me that it's also going to uninstall half my system with it.

---

### Post by Exgbear on 2008-04-18
> **Rinzwind said:**
> Now all you need to do is make a bug report so no-one else falls into this trap :)
Consider that the price for getting helped >:)\

lol

I saw what you did and went: wtf is wrong with deleting tar!? and then: duh, obvious!! :D

I'll be happy to write up a bug report for this one.  When I have a minute, I'll have to poke around and see where they need to be submitted.

I'm in QA so I tend to do really really stupid stuff like this all of the time, I just didn't expect to find myself in a "chicken vs. egg" situation.

---

### Post by Rinzwind on 2008-04-18
If you don't/are not able to create one post it here and I'll have a go :)

And the egg was 1st: birds came after dino's and dino's lay eggs too. From 1 egg came a faulty dino that could fly and eventually a chicken was born somewhere  :) :)

---

### Post by tnl2k7 on 2008-04-18
Glad to see you got it fixed :D

Yeah I really think this dependency issue should be reported to the Ubuntu developers, it's a pretty large problem lol.

---

### Post by Exgbear on 2008-04-18
Bug #219324

---

