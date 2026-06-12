---
title: "[SOLVED] Update Manager and apt-get not working"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by AThree on 2008-01-29
Hello, I've searched the forums for quite a bit, but I cannot find an answer to my problem.
I have major problems with my hard disk at the moment (I had it in Windows and now still in Ubuntu), it crashes often and tells me to run fsck manually about 3/4 times a week. As a result, many things go corrupted, however, I've always been able to fix them (I've learned backing up important files to another drive very helpful).

Now, I believe my newest error with Update Manger and apt-get has something to do with corrupt files (from what I can gather from searching the forums). I run Update Manager, hit install updates, it then downloads, it finishes and starts to install them when I see this message:

"Not all changes and updates succeeded. For further details of the failure, please expand the 'terminal' panel below.

dpkg: syntax error in triggers Deferred in file `/var/lib/dpkg/triggers/Unincorp' at character `U' midline
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:"

And I'm pretty much stuck, I have no idea what to do, so any help will be greatly appreciated. Thanks :)

---

### Post by spiderbatdad on 2008-01-29
try running ```
sudo dpkg-reconfigure -a
``` look at man dpkg and man dpkg-reconfigure

---

### Post by AThree on 2008-01-29
I typed in 'sudo dpkg-reconfigure -a' and it said:
"dpkg-query: syntax error in triggers Deferred file `/var/lib/dpkg/triggers/Unincorp' at character `U' midline
/usr/sbin/dpkg-reconfigure: acpi is not installed"

---

### Post by PmDematagoda on 2008-01-29
Could you post the output of:-
```
ls -la /var/lib/dpkg/triggers
```

---

### Post by AThree on 2008-01-29
total 20
drwxr-xr-x 2 root root 4096 2008-01-29 13:02 .
drwxr-xr-x 7 root root 4096 2008-01-29 13:02 ..
-rw-r--r-- 1 root root    6 2007-11-06 16:02 ldconfig
-rw------- 1 root root    0 2008-01-29 13:31 Lock
-rw-r--r-- 1 root root  588 2008-01-27 16:05 Unincorp
-rw-r--r-- 1 root root    0 2008-01-29 13:31 Unincorp.new
-rw-r--r-- 1 root root   16 2007-10-16 00:17 update-initramfs

---

That's what it showed.

---

### Post by PmDematagoda on 2008-01-29
I am not very sure, but I am very suspicious of the following line:-
```
-rw-r--r-- 1 root root 0 2008-01-29 13:31 Unincorp.new
```

Also, it seems that Unincorp.new has taken over the old Unincorp file's permissions as seen here:-
```
-rw-r--r-- 1 root root **588** 2008-01-27 16:05 Unincorp
-rw-r--r-- 1 root root **0** 2008-01-29 13:31 Unincorp.new
```

I am not sure if deleting the new Unincorp file would fix the problem since I have never seen a problem like this, so it might be better if we wait for someone to say if this is normal or abnormal.

---

### Post by AThree on 2008-01-29
Okay, thanks for your help so far though :)

---

### Post by AThree on 2008-01-29
*bump*

---

### Post by AThree on 2008-01-29
Bumping Again

---

### Post by AThree on 2008-01-29
Bumping Again

---

### Post by AThree on 2008-01-29
Sorry for all the bumps, but I still haven't been able to fix my problem

---

### Post by AThree on 2008-01-30
Anyone got any ideas on what I should do?

---

### Post by philinux on 2008-01-30
Well just for comparison here's my triggers output.

```
ls -la /var/lib/dpkg/triggers
total 16
drwxr-xr-x 2 root root 4096 2008-01-29 12:01 .
drwxr-xr-x 7 root root 4096 2008-01-30 12:39 ..
-rw-r--r-- 1 root root    6 2007-11-05 22:37 ldconfig
-rw------- 1 root root    0 2008-01-30 12:39 Lock
-rw-r--r-- 1 root root    0 2008-01-29 12:01 Unincorp
-rw-r--r-- 1 root root   16 2007-10-16 00:17 update-initramfs

```

[edit] just looked at my unincorp file and found it has 0 bytes and is an empty text file.

---

### Post by PmDematagoda on 2008-01-30
Not sure about this, but post the output of:-
```
cat /var/lib/dpkg/triggers/Unincorp
```

---

### Post by AThree on 2008-01-30
Package: libsdl-ttf2.0-0
Status: install ok half-configured
Priority: optional
Section: libs
Installed-Size: 76
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: sdl-ttf2.0
Version: 2.0.9-1
Depends: libc6 (>= 2.6), libfreetype6 (>= 2.3.5), libsdl1.2debian (>= 1.2.10-1), zlib1g (>= 1:1.2.3.3.dfsg-1)
Description: ttf library for Simple DirectMedia Layer with FreeType 2 support
 SDL_ttf is a sample TrueType font library. It allows you to use
 TrueType fonts in SDL applications.
Original-Maintainer: Samuel Mimram <smimram@debian.org>

---

Was what I got from that.

---

### Post by philinux on 2008-01-30
How come mine is empty? Hope you get it fixed.

---

### Post by AThree on 2008-01-30
Maybe it's meant to be empty? I have no idea really at all

Thanks :)

---

### Post by PmDematagoda on 2008-01-30
Execute the following commands:-
```
sudo dpkg --configure -a
```
and
```
sudo apt-get install -f
```

Then post the Unincorp file again.

---

### Post by AThree on 2008-01-30
After doing "sudo dpkg --configure -a" This came up:
"dpkg: syntax error in triggers Deferred file `/var/lib/dpkg/triggers/Unincorp' at character `U' midline"

After doing "sudo apt-get install -f" This came up:
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libggi2 libgii1 libgii1-target-x
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
dpkg: syntax error in triggers Deferred file `/var/lib/dpkg/triggers/Unincorp' at character `U' midline
E: Sub-process /usr/bin/dpkg returned an error code (2)"

The inside of the Unincorp file shows:
"Package: libsdl-ttf2.0-0
Status: install ok half-configured
Priority: optional
Section: libs
Installed-Size: 76
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: sdl-ttf2.0
Version: 2.0.9-1
Depends: libc6 (>= 2.6), libfreetype6 (>= 2.3.5), libsdl1.2debian (>= 1.2.10-1), zlib1g (>= 1:1.2.3.3.dfsg-1)
Description: ttf library for Simple DirectMedia Layer with FreeType 2 support
 SDL_ttf is a sample TrueType font library. It allows you to use
 TrueType fonts in SDL applications.
Original-Maintainer: Samuel Mimram <smimram@debian.org>"

---

### Post by philinux on 2008-01-30
Whats in

cat /var/lib/dpkg/triggers/Unincorp.new

---

### Post by AThree on 2008-01-30
> **philinux said:**
> Whats in

cat /var/lib/dpkg/triggers/Unincorp.new

Nothing, it's blank inside.

---

### Post by PmDematagoda on 2008-01-30
Try this:-
```
sudo apt-get remove libsdl-ttf2.0-0
```

If that was successful then do:-
```
sudo apt-get install libsdl-ttf2.0-0
```

After those two commands are done, post the Unincorp file again.

---

### Post by AThree on 2008-01-30
After doing "sudo apt-get remove libsdl-ttf2.0-0" This came up:

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libggi2 libgii1 libgii1-target-x
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libsdl-ttf2.0-0
0 upgraded, 0 newly installed, 1 to remove and 9 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 77.8kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: syntax error in triggers Deferred file `/var/lib/dpkg/triggers/Unincorp' at character `U' midline
E: Sub-process /usr/bin/dpkg returned an error code (2)"

---

### Post by PmDematagoda on 2008-01-30
Ok, now this involves a bit of risk as it means editing the Unincorp file so do this only if you are willing to take a risk.

First open Nautilus in root mode using:-
```
gksudo nautilus
```

Then navigate to /var/lib/dpkg/triggers and make a backup of the Unincorp file or copy it somewhere else.

After you have made a backup of the Unincorp file open the current Unincorp file for editing using:-
```
gksudo gedit /var/lib/dpkg/triggers/Unincorp
```

Then remove everything that is there to make it blank and save the file.

Then try doing:-
```
sudo apt-get remove libsdl-ttf2.0-0
```
and
```
sudo apt-get install libsdl-ttf2.0-0
```
again.

---

### Post by AThree on 2008-01-30
It worked! I was able to remove "libsdl-ttf2.0-0" and then install it again, and then I tried Update Manager and it installed everything without any problems!

I can leave the Unincorp file blank, right? It doesn't seem to be causing any others problems so far.

Thank you so much for all your help :)

---

### Post by PmDematagoda on 2008-01-30
The default Unincorp is indeed a blank file, so I do not see the harm of keeping it blank especially since the problem has been solved.

---

### Post by lambono on 2008-02-25
Great.

I had the same problem and this fixed it!

Thanks

---

