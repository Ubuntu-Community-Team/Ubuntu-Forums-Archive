---
title: "Canon ip4200 printer on 64 bit 7.10"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by mike sumner on 2007-12-27
I have the printer working in a fashion, as when I plugged it in, I was taken through an install sequence which I dont remember much about. The print quality is appalling, so II am trying to install the drivers using the wiki here:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

I have twice tried this and I am getting stuck at the following point in the proceedings:
mike@acer-7520:~/canon$ tar -xvzf iP4200_Linux_260.tar.gz 
cnijfilter-common-2.60-1.i386.rpm
cnijfilter-common-2.60-1.src.rpm
cnijfilter-ip4200-2.60-1.i386.rpm
cnijfilter-ip4200-lprng-2.60-1.i386.rpm
mike@acer-7520:~/canon$ sudo alien cnijfilter-common-2.60-1.i386.rpm cnijfilter-ip4200-2.60-1.i386.rpm 
[sudo] password for mike:
mkdir: cannot create directory `cnijfilter-common-2.60': File exists
unable to mkdir cnijfilter-common-2.60:  at /usr/share/perl5/Alien/Package.pm line 257.
mike@acer-7520:~/canon$ sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
mike@acer-7520:~/canon$ 

Is this likely to be anything to do with me using the 64 bit version of ubuntu?
Hope someone can help.
Thanks.

---

### Post by blueridgedog on 2007-12-28
> **mike sumner said:**
> I hav
[sudo] password for mike:
mkdir: cannot create directory `cnijfilter-common-2.60': File exists
unable to mkdir cnijfilter-common-2.60:  at /usr/share/perl5/Alien/Package.pm line 257.


At line 257 of the Alien app, it is trying to make a directory called "cnijfilter-common-2.60", but can't due to the fact that the directory exists.  This may be due to the fact that you have run this a few times and there is "leftover" garbage from other attempts, but my first pass would be to remove or rename that directory.

Also, until it makes the deb file, sudo dpkg -i *.deb will not work as there no *.deb to act upon.

---

### Post by mike sumner on 2007-12-31
Thanks blueridgedog.

I do not understand

> **blueridgedog said:**
> 
Also, until it makes the deb file, sudo dpkg -i *.deb will not work as there no *.deb to act upon.

What makes the deb file and how do I make this happen?

Cheers, Mike

---

### Post by blueridgedog on 2007-12-31
You have an TGZ file with an RPM inside:

mike@acer-7520:~/canon$ tar -xvzf iP4200_Linux_260.tar.gz 
cnijfilter-common-2.60-1.i386.rpm
cnijfilter-common-2.60-1.src.rpm
cnijfilter-ip4200-2.60-1.i386.rpm
cnijfilter-ip4200-lprng-2.60-1.i386.rpm

Now you have an RPM file and want to convert it to a .deb file so you can install it.  You use alien to do so:

mike@acer-7520:~/canon$ sudo alien cnijfilter-common-2.60-1.i386.rpm cnijfilter-ip4200-2.60-1.i386.rpm 
[sudo] password for mike:
mkdir: cannot create directory `cnijfilter-common-2.60': File exists
unable to mkdir cnijfilter-common-2.60:  at /usr/share/perl5/Alien/Package.pm line 257.

However, it tells you above that it can't make the .deb file due to an error.

But, you tell it to install the deb file:

mike@acer-7520:~/canon$ sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory

It in turn tells you the file isn't there, hence my comment that until you get the alien error solved, there is no deb file to install.

Post the output of 

ls -al ~/cannon

Perhaps we can see what is going wrong.

---

### Post by mike sumner on 2008-01-02
> **blueridgedog said:**
> 
Post the output of 

ls -al ~/cannon

Perhaps we can see what is going wrong.


mike@acer-7520:~$ ls -al ~/canon
total 31904
drwxr-xr-x  3 mike mike     4096 2008-01-02 15:10 .
drwxr-xr-x 36 mike mike     4096 2008-01-02 15:06 ..
drwxr-xr-x  4 root root     4096 2007-12-18 23:59 cnijfilter-common-2.60
-r-xr-xr-x  1 mike mike    24398 2006-03-10 07:10 cnijfilter-common-2.60-1.i386.rpm
-r-xr-xr-x  1 mike mike  8629535 2006-03-10 07:10 cnijfilter-common-2.60-1.src.rpm
-r-xr-xr-x  1 mike mike  2101850 2006-03-10 07:10 cnijfilter-ip4200-2.60-1.i386.rpm
-r-xr-xr-x  1 mike mike   130067 2006-03-10 07:10 cnijfilter-ip4200-lprng-2.60-1.i386.rpm
-rw-r--r--  1 mike mike 10852648 2006-05-26 23:00 iP4200_Linux_260.tar.gz
-rw-r--r--  1 mike mike 10852648 2006-05-26 23:00 iP4200_Linux_260.tar.gz.1
mike@acer-7520:~$

---

### Post by blueridgedog on 2008-01-02
It looks like there is already a directory named cnijfilter-common-2.60 and that is one of the erros.  I suggest renaming it.

(in that directory)

sudo mv ./cnijfilter-common-2.60 ./cnijfilter-common-2.60.bak

Then try your rpm to deb conversion again.

---

### Post by mike sumner on 2008-01-03
OK, tried that:

mike@acer-7520:~/canon$ sudo alien cnijfilter-common-2.60-1.i386.rpm cnijfilter-ip4200-2.60-1.i386.rpm 
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/cnijfilter-common
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path libcups.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path libcups.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpopt.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path libcups.so.2, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libpopt.so.0
dpkg-shlibdeps: warning: unable to find dependency information for shared library libpopt (soname 0, path libpopt.so.0, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for libcups.so.2
dpkg-shlibdeps: warning: unable to find dependency information for shared library libcups (soname 2, path libcups.so.2, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: cnijfilter-common-2.60: No such file or directory
mike@acer-7520:~/canon$ 

Oh dear,  I just re-read the beginning of the wiki where it says it doesn't work for 64-bit!
Sorry, I missed that first time around.
Will there be a work-round?
Cheers, Mike

---

### Post by blueridgedog on 2008-01-03
It look like, from this line:

dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)

That you have the 32 bit rpm.  You should run the process with the 64 bit one (if available).

---

### Post by mike sumner on 2008-01-03
ahh, the joys of 64-bit........

Guess I need to write to canon.
Dont know why it didnt occur to me that all the rpms had "i386" written all over them!
Anyway, thanks for your help.

Cheers, Mike

---

### Post by blueridgedog on 2008-01-03
Sorry, a dead end seems so lame, but we tried.

---

### Post by exactopposite on 2008-01-03
> **mike sumner said:**
> ahh, the joys of 64-bit........

Guess I need to write to canon.
Dont know why it didnt occur to me that all the rpms had "i386" written all over them!
Anyway, thanks for your help.

Cheers, Mike

good luck with canon. i tried writing to them after using files from the japanese canon site and they wouldn't even aknowledge that the files existed.

---

