---
title: "Problems with ATI driver"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by Micro Rotors on 2006-01-25
How do I install this driver: 

ati-driver-installer-8.21.7-i386.run

I follow the command on thier web site and I changed the file name to the one I downloaded, I know the file is there, I see it!


> bill@micro:~$ sudo -i
root@micro:~# cd Desktop
root@micro:~/Desktop# ./ati-driver-installer-8.21.7-i386.run
-bash: ./ati-driver-installer-8.21.7-i386.run: No such file or directory
root@micro:~/Desktop#


---

### Post by hillbilly on 2006-01-25
is the file present under ~/Desktop ? Try typing in the complete path to the file and run it!

---

### Post by dueY on 2006-01-25
Try ```
sh ati-driver-installer-8.21.7-i386.run
```

---

### Post by Horndog on 2006-01-25
You have to change the permissions so you can execute that file.

---

### Post by Micro Rotors on 2006-01-25
yeah its right there on the desktop 

I have the ATI RADEON X300 SE PCI Express card if that makes a difference.

Thanks
Bill

---

### Post by Micro Rotors on 2006-01-25
Ok thanks Due y I got it to run, But it aborts because > vcdk is missing

and there is this in the install log > /tmp/fglrx ~/Desktop/fglrx-install
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.21.7-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://www.ati.com/support/driver.html>
dpkg-buildpackage: host architecture i386
 debian/rules build
echo "Using architecture: i386"
Using architecture: i386
if [ -f /tmp/fglrx/debian/control.template ]; then \
	cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
fi
for i in preinst postinst prerm postrm ; do \
  if [ -f /tmp/fglrx/debian/driver.$i ]; then \
    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
        -e "s/#DISTRO#/breezy/" /tmp/fglrx/debian/driver.$i > \
      /tmp/fglrx/debian/xorg-driver-fglrx.$i; \
  fi; \
done
if [ -f /tmp/fglrx/debian/10fglrx.template ]; then \
  sed -e "s|#XMODDIR#|usr/X11R6/lib/modules|" -e "s|#XMODDIR32#|usr/X11R6/lib32/modules|" \
    /tmp/fglrx/debian/10fglrx.template > /tmp/fglrx/debian/10fglrx; \
fi
dh_testdir
dh_testdir
 fakeroot debian/rules binary
/usr/bin/dpkg-buildpackage: line 175: fakeroot: command not found
~/Desktop/fglrx-install
[Error] Generate Package - error generating package : Ubuntu/5.10

oh boy

Bill

---

### Post by dueY on 2006-01-25
Read that V V V

---

### Post by Nrvnqsr on 2006-01-25
try following the instruction from this thread

[http://ubuntuforums.org/showthread.php?p=423589](http://ubuntuforums.org/showthread.php?p=423589)

---

### Post by Micro Rotors on 2006-01-25
[QUOTE= ]try following the instruction from this thread

[http://ubuntuforums.org/showthread.php?p=423589](http://ubuntuforums.org/showthread.php?p=423589)[/QUOTE]

BINGO - Thanks  Nrvnqsr that did the trick!

Bill

---

