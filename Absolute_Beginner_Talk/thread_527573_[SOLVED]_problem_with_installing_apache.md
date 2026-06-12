---
title: "[SOLVED] problem with installing apache"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by kchang on 2007-08-16
I am running Ubuntu 7.04 and am unable to install Apache2. When I do ./configure I receive the following error:

```
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
configure failed for srclib/apr
```

I have tried "sudo apt-get install libc6-dev g++ gcc" and "sudo apt-get install build-essential". Both give me:

```
Package libc6-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libc6-dev has no installation candidate

Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
```

I have checked System>Administration>Software Sources and both universe and multiverse are checked.

I feel that I am missing something really silly. Any suggestions?

---

### Post by p_quarles on 2007-08-16
Some reason you don't want to install Apache2 from the repos? That's certainly the easiest way.

---

### Post by Ek0nomik on 2007-08-16
Do you have 'Main' checked as well in your software sources?

I would suggest running:

```
sudo apt-get update
```

then try to:

```
sudo apt-get install build-essential
```

---

### Post by kchang on 2007-08-16
> **Ek0nomik said:**
> Do you have 'Main' checked as well in your software sources?

I would suggest running:

```
sudo apt-get update
```

then try to:

```
sudo apt-get install build-essential
```

I have everything but "Source Code" checked in Software Sources. As for "sudo apt-get update" this is my output:

```
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://security.ubuntu.com feisty-security/main Packages
Ign http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Ign http://us.archive.ubuntu.com feisty/main Sources
Ign http://security.ubuntu.com feisty-security/restricted Packages
Ign http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Ign http://us.archive.ubuntu.com feisty/universe Packages
Ign http://us.archive.ubuntu.com feisty/universe Sources
Ign http://us.archive.ubuntu.com feisty/multiverse Packages
Ign http://us.archive.ubuntu.com feisty/multiverse Sources
Ign http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Get:4 http://security.ubuntu.com feisty-security/multiverse Sources [1052B]
99% [4 Sources bzip2 0] [Waiting for headers]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://security.ubuntu.com feisty-security/multiverse Sources
  Sub-process bzip2 returned an error code (2)
Get:5 http://security.ubuntu.com feisty-security/restricted Packages [6403B]
99% [5 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err http://security.ubuntu.com feisty-security/restricted Packages
  Sub-process gzip returned an error code (1)
Get:6 http://security.ubuntu.com feisty-security/main Sources [12.8kB]
99% [6 Sources gzip 0]          
gzip: stdin: not in gzip format
Err http://security.ubuntu.com feisty-security/main Sources
  Sub-process gzip returned an error code (1)
```

It seems, IMHO, that it's an issue with the apt-get command because when I try to apt-get anything it errs out on me.

---

### Post by p_quarles on 2007-08-16
If the apt package manager isn't working at all, that's the first thing to fix. Start a new thread -- with that in the title -- and the helpful folks here can most likely get it working for you.

---

### Post by kchang on 2007-08-16
I checked the forums and found a couple of "apt-get not working" posts that seem to have a fix. I haven't tried installing Apache yet. I will post back on whether I succeeded or not. Thank you for all your help.

---

### Post by Ek0nomik on 2007-08-17
What about:

```
sudo apt-get clean
```

Does that take care of any errors?

---

### Post by kchang on 2007-08-20
> **kchang said:**
> I checked the forums and found a couple of "apt-get not working" posts that seem to have a fix. I haven't tried installing Apache yet. I will post back on whether I succeeded or not. Thank you for all your help.

Apt-get seemed to be the issue. Apache installed without error. Thank you everyone for your help and suggestions!

---

### Post by Ek0nomik on 2007-08-20
> **kchang said:**
> Apt-get seemed to be the issue. Apache installed without error. Thank you everyone for your help and suggestions!

Could you please supply the link or information that solved your problem, and then mark the thread as solved?

How to mark Solved:  [http://ubuntuforums.org/showthread.php?t=530449](http://ubuntuforums.org/showthread.php?t=530449)

---

### Post by kchang on 2007-08-20
[http://ubuntuforums.org/showthread.php?t=217867]("http://ubuntuforums.org/showthread.php?t=217867") That's the thread that had the solution.

---

