---
title: "command line configure does not"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by rtrdom on 2007-12-29
Recently downloaded OpenOffice.org2.3.1.  Untarred with tar  zxfs<file>.tar.gz. Used
cd to get into untarred file.  Typing configure with/without . or/  does not configure. Typing
install sh does no good,  How can I get the file "OOG680_m9_native_packed-1_en-US.9238 to configure so I can do make, make install etc.?

---

### Post by p_quarles on 2007-12-29
> **rtrdom said:**
> Recently downloaded OpenOffice.org2.3.1.  Untarred with tar  zxfs<file>.tar.gz. Used
cd to get into untarred file.  Typing configure with/without . or/  does not configure. Typing
install sh does no good,  How can I get the file "OOG680_m9_native_packed-1_en-US.9238 to configure so I can do make, make install etc.?
The correct command to run the configuration file is
```
./configure
```
Nothing else *should* work.

Anyway, please do the following two things, and I should be able to help you resolve this:
1) Make sure you have the build tools:
```
sudo apt-get install build-essential
```
2) Post the exact error output you get when running the ./configure command.

---

### Post by rtrdom on 2007-12-29
Thanks for the reply. This is what I get with ./configure, and the build-essential is already
the latest version.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jim@Bravo:~$ cd /home/jim/Downloads/OOG680_m9_native_packed-1_en-US.9238
jim@Bravo:~/Downloads/OOG680_m9_native_packed-1_en-US.9238$ ./configure
bash: ./configure: No such file or directory
jim@Bravo:~/Downloads/OOG680_m9_native_packed-1_en-US.9238$ 

If you can help, thanks. I've been working on this for hours, tried many, many things,
with no good results.

---

### Post by taurus on 2007-12-29
I don't think you have to run ./configure for OpenOffice.  You just run it if you want to use it.  What's the output of this command?

```
ls -la
```

---

### Post by p_quarles on 2007-12-29
What do you get from this:
```
ls -a ~/Downloads/OOG680_m9_native_packed-1_en-US.9238
```

---

### Post by rtrdom on 2007-12-29
This is the result of ls -a while in OOG ...etc

jim@Bravo:~/Downloads/OOG680_m9_native_packed-1_en-US.9238$ ./configure
bash: ./configure: No such file or directory

jim@Bravo:~/Downloads/OOG680_m9_native_packed-1_en-US.9238$ ls -a
.  ..  installdata  JavaSetup.jar  licenses  readmes  RPMS  setup
jim@Bravo:~/Downloads/OOG680_m9_native_packed-1_en-US.9238$

---

### Post by p_quarles on 2007-12-29
Run 
```
ls -la
```
like Taurus said, so we can see what kind of files those are.

---

### Post by rtrdom on 2007-12-29
.  ..  installdata  JavaSetup.jar  licenses  readmes  RPMS  setup
jim@Bravo:~/Downloads/OOG680_m9_native_packed-1_en-US.9238$ ls -la
total 272
drwxr-xr-x 6 jim jim   4096 2007-11-13 09:56 .
drwxr-xr-x 3 jim jim   4096 2007-12-29 20:34 ..
drwxr-xr-x 5 jim jim   4096 2007-11-13 09:56 installdata
-rw-r--r-- 1 jim jim 232932 2007-11-13 09:56 JavaSetup.jar
drwxr-xr-x 2 jim jim   4096 2007-11-13 09:56 licenses
drwxr-xr-x 2 jim jim   4096 2007-11-13 09:56 readmes
drwxr-xr-x 3 jim jim   4096 2007-11-13 09:56 RPMS
-rwxr-xr-x 1 jim jim  12568 2007-11-13 09:56 setup
jim@Bravo:~/Downloads/OOG680_m9_native_packed-1_en-US.9238$

---

### Post by taurus on 2007-12-29
```
./setup
```

---

### Post by rtrdom on 2007-12-29
I have run the wizard that the command brings up. It ran a wizard, again.  This time it failed with an error of not eough discspace. Please use aother directory for installation or
change your module selection.  Guess I'll quit for this evening and try to get more
disc space. I've worked on this since before lunch today and now this. When I get more
disc space, I'll try again and when successful will post here (if I can find it again).

    I do appreciate all the help you have given.  Perhaps someday I can help
someone.   Respectfully, rtrdom

---

### Post by p_quarles on 2007-12-29
No hurry, but you can find your available disk space by running this:
```
df -h
```
I think the problem actually may be that this is a prepackaged binary, and that you have the wrong package type. That command will either confirm or deny that the problem is actually disk space.

---

### Post by taurus on 2007-12-29
If you want to install it somewhere else besides your $HOME directory, then run it with

```
sudo ./setup
```
Perhaps you can point it to /opt if you have more disk space on /.

---

### Post by rtrdom on 2008-01-26
Thanks for the information.  I have completely removed Everything from the computer,
wiped the harddrive then did a clean install from my CD (downloaded the ISO and then
burned it). I am now in the process of getting back to using the computer. I have 
managed to install OOo by accurately reading the instructions and going into the
DEBS portion. 
Thanks again for the help.

---

