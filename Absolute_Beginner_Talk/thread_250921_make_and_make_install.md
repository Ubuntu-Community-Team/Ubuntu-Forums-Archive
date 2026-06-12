---
title: "make and make install"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by kamilczauz on 2006-09-04
im trying to install madwifi driver, so i downloaded it and followed the instructions.

It says to do make and then make install.

When i initially typed make, it gave me a command not found error, so i did apt-get install make.  After this, it gives me this error when i try to make.

Ive also tried apt-get install build-essential and still no luck

Here is the error, what must i do to fix it?

Thanks

```
kamil@kamil-laptop:~/Desktop/madwifi-0.9.2$ make
/bin/sh: line 0: cd: /lib/modules/2.6.15-26-386/build: No such file or directory
Makefile.inc:89: *** /lib/modules/2.6.15-26-386/build is missing, please set KERNELPATH.  Stop.
kamil@kamil-laptop:~/Desktop/madwifi-0.9.2$ 

```

---

### Post by zxee on 2006-09-04
You need all of the build-essential package which includes more than make alone.
> sudo apt-get install build-essential

---

### Post by taurus on 2006-09-04
> **zxee said:**
> You need all of the build-essentials package which includes more than make alone.
There is no **[COLOR="Blue"][SIZE="3"]s[/SIZE][/COLOR]** in build-essential!!!

---

### Post by zxee on 2006-09-04
> **taurus said:**
> There is no **[COLOR="Blue"][SIZE="3"]s[/SIZE][/COLOR]** in build-essential!!!

Sorry. Corrected in my response.

---

### Post by kamilczauz on 2006-09-04
yes, ive installed build-essential already, in my first post i noted that i installed it and i still get the same error.


please help:(

Thanks

---

### Post by taurus on 2006-09-04
If you look at the error message carefully, you will find out that you didn't install the headers for your kernel!!!  So, use synaptic and search for the right version of the header for your kernel and install it.  Then, build your madwifi again...

```
Makefile.inc:89: *** /lib/modules/2.6.15-26-386/build is missing, please set KERNELPATH.  Stop.
```

---

### Post by kamilczauz on 2006-09-04
hmm... thanks, i didnt know that the headers werent included... all is fine now, thanks

btw, i did uname -r and installed the linux headers for that version..

thanks guys

---

### Post by taurus on 2006-09-04
Yes, you can find out which version of kernel you are using with "uname -r" command.

---

