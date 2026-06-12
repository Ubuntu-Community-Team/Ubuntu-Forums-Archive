---
title: "Kernel Modules"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by Franks&amp;Beans on 2006-07-18
Using Dapper 

Am trying to update my ATI drivers and during a script install it comes up with:

[INDENT]The DRI drivers can not be installed without the latest kernel modules.Installation will be aborted. 
[/INDENT]
The install log file says:

[INDENT]./install.sh: line 678: make: command not found[/INDENT]

I think I need help to point me to which extra packages I need to install.

Thanks.

---

### Post by swamytk on 2006-07-18
$sudo apt-get install build-essential

---

### Post by Sef on 2006-07-18
> $sudo apt-get install build-essential

It's best to do this before the sudo apt-get install:

```
sudo apt-get update
```

then

```
sudo aptitude install build-essential
```

Aptitude is better in case you need uninstall.

---

### Post by Franks&amp;Beans on 2006-07-18
OK. Have done the above and installed build-essentials but it still comes up with exectly the same error. Am I missing something else?

Thanks.

---

### Post by muep on 2006-07-18
It is build-essential, not build-essentials.

Did you get any errors when you installed the package? If not, build-essential should be installed now.

Can you run make from the command line?

---

### Post by Franks&amp;Beans on 2006-07-18
Sorry my typo. Yes it did install properly. and can run make from command line.

I must be doing something wrong.

I am trying to install this driver as desrcibed at the bottom of this page.

[http://www.ubuntuforums.org/showthread.php?t=32015]("http://www.ubuntuforums.org/showthread.php?t=32015")

---

### Post by Franks&amp;Beans on 2006-07-18
Maybe this is progress?

Install.log now says:

"Makefile:173: *** Cannot find a kernel config file.  Stop."

Any thoughts?

---

