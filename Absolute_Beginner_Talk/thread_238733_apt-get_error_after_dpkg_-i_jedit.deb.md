---
title: "apt-get error after dpkg -i jedit.deb"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by limux on 2006-08-18
**[COLOR="Red"]!!!NEED HELP!!![/COLOR]**
=========================================================================
**[COLOR="Blue"]dpkg -i jedit_4.3pre6_all.deb[/COLOR]**
(Reading database ... 100755 files and directories currently installed.)
Preparing to replace jedit 4:04.03.06.00 (using jedit_4.3pre6_all.deb) ...
Unpacking replacement jedit ...
dpkg (subprocess): unable to execute old post-removal script: No such file or directory
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new post-removal script: No such file or directory
dpkg: error processing jedit_4.3pre6_all.deb (--install):
 subprocess new post-removal script returned error exit status 2
dpkg (subprocess): unable to execute new post-removal script: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 jedit_4.3pre6_all.deb

--------------------------------------

**[COLOR="Blue"]apt-get install jedit[/COLOR]**
Reading package lists... Done
Building dependency tree... Done
E: The package jedit needs to be reinstalled, but I can't find an archive for it.
=========================================================================

---

### Post by givré on 2006-08-18
try 
```
sudo apt-get install -f
```

---

### Post by Engnome on 2006-08-18
sudo dpkg --remove --force-depends --force-remove-reinstreq <package name>

if it doesnt work have alook here [http://ubuntuforums.org/showthread.php?t=39563](http://ubuntuforums.org/showthread.php?t=39563)

---

### Post by Kurt` on 2006-08-18
I had a similar problem here: [http://ubuntuforums.org/showthread.php?t=172504](http://ubuntuforums.org/showthread.php?t=172504)

I ended up manually editing /var/lib/dpkg/status/ (yes, I know it's bad).

Hopefully one of the above solutions will work for you. :D

Maybe I will try installing it again...

---

