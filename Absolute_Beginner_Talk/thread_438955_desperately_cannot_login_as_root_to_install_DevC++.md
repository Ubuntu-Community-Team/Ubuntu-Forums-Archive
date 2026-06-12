---
title: "desperately cannot login as root to install DevC++ and yahoo messenger"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by j_evenstar on 2007-05-10
hello, i've read the how to [here]("http://ubuntuforums.org/newthread.php?do=newthread&f=73") yet in my ubuntu 6.06 there's no option in the security tab (from system->administration-->login window) to "allow root to login with GDM". i really need to download devc++ since i have a long C program to work on (and that's what we use in the university)and i've no idea how to get it. can somebody help me? any response will be appreciated. thanks.
btw, my pc specs: AMD Athlon, 512 Mb RAM.

---

### Post by lloyd_b on 2007-05-10
In Ubuntu, you NEVER log in as root user.  Instead, you log in as a normal user, and use the "sudo" (and it's GUI equivalents) to gain root permissions for specific tasks.

Note: the link you provided is broken (it tries to create a new thread).  If you can provide some good info on what it is you're trying to accomplish, somebody here can probably provide some decent instructions.

Lloyd B.

---

### Post by taurus on 2007-05-10
Why do you need to log in to root?  Just use sudo if you need to install something.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by j_evenstar on 2007-05-10
thanks for the replies. i need to login as root since when i downloaded a .tar.gz file of C++ from [here]("http://freshmeat.net/projects/dev-cpp/") it said from the readme file to do the following:
> * First you need to make sure you have a installed all the C/C++ development packages when installing your distribution (those packages contains gcc, g++, make, standard include files and libraries). You should be able to obtain them on you distribution CD/web site.

* You then need Qt libraries installed. If you don't you can download the Qt package at : [ftp://ftp.trolltech.com/qt/source/qt-x11-2.3.0.tar.gz](ftp://ftp.trolltech.com/qt/source/qt-x11-2.3.0.tar.gz)
Follow the Qt INSTALL file after unpacking it and you should be able to installit quite easily.

* Now that your system is ready to run Dev-C++, type (as root) :

$> sh install.sh
or :
$> ./install.sh

This will launch the installation script. Follow the instructions and after the installation finish, change to your dev-c++ directory ($HOME/dev-c++ by default) and type :

$> ./devcpp

by the way, the correct how to link i read from is [this]("http://ubuntuforums.org/showthread.php?t=31053").

---

### Post by drowner on 2007-05-10
If you just stick a sudo infront of the commands it should be sweet, i would think

---

### Post by taurus on 2007-05-10
You don't have to log in as root to install .tar.gz.  

```
sudo ./install.sh
```
and use the same password that you log in with.

---

### Post by Lord Illidan on 2007-05-10
Regarding Dev C++, the version you are installing is frightfully old. There are other good c++ editors for Linux in the repositories, and they will be easier and better to install. Most probably, if you are using Dev C++ on Windows, it will be much newer than the linux version.

---

### Post by j_evenstar on 2007-05-10
first i navigated to the desktop since that's where the file was downloaded. unfortunately after i typed the the code then the password it "sudo: ./install.sh: command not found". then after i typed it again it then said "sudo: ./install.sh: command not found"

whoa this is just my first day of using linux...
> **Lord Illidan said:**
> Regarding Dev C++, the version you are installing is frightfully old. There are other good c++ editors for Linux in the repositories, and they will be easier and better to install. Most probably, if you are using Dev C++ on Windows, it will be much newer than the linux version.

so i need to read about how to download in the repositories?! if i really have the time i will, but we use Dev C++ in school, so it'd be better to be using the same at home.

---

### Post by taurus on 2007-05-10
Why did you put : after sudo anyway?

```
sudo ./install.sh
```
Otherwise, post the output of this command.

```
ls -la
```

---

### Post by j_evenstar on 2007-05-10
> **taurus said:**
> Why did you put : after sudo anyway?
no, that's the error returned by the terminal.

here's what ls-la returned:

```
total 11264
drwxr-xr-x  4 jillian jillian    4096 2009-05-10 08:50 .
drwxr-xr-x 23 jillian jillian    4096 2007-05-10 21:07 ..
-rwx------  1 jillian jillian  134144 2006-04-29 05:18 Alumni Directory.xls
-rw-r--r--  1 jillian jillian 1572524 2009-05-10 08:50 dev-src_Jul_30_23h03.tar. gz
drwxr-xr-x  2 jillian jillian    4096 2009-05-10 08:27 ffsettings
-rw-r--r--  1 jillian jillian 9651693 2009-05-10 08:20 firefox-2.0.0.3.tar.gz
-rwx------  1 jillian jillian  110592 2006-01-26 04:03 IEClub Directory_AY 2005- 2006.xls
-rw-r--r--  1 jillian jillian   13569 2009-05-10 08:31 installnewfirefox.sh
drwx------ 13 jillian jillian    4096 2007-05-10 00:57 My Pictures
```

---

### Post by taurus on 2007-05-10
> **j_evenstar said:**
> no, that's the error returned by the terminal.

here's what ls-la returned:

```
total 11264
drwxr-xr-x  4 jillian jillian    4096 2009-05-10 08:50 .
drwxr-xr-x 23 jillian jillian    4096 2007-05-10 21:07 ..
-rwx------  1 jillian jillian  134144 2006-04-29 05:18 Alumni Directory.xls
-rw-r--r--  1 jillian jillian 1572524 2009-05-10 08:50 dev-src_Jul_30_23h03.tar. gz
drwxr-xr-x  2 jillian jillian    4096 2009-05-10 08:27 ffsettings
-rw-r--r--  1 jillian jillian 9651693 2009-05-10 08:20 firefox-2.0.0.3.tar.gz
-rwx------  1 jillian jillian  110592 2006-01-26 04:03 IEClub Directory_AY 2005- 2006.xls
-rw-r--r--  1 jillian jillian   13569 2009-05-10 08:31 installnewfirefox.sh
drwx------ 13 jillian jillian    4096 2007-05-10 00:57 My Pictures
```

I don't see any **install.sh** on the list!  Are you sure you are in the right directory when you try to install it?

---

### Post by j_evenstar on 2007-05-10
i really need to learn this!!

okay, i extracted install.sh on the desktop (install .sh is found in dev-src_Jul_30_23h03.tar. gz/c++/setup/) ,then i navigated to the desktop using the terminal and typed "sudo ./install.sh". i then entered the password, afterwards it said:
> ** Dev-C++ installation script **

You must be root to install. Do you want to continue ?
 (Y/n) ?

so i entered "n".

---

### Post by mills on 2007-05-10
try "y"

---

### Post by j_evenstar on 2007-05-10
here is it: 
```
jillian@jillian-desktop:~$ cd /home/jillian/Desktop
jillian@jillian-desktop:~/Desktop$ sudo ./install.sh
Password:
** Dev-C++ installation script **

You must be root to install. Do you want to continue ?
 (Y/n) ? Y
tar: binary.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
Where do you want to install Dev-C++ ? [/home/jillian/dev-c++] : /home/jillian/dev-c++
mv: cannot stat `TODO': No such file or directory
mv: cannot stat `BUGS': No such file or directory
mv: cannot stat `bin/devcpp': No such file or directory
mv: cannot stat `bin/libqtintf.so*': No such file or directory

* This script will now guess your gcc and make paths
* Press enter if the path is correct for each program

make is located in : [make:] :
gcc is located in : [/usr/lib/gcc] :
g++ is located in : [g++:] :
gdb (or your favourite debugger) is located in : [/usr/bin/gdb] :
xterm, aterm or Eterm is located in : [/usr/bin/xterm] :

* Configuration file is now been written in /home/jillian/.devcpp/config


* Installation terminated, you may now run /home/jillian/dev-c++/devcpp

jillian@jillian-desktop:~/Desktop$
```

and there is no item in  /home/jillian/dev-c++/devcpp

---

### Post by Carlos Santiago on 2007-05-10
First you have to extract the files. You can extract them using the command line, with:
```
tar -zxvf dev-src_Jul_30_23h03.tar.gz

```

Then you have to CD to the dir where the file install.sh is!

```
Try:

cd ~/Desktop/dev-src_Jul_30_23h03 

or 

cd ~/Desktop/dev-src

or 

cd ~/Desktop/<and here type the name of the directory where your extracted files are>


```

Then type 
```
sudo ./install.sh

```

And plz, answer Yes when you are been asked if you want to continue!!!!


If you still getting errors, put the result of the command 'pwd' and 'ls -al' (without ' )

---

### Post by j_evenstar on 2007-05-10
```
jillian@jillian-desktop:~$ cd ~/Desktop/dev-src_Jul_30_23h03
bash: cd: /home/jillian/Desktop/dev-src_Jul_30_23h03: No such file or directory
jillian@jillian-desktop:~$

```

huhu what do i do now?

---

### Post by Carlos Santiago on 2007-05-10
put the result of 'ls -al'

---

### Post by j_evenstar on 2007-05-10
```
total 11264
drwxr-xr-x  4 jillian jillian    4096 2009-05-10 08:50 .
drwxr-xr-x 23 jillian jillian    4096 2007-05-10 21:07 ..
-rwx------  1 jillian jillian  134144 2006-04-29 05:18 Alumni Directory.xls
-rw-r--r--  1 jillian jillian 1572524 2009-05-10 08:50 dev-src_Jul_30_23h03.tar. gz
drwxr-xr-x  2 jillian jillian    4096 2009-05-10 08:27 ffsettings
-rw-r--r--  1 jillian jillian 9651693 2009-05-10 08:20 firefox-2.0.0.3.tar.gz
-rwx------  1 jillian jillian  110592 2006-01-26 04:03 IEClub Directory_AY 2005- 2006.xls
-rw-r--r--  1 jillian jillian   13569 2009-05-10 08:31 installnewfirefox.sh
drwx------ 13 jillian jillian    4096 2007-05-10 00:57 My Pictures
```

---

### Post by Carlos Santiago on 2007-05-10
You have a space in 'dev-src_Jul_30_23h03.tar. gz' that you shouldnt have.

Remove it, either graphically or with the command (just copy and paste):
```
mv dev-src_Jul_30_23h03.tar.\ gz dev-src_Jul_30_23h03.tar.gz
```

Then extract it with
```
tar -zxvf dev-src_Jul_30_23h03.tar.gz

```

---

### Post by j_evenstar on 2007-05-10
i don't think it has a space. here: 
```
jillian@jillian-desktop:~$ cd /home/jillian/Desktop
jillian@jillian-desktop:~/Desktop$ mv dev-src_Jul_30_23h03.tar.\ gz dev-src_Jul_30_23h03.tar.gz
mv: cannot stat `dev-src_Jul_30_23h03.tar. gz': No such file or directory
jillian@jillian-desktop:~/Desktop$ cd
jillian@jillian-desktop:~$ mv dev-src_Jul_30_23h03.tar.\ gz dev-src_Jul_30_23h03.tar.gz
mv: cannot stat `dev-src_Jul_30_23h03.tar. gz': No such file or directory
jillian@jillian-desktop:~$ cd /home/jillian/Desktop
jillian@jillian-desktop:~/Desktop$ ls
Alumni Directory.xls         firefox-2.0.0.3.tar.gz             install.sh
dev-src_Jul_30_23h03.tar.gz  IEClub Directory_AY 2005-2006.xls  My Pictures
ffsettings                   installnewfirefox.sh
jillian@jillian-desktop:~/Desktop$ ls-al
bash: ls-al: command not found
```

---

### Post by Carlos Santiago on 2007-05-10
then extract it with the command 
```
tar -zxvf dev-src_Jul_30_23h03.tar.gz
```

and then put the result of 

```
ls  -al

```

---

### Post by j_evenstar on 2007-05-10
```
jillian@jillian-desktop:~$ cd /home/jillian/Desktop
jillian@jillian-desktop:~/Desktop$ tar -zxvf dev-src_Jul_30_23h03.tar.gz
about.pas
cpp_compoptions.pas
debugfrm.pas
dev_module.pas
editor.pas
enviropt.pas
firbfrm.pas
help.pas
infofrm.pas
line.pas
main.pas
newproject.pas
outputfrm.pas
pas_compoptions.pas
project.pas
projectoptions.pas
removeunit.pas
splash.pas
templatefrm.pas
tooleditfrm.pas
toolfrm.pas
utils.pas
version.pas
dev.dpr
tooleditfrm.dfm
about.xfm
cpp_compoptions.xfm
debugfrm.xfm
enviropt.xfm
firbfrm.xfm
help.xfm
infofrm.xfm
line.xfm
main.xfm
newproject.xfm
outputfrm.xfm
pas_compoptions.xfm
projectoptions.xfm
removeunit.xfm
splash.xfm
templatefrm.xfm
toolfrm.xfm
dev.res
dev.conf
c++/
c++/setup/
c++/setup/install.sh
c++/setup/INSTALL
c++/setup/README
c++/setup/install.sh~
c++/setup/.#install.sh
c++/setup/install.~sh
c++/setup/#install.sh#
c++/setup/README~
c++/templates/
c++/templates/gtk+.ico
c++/templates/gtk+.template
c++/templates/gtk+_c.txt
c++/templates/hello.ico
c++/templates/hello.template
c++/templates/hello_c.txt
c++/templates/hello_cpp.txt
c++/templates/opengl.template
c++/templates/opengl.txt
c++/templates/opengl_cpp.txt
c++/templates/test.template
c++/templates/test_cpp.txt
c++/docs/
c++/docs/cpp/
c++/docs/cpp/win32/
c++/docs/cpp/linux/
c++/docs/index.html
c++/docs/compoptions.html
c++/docs/mailinglist.html
c++/docs/gpl.html
c++/docs/templates.html
c++/docs/TOPICS.txt
c++/docs/pas/
c++/docs/pas/linux/
c++/docs/pas/win32/
c++/docs/TOPICS.txt~
pas/
pas/setup/
pas/setup/install.sh
pas/setup/INSTALL
pas/setup/README
pas/setup/install.sh~
pas/setup/install.~sh
pas/templates/
pas/templates/gtk+.ico
pas/templates/gtk+.template
pas/templates/gtk+.txt
pas/templates/hello.ico
pas/templates/hello.template
pas/templates/hello.txt
pas/templates/opengl.template
pas/templates/opengl.txt
Makefile
synedit/
synedit/CVS/
synedit/CVS/Root
synedit/CVS/Repository
synedit/CVS/Entries
synedit/Contributors.txt
synedit/Page.bmp
synedit/Changelog.rtf
synedit/SynCompletionProposal.pas
synedit/Readme.txt
synedit/SynDBEdit.pas
synedit/SynEdit.inc
synedit/SynEdit.pas
synedit/SynEdit.res
synedit/SynEditAutoComplete.pas
synedit/SynEditExport.pas
synedit/SynEditHighlighter.pas
synedit/SynEditKeyCmdEditor.dfm
synedit/SynEditKeyCmdEditor.pas
synedit/SynEditKeyCmds.pas
synedit/SynEditKeyCmdsEditor.dfm
synedit/SynEditKeyCmdsEditor.pas
synedit/SynEditMiscClasses.pas
synedit/SynEditMiscProcs.pas
synedit/SynEditPrint.pas
synedit/SynEditPrintHeaderFooter.pas
synedit/SynEditPrintMargins.pas
synedit/SynEditPrintMarginsDialog.dfm
synedit/SynEditPrintMarginsDialog.pas
synedit/SynEditPrintPreview.pas
synedit/SynEditPrintTypes.pas
synedit/SynEditPrint_Old.pas
synedit/SynEditPrinterInfo.pas
synedit/SynEditPropertyReg.pas
synedit/SynEditPythonBehaviour.pas
synedit/SynEditReg.dcr
synedit/SynEditReg.pas
synedit/SynEditReg.res
synedit/SynEditSearch.pas
synedit/SynEditStrConst.pas
synedit/SynEditTextBuffer.pas
synedit/SynEditTypes.pas
synedit/SynExportHTML.pas
synedit/SynExportRTF.pas
synedit/SynHighlighterADSP21xx.pas
synedit/SynHighlighterAWK.pas
synedit/SynHighlighterAsm.pas
synedit/SynHighlighterBaan.pas
synedit/SynHighlighterBat.pas
synedit/SynHighlighterCAC.pas
synedit/SynHighlighterCache.pas
synedit/SynHighlighterCpp.pas
synedit/SynHighlighterCss.pas
synedit/SynHighlighterDfm.pas
synedit/SynHighlighterDml.pas
synedit/SynHighlighterFortran.pas
synedit/SynHighlighterFoxpro.pas
synedit/SynHighlighterGalaxy.pas
synedit/SynHighlighterGeneral.pas
synedit/SynHighlighterHC11.pas
synedit/SynHighlighterHP48.pas
synedit/SynHighlighterHP48Utils.pas
synedit/SynHighlighterHashEntries.pas
synedit/SynHighlighterHtml.pas
synedit/SynHighlighterIni.pas
synedit/SynHighlighterInno.pas
synedit/SynHighlighterJScript.pas
synedit/SynHighlighterJava.pas
synedit/SynHighlighterKix.pas
synedit/SynHighlighterM3.pas
synedit/SynHighlighterMPerl.pas
synedit/SynHighlighterManager.pas
synedit/SynHighlighterModelica.pas
synedit/SynHighlighterMulti.pas
synedit/SynHighlighterPHP.pas
synedit/SynHighlighterPas.pas
synedit/SynHighlighterPerl.pas
synedit/SynHighlighterProgress.pas
synedit/SynHighlighterPython.pas
synedit/SynHighlighterSQL.pas
synedit/SynHighlighterSml.pas
synedit/SynHighlighterTclTk.pas
synedit/SynHighlighterVB.pas
synedit/SynHighlighterVBScript.pas
synedit/SynHighlighterXML.pas
synedit/SynMemo.pas
synedit/SynRegExpr.pas
synedit/SynTextDrawer.pas
synedit/kTextDrawer.pas
synedit/synedit_kylix.dpk
synedit/synedit_kylix.res
synedit/synedit_kylix.conf
synedit/synedit_kylix.kof
synedit/synedit_kylix.dcp
synedit/bplsynedit_kylix.so
jillian@jillian-desktop:~/Desktop$ ls  -al
total 13700
drwxr-xr-x  7 jillian jillian    4096 2007-05-10 23:24 .
drwxr-xr-x 25 jillian jillian    4096 2007-05-10 23:07 ..
-rw-r--r--  1 jillian jillian    3501 2001-07-31 04:46 about.pas
-rw-r--r--  1 jillian jillian    5797 2001-07-31 04:46 about.xfm
-rwx------  1 jillian jillian  134144 2006-04-29 05:18 Alumni Directory.xls
drwxr-xr-x  5 jillian jillian    4096 2001-04-15 14:27 c++
-rw-r--r--  1 jillian jillian    8066 2001-07-04 21:30 cpp_compoptions.pas
-rw-r--r--  1 jillian jillian    7065 2001-07-04 21:30 cpp_compoptions.xfm
-rw-r--r--  1 jillian jillian    2420 2001-07-20 02:10 debugfrm.pas
-rw-r--r--  1 jillian jillian    1556 2001-07-20 02:10 debugfrm.xfm
-rw-r--r--  1 jillian jillian     228 2001-07-18 08:19 dev.conf
-rw-r--r--  1 jillian jillian    1823 2001-04-24 09:58 dev.dpr
-rw-r--r--  1 jillian jillian   24237 2001-07-18 19:30 dev_module.pas
-rw-r--r--  1 jillian jillian      32 2001-03-21 07:37 dev.res
-rw-r--r--  1 jillian jillian 1572524 2009-05-10 08:50 dev-src_Jul_30_23h03.tar.gz
-rw-r--r--  1 jillian jillian    5663 2001-07-18 18:24 editor.pas
-rw-r--r--  1 jillian jillian   23037 2001-07-19 00:18 enviropt.pas
-rw-r--r--  1 jillian jillian   12442 2001-07-19 00:18 enviropt.xfm
drwxr-xr-x  2 jillian jillian    4096 2009-05-10 08:27 ffsettings
-rw-r--r--  1 jillian jillian     321 2001-07-20 02:10 firbfrm.pas
-rw-r--r--  1 jillian jillian     487 2001-07-20 02:10 firbfrm.xfm
-rw-r--r--  1 jillian jillian 9651693 2009-05-10 08:20 firefox-2.0.0.3.tar.gz
-rw-r--r--  1 jillian jillian    2755 2001-04-16 01:55 help.pas
-rw-r--r--  1 jillian jillian    7608 2001-04-16 01:55 help.xfm
-rwx------  1 jillian jillian  110592 2006-01-26 04:03 IEClub Directory_AY 2005-2006.xls
-rw-r--r--  1 jillian jillian    2787 2001-07-04 21:14 infofrm.pas
-rw-r--r--  1 jillian jillian    3027 2001-07-04 21:14 infofrm.xfm
-rw-r--r--  1 jillian jillian   13569 2009-05-10 08:31 installnewfirefox.sh
-rwxr-xr-x  1 jillian jillian    1923 2001-07-04 17:37 install.sh
-rw-r--r--  1 jillian jillian    1256 2001-06-07 07:34 line.pas
-rw-r--r--  1 jillian jillian    1273 2001-06-07 07:34 line.xfm
-rw-r--r--  1 jillian jillian   53171 2001-07-31 04:49 main.pas
-rw-r--r--  1 jillian jillian  154935 2001-07-31 04:49 main.xfm
-rw-r--r--  1 jillian jillian    1183 2001-07-31 05:03 Makefile
drwx------ 13 jillian jillian    4096 2007-05-10 00:57 My Pictures
-rw-r--r--  1 jillian jillian    8718 2001-07-18 18:44 newproject.pas
-rw-r--r--  1 jillian jillian   55649 2001-07-18 18:44 newproject.xfm
-rw-r--r--  1 jillian jillian    1578 2001-05-03 05:38 outputfrm.pas
-rw-r--r--  1 jillian jillian    1794 2001-05-03 05:38 outputfrm.xfm
drwxr-xr-x  4 jillian jillian    4096 2001-04-15 13:51 pas
-rw-r--r--  1 jillian jillian    8763 2001-06-07 06:06 pas_compoptions.pas
-rw-r--r--  1 jillian jillian    7405 2001-06-07 06:06 pas_compoptions.xfm
-rw-r--r--  1 jillian jillian    2432 2001-05-19 21:22 projectoptions.pas
-rw-r--r--  1 jillian jillian    3281 2001-05-19 21:22 projectoptions.xfm
-rw-r--r--  1 jillian jillian    9353 2001-07-05 23:28 project.pas
-rw-------  1 jillian jillian       0 2007-05-10 23:22 qt-x11-2.3.0.tar.gz
-rw-------  1 jillian jillian 1397320 2007-05-10 23:24 qt-x11-2.3.0.tar.gz.part
-rw-r--r--  1 jillian jillian    1028 2001-04-23 20:53 removeunit.pas
-rw-r--r--  1 jillian jillian     845 2001-04-22 10:56 removeunit.xfm
-rw-r--r--  1 jillian jillian    1303 2001-07-06 22:13 splash.pas
-rw-r--r--  1 jillian jillian  473608 2001-07-06 22:13 splash.xfm
drwxr-xr-x  3 jillian jillian    4096 2001-07-31 05:00 synedit
-rw-r--r--  1 jillian jillian   13690 2001-04-23 20:53 templatefrm.pas
-rw-r--r--  1 jillian jillian   19180 2001-04-22 10:04 templatefrm.xfm
-rw-r--r--  1 jillian jillian    4453 2001-04-17 04:39 tooleditfrm.dfm
-rw-r--r--  1 jillian jillian    2888 2001-04-17 04:39 tooleditfrm.pas
-rw-r--r--  1 jillian jillian    4533 2001-04-23 20:53 toolfrm.pas
-rw-r--r--  1 jillian jillian    8192 2001-03-29 14:58 toolfrm.xfm
-rw-r--r--  1 jillian jillian    7017 2001-07-07 07:31 utils.pas
-rw-r--r--  1 jillian jillian    1323 2001-07-16 20:49 version.pas
jillian@jillian-desktop:~/Desktop$

```

thanks for this. uhm so what do i do next? sorry for asking alot of questions but i really ned to install devc++, just this one..
oh no didn't realize my desktop's flooded!

---

### Post by Carlos Santiago on 2007-05-10
Well is seems you have your files all around the Desktop.
They should all be in an unique folder , but there is not problem besides esthetic.
You you can delete them later, after you finish the installation.

Now (inside Desktop) type:
```
sudo ./install.sh
```

---

### Post by j_evenstar on 2007-05-10
```
jillian@jillian-desktop:~/Desktop$ sudo ./install.sh
Password:
** Dev-C++ installation script **

You must be root to install. Do you want to continue ?
 (Y/n) ? Y
tar: binary.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
Where do you want to install Dev-C++ ? [/home/jillian/dev-c++] : /home/jillian/dev-c++
mv: cannot stat `TODO': No such file or directory
mv: cannot stat `BUGS': No such file or directory
mv: cannot stat `bin/devcpp': No such file or directory
mv: cannot stat `bin/libqtintf.so*': No such file or directory

* This script will now guess your gcc and make paths
* Press enter if the path is correct for each program

make is located in : [make:] :
gcc is located in : [/usr/lib/gcc] :
g++ is located in : [g++:] :
gdb (or your favourite debugger) is located in : [/usr/bin/gdb] :
xterm, aterm or Eterm is located in : [/usr/bin/xterm] :

* Configuration file is now been written in /home/jillian/.devcpp/config


* Installation terminated, you may now run /home/jillian/dev-c++/devcpp

jillian@jillian-desktop:~/Desktop$
```
opened the folder and found no items. should i install Qt? as said in the install file..

---

### Post by Carlos Santiago on 2007-05-10
plz attach the complete and compressed file: dev-src_Jul_30_23h03.tar.gz

Let me look at it

---

### Post by j_evenstar on 2007-05-10
the forum only allows a max .gz file of 976.6 KB. so [here]("http://freshmeat.net/projects/dev-cpp/") is the url where i downloaded it. it's under TAR/GZ. thanks.

---

### Post by Carlos Santiago on 2007-05-10
Why dont you just download the bin file ([http://download.sourceforge.net/dev-cpp/devcpp-bin_070.tar.gz)?](http://download.sourceforge.net/dev-cpp/devcpp-bin_070.tar.gz)?)

---

### Post by Carlos Santiago on 2007-05-10
The link to the dev file is broken!

---

### Post by j_evenstar on 2007-05-10
i don't know, really. i just googled devc++ for linux and that's what i chose. i'll download it then. after that?
thanks for your patience, really.
here's the link: [http://freshmeat.net/projects/dev-cpp/](http://freshmeat.net/projects/dev-cpp/)  *the .tar.gz file is under TAR/GZ.

also, the sourceforge link takes time to load.....

---

### Post by Carlos Santiago on 2007-05-10
let me explain you two things:

1. when you do
sudo <something>
you are executing <something> as root

for example
cd ~
you go to your home. 

But with
sudo cd ~
you go to root's home

You can try these and see the result.

2. when you type
./<something>

you are executing <something> located in directory '.'
And '.' is the directory where you are working on.

Good luck

---

### Post by Carlos Santiago on 2007-05-10
First make
```
sudo apt-get install qt-x11-free-dbg
```

Then uncompress the devcpp-bin_070.tar.gz file with
```
tar -zxvf devcpp-bin_070.tar.gz
```

Then 
```
cd devcpp-bin_070
```

And finally

```
sudo ./install.sh
```

To start just type
```
devcpp
```

If it doesnt work, type 
```
~/dev-c++/devcpp
```

---

