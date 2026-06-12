---
title: "make: *** No rule to make target `clean'.  Stop."
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by coldstatue on 2007-06-01
I'm working on getting an obscure foreign laptop up and running on a wireless network. Wired works fine. I finally went for the linux ant driver loader free trial. I got an intermittent connection, and decided I would work on the wpa functionality. After installing the supplicant, I try to run dldrwpaconfig --setup, (same happens with just dldrconfig) and get this error(preceding stuff shown):
```

dldrwpaconfig
dldr_wpa_supplicant version 0.4.7.0.

You can compile the supplicant with OpenSSL support or not. If you compile
the supplicant without OpenSSL, you will be only able to use WPA-PSK ("WPA
Personal"). To compile with OpenSSL support, you must have the
'openssl-devel' or the 'libssl-dev' package installed.
#I HAVE LIBSSL-DEV

Do you want to compile the supplicant with OpenSSL support? [yes] n 
#DOESN'T MATTER Y OR N - SAME HAPPENS

Building the software, please wait...
ERROR: Compilation failed! Please take a look at the
'/var/run/dldrwpa-buildlog' file for the complete build log.
```

Here's what I get from the log.

```
make: *** No rule to make target `clean'.  Stop.
```

I've been searching quite a bit, and it seems this problem can be caused by a gcc version mismatch, but I don't know what my installed version is supposed to match. No idea where to check. In what I have found, no one really breaks it down into laymen's terms, because all parties in the discussions I've found are way beyond me in terms of knowledge. I'm not sure if this is going to fix my issue, as the connection is intermittent even when I remove all security from the router but MAC filtering... Still, I figure one bite at a time gets things done and helps me learn. If nothing else, I'll probably pick up on some terminology.
This is a pretty fresh linux install, so I might be missing some things, just not sure what
Thanks.

---

### Post by renzokuken on 2007-06-01
run 

```
sudo apt-get install build-essential
```

and try again

---

### Post by coldstatue on 2007-06-01
that did it. thanks!

---

