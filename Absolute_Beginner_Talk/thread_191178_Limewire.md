---
title: "Limewire"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by J0E0NE on 2006-06-07
Im having a few problems converting the rpm of limewire for linux into a .deb heres my error (im using alien):
joe@ubuntu:~$ sudo alien LimeWireLinux.rpm
Password:
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/limewire-free
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXt (soname 6, path /usr/lib32/libXt.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6, dependency field Depends)
dh_gencontrol
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: LimeWire-free-4.10.9: No such file or directory

that all means nothing to me :neutral: what am I doing wrong?

Thanks in advance ;)

---

### Post by noelsanidad on 2006-06-07
Hi, why don't you use frostwire instead of limewire.

---

### Post by J0E0NE on 2006-06-07
Hey thanks im downloading now ;)  I didn't know it existed :o

---

### Post by Robgould on 2006-06-07
You should try automatix. It has frostwire and a bunch of other stuff that you will like I'm sure.

---

### Post by Rackerz on 2006-06-07
I think you have some missing dependencies, that's why it can't make the .deb.

---

### Post by hotbrainz on 2006-06-07
Please read this thread, the instructions here are excellent and should hopefully solve any problem u mite have :)

[http://ubuntuforums.org/showthread.php?t=59857&highlight=p2p+filesharing]("http://ubuntuforums.org/showthread.php?t=59857&highlight=p2p+filesharing")

This does not exactly tell you what to do for Limeware but i think after reading it you will be able to do   it.

---

### Post by J0E0NE on 2006-06-07
Ty all =D>

---

