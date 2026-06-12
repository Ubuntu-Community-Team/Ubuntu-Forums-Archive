---
title: "Java Installation Problem"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by Koech on 2006-05-25
I've tried to update to j2re 1.5.0_06 but I get:

[FONT="Courier New"]root@Questa:/home/questa/Desktop#   sudo apt-get install sun-java5-bin
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  sun-java5-jre
Suggested packages:
  sun-java5-plugin ia32-sun-java5-plugin sun-java5-fonts
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed
  sun-java5-bin sun-java5-jre
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/29.5MB of archives.
After unpacking 83.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 74645 files and directories currently installed.)
Unpacking sun-java5-bin (from .../sun-java5-bin_1.5.0-06-1_i386.deb) ...
sun-dlj-v1-1 license could not be presented
dpkg: error processing /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Unpacking sun-java5-jre (from .../sun-java5-jre_1.5.0-06-1_all.deb) ...
sun-dlj-v1-1 license could not be presented
dpkg: error processing /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb
 /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Questa:/home/questa/Desktop#
[/FONT]

Could anyone explain this?

---

### Post by adam.tropics on 2006-05-25
There was another thread with this error, but that was solved just by trying again!!

If thats no go then you could alwyas try the 'old way' if you have a little patience,
all explained[ here.]("http://www.ubuntuforums.org/showpost.php?p=823249&postcount=2")

---

### Post by Koech on 2006-05-25
Thanks, I'll retry. Hope it works.

---

### Post by nalmeth on 2006-05-25
Reading your output, the problem seems to have come up from the license agreement not presenting itself. Probably just problem's getting Java 1.5 into multiverse for mass availability. I think you can still use automatix to install it, if you want it right away.

---

### Post by Ben Sprinkle on 2006-05-25
:D what i did was download java manually from site [http://www.java.com](http://www.java.com)  then type ./jre(numbers-after-jre) in the java directory, then go in konqueror and link it to the java directory

---

### Post by Koech on 2006-05-25
That way didn't work showversion still is 1.4.2, and sites still indicate I need a plugin.

---

### Post by Sef on 2006-05-25
Are you on Dapper or Breezy?

---

### Post by Koech on 2006-05-25
Sorry for the delay, I'm Dapper.

---

### Post by nalmeth on 2006-05-25
Sorry, I shouldn't have recommended automatix just yet. There is a beta version which you can use with dapper, but I wouldn't go around telling new user's to try it just yet.

---

### Post by Sef on 2006-05-25
The easy way to install java version 1.5.0.06:

> Ubuntu 6.06

Thanks to a redistribution license change from Sun, official Sun java packages are now available in the multiverse repositories. Install it from the Applications -> Add/Remove... menu, or install the sun-java5-bin package. 

[RestrictedFormats]("http://wiki.ubuntu.com/RestrictedFormats")

---

### Post by Koech on 2006-05-25
Thanks, i got it. The only way that works is to download the file from sun and with fakeroot change it to .deb then sudo dpkg -i ... That way I succeeded. The java way ie   linking with mozilla and ./ etc didn't work. Thanks for the help.

---

### Post by Sef on 2006-05-25
You're welcome.  Glad you got it working.  Please post any other questions you have in a new thread.

---

### Post by dwangoac on 2006-06-02
I found that issuing the command sudo dpkg-reconfigure debconf and setting it to Dialog fixed the problem.  The issue was that the license that you are required to accept can't be displayed if you have selected noninteractive responses from debconf.  FWIW, I also had to remove the package "gji", but that's a different problem...

(This is my first post here, so I'm probably not doing something right.  Please be kind to me.  : )

Good luck,

A.C.
******

---

### Post by fuji on 2006-06-07
> I found that issuing the command sudo dpkg-reconfigure debconf and setting it to Dialog fixed the problem.
Thanks man!  That was the reason why.

---

