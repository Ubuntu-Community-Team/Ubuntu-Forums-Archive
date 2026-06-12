---
title: "Where is the 'xine' executable installed?"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by smith.norton on 2006-12-24
I have installed both xine-lib and xine-ui on my Ubuntu 6.06 system. 'man xine' shows a man page for xine. However the command 'xine' doesn't work.

On running 'xine-check' I get the following output.

```
$ xine-check
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.15-23-386)
[ good ] intel compatible processor, checking MTRR support
[ hint ] you have MTRR support but it's unused.
         It seems like your X server didn't set any MTRR ranges for the
         graphics card. Maybe upgrading your X server helps...
         You don't have a PCI graphics card, do you? AFAIK, MTRR only
         helps with AGP cards.
         press <enter> to continue...

[ good ] unable to find 'xine' binary in usual places
[OUCH!!] There is no 'xine' executable in your PATH
         Maybe you don't have xine-ui installed?
         If xine-ui is installed, it would probably be a good idea to add
         it's binary directory to your PATH...
         press <enter> to continue...
```


```
$ ls -ld `find / -name xine 2> /dev/null`
drwxr-xr-x 2 root root 4096 2006-12-16 00:16 /usr/local/include/xine
drwxr-xr-x 3 root root 4096 2006-12-15 22:54 /usr/local/lib/xine
drwxr-xr-x 4 root root 4096 2006-12-16 00:13 /usr/local/share/doc/xine
drwxr-xr-x 7 root root 4096 2006-12-23 22:04 /usr/local/share/xine
```

So, I don't have any 'xine' executable installed in my system. But I had installed xine-ui. What's the problem? How do I run the xine player? :(

- Smith

---

### Post by Adrenal on 2006-12-24
Should be in the "multimedia" section of your gnome menu

---

### Post by po0f on 2006-12-24
smith.norton,

It's probably `xine-ui`.  Did you custom compile it?  Look in /usr/lcoal/bin.

---

### Post by smith.norton on 2006-12-24
Yes, I compiled both xine-lib and xine-ui from the source. How can it be xine-ui? As I said, man page for xine exists and I can view it using 'man xine'.

Also, there is no 'xine-ui' present as executable. Anybody can help me out?

- Smith

---

### Post by po0f on 2006-12-24
smith.norton,

Did you remember to `make install` after compiling xine-ui?  What are the contents of /usr/local/bin?
```
[FONT="Courier New"]$ ls -l /usr/local/bin[/FONT]
```

[EDIT]

Post the output of this command as well:
```
[FONT="Courier New"]$ echo $PATH[/FONT]
```

---

