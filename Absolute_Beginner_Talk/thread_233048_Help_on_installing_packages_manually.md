---
title: "Help on installing packages manually"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by breeky5 on 2006-08-09
Hi everyone


I'm having problems with installing packages manually on linux platform. I'm basically new to this operating system so I don't know much about the procedures on how to install programs. By the way i'm using Ubuntu 5.10.

I know that in order to make windows programs run on linux, I have to install another program to make them work, like WINE. So I tried installing WINE package. After using the './configure' command i got this error message:

configure: error: no suitable lex found. Please install the 'flex' package.

// It seems like wine is looking for another program for it's dependencies.

After receiving the error message, I downloaded the flex-2.5.31 package and installed it using the same method. The './configure' and 'make' command was executed successfully and found no errors. However when I checked the make file using the 'make check' command, It found 3 errors:

Results:
Tests succeeded: 35
Tests FAILED: 3
make[3]: *** [check-local] Error 1
make[3]: Leaving directory `/home/user/Desktop/Installers/flex-2.5.31/tests'
make[2]: *** [check-am] Error 2
make[2]: Leaving directory `/home/user/Desktop/Installers/flex-2.5.31/tests'
make[1]: *** [check-recursive] Error 1
make[1]: Leaving directory `/home/user/Desktop/Installers/flex-2.5.31/tests'
make: *** [check-recursive] Error 1

Same thing happens when I try to Install it.

Does anybody know why this is happening?

---

### Post by kebes on 2006-08-09
First off, you should only try to install manually if you've tried (and failed!) with a package-based install. Nowadays the WINE people have excellent repositories that work great with Ubuntu:
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

Specifically, for your version of Ubuntu (5.10), you should add:
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) breezy main
to your package list ("/etc/apt/sources.list") and then try to install:
$ sudo aptitude update
$ sudo aptitude install wine

If that doesn't work, then you can go the manual route. Again, however, when you run into a dependency problem, in my experience it's best to try to fix it first using the "automatic method" (either apt-get or aptitude on the command-line, or equivalently using the Synaptic or Adept GUI programs).

My advice is to try the auto way first. If that doesn't work, then try to figure out those errors. For instance, what happens if you go to the next step, and just do "make install" for that flex package? Do you get errors or does it proceed?

---

### Post by breeky5 on 2006-08-09
Umm the real scenario is, I'm trying to install wine on a different computer with no internet connection that's why I can't do the update thing. I tried to install the program the old fashion way by compiling the package from tar.gz and unfortunately it failed. Even if I try to install the program using the 'make install' command, I still got the same errors.

---

### Post by kebes on 2006-08-09
I know I keep side-stepping your actual question, but is it not easier to download the .deb file from here (on a computer with net access!):
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
and then bring it over to your other computer (via CD, USB key, etc.). You can try to force apt-get to install the .deb file (I think you have to put the file in /var/cache/apt/archives/ and then maybe use the --no-download option), or use dpkg to install the .deb file.


With regard to those flex make errors: they look quite generic. Maybe if you look around in the make file (in the 'check' section) or in the tests file, you can identify what tests specifically are creating the errors? (you could try commenting out various things and seeing when the errors go away... or putting in harmless lines in the script like 'echo "File position #25" ' to identify which lines create the errors)... Once you identify what checks specifically are causing the problems you'll have a better change of fixing it.

My gut instinct is that it's a missing dependency. Typically when installing things manually, the main problem is "dependency hell" where you have to go tracking down package and package each time there is a problem. Hence why a net connection and "apt-get" is so wonderful. In your case, check through the documention for flex and see what it needs. Make sure all of this is installed before going any further. (Same thing for WINE.) If everything is indeed installed, then like I said check the make file for hints about what kinds of checks might be going wrong.

I know this help isn't very specific, but the errors in question are also non-specific. I hope this helps somewhat...

---

### Post by breeky5 on 2006-08-10
I think the problem is about where I must place the file in order to install properly. Cause there's an error also that says "Leaving Directory.... Permission Denied". What do you think about that? 

And another thing, do you know Automatix or EasyUbuntu? Can it help me solve my problem?


Well, thanks for the information about the .deb file and commenting scripts, I'll give it a try.

---

### Post by kebes on 2006-08-10
> **breeky5 said:**
> I think the problem is about where I must place the file in order to install properly. Cause there's an error also that says "Leaving Directory.... Permission Denied". What do you think about that? 

Oh of course! Were you doing "make install" as root? Typically the "./configure" and "make" steps can be done as any user (just compiling), but to do "make install" you need to be root (because files will be copied to system directories). You should of course only do this if you trust the source of the package, but you just do:

$ sudo make install
(and enter the password)

or you can go:
$ sudo -s
to jump into a root shell and do it from there.

It might be as simple as that.

> 
And another thing, do you know Automatix or EasyUbuntu? Can it help me solve my problem?

Automatix will install WINE among other things (you get to pick from a list), but you need to have a working net connection. Like aptitude/apt-get it resolves dependencies and downloads all the required files. Getting it to work without a net connection would be challenging, I'm guessing.


> Well, thanks for the information about the .deb file and commenting scripts, I'll give it a try.

I hope the root thing was the answer. If not, post again.

---

### Post by breeky5 on 2006-08-10
Hahaha! Yeah I was doing 'make install' as root and errors continue to appear. To my frustration, I typed any key that comes into my mind and surprisingly, lo and behold, it worked!!

I really don't understand what happend at first and the difference of adding sudo or not to the command till I read ur remarks.

The installation went well, however when I type winecfg or try to execute the .exe file, this error appears,

breeky5@RJAY:~/Desktop/Windows Installers$ wine winamp.exe
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

Any ideas? I installed wine-0.9.18

And also is there a gui for this program? where can I find it?

---

### Post by kebes on 2006-08-10
Wine typically installs a graphical file-browser:
[http://www.winehq.com/site/docs/wineusr-guide/explorer-like-wine](http://www.winehq.com/site/docs/wineusr-guide/explorer-like-wine)

You should find this program (called "winefile" I think) and run it. If it opens then that will confirm that wine is installed properly. There is a graphical component for configuring wine called "winecfg" located here probably:
/usr/local/bin/winecfg

Like I said it's probably best to make sure that Wine is installed properly, using a simple app as a starting point. "winefile" is one good test, and the windows notepad program (c:\windows\notepad.exe) is another simple one.

If your install is working then you can move forward.

I assume that you installed the program you are trying to use? In wine you usually go "wine setup.exe" to perform the setup... the program will have a chance to set registry keys and so forth. Then you can try to run the exe file for that application.

So try to figure out if your error is occuring throughout wine or only with the particular program you are trying to run. If it's only that particular program, do a search on the wine database:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

and see if anyone has hints for that particular app. Also look at the wine documentation and man-pages:
[http://www.winehq.com/site/documentation](http://www.winehq.com/site/documentation)

I believe there is a way to run wine with additional output of information. There might be a more useful error message in the verbose output. Sometimes a particular program needs a DLL of some sort that you can track down.

---

### Post by kebes on 2006-08-10
I just noticed you said that the error occured with "winecfg" also. Clearly your Wine install is not happy.

It might be trying to launch as root ("sudo wine winamp.exe") and see what happens. If root is able to launch then maybe it's a permissions problem. (Wine is intended to run as normal use, and it's not a good idea to run it as root, but at least this will help determine the cause of the problem.)


According to some sources:
[http://www.winehq.com/pipermail/wine-users/2006-July/022808.html](http://www.winehq.com/pipermail/wine-users/2006-July/022808.html)

The problem might be with:
"winex11drv.so" or "winex11.drv.so"

Make sure that you have this file somewhere (find / -name "winex11*"). Also since ".so" files are usually kernel modules, so you might have to add it to a config somewhere so that it gets loaded properly.

I believe this is done by putting the name of the include path in "/etc/ld.so.conf" and using the "ldconfig" command to force a refresh of runtime link libraries. However I'm not very sure about that so read some documentation before doing anything.

Hope that helps.

---

### Post by breeky5 on 2006-08-11
Yeah maybe it's the missing X11 development support! :-k 

I compiled the package again to track down errors and this is what came up:

configure: WARNING: X development files not found. Wine will be built without
configure: WARNING: X support, which currently does not work, and probably
configure: WARNING: isn't what you want anyway. You will need to install devel
configure: WARNING:  packages of Xlib/Xfree86 at the very least.

configure: WARNING: Your system appears to have the FreeType 2 runtime libraries
configure: WARNING: installed, but 'freetype-config' is not in your PATH. Install
configure: WARNING: the freetype-devel package (or its equivalent on your distribution)
configure: WARNING: to enable Wine to use TrueType fonts.

configure: WARNING: FontForge is missing.
configure: WARNING: Fonts will not be built. Dialog text may be invisible or unaligned.

There were no errors, only warnings. 

Maybe i'll try to research more about X development and update you the progress. 

If you have comments just let me know. Thanks~ :grin:

---

