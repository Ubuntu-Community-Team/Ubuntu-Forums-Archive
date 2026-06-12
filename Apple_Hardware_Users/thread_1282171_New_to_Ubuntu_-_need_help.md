---
title: "New to Ubuntu - need help"
date: 2009-10-04
forum: Apple Hardware Users
---

### Post by cranetoo on 2009-10-04
Hi - 

I'm a newcomer to linux...

I have an old G3 laptop and successfully Ubuntu 8.04 server.

I'm trying to get two apps running, CrashPlan and SqueezeCenter.

Seems like I need java running..  I've tried to install java6-jre.

I get:

The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-16-0ubuntu1.8.04) but it is not installable or
                          ia32-sun-java6-bin (= 6-16-0ubuntu1.8.04) but it is not installable
E: Broken packages

---

Can anyone help me get java installed?  Thanks!

Craig

---

### Post by oboedad55 on 2009-10-04
> **cranetoo said:**
> Hi - 

I'm a newcomer to linux...

I have an old G3 laptop and successfully Ubuntu 8.04 server.

I'm trying to get two apps running, CrashPlan and SqueezeCenter.

Seems like I need java running..  I've tried to install java6-jre.

I get:

The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-16-0ubuntu1.8.04) but it is not installable or
                          ia32-sun-java6-bin (= 6-16-0ubuntu1.8.04) but it is not installable
E: Broken packages

---

Can anyone help me get java installed?  Thanks!

Craig

How are you trying to install java? I usually do it through synaptic, that way it will automagically pull in the dependencies.

---

### Post by cranetoo on 2009-10-04
> **oboedad55 said:**
> How are you trying to install java? I usually do it through synaptic, that way it will automagically pull in the dependencies.

I don't think I have synaptic since I'm running server (no gui)...  But I'm so new I could be wrong.

So to install I typed 'sudo apt-get install sun-java6-jre'

---

### Post by oboedad55 on 2009-10-04
> **cranetoo said:**
> I don't think I have synaptic since I'm running server (no gui)...  But I'm so new I could be wrong.

So to install I typed 'sudo apt-get install sun-java6-jre'

Yeah, you're right. I didn't realize you were running a server. Have you tried installing sun-java6-bin first?

---

### Post by cranetoo on 2009-10-04
> **oboedad55 said:**
> Yeah, you're right. I didn't realize you were running a server. Have you tried installing sun-java6-bin first?

yup - I got:


sudo apt-get install sun-java6-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-bin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  sun-java6-jre
E: Package sun-java6-bin has no installation candidate

---

### Post by oboedad55 on 2009-10-04
> **cranetoo said:**
> yup - I got:


sudo apt-get install sun-java6-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-bin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  sun-java6-jre
E: Package sun-java6-bin has no installation candidate

Well? I booted up into my 8.04 installation and it looks as if what you're doing is exactly right. I thought maybe hardy used an older version of java or something, but nope. I wish I had more useful info for you. :confused:

---

### Post by cranetoo on 2009-10-04
Well... thank you anyway for trying.  Maybe someone else can help...

---

### Post by llamabr on 2009-10-04
dumb question maybe, but did you try:

```
sudo apt-get update && sudo apt-get install sun-java6-bin
```

---

### Post by cranetoo on 2009-10-04
> **llamabr said:**
> dumb question maybe, but did you try:

```
sudo apt-get update && sudo apt-get install sun-java6-bin
```

No dumb questions as far as I'm concerned.. (I'm stuck!)  :confused:

I got a long list of stuff after the get update/ get install sun java.... Here's the tail end:

Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-backports/main Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-backports/restricted Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-backports/universe Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-security/main Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-security/restricted Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-security/main Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-security/restricted Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-security/universe Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-security/universe Sources
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-security/multiverse Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) hardy-security/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-bin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  sun-java6-jre
E: Package sun-java6-bin has no installation candidate

---

### Post by cranetoo on 2009-10-04
I kept looking and it looks like this may be the problem.  There is no JRE for PPC!    Is that correct?  [http://ubuntuforums.org/showthread.php?t=870185](http://ubuntuforums.org/showthread.php?t=870185)

Is that a big deal?  I just want to install and run CrashPlan on my ibook g3 with ubuntu server.

I'll keep trying but any tips would be great.  Thanks

---

### Post by buntybuntu on 2009-10-07
This might be dumb, but if all you need is a JVM, then try installing Kaffe. 
 
sudo aptitude install kaffe
 
Hope this helps
buntyBuntu

---

### Post by jml on 2009-10-07
At the risk of stating the blindingly obvious, the OP mentions that the computer in question is an old G3.  If memory serves me, that is PowerPC architecture.  There is no longer official support for the PowerPC.  The PowerPC version is now community supported.  I don't know for sure, but that fact may have an impact on driver, and application availability.

Joe

---

### Post by cranetoo on 2009-10-08
Seems like Kaffe is worth a try.  At the moment I'm working on installing the IBM java version but I'm stuck with an installation error.  I'm using the instructions here [http://ubuntuforums.org/showthread.php?t=1116368](http://ubuntuforums.org/showthread.php?t=1116368)... I started here [https://help.ubuntu.com/community/JavaInstallation](https://help.ubuntu.com/community/JavaInstallation) but got a similar error.

I'm trying these with Jaunty instead of Hardy...  I'm going to keep trying this path for a while longer (I'm learning) and then if I can't make it work I'll try some other java versions.  

Thanks again for the continued input... I'd love other suggestions...  At first I was frustrated but now I'm just having fun.

Craig

---

