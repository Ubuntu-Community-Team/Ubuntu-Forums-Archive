---
title: "[SOLVED] Ubuntu 7.10 Kernel Version?"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by tomihasa on 2008-01-27
What is Ubuntu 7.10's Linux kernel version? Can you find it out like this:

```

cat /proc/version

```

Mine says "Linux version 2.6.22-14-cel". Is that correct? I'm going to download OpenOffice.org 2.3.1, and the official page says I need Linux kernel 2.2.13.

---

### Post by candtalan on 2008-01-27
mine says
Linux version 2.6.22-14-generic (and other stuff..)

If an application says it needs a version like
'need Linux kernel 2.2.13'  then it usually means it needs that version or any subsequent version. So my understanding is you will be fine.

---

### Post by y-lee on 2008-01-27
> **tomihasa said:**
> What is Ubuntu 7.10's Linux kernel version? Can you find it out like this:

```

cat /proc/version

```


Well that seems to work.

I always used

 ```
uname -a
```

---

### Post by scorp123 on 2008-01-27
> **tomihasa said:**
>  What is Ubuntu 7.10's Linux kernel version? Can you find it out like this: cat /proc/version The standard UNIX command for this is ```
uname  -a
```

> **tomihasa said:**
>  I need Linux kernel 2.2.13. That's a very very ancient release that probably won't even run on today's hardware (e.g. no SATA support back then). What they probably want to say is "2.2.13 or better".

As for OpenOffice ... why download it? The new release will probably soon be available in the repos anyway and you will be able to easily install it via "Synaptic". Depending on your level of knowledge those "download + install it yourself" programs can cause a lot of trouble and cause more frustration than the few new features are worth, IMHO.

---

### Post by John.Michael.Kane on 2008-01-27
> **tomihasa said:**
> What is Ubuntu 7.10's Linux kernel version? Can you find it out like this:

```

cat /proc/version

```

Mine says "Linux version 2.6.22-14-cel". Is that correct? I'm going to download OpenOffice.org 2.3.1, and the official page says I need Linux kernel 2.2.13.
Yes passing cat /proc/version will work, as will passing the below command.

```
uname -r
```

Will print the kernel release.

Example output from test machine.
```
2.6.23.14-107.fc8
```

---

### Post by tomihasa on 2008-01-27
> **scorp123 said:**
> The standard UNIX command for this is ```
uname  -a
```
As for OpenOffice ... why download it? The new release will probably soon be available in the repos anyway and you will be able to easily install it via "Synaptic". Depending on your level of knowledge those "download + install it yourself" programs can cause a lot of trouble and cause more frustration than the few new features are worth, IMHO.

Unfortunately, I haven't been able to make my Internet connection work yet with my PS3 when I'm using Ubuntu 7.10 in it:

[http://ubuntuforums.org/showthread.php?t=679785](http://ubuntuforums.org/showthread.php?t=679785)

If you mean the Add/Remove Applications thing, it says:

"The list of available applications is out of date"
"To reload the list you need a working internet connection."

---

### Post by scorp123 on 2008-01-27
> **tomihasa said:**
> Unfortunately, I haven't been able to make my Internet connection work yet with my PS3 when I'm using Ubuntu 7.10 in it:

[http://ubuntuforums.org/showthread.php?t=679785](http://ubuntuforums.org/showthread.php?t=679785)

If you mean the Add/Remove Applications thing, it says:

"The list of available applications is out of date"
"To reload the list you need a working internet connection." Downloading OpenOffice won't help you. Chances are that the package has dependencies that need to be resolved too. Besides: "PS3" ... as in "Sony PlayStation 3"? That would explain the kernel version you mentioned in your first posting: 2.6.22-14-**cel** ... BUT: Version 2.3.1 is for **Intel i386** CPU's .... You having a PS3 would need to go for the **Motorola/IBM PowerPC "Linux PPC"** release, and that one is still stuck at **version 1.1.2** .... So if you really want 2.3.1 you'd need to compile it yourself. You'd need many compiler packages, development libraries, ... and to get all that you'd need a working Internet connection. So you're kinda stuck there, I fear.

---

