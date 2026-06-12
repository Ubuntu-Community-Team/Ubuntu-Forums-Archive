---
title: "C++ Compiler for Ubuntu 6"
date: 2006-09-06
forum: Apple PPC Users
---

### Post by sshahir on 2006-09-06
I am new with Ubuntu Linux and would like to use C++ compiler, but the compiler is not embedded with the first installation, and I have to download the compiler. First, I have to connect to Internet before I can download it. But I have problem with Internet connection ([http://www.ubuntuforums.org/showthread.php?t=251867)](http://www.ubuntuforums.org/showthread.php?t=251867)). 

If I down load the compiler in Windows environment, I cannot transfer it to Linux environment.

I appreciate for any comment about that how I can get C++ compiler for Ubuntu 6. Thanks.

sshahir

---

### Post by IYY on 2006-09-06
What you need is the build-essential package. It's on the install CD, so you don't need to download anything. If the CD is in your repositories and is inserted,

sudo apt-get install build-essential

---

### Post by sshahir on 2006-09-06
Thanks a lot. I got it.

Regards,
sshahir

---

### Post by soberdanish on 2006-09-10
I want to work on NS-2 for that i need a c++compiler on UBUNTU.
I still did not get that how do i get the c++ compiler on UBUNTU.
I will highly appreciate if someone can please tell in detail.

Best regards

---

### Post by Buffalo Soldier on 2006-09-10
> **soberdanish said:**
> I want to work on NS-2 for that i need a c++compiler on UBUNTU.
I still did not get that how do i get the c++ compiler on UBUNTU.
I will highly appreciate if someone can please tell in detail.

Best regards[list]
[*] Insert your Ubuntu Installation CD
[*] at the terminal/command line (Applications -> Accesorries -> Terminal) run ```
gksudo apt-get install build-essential
```
[/list]
build-essential contains not only C++ compilers but other compilers and common tools for making packages/applications.

---

