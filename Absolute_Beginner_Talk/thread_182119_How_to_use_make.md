---
title: "How to use make"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by adam s on 2006-05-25
Hi,

I am trying to get my logitec webcam zoom to work.

I am trying to set this up using the instructions at [http://www.saillard.org/linux/pwc/INSTALL.en](http://www.saillard.org/linux/pwc/INSTALL.en)

When I get to the following commands :
>3) compile the module (this needs the source of your actual kernel to
>     be installed)
>        # cd pwc-10.0.9rc1
>	# make

I get the error 

adam@....:~/temp/pwc-10.0.12-rc1$ make
bash: make: command not found

What am I doing wrong? How can I fix it.

Thanks in advance,

Adam.

I am running Breezy 5.10 and running the Gnome front end.

---

### Post by mlind on 2006-05-25
```

sudo apt-get install build-essential

```

You must install build-essential package in order to get the build environment.
For kernel modules, you also need to install gcc-3.3 !

---

### Post by adam s on 2006-05-25
Thanks for the help so far,

I now get the error :

adam@....:~/temp/pwc-10.0.12-rc1$ make
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/home/adam/temp/pwc-10.0.12-rc1 modules
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
make: *** [all] Error 2


I have the directory /lib/modules/2.6.12-10-386/ but there is no build directory there.
Is there something else I need to install or can I direct the makefile elsewhere?

Thanks in advance for your help - this is the first time I have used make in Linux.


Adam.

---

### Post by Sef on 2006-05-25
Did you switch to the download directory?

Check out these two sites:

[installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware.php")

[installing]("http://monkeyblog.org/ubuntu/installing.html")

---

### Post by mlind on 2006-05-25
it could be that you need linux-kernel-headers package installed.

---

### Post by adam s on 2006-05-26
What is the name for the kernal headers?

I have searched in the Synaptic Package manager for 2.6 and kernal and have not come up with anything?

Thanks,

Adam.

---

### Post by mlind on 2006-05-26
[QUOTE=adam s]What is the name for the kernal headers?

I have searched in the Synaptic Package manager for 2.6 and kernal and have not come up with anything?

Thanks,

Adam.[/QUOTE]

I believe it's this one. Just 'linux-kernel-headers'. It's a meta-package that will
depend on your current kernel.
```

$ apt-cache policy linux-kernel-headers
linux-kernel-headers:
  Installed: 2.6.11.2-0ubuntu18
  Candidate: 2.6.11.2-0ubuntu18
  Version table:
 *** 2.6.11.2-0ubuntu18 0
        500 http://fi.archive.ubuntu.com dapper/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by joshrobinson on 2006-05-26
yeah the headers should solve your problem like said above.. if it doesnt you can use synaptic for a search of headers, and find the one that matches your kernel (if the meta package doesnt solve it like said above)

---

