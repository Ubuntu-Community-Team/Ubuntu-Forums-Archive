---
title: "installing a program from source !"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by medya on 2007-04-27
hi [there is a program]("http://sourceforge.net/project/showfiles.php?group_id=146506&package_id=221578") to convert dictionary databases to StarDict ,

I suck in installing programs from source , I did this and I got this error, it seems the "configure" cant find my libxml2 ?

here is the result of my .configure 

```
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for xml2-config... no
checking for libxml - version >= 2.5.0... no
*** The xml2-config script installed by LIBXML could not be found
*** If libxml was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XML2_CONFIG environment variable to the
*** full path to xml2-config.
configure: error: You must have libxml2 >= 2.5.0 installed

```
what to do ?

---

### Post by Kobalt on 2007-04-27
Open up Synaptic package manager, search for *libxml2*, install it then try again your compilation...

---

### Post by medya on 2007-04-27
but it is already installed , it seems I need to tell it , where it is located , but I dont know how

---

### Post by medya on 2007-04-27
so can somebody tell me where I can learn to compile this program?

---

### Post by Seisen on 2007-04-27
I know exactly what you are talking about

```
./configure --prefix=whereverthefile is locate
```

Say the file was in /usr/bin, it would look like this.

```
./configure --prefix=/usr/bin
```

---

### Post by Compyx on 2007-04-27
Don't do that. With the --prefix option you tell configure where to install the files you're compiling, not where to look for headers.

The package you need is probably 'libxml2-dev', this will provide the headers the configure script needs.

---

### Post by jvmborges on 2008-07-18
Thanks, I was having the same problem to install neurofitter and the installation of the package libxml2-dev works for my problem.

---

