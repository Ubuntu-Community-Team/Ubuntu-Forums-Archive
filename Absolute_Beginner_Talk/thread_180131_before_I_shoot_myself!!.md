---
title: "before I shoot myself!!"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by peterj on 2006-05-21
ok trying to work out java.
uninstalled that rubbish blackdown 1.4 version.
installed java 1.5 through the repository.
now when I go onto my favourite site...[www.funkypool.com](www.funkypool.com)
i get 'plugin required.
firefox doesnt recognise me as having any java through the about:plugins command.
maybe I haven't installed it at all?
normally when I do it through the add/remove programs it does it all for me I think
thanks

---

### Post by Klaidas on 2006-05-21
The easiest way to install it would be using Automatix - [http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)
So you don't have to shoot yourself anymore! :)

---

### Post by peterj on 2006-05-21
the roblem there lies in installing automatix! It wont work right for me, says I need a different version. and other options?!

---

### Post by alphaomega on 2006-05-21
Do you have your java enabled in Firefox's preferences?  funkypool works for me.

---

### Post by adamkane on 2006-05-21
Breezy:
Add extra repositories:
[http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories)
Install J2RE:
[http://easylinux.info/wiki/Ubuntu#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox]("http://easylinux.info/wiki/Ubuntu#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox")

Dapper:
Add extra repositories:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories)
Install J2RE:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox")

---

### Post by glinsvad on 2006-05-21
First, visit the Wiki on [Restricted Formats]("https://wiki.ubuntu.com/RestrictedFormats"). The following works fine with Breezy running linux2.6.12-10-386 (check your version by typing "uname -r" in terminal)...

Go to [http://java.sun.com/j2se/1.5.0/download.jsp]("http://java.sun.com/j2se/1.5.0/download.jsp")
and check for the newest version (currently I think it's JRE 5.0 Update 6). Find "jre-1_5_0_06-linux-i586.bin" or equivalent and download it.

To build a Debian-package from the downloaded BIN-file install fakeroot and some Java stuff (java-common might already be installed)
```

sudo apt-get install fakeroot java-package java-common

```

Then make the Debian package
```

fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin

```

Finally install the newly built Debian-package the usual way
```

sudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb

```

---

### Post by KarmaKing on 2006-05-21
I was wondering about this too.  Wich Java do I download.  It says i586, is that right? I thought I am using 386

 Download Now!  Linux RPM in self-extracting file   	jre-1_5_0_06-linux-i586-rpm.bin 15.47 MB

or

Download Now! Linux self-extracting file 	jre-1_5_0_06-linux-i586.bin 	15.99 MB

---

### Post by Nikusan on 2006-05-22
[QUOTE=peterj]ok trying to work out java.
uninstalled that rubbish blackdown 1.4 version.
installed java 1.5 through the repository.
now when I go onto my favourite site...[www.funkypool.com](www.funkypool.com)
i get 'plugin required.
firefox doesnt recognise me as having any java through the about:plugins command.
maybe I haven't installed it at all?
normally when I do it through the add/remove programs it does it all for me I think
thanks[/QUOTE]

You need to run this command and select the sun java:
  ```
sudo update-alternatives --config java
```

---

### Post by hotbrainz on 2006-05-22
Hey Karmaking,

i586 is the rite one. Download it and use 386 in the commands. It works just fine. Just got it done my self :)

---

### Post by hotbrainz on 2006-05-22
the version you need is :

Linux self-extracting file jre-1_5_0_06-linux-i586.bin 15.99 MB

Then you may use eclipse to edit the java scripts

[https://wiki.ubuntu.com/EclipseIDE]("https://wiki.ubuntu.com/EclipseIDE")

---

