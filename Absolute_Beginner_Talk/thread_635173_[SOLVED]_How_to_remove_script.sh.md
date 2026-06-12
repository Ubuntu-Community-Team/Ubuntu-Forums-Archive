---
title: "[SOLVED] How to remove script.sh"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by jryprt on 2007-12-08
I ran this script( sh snowscript.sh ) after downloading it works fine but I want to remove it . Is it  rm sh snowscript.sh  ?

---

### Post by taurus on 2007-12-08
```
rm snowscript.sh
-or-
sudo rm snowscript.sh
```

---

### Post by jryprt on 2007-12-08
I got this
jerry@jerry-desktop:~$ rm snowscript.sh
jerry@jerry-desktop:~$ sudo rm snowscript.sh
[sudo] password for jerry:
rm: cannot remove `snowscript.sh': No such file or directory
jerry@jerry-desktop:~$

---

### Post by lavinog on 2007-12-08
is the script located in the Desktop directory?
try ls first and see if that script exists
sometimes tab auto completion helps too.

what does the script do?

---

### Post by toupeiro on 2007-12-08
is it in your desktop directory?

---

### Post by dbott67 on 2007-12-08
What directory is the file in?  You need to either be in the directory that the file is in, or specify the complete path to the file:

```
dbott@gutsy:~$ cd /path/to/file/
dbott@gutsy:/path/to/file$ rm snowscript.sh

```

or
```
dbott@gutsy:~$ rm /path/to/file/snowscript.sh

```
 
-Dave

---

### Post by taurus on 2007-12-08
> **jryprt said:**
> I got this
jerry@jerry-desktop:~$ rm snowscript.sh
jerry@jerry-desktop:~$ sudo rm snowscript.sh
[sudo] password for jerry:
rm: cannot remove `snowscript.sh': No such file or directory
jerry@jerry-desktop:~$

You need to be in the right directory before you remove it OR you have to include the whole path to it.

---

### Post by jryprt on 2007-12-08
I got it from this  [http://ubuntuforums.org/showthread.php?t=612076&highlight=snow](http://ubuntuforums.org/showthread.php?t=612076&highlight=snow)
go to post # 6  then post # 3 its for snow on the desk top compiz

---

### Post by jryprt on 2007-12-08
> **dbott67 said:**
> What directory is the file in?  You need to either be in the directory that the file is in, or specify the complete path to the file:

```
dbott@gutsy:~$ cd /path/to/file/
dbott@gutsy:/path/to/file$ rm snowscript.sh

```

or
```
dbott@gutsy:~$ rm /path/to/file/snowscript.sh

```
 
-Dave
I cd to snow got this
jerry@jerry-desktop:~$ cd /home/jerry/snow
jerry@jerry-desktop:~/snow$ 
jerry@jerry-desktop:~/snow$ /home/jerry/snow$ rm snowscript.sh
bash: /home/jerry/snow$: No such file or directory
jerry@jerry-desktop:~/snow$  rm /home/jerry/snow/snowscript.sh
rm: cannot remove `/home/jerry/snow/snowscript.sh': No such file or directory
jerry@jerry-desktop:~/snow$ 

this in the home folder?

---

### Post by Taboo Mirage on 2007-12-08
> **jryprt said:**
> I got this
jerry@jerry-desktop:~$ rm snowscript.sh
jerry@jerry-desktop:~$ sudo rm snowscript.sh
[sudo] password for jerry:
rm: cannot remove `snowscript.sh': No such file or directory
jerry@jerry-desktop:~$

The first time you input "rm snowscript.sh" it deleted it.  You didn't need to do the second "sudo rm snowscript.sh" as it was already deleted at this point.

You need to do nothing else.  It's gone.

If you want to make sure there are no occurrences of it elsewhere, run this:

```
find ~ -name snowscript.sh
```

If it returns no results, then the script is definitely gone.  If it returns a result it will show you the path too.

---

### Post by dbott67 on 2007-12-08
You can confirm it's gone by typing ls -all in the appropriate directory:
```
dbott@gutsy:~/Desktop$ ls -all
total 34568
drwxr-xr-x  2 dbott dbott     4096 2007-12-01 22:58 .
drwxr-xr-x 46 dbott dbott     4096 2007-12-06 16:04 ..
-rw-r--r--  1 dbott dbott 29657696 2007-11-22 10:13 camtasiaf.exe
-rw-r--r--  1 dbott dbott      251 2007-11-08 14:13 Compiz Configuration Settings Manager.desktop
lrwxrwxrwx  1 dbott dbott       31 2007-11-06 21:36 Mount NAS Drives -> /home/dbott/Mount_NAS_Drives.sh
-rw-r--r--  1 dbott dbott      321 2007-11-08 09:44 Mount NAS Drives~
-rw-r--r--  1 dbott dbott  5668352 2007-11-25 15:38 Tech-Nov2007.ppt
lrwxrwxrwx  1 dbott dbott       25 2007-11-06 20:47 VNC Listen -> /home/dbott/vnc-listen.sh
-rw-r--r--  1 dbott dbott       30 2007-11-29 09:42 VNC Listen~

```

Look for the snowscript.sh file (or lack thereof...)

-Dave

---

### Post by jryprt on 2007-12-08
> **Taboo Mirage said:**
> The first time you input "rm snowscript.sh" it deleted it.  You didn't need to do the second "sudo rm snowscript.sh" as it was already deleted at this point.

You need to do nothing else.  It's gone.

If you want to make sure there are no occurrences of it elsewhere, run this:

```
find ~ -name snowscript.sh
```

If it returns no results, then the script is definitely gone.  If it returns a result it will show you the path too.
Your right its gone Thank to all.

---

