---
title: "Problem executing file on Ubuntu 7.04 64-Bit"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by TheMafioso on 2007-04-24
Hi Guys,

I've recently installed Ubuntu 7.04, 64-Bit version on my machine for doing some college work.
I'm trying to install a software named Glomosim on it (it is a software for simulating wireless networks). However when I try to run its executable 'pcc' by doing ./pcc I get the error "No such file or directory". I do have this file in the present working directory as shown by ls command, so I don't know why I'm getting this error ... any possible reasons ???

Regards,

---

### Post by SaddaGocaraRupa on 2007-04-24
isn't the executable usually in /usr/bin ? have a look there...if there's nothing maybe it's not installed properly..

---

### Post by taurus on 2007-04-24
Can you post the output of this command in the directory where pcc is?  Perhaps you need to change the permissions of that file so you can run it.

```
ls -la
```

---

### Post by TheMafioso on 2007-04-24
ls -la command gives this output

```

abeer@abeerb:~/glomosim-2.03/parsec/redhat-7.2/bin$ ls -la
total 200
drwxr-xr-x   2 abeer abeer     16    2007-04-24 17:38 .
drwxr-xr-x   6 abeer abeer     32    2007-04-24 17:38 ..
-rwxrwxrwx   1 abeer abeer 101429 2002-02-17 12:21 parsecc
-rwxr-xr-x   1 abeer abeer 101429 2002-02-17 12:21 pcc

```

When i try to execute pcc, I get this output
```

abeer@abeerb:~/glomosim-2.03/parsec/redhat-7.2/bin$ ./pcc
bash: ./pcc: No such file or directory

```

@SaddaGocaraRupa It dosen't install in a way normal software's do....its a command line program...the pcc is actually a parser used to compile glomosim source..

---

### Post by taurus on 2007-04-24
What's the output of this command then?

```
file pcc
```

---

### Post by TheMafioso on 2007-04-24
It shows
```

pcc: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5,
dynamically linked (uses shared libs), not stripped

```

hmmm...is it due to the my linux's 64-Bit version ?

---

### Post by taurus on 2007-04-24
Yes.  If you want to run some 32bit binaries on your 64bit system, you need to install all those 32bit libraries first.  Try that and see if you can run pcc again.

Also, what's the output of this command?

```
ldd pcc
```

---

### Post by TheMafioso on 2007-04-24
^Well it says
```

not a dynamic executable

```

I don't know what all 32-Bit libraries are required...any way if I could find it out...
Alternatively, if I would install the 32-bit version of ubuntu, it should work right...Just asking this version of parsec(ie. pcc) is for redhat-7.2 (though it also works on fc6 in college)

---

### Post by jsym on 2007-04-25
I seem to have the exact same problem while trying to install S-Plus 7.0. :) 

See:
[http://ubuntuforums.org/showthread.php?t=422767]("http://ubuntuforums.org/showthread.php?t=422767")

I'll see about installing the 32 bit libraries (not sure what they are though) and report back.  Why would Feisty dump these libraries anyway (Everything was working fine in earlier versions so I assume the libraries were installed then)?

---

### Post by jsym on 2007-04-25
SOLVED! \\:D/ 

At least for me. ;) 

The missing libraries are part of the Linux Standard Base (see [http://www.linux-foundation.org/en/LSB]("http://www.linux-foundation.org/en/LSB")) and can be installed simply by choosing **lsb-core** in synaptic.

Hope this helps you out.

---

