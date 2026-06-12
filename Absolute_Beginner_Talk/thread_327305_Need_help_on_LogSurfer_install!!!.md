---
title: "Need help on LogSurfer install!!!"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by DieslWeasl on 2006-12-28
I can't figure this out:

I untarred the LogSurfer package and tried an install but I got an error message.  For any gurus out there I'll just go ahead and post most of what I did in terminal:

root@silver:~/Desktop/logsurfer+-1.7# make install
for subdir in man src; do \
                echo making install in $subdir ; \
                (cd $subdir; make prefix='/usr/local' bindir='/usr/local/bin' mandir='/usr/local/man' CPPFLAGS='-DWARN_ROOT' CC='gcc' CFLAGS='-g -O' LDFLAGS='' DEF_DUMPFILE='/dev/null' DEF_CONFFILE='/usr/local/etc/logsurfer.conf' LIBS='' INSTALL='/usr/bin/install -c' INSTALL_PROGRAM='/usr/bin/install -c' INSTALL_DATA='/usr/bin/install -c -m 644' DEFS='-DHAVE_CONFIG_H' install); \
        done
making install in man
make[1]: Entering directory `/home/sean/Desktop/logsurfer+-1.7/man'
/usr/bin/install -c -m 644 logsurfer.1 /usr/local/man/man1/logsurfer.1
/usr/bin/install: cannot create regular file `/usr/local/man/man1/logsurfer.1': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/sean/Desktop/logsurfer+-1.7/man'
making install in src
make[1]: Entering directory `/home/sean/Desktop/logsurfer+-1.7/src'
/usr/bin/install -c logsurfer /usr/local/bin/logsurfer
make[1]: Leaving directory `/home/sean/Desktop/logsurfer+-1.7/src'

So that's the long and the short of it.... any ideas???

---

### Post by taurus on 2006-12-28
Aren't you supposed to run "./configure && make" first before you ran "**sudo** make install"?

---

### Post by DieslWeasl on 2006-12-29
> **taurus said:**
> Aren't you supposed to run "./configure && make" first before you ran "**sudo** make install"?

Sorry, I should have stated that... I did go ahead and run "./configure and make", I just copied and pasted from my last entry in term.  The "config and make" parts went well, it was the tail end of the "make install" that didn't work......... 

Anybody have any ideas.....

I'm a noob to Linux and Ubuntu, I just finished installing it yesterday....

---

### Post by taurus on 2006-12-29
Since it needs to install the binary to /usr/local/bin which you don't have permission to write to, therefore, you need to run it with the sudo command!

```
**sudo** make install
(and use the same password that you login in with...)
```

---

### Post by DieslWeasl on 2006-12-29
> **taurus said:**
> Since it needs to install the binary to /usr/local/bin which you don't have permission to write to, therefore, you need to run it with the sudo command!

```
**sudo** make install
(and use the same password that you login in with...)
```

Taurus, yep... I did sudo that command... still it didn't work...

---

### Post by taurus on 2006-12-29
You mean you get the same message as above!  What's the output of this command then?

```
ls -la /usr/local/bin
```

---

### Post by DieslWeasl on 2006-12-29
Taurus,

here is the output:

sean@silver:~$ ls -la /usr/local/bin
total 144
drwxr-xr-x 2 root root   4096 2006-12-29 06:48 .
drwxr-xr-x 9 root root   4096 2006-12-27 14:09 ..
-rwxr-xr-x 1 root root 134539 2006-12-29 06:48 logsurfer
sean@silver:~$


Any ideas??

---

