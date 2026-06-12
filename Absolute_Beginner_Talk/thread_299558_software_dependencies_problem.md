---
title: "software dependencies problem"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by kester111 on 2006-11-14
Hi all,

I've run into some big problems with software dependencies.

Basically, while installing some piece of software from the debian 
site, it claimed that the package libc6 was not installed. i tried to install this, also from debian, but in turn it depended on a package called 
tzdata....tzdata could not install due to a conflict with some existing software (locale I think). Now i have the following problems.....
the synaptic package manager will not update anything because it claims that 
some packages are broken. I can't seem to get apt-get or dpkg to 
install, reinstall or otherwise fix libc6 or the other two packages 
which are broken (related to libc6) - it claims that libc6 depends on tzdata and this is not installable.  here's an example of the sort of thing;

kester@kester-laptop:/usr/share$ sudo apt-get -f dist-upgrade libc6-i386 libc6 libc6-dev
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-8 is installed
  libc6-i386: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-8 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

I'm stuck. Does anyone know how to fix this?

---

### Post by BarfBag on 2006-11-14
Man that's tough.  Try apt-get update.

---

### Post by kester111 on 2006-11-14
No joy with apt-get update or by using apt-get -f install 
or pdate, or by using apt-get upgrade or dist-upgrade.....

---

### Post by CatKiller on 2006-11-14
Forcing a dist-upgrade sounds a bit hardcore to me, but maybe you know what you're doing.

You could try a **sudo dpkg --configure -a** to configure any packages that are downloaded but not configured.

You could also try purging the broken packages, in case that will help you get your package management working again.

Are you running Edgy or something? My libc6 and libc6-dev packages don't seem to depend on tzdata.

You shouldn't mix-and-match Ubuntu and Debian stuff. But you probably know this by now.

---

### Post by kester111 on 2006-11-14
I guess not - it seemed like a good idea at the time though.

Stuff like dpkg --configure doesn't seem to work. I think that 
libc6 is too fundamental to purge. 

As far as I can tell, libc6 is unpacked but not configured. What i need 
if possible is to remove the deb version without touching the already installed version. Don't know if that's possible though.

---

### Post by Bachstelze on 2006-11-14
Never mind, I should have read more carefully...

---

### Post by CatKiller on 2006-11-14
> **kester111 said:**
> I guess not - it seemed like a good idea at the time though.

I just checked, and the -f option is **fix**, not **force** as I'd thought. So I owe you an apology. Sorry.

> Stuff like dpkg --configure doesn't seem to work. I think that 
libc6 is too fundamental to purge. 

As far as I can tell, libc6 is unpacked but not configured. What i need 
if possible is to remove the deb version without touching the already installed version. Don't know if that's possible though.

There is the option in Synaptic to force a version of a package. So you could force the libc6 to the Ubuntu version from the repositories, that may break the program you wanted to install, rather than the Debian one, that breaks everything else. Provided Synaptic is moderately functional. Otherwise, there may be a command-line equivalent that will work, but my skills in this area are not up to the task.

---

### Post by kester111 on 2006-11-14
kester@kester-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-8 is installed
  libc6-i386: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-8 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies



I think the problem may well arise because the file 
/var/lib/dpkg/status 
contains;

Package: libc6
Status: purge ok unpacked
Priority: required
Section: libs
Installed-Size: 9572
Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Architecture: amd64
Source: glibc
Version: 2.3.6.ds1-8
Config-Version: 2.3.6-0ubuntu20
Replaces: ldso (<= 1.9.11-9), timezone, timezones, gconv-modules, libtricks, netkit-rpc, netbase (<< 4.0)
Provides: glibc-2.3.6.ds1-1, glibc-2.3.6-2
Depends: tzdata
Suggests: locales, glibc-doc
Conflicts: strace (<< 4.0-0), libnss-db (<= 2.2-6.1.1), timezone, timezones, gconv-modules, libtricks, libc6-doc, netkit-rpc, wine (<< 0.0.20031118-1), cyrus-imapd (<< 1.5.19-15), e2fsprogs (<< 1.35-7), initrd-tools (<< 0.1.84.1), libterm-readline-gnu-perl (<< 1.15-2)
Conffiles:
 /etc/init.d/glibc.sh c9816a0fc91156ccc4c48d62d1447c23
 /etc/ld.so.conf.d/x86_64-linux-gnu.conf newconffile
Description: GNU C Library: Shared libraries
 Contains the standard libraries that are used by nearly all programs on
 the system. This package includes shared versions of the standard C librar
 and the standard math library, as well as many others.


ie tzdata dependency is listed....if it were possible to 
remove the record of this and the install has not proceeded too far 
(the package is unpacked but not configured) I'm hoping it is possible to return to the original version of libc6.....or perhaps reinstall it. 
Unfortunately, I don't know how to go about this, or even if it's possible.

---

### Post by CatKiller on 2006-11-14
As a possible: **sudo aptitude keep libc6 libc6-dev**

From **man aptitude**:
>        **remove, purge, hold, keep, reinstall**
              These commands are the same as **&#8216;&#8216;install&#8217;&#8217;**, but apply the  named
              action to all packages given on the command line for which it is
              not overridden. The difference between **hold**  and  **keep**  is  that
              **hold**  will  cause a package to be ignored by future **upgrade** com&#8208;
              mands, while **keep** merely cancels any scheduled  actions  on  the
              package.

              For  instance,  &#8216;&#8216;**aptitude  remove  &#8217;~ndeity&#8217;**&#8217;&#8217;  will remove all
              packages whose name contains **&#8216;&#8216;deity&#8217;&#8217;**.


---

### Post by kester111 on 2006-11-14
Catkiller - your force option in synaptic has worked - you're a life saver, except maybe for cats. 

Now I'm going home before I break my system any further today. 

:mrgreen:

---

### Post by CatKiller on 2006-11-14
> **kester111 said:**
> Catkiller - your force option in synaptic has worked - you're a life saver, except maybe for cats. 

I've saved at least one cat. The name's an anagram.

> Now I'm going home before I break my system any further today. 

:mrgreen:

Probably a good plan :biggrin:

---

### Post by stucky on 2006-12-16
Catkiller! I LOVE YOU, MAN (no gender bias implied)!!!

I've been battling for two days trying to get out of dependency hell with libfontconfig1 which wanted fontconfig-config 2.3xxxx and I already had 2.4xxxx installed. Forcing it to downgrade was the trick. Thanks for pointing out that Synaptic feature.

---

