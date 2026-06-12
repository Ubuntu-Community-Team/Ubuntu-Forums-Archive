---
title: "Problem installing Texmaker"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2007-03-02
I am trying to install Texmaker ([http://www.xm1math.net/texmaker/download.html](http://www.xm1math.net/texmaker/download.html)) which I want to use as an editor for Latex. I have downloaded the installer file (texmaker_linux_installer) onto my desktop but cannot complete the installation process. Here is what I did:

```
sudo ./texmaker_linux_installer
```

After giving the paswword, I get the following error message:

```
./texmaker_linux_installer: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by ./texmaker_linux_installer)

```

Any ideas on how to proceed?

Thanks in advance.

---

### Post by amd-64 on 2007-03-03
Any reason why you did not use the synaptic version
```
sudo apt-get install texmaker
```

You may have some unsatisfied dependencies and apt/synaptic will also update all the dependencies for you.

---

### Post by aam-aadmi on 2007-03-03
I saw in some posts that people are downloading the binary and installing rather than using the version available in the repository. For instance, here
[http://www.ubuntuforums.org/archive/index.php/t-131507.html](http://www.ubuntuforums.org/archive/index.php/t-131507.html)

Maybe I should just try the version available in the repos.

---

### Post by amd-64 on 2007-03-03
It is possible that the developer version is more up to date at some points in time. However, I found that the repos for feisty have the latest texmaker ver. 1.5 which is the same version if you would download the binary installer.

If you use the repos, make sure to update the package list first in synaptic or using 
```
sudo apt-get update
```

---

### Post by aam-aadmi on 2007-03-04
I used the repository to download and install Texmaker and it seems to be working fine. Thanks amd-64.

---

### Post by amd-64 on 2007-03-04
Great, I usually use kile but will check texmaker too.

---

