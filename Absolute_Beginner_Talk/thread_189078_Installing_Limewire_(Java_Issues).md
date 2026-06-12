---
title: "Installing Limewire (Java Issues)"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by rjcube on 2006-06-04
To install Limewire, I need Java Runtime Environment, right now I have java running in FireFox, but not able to start up limewire. I get errors saying there is no supported java. And from what I understand to install the proper form of java you need to access /usr/bin which requires administrative access or root, and I have no idea how to access this.

What do I need to do to get Java, and Limewire Proparly installed?

---

### Post by Tedd on 2006-06-04
Look around for easyubuntu, and that will install Java for you, I believe. Then in terminal, do "sudo apt-get install alien" and it'll install alien. Go to the LimeWire page and download the .rpm for Limewire. Do "sudo alien LimeWireLinux.rpm" and when it spits out a .deb, do "sudo dpkg -i *.deb".

---

### Post by Qrk on 2006-06-04
Java is included in the Dapper repositories. After enableing the extra ones, you should be able to simply 

```
sudo apt-get install sun-java5-jre
```

Limewire ought to work fine after this, but nothing goes perfectly.

---

### Post by rjcube on 2006-06-04
I now have Limewire Installed (thanks tedd), but it will not run. 

Heres what comes up when I try to run limewire:
```
rjcube@rjcube-desktop:~$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com

```

I have used Easyubuntu, but the thing about that, is it only installs it for the web.

And Lastly, When I type in:

```
sudo apt-get install sun-java5-jre
```

It brings me this:

```
rjcube@rjcube-desktop:~$ sudo apt-get install sun-java5-jre
Password:
Reading package lists... Done
Building dependency tree... Done
sun-java5-jre is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up emacs21 (21.4a-3ubuntu2) ...
emacs-install emacs21
install/cedet-common: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-autogen.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-compat.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-edebug.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-load.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/ezimage.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/fame.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/inversion.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/mode-local.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/pprint.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/sformat.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/working.elc
Done
install/dictionaries-common: Byte-compiling for emacsen flavour emacs21
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/debian-ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/flyspell.elc
Done
emacsen-common: Handling install of emacsen flavor emacs21
emacsen-common: byte-compiling for emacs21
Loading 00debian-vars (source)...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Wrote /etc/emacs21/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs21/site-lisp/debian-startup.elc
Done
install/speedbar: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Source file `/usr/share/emacs21/site-lisp/speedbar/dframe.el' newer than byte-compiled file
Wrote /usr/share/emacs21/site-lisp/speedbar/bigclock.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/dframe.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/rpm.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-ant.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-gud.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-html.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-image.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-info.el:
  !! Wrong type argument ((stringp nil))
Wrote /usr/share/emacs21/site-lisp/speedbar/sb-rmail.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-texinfo.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-w3.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/speedbar.el:
  !! Wrong type argument ((stringp nil))
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-load.elc
Done
emacs-install: /usr/lib/emacsen-common/packages/install/speedbar emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 5.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cedet-common:
 cedet-common depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing cedet-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eieio:
 eieio depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
 eieio depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing eieio (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of speedbar:
 speedbar depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing speedbar (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs21
 cedet-common
 eieio
 speedbar
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

EDIT: It seems that I do have the JRE installed, but Limewire is going to the wrong directory to access it

currently Java Runtime is in /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/bin/java

---

### Post by Qrk on 2006-06-04
You'll have to do this:  
```
sudo update-alternatives --config java
```

and choose the sun java, not the blackdown java,

---

### Post by rjcube on 2006-06-04
[QUOTE=Qrk]You'll have to do this:  
```
sudo update-alternatives --config java
```

and choose the sun java, not the blackdown java,[/QUOTE]

Thanks! That worked perfectly!

---

### Post by Fornie on 2006-06-04
hello :)

this might be off topic but please post the link where i can download limewire for dapper drake? thanks a lot

---

### Post by rjcube on 2006-06-04
[QUOTE=Fornie]hello :)

this might be off topic but please post the link where i can download limewire for dapper drake? thanks a lot[/QUOTE]

umm...im not 100% sure but im pretty sure thats just the regular version at the [Ubuntu Download Page]("http://www.ubuntulinux.org/download")

EDIT: ooooh...woops, i thought he asked where to get the OS

---

### Post by Qrk on 2006-06-04
[http://www.limewire.com/english/content/downloadfree2.shtml](http://www.limewire.com/english/content/downloadfree2.shtml)

---

