---
title: "How-to: Installing IBM-Java on PowerPC"
date: 2009-04-04
forum: Apple Hardware Users
---

### Post by tiresia on 2009-04-04
The default Java for PowerPC available in Ubuntu is openjdk, that you can install via apt-get (for more info visit [http://openjdk.java.net](http://openjdk.java.net))
You may also be interested in other projects such as Kaffe - although "Kaffe is not Java" (for more info visit [http://www.kaffe.org/](http://www.kaffe.org/))

**This How-to deals with the process of installing IBM-Java on PowerPC machines running Ubuntu Intrepid 8.10 and Jaunty 9.04 **(but it should work also in Hardy 8.04)
**[COLOR="Red"]WARNING You can screw up your system. Try at your own risk![/COLOR]** - *and forgive me for my english!* :)

Sun has never released Java for Linux on PowerPC. On Debian-platforms you can download a ppc-release of Java from IBM Web-site and generate an installable .deb package using the tool make-jpkg (that comes with the 'java-package').
In Ubuntu this process fails, because make-jpkg needs a library (libstdc++5) that you can't install with apt-get, because it needs another package (gcc-3.3), that is not available [https://bugs.launchpad.net/ubuntu/+source/gcc-3.3/+bug/326964](https://bugs.launchpad.net/ubuntu/+source/gcc-3.3/+bug/326964)
(by the way, this produces another problem by installing ppc-codecs from medibuntu [https://bugs.launchpad.net/ubuntu/+source/gcc-3.3/+bug/312734](https://bugs.launchpad.net/ubuntu/+source/gcc-3.3/+bug/312734))


Therefore, **installing IBM-Java will follow in three steps**:

1. Make make-jpkg working properly, downloading libstdc++5 from the debian repositories
2. Download IBM-Java, create and install an ibm-java .deb package
3. Check the installed IBM-Java and link the browser plugin to Firefox



[SIZE="3"]**1. _An (almost) properly working make-jpkg_**[/SIZE]

Download java-package
```
sudo apt-get java-package
```
Download libstdc++5 for PowerPC to your Desktop from this link [http://packages.debian.org/lenny/libstdc++5](http://packages.debian.org/lenny/libstdc++5) and install it ```
cd Desktop
sudo dkpg -i libstdc++5_3.3.6-18_powerpc.deb
sudo apt-get update
```


**[SIZE="3"]2. _Installing IBM-Java_[/SIZE]**

Create a directory (ex. Downloads/IBM-Java) and download IBM-Java from this link (free registration required)  
[http://www.ibm.com/developerworks/java/jdk/linux/download.html](http://www.ibm.com/developerworks/java/jdk/linux/download.html)

IBM releases Java for 32-bit and 64-bit ppc. Choose according to your architecture (Apple G3, G4= 32-bit; Apple G5=64-bit).
After the registration, you have the option to download using Download Director or via http. Since you need Java to use the Download Director, choose to download via http
Ubuntu (and Debian) users needs files ending with .tgz (not .rpm!)
You can install just the Java Runtime Environment (JRE), or the Java development Kit (JDK) that contains also JRE.
But **not every version is supported by the java-package**.
If you want to see, which version your java-package supports, have a look to the file /usr/share/doc/java-package/SUPPORTED.gz (do not edit it!)

I downloaded ibm-java-sdk-6.0-4.0-linux-ppc.tgz, that is not supported but it looks quite similar to another supported version (ibm-java-sdk-6.0-4.0-linux-ppc.tgz)
Therefore I renamed the downloaded package to the supported version ```
cd Downloads/IBM-Java
mv ibm-java-sdk-6.0-4.0-linux-ppc.tgz ibm-java-sdk-6.0-0.0-linux-ppc.tgz
```
Make an installable .deb package ```
fakeroot make-jpkg ibm-java-sdk-6.0-0.0-linux-ppc.tgz
```
Most probably you will get some errors.
Wait until it has finished and install it (the generated package I got is called 'ibm-j2sdk1.6_1.6.0_powerpc.deb') ```
sudo dpkg -i ibm-j2sdk1.6_1.6.0_powerpc.deb
```


**[SIZE="3"]3. _Check the installed IBM-Java and link the browser plugin to Firefox_[/SIZE]**

Check the installed Java's version
```
java -version
```
The installed browser plugin is 'libjavaplugin_oji.so' (/usr/lib/j2sdk1.6-ibm/jre/plugin/ppc/ns7/libjavaplugin_oji.so).
There are several broken links in /etc/alternatives and in /usr/lib/mozilla-firefox/plugins/
You need to unlink and to relink them to the new installed plugin.
I notice that it should already work if you link the plugin to /etc/alternatives/mozilla-javaplugin.so
```
sudo unlink /etc/alternatives/mozilla-javaplugin.so
sudo ln -s /usr/lib/j2sdk1.6-ibm/jre/plugin/ppc/ns7/libjavaplugin_oji.so /etc/alternatives/mozilla-javaplugin.so 
```
Restart Firefox and check if the java plugins were loaded
Type in the Navigation Toolbar
```
about:plugins
```
Visit this link to check if the java-plugin is working
[http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

______________________
Useful links:

[http://peter.makholm.net/2007/04/16/java-on-linuxppc/](http://peter.makholm.net/2007/04/16/java-on-linuxppc/)
[http://www.ibm.com/developerworks/systems/library/es-apple.html](http://www.ibm.com/developerworks/systems/library/es-apple.html)
[http://www.debianhelp.co.uk/debianjava.htm](http://www.debianhelp.co.uk/debianjava.htm)
[http://www.debianhelp.co.uk/javadeb.htm](http://www.debianhelp.co.uk/javadeb.htm)
[http://www.debianhelp.co.uk/browserplugins.htm](http://www.debianhelp.co.uk/browserplugins.htm)****

---

### Post by catull on 2009-07-17
tiresia


I followed the steps and indeed the JDK/JRE is installed in /usr/lib/j2sdk1.6-ibm.

When I call /usr/lib/j2sdk1.6-ibm/bin/java or ./java when being in that folder, I get

> /usr/lib/j2sdk1.6-ibm/bin/java
zsh: no such file or directory: /usr/lib/j2sdk1.6-ibm/bin/java
[1]    7212 exit 127   /usr/lib/j2sdk1.6-ibm/bin/java

As this is a link to  > /usr/lib/j2sdk1.6-ibm/jre/bin/java, running that command I get a similar error:

> /usr/lib/j2sdk1.6-ibm/jre/bin/java
zsh: no such file or directory: /usr/lib/j2sdk1.6-ibm/jre/bin/java
[1]    7213 exit 127   /usr/lib/j2sdk1.6-ibm/jre/bin/java

No difference if called as java-j2sdk1.6-ibm.

A trace is also confusing, as all directories do exist, and are chmod 0755.

> strace /usr/lib/j2sdk1.6-ibm/jre/bin/java
execve("/usr/lib/j2sdk1.6-ibm/jre/bin/java", ["/usr/lib/j2sdk1.6-ibm/jre/bin/ja"...], [/* 49 vars */]) = -1 ENOENT (No such file or directory)
dup(2)                                  = 3
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fstat64(3, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xf7ffb000
_llseek(3, 0, 0xff9801c8, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: No such file or dir"..., 40strace: exec: No such file or directory
) = 40
close(3)                                = 0
munmap(0xf7ffb000, 4096)                = 0
exit_group(1)                           = ?


Did you set LD_ASSUME_KERNEL ?
The binaries are reported as built for kernel 2.4.19 . . .

Any help is appreciated.


Thanks,
--
catull

---

### Post by catull on 2009-07-18
Hmm


Installing the 32-bit version on my G5 solved the problem.
Make-jpkg gave a ton of errors; it did not give as many with the 64-bit version.

Thanks again for the howto.


Regards,
--
catull

---

### Post by Nullack on 2009-07-18
The powerpc java packages are all messed up in the repos. Why even have sunhava 1.5 and 1.6 in the repos for powerpc if the pckages arent suitable for that platform? Synaptic errors out when trying to install the JRE on powerpc.

---

### Post by cranetoo on 2009-10-08
Hi - Thank you for posting these instructions.

I followed them but got this error:

dpkg-shlibdeps: failure: couldn't find library libXp.so.6 needed by /tmp/make-jpkg.oNeFhoIABg/install/usr/lib/j2sdk1.6-ibm/jre/lib/ppc/motif21/libmawt.so (its RPATH is '/usr/lib/j2sdk1.6-ibm/jre/lib/ppc/motif21:/usr/lib/j2sdk1.6-ibm/jre/lib/ppc/motif21/..').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
    dh_gencontrol
dpkg-gencontrol: warning: unknown substitution variable ${shlibs:Depends}
    dh_md5sums
md5sum: usr/lib/j2sdk1.6-ibm/src.zip: Input/output error
md5sum: usr/lib/j2sdk1.6-ibm/docs/content/apidoc/Security/JAAS/JAASLinPPC64/javax/security/auth/DestroyFailedException.html: Input/output error
dh_md5sums: command returned error code

Aborted (dh_md5sums).

Removing temporary directory: done


Did I miss something? Can anyone help?  (I'm a novice...)  Thanks!

---

### Post by JigglyWiggly_ on 2010-06-04
I made a deb, just incase you guys want it, works for me...
[http://3dslice.net/downloads/PrimeGen/ibm-j2sdk1.6_1.6.0_powerpc.deb](http://3dslice.net/downloads/PrimeGen/ibm-j2sdk1.6_1.6.0_powerpc.deb)

---

