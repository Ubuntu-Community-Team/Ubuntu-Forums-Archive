---
title: "OK, Need help Installing"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by crimsonsky on 2007-12-05
Hello,

I searched all the forums and everything about how to install rpm. now i have to run it as the root. i tried the comman

```
sudo # rpm -Uvh flash-plugin-9.0.115.0-release.i386.rpm
```

after i press enter it tells me this:

> usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }


i looked at sudo forums and everywhere says all i have to do is put sudo infront of the command. what are all these options? and how do i upgrade this thing??? thank yo

---

### Post by diatribe on 2007-12-05
you dont put the # in front of the rpm command

---

### Post by crimsonsky on 2007-12-05
now it gave me this error, how to i get the dependencies

> error: Failed dependencies:
        /bin/bash is needed by flash-plugin-9.0.115.0-release.i386
        /bin/sh is needed by flash-plugin-9.0.115.0-release.i386
        libX11.so.6 is needed by flash-plugin-9.0.115.0-release.i386
        libXext.so.6 is needed by flash-plugin-9.0.115.0-release.i386
        libXt.so.6 is needed by flash-plugin-9.0.115.0-release.i386
        libc.so.6 is needed by flash-plugin-9.0.115.0-release.i386
        libc.so.6(GCC_3.0) is needed by flash-plugin-9.0.115.0-release.i386
        libc.so.6(GLIBC_2.0) is needed by flash-plugin-9.0.115.0-release.i386
        libc.so.6(GLIBC_2.1) is needed by flash-plugin-9.0.115.0-release.i386
        libc.so.6(GLIBC_2.1.3) is needed by flash-plugin-9.0.115.0-release.i386
        libc.so.6(GLIBC_2.2) is needed by flash-plugin-9.0.115.0-release.i386
        libc.so.6(GLIBC_2.3) is needed by flash-plugin-9.0.115.0-release.i386
        libdl.so.2 is needed by flash-plugin-9.0.115.0-release.i386
        libdl.so.2(GLIBC_2.0) is needed by flash-plugin-9.0.115.0-release.i386
        libdl.so.2(GLIBC_2.1) is needed by flash-plugin-9.0.115.0-release.i386
        libfontconfig.so.1 is needed by flash-plugin-9.0.115.0-release.i386
        libfreetype.so.6 is needed by flash-plugin-9.0.115.0-release.i386
        libglib-2.0.so.0 is needed by flash-plugin-9.0.115.0-release.i386
        libgobject-2.0.so.0 is needed by flash-plugin-9.0.115.0-release.i386
        libgtk-x11-2.0.so.0 is needed by flash-plugin-9.0.115.0-release.i386
        libm.so.6 is needed by flash-plugin-9.0.115.0-release.i386
        libm.so.6(GLIBC_2.0) is needed by flash-plugin-9.0.115.0-release.i386
        libpthread.so.0 is needed by flash-plugin-9.0.115.0-release.i386
        libpthread.so.0(GLIBC_2.0) is needed by flash-plugin-9.0.115.0-release.i386
        libpthread.so.0(GLIBC_2.1) is needed by flash-plugin-9.0.115.0-release.i386
        libpthread.so.0(GLIBC_2.2) is needed by flash-plugin-9.0.115.0-release.i386
        libpthread.so.0(GLIBC_2.2.3) is needed by flash-plugin-9.0.115.0-release.i386
        libpthread.so.0(GLIBC_2.3.2) is needed by flash-plugin-9.0.115.0-release.i386


---

### Post by diatribe on 2007-12-05
rpm isnt good with dependencies, you shouldnt have installed t in the first place.  use alien to convert it to deb and install it that way

edit: and actually did rpm uninstall dpkg, cause it seems like you are missing some fairly important things from your system.

---

### Post by crimsonsky on 2007-12-05
dpkg is still there, cus when i tried this,```
sudo get-apt dpkg
``` it told it was the newest version and libid3tag0 and libimlib2 is not needed. but how do i get all those important files

---

### Post by Duck2006 on 2007-12-05
This may help with the *.rpm file

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by slimx3m on 2007-12-14
> **Duck2006 said:**
> This may help with the *.rpm file

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

thnx for the link, i've been i trying to convert a rpm to deb using alien, but the only thing is does is that creates a folder and then it quits. what does any body knows that problem it could be?

---

### Post by Duck2006 on 2007-12-14
This may help.

[http://howtoforge.net/converting_rpm_to_deb_with_alien](http://howtoforge.net/converting_rpm_to_deb_with_alien)

---

### Post by slimx3m on 2007-12-14
thx for the tutorial page. 

i tried that, but i don't know why whenever i am converting from rpm to deb it will just create a folder and never finishing the conversion.

fyi: i am converting a package that contains a script, and even though i specify the *-c* it is just create a folder and never finishes.  i will search some more and keep you guys updated.

---

### Post by slimx3m on 2007-12-15
> **slimx3m said:**
> thx for the tutorial page. 

i tried that, but i don't know why whenever i am converting from rpm to deb it will just create a folder and never finishing the conversion.

fyi: i am converting a package that contains a script, and even though i specify the *-c* it is just create a folder and never finishes.  i will search some more and keep you guys updated.

what i finished doing was, extracting the *.rpm and then making a *.tar.gz and then converting it to a*.deb file.

hope this helps

---

