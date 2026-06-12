---
title: "Compiling problem"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Rockyhead on 2006-08-08
I'm trying to get WLAN to work on my laptop, and am in need of compiling a utility program for it (this one here: [http://www.marvec.org/amilo/](http://www.marvec.org/amilo/) )

But as I type "make", all I get is error messages:

huolto@Rockyhead:~/fsaa1655g$ make
make -C /lib/modules/2.6.15-26-amd64-generic/build SUBDIRS=/home/huolto/fsaa1655g modules
make: *** /lib/modules/2.6.15-26-amd64-generic/build: Tiedostoa tai hakemistoa ei ole. Seis.
make: *** [default] Virhe 2

I've read some solutions about installing build-essential and linux-headers, but I have those already...

Oh yeah, Dapper 64bit;) And since most of you won't understand Finnish: 

Tiedostoa tai hakemistoa ei ole. Seis. -> File or directory doesn't exist. Stop.

Virhe 2 -> Error 2

---

### Post by moma on 2006-08-08
Hello (terve)

It is looking for kernel source (or kernel/linux headers).   

Install linux-headers:
$ sudo apt-get install linux-headers-$(uname -r)
If you have compiled your own kernel then $(uname -r) may not match.

Your kernel source is probably in **/usr/src/linux** or **/usr/src/linux-headers-2.6.15-26-amd64-generic **. Create a link from 
/lib/modules/2.6.15-26-amd64-generic/build to that directory.

Something like this:
$ sudo ln -s  /usr/src/linux-headers-2.6.15-26-amd64-generic  /lib/modules/2.6.15-26-amd64-generic/build

As an example, my system has this link:
$ [COLOR="Green"] ls -l /lib/modules/2.6.15-26-k7/build[/COLOR]
```
lrwxrwxrwx 1 root root 35 2006-07-29 17:41 /lib/modules/2.6.15-26-k7/build -> /usr/src/linux-headers-2.6.15-26-k7
```
Toivottavasti tãmã auttaa.

---

### Post by Rockyhead on 2006-08-09
Problem solved, thanks for that...

I didn't have the kernel source, but the link you mentioned existed...:rolleyes: 

Kyllä auttoi, kiitän ja kumarran

---

