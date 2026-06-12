---
title: "How to install Foxit reader"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by hosammy on 2007-08-16
How to install Foxit Reader for Desktop Linux and use it as default reader in the firefox browser instead of the Adobe acrobatreader?
Which directory you would suggest to place the executable foxit file?

---

### Post by Hobo Joe on 2007-08-16
Could you give a link to where you got the files and or the guide?

---

### Post by Arthur Archnix on 2007-08-16
It's possible that you could use WINE to install foxit. But linux has better pdf readers installed by default. Their also really lightweight, which is probably what drew you to foxit on your windows machine in the first place.

In other words, no need for foxit or adobe. There are at least two or three other options. Look in the repo's under add/remove.

---

### Post by hosammy on 2007-08-16
Reply to Hobo Joe,

The link of foxit is:

[http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/)
There is no instruction to install it. The file format id in the form of tar.gz

Reply to Arthur Archnix
What sort of option be available in Yelp?
I think I need not use wine to install foxit because there is linux version instead of the Windows version. The reason I like foxit because the file size is smaller and the speed is faster. The most important thing is it support the chinese font. The adobe reader can only commit the basic which does not support the chinese font.

---

### Post by jrusso2 on 2007-08-16
I have never been able to get the Linux version of foxit to work on Ubuntu it seems to have some problem there.  Anyway I have run it on Debian and its not anywhere near as good as the windows version as it was a beta.

I think some people have gotten the windows version to work with WINE.  But I don't know how you can make a windows app default.

---

### Post by le_vainqueur on 2008-05-09
I know this is an old post, but it took me quite a while to get Foxit working, so I thought I would post my solution here.

As stated above, the Linux version of Foxit doesn't seem to work in Ubuntu.  I wasn't able to find anyone on the web who had success with it.  Also, most people pointed out that the Linux version is not nearly as useful as the Windows version.

That being said, I was not able to get the installer to run with Wine.  Both versions 2.3 and 2.2 failed to give me any sort of result.  The resulting error when running wine from the terminal was:

> preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\temp\\fox80f5.tmp\\Foxit Reader Setup.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\temp\\fox80f5.tmp\\Foxit Reader Setup.exe" failed, status c0000135


I don't know what this means...maybe preloader is causing some sort of conflict?  Regardless, I was at a loss.  I realized, however, that there were some alternate downloads available on the site.  I decided to download the .zip file instead of the .exe file.  This does, in fact, solve my problem.  Within the .zip file there is a single .exe file which will run in Wine without any tweaking.  

I tested the drawing markup and commenting tools (the reason I was determined to get Foxit working), and they seem to function perfectly.  I tried PDFEdit, but it was sluggish, and overall frustrating to use.  With Foxit, though, I am able to do my research efficiently.


Hope this helps,

LV

---

### Post by doookiee on 2008-05-25
LV almost got it :)


Fix: In order to get the installer to work you need to copy mfc42.dll from your " Windows/system32" folder (or a websearch ;)) to your Wine-" Windows/system32" folder ( " /home/%my username%/.wine/drive_c/windows/system32 "  on my system, but also accessible through the " Browse C:\ drive" entry in the Wine menu). 

After that 1. Follow these instructions: [http://sodeve.net/foxit-reader-on-ubuntu-linux-through-wine/](http://sodeve.net/foxit-reader-on-ubuntu-linux-through-wine/) 2. In the "Properties" ->" Permissions tab" of the .sh file previous tutorial made you create, tick the box next to "Execute". It should work now.

---

