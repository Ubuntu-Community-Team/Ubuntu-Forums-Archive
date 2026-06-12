---
title: "/bin/sh needed error"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by antonyant11 on 2008-02-14
I keep getting this message while trying to load an rpm

:confused:

does this mean i have to reinstall bash? If so how do i do that?

thanks in advance:)

---

### Post by mali2297 on 2008-02-14
What do you mean by *trying to load an rpm*?
How? 
With **alien**?

What program do you want to install? 
Have you looked for a .deb instead of a .rpm file?:-s

---

### Post by jan quark on 2008-02-14
> RPM Package (.rpm)
    RPM is another popular way of packaging software, and it's used by popular distributions such as Fedora Core, SUSE Linux and Mandriva. RPM is not used by the Ubuntu Package Manager, but there does exist a command for converting an RPM into a Deb; this doesn't mean that any RPM will work on your system, though! The same program can also install the RPM directly so that you won't have to do this yourself. The command is not available right away so you'll need to install it yourself - the package is called alien and is of course available through Synaptic. If the user carl wants to install an RPM called test.rpm located on his desktop, he will enter sudo alien -i /home/carl/Desktop/test.rpm.

taken form monkeyblog

---

### Post by oedha on 2008-02-14
you have to install alien....if you still force yourself to use rpm
is there no *.deb for you ? what program is that ?

---

### Post by antonyant11 on 2008-02-14
I am trying to install maya 8.0

using

rpm -i Maya8_0-8.0-163.i686.rpm AWCommon-10.80-12.i686.rpm AWCommon-server-10.80-7.x86_64.rpm

I will load alien and try that way, thanks:)

---

### Post by mali2297 on 2008-02-14
> **antonyant11 said:**
> I am trying to install maya 8.0

using

rpm -i Maya8_0-8.0-163.i686.rpm AWCommon-10.80-12.i686.rpm AWCommon-server-10.80-7.x86_64.rpm

I will load alien and try that way, thanks:)

Do you use the 32bit or 64bit version of Ubuntu?
In the first case you should use the *.i686.rpm files, otherwise the *.x86_64.rpm files. 

There is a howto [here]("http://ubuntuforums.org/showthread.php?t=66859").

---

### Post by antonyant11 on 2008-02-14
thanks for your help i am working my way through the installing maya forum now:)

---

### Post by hyper_ch on 2008-02-14
RPM --> Red Hat Packages
.deb --> Debian Packages (as Ubuntu is a Debian derivate, it also uses .deb)

Its best to find .debs. [http://www.getdeb.net](http://www.getdeb.net) is a good place to find .debs for ubuntu that are not in the repos (but Maya isn't in there either).

---

### Post by waylandbill on 2008-02-14
A word of warning using rpms. Even though Red Hat and Ubuntu are both Linux, and most things will be the same, there are some differences. File locations could be different. Files in the same location could have different enough contents or configurations to cause trouble. It's best to find a package designed for the system. You can always request that the package be included in the universe. If all else fails, you should grab a source package and build it. This may be a better way than getting a package designed for a different distro in the end.

---

### Post by antonyant11 on 2008-02-14
I tried to run the tutorial but after running alien I get this

t the end of converting the rpms i get this

Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
xargs -0 -r -i cp -a {} debian/maya8-0-docs-en-us
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find Maya8_0-docs_en_US-8.0 -type d -exec chmod 755 {} ;
find: Maya8_0-docs_en_US-8.0: No such file or directory
rm -rf Maya8_0-docs_en_US-8.0
](*,)

---

### Post by hyper_ch on 2008-02-14
if the conversion of the rpm fails, you could still compile it from source (or check if there is a .deb somewhere else).

---

### Post by mali2297 on 2008-02-14
> 
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)


Check if you have 32bit or 64bit,
```

uname -m

```
If it's x86_64, run
```

alien -cv AWCommon-server-10.80-7.x86_64.rpm
alien -cv AWCommon-10.80-12.x86_64.rpm 
alien -cv Maya8_0-8.0-163.x86_64.rpm 

```
Adjust the dpkg commands accordingly,
```

sudo dpkg -i AWCommon-server-10.80-7.x86_64.deb
sudo dpkg -i AWCommon-10.80-12.x86_64.deb 
sudo dpkg -i Maya8_0-8.0-163.x86_64.deb 

```

---

