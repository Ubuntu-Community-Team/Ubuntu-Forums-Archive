---
title: "Compiling Error.  Please help!"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by gamgee911 on 2007-10-21
I am trying to compile Avant Window Manager from source and I am having issues with my compiler.  After entering "./compile"  I get the following output:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

```

I have Ubuntu 7.04 and its up to date with updates (going to upgrade to 7.10 soon).  I am probably missing something obvious, anybody know what it is?

---

### Post by llamakc on 2007-10-21
sudo apt-get install build-essential

---

### Post by gamgee911 on 2007-10-21
ah, thank you :)

---

### Post by gamgee911 on 2007-10-21
Ok, It won't let me do that.  Here's what I get in terminal:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Broken packages
```

Am I missing a repository?

---

### Post by llamakc on 2007-10-21
Try updating first:

sudo apt-get update

then the install build-essential line again.

---

### Post by gamgee911 on 2007-10-21
No luck.  Still getting the same error.

---

### Post by llamakc on 2007-10-21
> **gamgee911 said:**
> No luck.  Still getting the same error.

Occasionally while packages are being upgraded on the servers you'll get this error. The easiest fix is to just wait a couple hours and try again.

---

### Post by gamgee911 on 2007-10-21
ok, thank you

---

