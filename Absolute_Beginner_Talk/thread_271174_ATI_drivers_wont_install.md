---
title: "ATI drivers wont install"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-10-04
Hi,

I almost sorted out all my problems from this post.
[http://www.ubuntuforums.org/showthread.php?t=271119&highlight=aktiwers](http://www.ubuntuforums.org/showthread.php?t=271119&highlight=aktiwers)
You dont need to read it, as I will post the last remaining problem here.

Its when I try to install my ATI Drivers, I get this error:

>  			 				aktiwers@HAL:~$ sudo sh ./ati-driver-installer-8.29.6.run Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.29.6............................................ .................................................. .................................................. .................................................. .................................................. .................................................. .................................................. .................................................. .................................................. .................................
-e ==================================================  
-e  ATI Technologies Linux Driver Installer/Packager
-e ==================================================  
./ati-installer.sh: 176: Syntax error: Bad substitution
Removing temporary directory: fglrx-install
aktiwers@HAL:~$

How would I fix this, and install my ATI drivers again?

---

### Post by WalmartSniperLX on 2006-10-04
try just using 

```
 sudo sh ati-driver-installer-8.29.6.run 
```

I used this: [http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910) It uses the terminal the whole way there. Just make sure you change the name of the driver in the tutorial to the verison you downloaded when following the steps

---

### Post by aktiwers on 2006-10-04
> **WalmartSniperLX said:**
> try just using 

```
 sudo sh ati-driver-installer-8.29.6.run 
```I used this: [http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910) It uses the terminal the whole way there. Just make sure you change the name of the driver in the tutorial to the verison you downloaded when following the steps

Thanks for the reply.

Both things turn out the same error. 
In the guide I get to this point when the error shows up:

> aktiwers@HAL:~$ ./ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.29.6.............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager
-e ==================================================
./ati-installer.sh: 176: Syntax error: Bad substitution
Removing temporary directory: fglrx-install
aktiwers@HAL:~$


Any idea?

---

### Post by Crooksey on 2006-10-04
Try downloading the newest or another file, possibly corrupt.

---

### Post by aktiwers on 2006-10-04
I have tried that. Also I have the old versions on my PC, and they do the same thing :(

---

### Post by _ra_ on 2006-10-06
the error occurs simply because th installer doesn't get the right shell..
ubuntu has a symlink for /bin/sh on dash instead of bash...
do a symlink on bash and it should work  :

      sudo ln -sf bash /bin/sh

worked for me..
if you want you can change back to dash afterwards, but i don't think there a neeed for it since bash is a pretty standart shell  :

      sudo ln -sf dash /bin/sh


got it from :
   [http://rage3d.com/board/showthread.php?t=33868060](http://rage3d.com/board/showthread.php?t=33868060)

---

### Post by genti on 2006-10-17
Yep, that did it for me. Thanks!

---

