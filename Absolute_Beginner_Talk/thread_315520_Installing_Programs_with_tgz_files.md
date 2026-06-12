---
title: "Installing Programs with tgz files"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by chocomoojuice on 2006-12-09
I've downloaded a program which is contained within a .tgz file.  I have a general installation tutorial with which I think I can install the program, but one important question is lingering in my mind.  After looking at system requirements for the program, I noticed that under Additional Dependencies, it said the following:
libc6 >= 2.2.4-4, xlibmesa3 or libgl1, python >= 2.3, python-gtk2 >= 2.6, python-glade2, wget (python 2.4 and python2.4-dbus strongly recommended)
Now, if I simply install this program, will these Additional Dependencies be automatically installed, or do I need to use download programs such as Synaptic to browse for and install each and every package before installing my program.

P.S.
My installation tutorial said that the .tgz file might just contain a binary file to run.  I automatically think of an .exe file (being a previous Windows user), but am not sure if it is the same case in Ubuntu.  What types of files are binary files?

- James

---

### Post by taurus on 2006-12-09
If you build something from source, you need to find and install those dependencies yourself...

In Linux, a binary file can have any extension.  As long as it has an executeable permission, you can run it...

---

### Post by chocomoojuice on 2006-12-09
Thanks yet again taurus, you're a lifesaver.

---

### Post by taurus on 2006-12-09
You're welcome.

Next question!  :mrgreen:

---

### Post by chocomoojuice on 2006-12-09
Unfortunately, after about 2 hours of searching the web for some clues, I've failed in my attempts to install this damn program.  I am following this site's general guidelines [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/), under the section named "Source Package (.tar, .tar.gz, .tgz, .tar.bz, ...)". 

First, I extract the .tgz files successfully, and proceed to enter the terminal.  

I then cd the directory where I've extracted the files from the .tgz, and I enter "./configure", which responds saying "bash: ./configure: No such file or directory".

I then go into Synaptic and ensure all the required dependencies are present, which to my knowledge are.  I then try typing "make", which responds saying: "make: *** No targets specified and no makefile found.  Stop."

I make note of the fact that the tutorial says "Then you compile it with make and after it's been compiled you can install it." after having successfully completed the make step, but I continue trying the steps that follow.

I try entering "sudo make install", but it fails telling me "make: *** No rule to make target `install'.  Stop.", which I figure is due to the fact that the last step failed.

I also tryed installing the checkinstall package to use in the installation process, which seemed to work to a certain point, but failed in the end in the same manner as the last step.

I'm sorry if any of the above explanations don't make sense.  I'm learning the concepts and steps as I go along, so excuse my thorough and sometimes redundantly basic review of my process.

---

### Post by riven0 on 2006-12-09
What program are you trying to install? Maybe we can look over the readme.

---

### Post by taurus on 2006-12-09
While you are still in that directory, paste the output of this command here?

```
ls -la
```

---

### Post by Famicommie on 2006-12-09
If typing ./configure doesn't do anything, then the files probably don't have a configure script.

---

### Post by chocomoojuice on 2006-12-09
Typing "ls -la" command responds with this taurus:

total 132
drwxr-xr-x 6 james james  4096 2006-12-09 08:06 .
drwxr-xr-x 3 james james  4096 2006-12-09 07:09 ..
drwxr-xr-x 2 james james  4096 2006-10-28 23:19 bin
-rw-r--r-- 1 root  root     40 2006-12-09 07:58 description-pak
drwxr-xr-x 3 james james  4096 2006-10-28 23:19 share
drwxr-xr-x 4 james james  4096 2006-10-28 23:19 .transgaming
-rw-r--r-- 1 james james 98478 2006-10-28 23:19 update.reg
drwxr-xr-x 5 james james  4096 2006-10-28 23:19 winex

By the way, I am attempting to install Cedega.

> If typing ./configure doesn't do anything, then the files probably don't have a configure script.
I see.  However, shouldn't typing "make" have created a ./configure script?

---

### Post by taurus on 2006-12-09
You probably get the binaries in bin so change in there and see what do you have!

```
cd bin
ls -la
```

---

### Post by chocomoojuice on 2006-12-09
```
cd bin
ls -la
``` responds with:

total 24
drwxr-xr-x 2 james james  4096 2006-10-28 23:19 .
drwxr-xr-x 6 james james  4096 2006-12-09 08:06 ..
-rwxr-xr-x 1 james james 13749 2006-10-28 23:19 winex3

---

### Post by taurus on 2006-12-09
Try to run that program...

```
./winex3
```

---

### Post by chocomoojuice on 2006-12-09
running winex3 yields the following, lengthy results:
```
./winex3: 160: /usr/lib/transgaming_cedega//winex/bin/pthreads_stack_test: not found
[: 160: 0: unexpected operator
cp: cannot stat `/usr/lib/transgaming_cedega//.transgaming': No such file or directory
chmod: cannot access `/home/james/.transgaming': No such file or directory
./winex3: 250: cannot open /usr/lib/transgaming_cedega//.transgaming/config: No such file
ln: creating symbolic link `/home/james/.transgaming/c_drive/windows/system32/regsvr32' to `/usr/lib/transgaming_cedega//winex/bin/regsvr32': No such file or directory
ln: creating symbolic link `/home/james/.transgaming/c_drive/windows/system32/regsvr32.so' to `/usr/lib/transgaming_cedega//winex/bin/regsvr32.so': No such file or directory
ln: creating symbolic link `/home/james/.transgaming/c_drive/windows/system32/regsvr32.exe' to `/usr/lib/transgaming_cedega//winex/bin/regsvr32': No such file or directory
ln: creating symbolic link `/home/james/.transgaming/c_drive/windows/system32/regsvr32.exe.so' to `/usr/lib/transgaming_cedega//winex/bin/regsvr32.so': No such file or directory
ln: creating symbolic link `/home/james/.transgaming/c_drive/windows/system32/wcmd.exe' to `/usr/lib/transgaming_cedega//winex/bin/wcmd': No such file or directory
ln: creating symbolic link `/home/james/.transgaming/c_drive/windows/system32/wcmd.exe.so' to `/usr/lib/transgaming_cedega//winex/bin/wcmd.so': No such file or directory
ln: creating symbolic link `/home/james/.transgaming/c_drive/windows/system32/winebrowserlink' to `/usr/lib/transgaming_cedega//winex/bin/winebrowserlink': No such file or directory
ln: creating symbolic link `/home/james/.transgaming/c_drive/windows/system32/winebrowserlink.so' to `/usr/lib/transgaming_cedega//winex/bin/winebrowserlink.so': No such file or directory
cp: cannot stat `/usr/lib/transgaming_cedega//.transgaming/c_drive/windows/Fonts/*': No such file or directory
./winex3: 250: cannot open /usr/lib/transgaming_cedega//update.reg: No such file
Updating TransGaming config and registry info
WARNING: Your old config file has been moved to config.old. Any modifications you made to this file
will have to be replaced.
mv: cannot stat `/home/james/.transgaming/config': No such file or directory
./winex3: 322: cannot open /usr/lib/transgaming_cedega//.transgaming/config: No such file
cp: cannot stat `/usr/lib/transgaming_cedega//.transgaming/dyndata.reg': No such file or directory
./winex3: 322: cannot open /usr/lib/transgaming_cedega//update.reg: No such file
mkdir: cannot create directory `/home/james/.transgaming/c_drive/My Documents': No such file or directory
cp: target `/home/james/.transgaming/c_drive/windows/' is not a directory: No such file or directory
ln: creating symbolic link `/home/james/.transgaming/c_drive/windows/system32/regsvr32' to `/usr/lib/transgaming_cedega//winex/bin/regsvr32': No such file or directory
ln: creating symbolic link `/home/james/.transgaming/c_drive/windows/system32/regsvr32.so' to `/usr/lib/transgaming_cedega//winex/bin/regsvr32.so': No such file or directory
ln: creating symbolic link `/home/james/.transgaming/c_drive/windows/system32/regsvr32.exe' to `/usr/lib/transgaming_cedega//winex/bin/regsvr32': No such file or directory
ln: creating symbolic link `/home/james/.transgaming/c_drive/windows/system32/regsvr32.exe.so' to `/usr/lib/transgaming_cedega//winex/bin/regsvr32.so': No such file or directory
ln: creating symbolic link `/home/james/.transgaming/c_drive/windows/system32/wcmd.exe' to `/usr/lib/transgaming_cedega//winex/bin/wcmd': No such file or directory
ln: creating symbolic link `/home/james/.transgaming/c_drive/windows/system32/wcmd.exe.so' to `/usr/lib/transgaming_cedega//winex/bin/wcmd.so': No such file or directory
ln: creating symbolic link `/home/james/.transgaming/c_drive/windows/system32/winebrowserlink' to `/usr/lib/transgaming_cedega//winex/bin/winebrowserlink': No such file or directory
ln: creating symbolic link `/home/james/.transgaming/c_drive/windows/system32/winebrowserlink.so' to `/usr/lib/transgaming_cedega//winex/bin/winebrowserlink.so': No such file or directory
cp: cannot stat `/usr/lib/transgaming_cedega//.transgaming/tg_config_version': No such file or directory
Update complete
usage: cedega [-use-pthreads <yes/no>] [[-]-winver <version>] [[-]-debugmsg <debug>] [[-]-version] [[-]-use-dos-cwd <dir>] [[-]monitor-cdrom-eject] <application> [application parameters]

If you require additional help, please refer the HOWTO guide in the downloads section of the subscribers area.
```

Seems to me like this would be a program file meant to be run after installing Cedega since so many files appear to be missing.

---

### Post by taurus on 2006-12-09
What about

```
cd ../winex
ls -la <-- paste the output here
cd ../share
ls -la <-- paste the output here
cd ../.transgaming
ls -la <-- paste the output here

```

---

### Post by chocomoojuice on 2006-12-09
cd ../winex
ls -la

```
total 20
drwxr-xr-x 5 james james 4096 2006-10-28 23:19 .
drwxr-xr-x 6 james james 4096 2006-12-09 08:06 ..
drwxr-xr-x 2 james james 4096 2006-10-28 23:19 bin
drwxr-xr-x 2 james james 4096 2006-10-28 23:19 lib
drwxr-xr-x 2 james james 4096 2006-10-28 23:19 pthread_lib
```



cd ../share
ls -la

```
total 12
drwxr-xr-x 3 james james 4096 2006-10-28 23:19 .
drwxr-xr-x 6 james james 4096 2006-12-09 08:06 ..
drwxr-xr-x 4 james james 4096 2006-10-28 23:19 share
```



cd ../.transgaming
ls -la

```
total 52
drwxr-xr-x 4 james james  4096 2006-10-28 23:19 .
drwxr-xr-x 6 james james  4096 2006-12-09 08:06 ..
drwxr-xr-x 5 james james  4096 2006-10-28 23:19 c_drive
-rw-r--r-- 1 james james 13854 2006-10-28 23:19 config
-rw-r--r-- 1 james james 10953 2006-10-28 23:19 config.cedega_5.2.7
-rw-r--r-- 1 james james   158 2006-10-28 23:19 dyndata.reg
drwxr-xr-x 2 james james  4096 2006-10-28 23:19 icons
-rw-r--r-- 1 james james     3 2006-10-28 23:19 tg_config_version
```

---

### Post by ZERO_SHIFT on 2006-12-09
These are the following standard steps for installing programs with tgz files.

```
cd <directory name>
```

```
./configure
```

```
make
```

```
sudo make install
```

As for executing a file you could try ```
sudo bash ./<filename>
```

Hope this helps.:D

---

### Post by taurus on 2006-12-09
Look in winex/bin to see if there is a setup or install program.  Otherwise, what's the output of this command then?

```
cd winex/bin
ls -la <-- paste the output here
cd ../..
pwd <-- paste the output here
```

---

### Post by chocomoojuice on 2006-12-09
cd winex/bin
ls -la

```
total 532
drwxr-xr-x 2 james james   4096 2006-10-28 23:19 .
drwxr-xr-x 5 james james   4096 2006-10-28 23:19 ..
-rwxr-xr-x 1 james james   9596 2006-10-28 23:19 fnt2bdf
-rwxr-xr-x 1 james james   4884 2006-10-28 23:19 pthreads_stack_test
lrwxrwxrwx 1 james james     11 2006-12-09 07:09 regapi -> winelibwrap
-rwxr-xr-x 1 james james  25096 2006-10-28 23:19 regapi.so
lrwxrwxrwx 1 james james     11 2006-12-09 07:09 regsvr32 -> winelibwrap
-rwxr-xr-x 1 james james  18536 2006-10-28 23:19 regsvr32.so
lrwxrwxrwx 1 james james     11 2006-12-09 07:09 wcmd -> winelibwrap
-rwxr-xr-x 1 james james  64964 2006-10-28 23:19 wcmd.so
-rwxr-xr-x 1 james james  15596 2006-10-28 23:19 wine
lrwxrwxrwx 1 james james     11 2006-12-09 07:09 winebrowserlink -> winelibwrap
-rwxr-xr-x 1 james james  24108 2006-10-28 23:19 winebrowserlink.so
-rwxr-xr-x 1 james james  15768 2006-10-28 23:19 wineclipsrv
lrwxrwxrwx 1 james james     11 2006-12-09 07:09 winedbg -> winelibwrap
-rwxr-xr-x 1 james james 209492 2006-10-28 23:19 winedbg.so
-rwxr-xr-x 1 james james  55924 2006-10-28 23:19 winedump
-rwxr-xr-x 1 james james    337 2006-10-28 23:19 wine_forceeject
-rwxr-xr-x 1 james james  18443 2006-10-28 23:19 winelauncher
-rwxr-xr-x 1 james james   1421 2006-10-28 23:19 winelibwrap
-rwxr-xr-x 1 james james  10820 2006-10-28 23:19 wine-preloader
-rwxr-xr-x 1 james james   7740 2006-10-28 23:19 wineserver
-rwxr-xr-x 1 james james   9881 2006-10-28 23:19 wineshelllink
```




cd ../..
pwd

NOTE: I'm wondering if I've done this wrong.  I followed your instructions for this step correctly I think though, assuming that before typing "cd ../.." I was cded to the winex/bin directory.

```
/home/james/Desktop/Cedega v5.2.7 Engine/Cedega v5.2.7 Engine.rar_FILES/cedega-engine-5.2.7-local-update.i386.cpkg_FILES/cedega_5.2.7-1.i386.p2p.tgz_FILES
```

P.S.
Would me sending you the original .tgz file help?  If so, just let me know and I'll give you one of my messenger contacts.

---

### Post by taurus on 2006-12-09
Okay, try this

```
cd .transgaming
chmod 755 config
sudo ./config
```

---

### Post by chocomoojuice on 2006-12-09
chmod 755 config

```
james@james-desktop:~/Desktop/Cedega v5.2.7 Engine/Cedega v5.2.7 Engine.rar_FILES/cedega-engine-5.2.7-local-update.i386.cpkg_FILES/cedega_5.2.7-1.i386.p2p.tgz_FILES/.transgaming$ 

```
sudo ./config

```
Password:
./config: 1: WINE: not found
./config: 2: Syntax error: ";;" unexpected
james@james-desktop:~/Desktop/Cedega v5.2.7 Engine/Cedega v5.2.7 Engine.rar_FILES/cedega-engine-5.2.7-local-update.i386.cpkg_FILES/cedega_5.2.7-1.i386.p2p.tgz_FILES/.transgaming$ 

```

---

### Post by taurus on 2006-12-09
Is there a README or INSTALL in ~/Desktop/Cedega v5.2.7 Engine?

```
ls -la ~/Desktop/Cedega v5.2.7 Engine
```

---

### Post by chocomoojuice on 2006-12-09
Ok, the original file I downloaded came in a rar file, which extracts into:
cedega-5.2.7-releasenotes.html
cedega-engine-5.2.7-local-update.i386.cpkg
md5sums

md5sums contains the following code
```
27114f337630e6932d9798a079b7f8f8  cedega-engine-5.2.7-local-update.i386.cpkg
```

cedega-5.2.7-releasenotes.html contains no information regarding installation instructions.  This is almost the same document:
[http://downloads.transgaming.com/files/cedega-5.2.8-releasenotes.html](http://downloads.transgaming.com/files/cedega-5.2.8-releasenotes.html)

---

