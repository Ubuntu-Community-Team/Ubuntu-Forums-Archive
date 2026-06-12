---
title: "Installing Windows Applications Using Wine"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by ablindog on 2007-04-14
Thanks for all forum's help! I gave up on M$, beta'ed Vista 1 year and had to find something better.Downlaoded Edgy overtop XP saving only MP3s,Docs, etc It's been a bit of a steep learning curve but after getting dual monitors working in the resolution I wanted and upgrading to Feisty, things are looking up.

 I am trying To install Windows applications using Wine, have d/led .exe files to my desktop and am now lost. The Wine documention says 
  
3.      Open the terminal, and cd into the directory where the .EXE is located."
this hasn't helped me because every command I type returns
 " bash: cd: /blah/blah: Not a directory"

One example of what I've tried...........
ablindog@ablindog-desktop:~$ cd /ablindog/desktop RipIt4Me.exe

Is there:redface:  an easy place to d/l files to that I will be able to direct  the "cd" to be able to locate them?

---

### Post by ethidda on 2007-04-14
The easiest way is to download into your home folder, which the terminal starts up in.

when you do cd, it has to be into a directory, so you command would not have worked. Instead, try these two commands:

cd /ablindog/desktop
wine RipIt4Me.exe

---

### Post by N Clement on 2007-04-14
When you give the cd command something like:
```
$cd /*pathhere*
```
it treats /*pathhere* as an absolute path--it starts at the very bottom of the file system tree. If you have downloaded them to your desktop, for example, to change to that directory, you would do:
```
~$ cd ./Desktop
```,

The ./ is critical because it means that the path is being defined relative to your current working directory.

---

### Post by ablindog on 2007-04-15
I tried  cd /ablindog/desktopwine RipIt4Me.exe
 cd /ablindog/desktop wine RipIt4Me.exe
and 
 cd /ablindog/desktop wine RipIt4Me.exe

no help. Thanks for the quick response:o

---

### Post by ethidda on 2007-04-15
hmm...

if you downloaded it to your desktop and you can see it on your desktop, try

```
cd ~/Desktop
wine RipIt4Me.exe
```

you can also do an 'ls' command after you cd ~/Desktop to make sure that it's there. Double check that you spelled the file name correctly.

---

### Post by ablindog on 2007-04-15
> **N Clement said:**
> When you give the cd command something like:
```
$cd /*pathhere*
```
it treats /*pathhere* as an absolute path--it starts at the very bottom of the file system tree. If you have downloaded them to your desktop, for example, to change to that directory, you would do:
```
~$ cd ./Desktop
```,

The ./ is critical because it means that the path is being defined relative to your current working directory.

cd ./Desktop     was the answer to my question about location and finding the d/l'ed files. 
File wouldn't open so I have more searching to do, but you have really helped. Thank-you

---

### Post by david_kt on 2007-04-15
> **ablindog said:**
> 
File wouldn't open so I have more searching to do, but you have really helped. Thank-you

If you run in terminal, you should have error message in terminal if the you say the file would not open. Could you post the error here?

DK

---

### Post by ablindog on 2007-04-16
david_kt

The message is 

ablindog@ablindog-desktop:~/Desktop$ wine ripit4me.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\ablindog\\Desktop\\ripit4me.exe") not found
err:module:import_dll Library MSVCP60.dll (which is needed by L"Z:\\home\\ablindog\\Desktop\\ripit4me.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\ablindog\\Desktop\\ripit4me.exe" failed, status c0000135

I haven't been able to spend much time researching, I was able to install DVDDcrypter with no problems. I don't like asking for help if I haven't put in the time/research. I think I just have to grab the .dlls and put them in the c drive but I don't know the the command to do that yet.     

:D Your help is Happily Welcomed

---

### Post by david_kt on 2007-04-16
Yes, you are right. Just download these 2 dlls:

[http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/M/mfc42.dll]("http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/M/mfc42.dll")
[http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/M/MSVCP60.DLL]("http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/M/MSVCP60.DLL")

and put it in ~/.wine/drive_c/windows/system32

and then winecfg, set library for this two dll (native and then builtin. And try to run again.

DK

---

### Post by ablindog on 2007-04-16
Thanks for the info.... I'll try that tonight when I get home and let you know.

---

### Post by ablindog on 2007-04-16
Worked great after I figured out that it required an "install" command

ablindog@ablindog-desktop:~/Desktop$ install mfc42.dll ~/.wine/drive_c/windows/system32

You all solved my problem, Thank-You

---

