---
title: "Installing Java Runtime environment"
date: 2005-07-02
forum: Absolute Beginner Talk
---

### Post by aniket on 2005-07-02
Hi everybody,

can anyone tell me how to install java runtime environment in ubuntu?

thanks,

aniket

---

### Post by sapo on 2005-07-02
Just read this  :grin: 

[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

And read the "how to add new repositories" first

---

### Post by djlinuxgod2@comcast.net on 2005-09-20
Did that work for you?  I tried that and the package wasn't available.

---

### Post by karuptdata on 2005-09-20
The way i installed it was i just downloaded the .bin from java extracted the file then created a directory usr/java then moven the jre file in that directory.

---

### Post by listen on 2005-09-24
did the way ubuntu wiki restricted formats [https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29) advised, but got the following errors during installing..

/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 285: /etc/mailcap: Permission denied
mkdir: cannot create directory `/usr/share/icons/HighContrast/48x48/apps': Permission denied
mkdir: cannot create directory `/usr/share/icons/HighContrastInverse/48x48/apps': Permission denied
mkdir: cannot create directory `/usr/share/icons/LowContrast/48x48/apps': Permission denied
cp: cannot create regular file `/usr/share/pixmaps/sun-java.png': Permission denied
cp: cannot create regular file `/usr/share/icons/HighContrast/48x48/apps/sun-java.png': No such file or directory
cp: cannot create regular file `/usr/share/icons/HighContrastInverse/48x48/apps/sun-java.png': No such file or directory
cp: cannot create regular file `/usr/share/icons/LowContrast/48x48/apps/sun-java.png': No such file or directory
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 433: /usr/share/mime-info/java-archive.keys: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 434: /usr/share/mime-info/java-archive.keys: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 435: /usr/share/mime-info/java-archive.keys: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 436: /usr/share/mime-info/java-archive.keys: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 437: /usr/share/mime-info/java-archive.keys: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 438: /usr/share/mime-info/java-archive.keys: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 441: /usr/share/mime-info/java-archive.mime: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 442: /usr/share/mime-info/java-archive.mime: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 445: /usr/share/application-registry/java-archive.applications: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 446: /usr/share/application-registry/java-archive.applications: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 447: /usr/share/application-registry/java-archive.applications: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 448: /usr/share/application-registry/java-archive.applications: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 449: /usr/share/application-registry/java-archive.applications: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 450: /usr/share/application-registry/java-archive.applications: Permission denied
mkdir: cannot create directory `/usr/share/icons/HighContrast/48x48/apps': Permission denied
mkdir: cannot create directory `/usr/share/icons/HighContrastInverse/48x48/apps': Permission denied
mkdir: cannot create directory `/usr/share/icons/LowContrast/48x48/apps': Permission denied
cp: cannot create regular file `/usr/share/pixmaps/sun-java.png': Permission denied
cp: cannot create regular file `/usr/share/icons/HighContrast/48x48/apps/sun-java.png': No such file or directory
cp: cannot create regular file `/usr/share/icons/HighContrastInverse/48x48/apps/sun-java.png': No such file or directory
cp: cannot create regular file `/usr/share/icons/LowContrast/48x48/apps/sun-java.png': No such file or directory
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 433: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 434: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 435: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 436: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 437: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 438: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 441: /usr/share/mime-info/java-web-start.mime: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 442: /usr/share/mime-info/java-web-start.mime: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 445: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 446: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 447: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 448: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 449: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/mark/Desktop/jre-1_5_0_05-linux-i586.bin: line 450: /usr/share/application-registry/java-web-start.applications: Permission denied

Done.

Testing extracted archive... okay.

Create debian package:
    dh_testdir
    dh_testroot
    dh_installchangelogs
    dh_installdocs
    dh_compress
    dh_fixperms
    dh_installdeb
    dh_shlibdeps
dpkg-shlibdeps: warning: could not find path for libXp.so.6
dpkg-shlibdeps: warning: could not find any packages for  (libXp.so.6)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXp (soname 6, path , dependency field Depends)
    dh_gencontrol
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
    dh_md5sums
md5sum: usr/lib/j2re1.5-sun/lib/deploy.jar: Input/output error
    dh_builddeb
dpkg-deb: building package `sun-j2re1.5' in `/tmp/make-jpkg.XXXX2T2ycx/sun-j2re1.5_1.5.0+update05_i386.deb'.
tar: ./usr/lib/j2re1.5-sun/lib/deploy.jar: File shrank by 1678907 bytes; padding with zeros
tar: Error exit delayed from previous errors
dpkg-deb: subprocess tar -cf returned error exit status 2
dh_builddeb: command returned error code 512

Aborted (--destdir=/tmp/make-jpkg.XXXX2T2ycx).

Removing temporary directory: done

at the end, didnt install.....does anyone know what's going on and how to resolve this...thanks in advance.

---

### Post by Benzima on 2005-09-24
After hours of bashing my head into the keyboard I found and used this , also from wiki:

[https://wiki.ubuntu.com/JavaPackageBuildNewVersions](https://wiki.ubuntu.com/JavaPackageBuildNewVersions)

Bookmark it, now.

---

### Post by bored2k on 2005-09-24
1. [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp)
2.
Download Linux self-extracting file jre-1_5_0_04-linux-i586.bin  (or whatever the file is) 15.83 MB
3.
```
sudo apt-get install fakeroot java-package
```
4.
```
fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin
```
or
```
fakeroot make-jpkg jre-*
```
or
```
fakeroot make-jpkg jdk-*
```
5.
```
sudo dpkg -i *.deb 
```

---

### Post by YourSurrogateGod on 2005-09-24
[QUOTE=djlinuxgod2@comcast.net]Did that work for you?  I tried that and the package wasn't available.[/QUOTE]
Your package manager couldn't find sun-j2re1.5?

If so, then read [this](http://ubuntuguide.org/#extrarepositories).

---

### Post by bored2k on 2005-09-24
[QUOTE=YourSurrogateGod]Your package manager couldn't find sun-j2re1.5?

If so, then read [this](http://ubuntuguide.org/#extrarepositories).[/QUOTE]
 Java goes on and off the backports. Sometimes its there, sometimes it isnt.

---

