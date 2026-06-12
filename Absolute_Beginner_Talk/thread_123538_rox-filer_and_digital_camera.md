---
title: "rox-filer and digital camera"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-01-30
i'm using rox-filer and 9wm. i'm having trouble finding my digital camera. when i used gnome, an icon would just appear on the desktop. using nautilus, i could click on the computer icon and there it would be. 9wm is a super minimal wm (icon? LOL!) and there doesn't appear to be a 'computer' icon in rox-filer. i checked mnt, dev and didn't see fstab either. my machine is too slow for gnome and i could probably go to art school and draw the picture by the time nautilus opens.

---

### Post by az on 2006-01-30
If you run gnome-volume-manager (from a terminal) it will take care of all that for you. 

Other than that, you can just mount your drives by hand.  There are applets and tools which will do that for you...

---

### Post by fuscia on 2006-01-30
[QUOTE=azz]If you run gnome-volume-manager (from a terminal) it will take care of all that for you. 

Other than that, you can just mount your drives by hand.  There are applets and tools which will do that for you...[/QUOTE]

thanks, azz. as i've dumped everything gnome, any suggestion on a tool? also, is mounting it myself something i can easily find out about? (i never know if i'm far off, or if i'm standing on it.)

---

### Post by az on 2006-01-30
@dora:~$ apt-cache show xvmount
Package: xvmount
Priority: optional
Section: universe/utils
Installed-Size: 144
Maintainer: Volker Ossenkopf <ossk@ph1.uni-koeln.de>
Architecture: i386
Version: 3.7-7
Depends: libc6 (>= 2.3.2.ds1-4), libx11-6 | xlibs (>> 4.1.0), xviewg (>= 3.2p1.4-6), debconf
Filename: pool/universe/x/xvmount/xvmount_3.7-7_i386.deb
Size: 21832
MD5sum: f513f29c8561c942c99837fba63671ce
Description: Small graphical utility for mounting devices by users
 Users can mount a predefined subset of all user mountable devices
 in /etc/fstab by mouse clicking in a simple OpenLook based graphical
 interface. Xvmount then calls the mount and umount commands to perform
 the actual operation.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu


I think there are a dozen others.  Some are windowmaker dockapps or system monitor plugins (gkrellm?)

---

### Post by fuscia on 2006-01-31
thanks, azz. ran into a slight problem when i ran xvmount...

*xvmount: error while loading shared libraries: libxview.so.3: cannot open shared object file: No such file or directory*

i tried reinstalling xvmount and got the same error. that specific library is not listed in synaptic, so i guess it must be part of another library?

i also tried something called 'mountapp', but got a 'no such thing' when i tried to run it.

if worse comes to worst, i can always go back to nautilus, so this isn't desperate. i'd just like to be able to do this in as spartan a manner possible.

---

