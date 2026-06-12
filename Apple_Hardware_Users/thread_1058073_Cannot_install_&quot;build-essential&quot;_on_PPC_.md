---
title: "Cannot install &quot;build-essential&quot; on PPC 8.04"
date: 2009-02-02
forum: Apple Hardware Users
---

### Post by ondrugs on 2009-02-02
Hello all,

Has anyone come across this issue? This is the last bit of "apt-get install build-essential":

[INDENT]The following packages have unmet dependencies.
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages
[/INDENT]

I've already done a "apt-get update" and "apt-get dist-upgrade".
Actually, I've just spotted the issue, but not sure how to sort it (I'm no good at apt):

[INDENT]The following packages have unmet dependencies.
  libc6-dev: Depends: libc6 (= 2.7-10ubuntu3) but 2.7-10ubuntu4 is to be installed
E: Broken packages
[/INDENT]

I'm not sure how to interpret this:

[INDENT]root@mac-mini:~# apt-cache depends libc6-dev
libc6-dev
  Depends: libc6
  Depends: linux-libc-dev
  Suggests: glibc-doc
  Suggests: manpages-dev
 |Recommends: gcc
  Recommends: <c-compiler>
    bcc
    gcc
    gcc-3.3
    gcc-3.4
    gcc-4.1
    gcc-4.2
  Conflicts: <libstdc++2.10-dev>
  Conflicts: <gcc-2.95>
  Conflicts: binutils
  Conflicts: <libc-dev>
  Replaces: man-db
  Replaces: gettext
  Replaces: ppp
  Replaces: <libgdbmg1-dev>
[/INDENT]

Any thoughts?

Any thoughts?

---

### Post by mkvnmtr on 2009-02-02
I would go to the package manager and remove any broken packages. Make a note of them because you may want to reinstall them later. Then I would put build essentials in the search box of the package manager. I would check the dependiences and make a note of what it recommends and what it suggests. Then I would try to install it with the package manager. Then I would think about installing the packages that were broken.

---

### Post by hadisen on 2009-04-14
The same thing is happening to me right now. I installed Ubuntu 8.04.2 on my Subnotebook and everything works fine (even WLAN and Bluetooth were configured pretty fast), however I am not able to install the g++ or build-essential packages. I am getting exactly the same error messages as you do. I've been googling for a solution for 4 hours now and noticed that I am not alone with this problem (showthread.php?t=1071458 showthread.php?t=525292 and this one) - but I did not find a solution. If it is not possible to compile C++-scripts I guess I will have to install another linux-distribution ? If anyone has an idea, please tell us.

I finally found something that might be helpful:
[https://bugs.launchpad.net/ubuntu/+source/build-essential/+bug/360550](https://bugs.launchpad.net/ubuntu/+source/build-essential/+bug/360550)
I'll give it a try.

---

### Post by hadisen on 2009-04-14
I also found this bug-report, which is probably closely related to our problem: [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/276465](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/276465). However it does not help me . . .

---

### Post by hadisen on 2009-04-14
I am finally able to install the build-essentials package without the message E: Broken packages. For this I had to reinstall the following packages in the 2.7-10ubuntu4 version using the synaptic manager:

libc6
libc6-dev
libc6-i686

gpp 4.2 was used to compile my kernel. If you have an older version installed, you may have to use the 2.7-10ubuntu3 version. Bye bye folks
 ):P

---

### Post by mikull on 2009-08-17
could u explain how to re-install!?
if i remove those packages,my ubuntu would surely die as the dependencies for those packages are heaps.
so could u shed some light on how exactly u did it..

---

### Post by shivathreya on 2009-08-22
Try "sudo apt-get -f install"

Shiva

---

