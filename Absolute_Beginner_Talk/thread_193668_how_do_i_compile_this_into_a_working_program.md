---
title: "how do i compile this into a working program?"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-06-10
I downloaded a zipped .src file. but dont know how to make it a program, is there a simple way of doing that? the attachments are the screenshots of the files in the program,

---

### Post by taurus on 2006-06-10
What does the ReadMe.txt tell you what to do?

---

### Post by tartarian on 2006-06-10
Take a look at the readme and install files - there are usually install instructions in there.

If not then normally to compile a program you need to navigate to that folder in the terminal and run the following commands:
./configure
make
make install

---

### Post by maddbaron on 2006-06-10
[QUOTE=tartarian]Take a look at the readme and install files - there are usually install instructions in there.

If not then normally to compile a program you need to navigate to that folder in the terminal and run the following commands:
./configure
make
make install[/QUOTE]

no readme file around...

i entered wrong in terminal can you correct me please?](*,) ](*,) ](*,)

---

### Post by tartarian on 2006-06-10
Sorry should have told you how to navigate to that directory!

to get "into" the directory in the terminal you need to use the cd command (change directory)

so:
```

cd /home/maddbaron/Desktop/vscap20s

```

then try ./configure
make
make install

if that doesnt work then could you post the content of the ReadMe.txt file please.

---

### Post by maddbaron on 2006-06-10
> maddbaron@alchemist:~$ cd /home/maddbaron/Desktop/vscap20s
maddbaron@alchemist:~/Desktop/vscap20s$ ./configure
bash: ./configure: No such file or directory
maddbaron@alchemist:~/Desktop/vscap20s$ make install
make: *** No rule to make target `install'.  Stop.
maddbaron@alchemist:~/Desktop/vscap20s$ make
make: *** No targets specified and no makefile found.  Stop.
maddbaron@alchemist:~/Desktop/vscap20s$


no readme.txt file.

---

### Post by tartarian on 2006-06-10
There is on the first screenshots you posted! (the third one from the left):p

---

### Post by maddbaron on 2006-06-10
i had to organize by type to see that...thanks here is the read me. i dont see n e thin g bout compiling.(this stuff is confusing)

> ========================================================================

       MICROSOFT FOUNDATION CLASS LIBRARY : vscap

========================================================================





AppWizard has created this vscap application for you.  This application

not only demonstrates the basics of using the Microsoft Foundation classes

but is also a starting point for writing your application.



This file contains a summary of what you will find in each of the files that

make up your vscap application.



vscap.h

    This is the main header file for the application.  It includes other

    project specific headers (including Resource.h) and declares the

    CVscapApp application class.



vscap.cpp

    This is the main application source file that contains the application

    class CVscapApp.



vscap.rc

    This is a listing of all of the Microsoft Windows resources that the

    program uses.  It includes the icons, bitmaps, and cursors that are stored

    in the RES subdirectory.  This file can be directly edited in Microsoft

	Developer Studio.



res\vscap.ico

    This is an icon file, which is used as the application's icon.  This

    icon is included by the main resource file vscap.rc.



res\vscap.rc2

    This file contains resources that are not edited by Microsoft 

	Developer Studio.  You should place all resources not

	editable by the resource editor in this file.



vscap.clw

    This file contains information used by ClassWizard to edit existing

    classes or add new classes.  ClassWizard also uses this file to store

    information needed to create and edit message maps and dialog data

    maps and to create prototype member functions.



/////////////////////////////////////////////////////////////////////////////



For the main frame window:



MainFrm.h, MainFrm.cpp

    These files contain the frame class CMainFrame, which is derived from

    CFrameWnd and controls all SDI frame features.



res\Toolbar.bmp

    This bitmap file is used to create tiled images for the toolbar.

    The initial toolbar and status bar are constructed in the

    CMainFrame class.  Edit this toolbar bitmap along with the

    array in MainFrm.cpp to add more toolbar buttons.



/////////////////////////////////////////////////////////////////////////////



AppWizard creates one document type and one view:



vscapDoc.h, vscapDoc.cpp - the document

    These files contain your CVscapDoc class.  Edit these files to

    add your special document data and to implement file saving and loading

    (via CVscapDoc::Serialize).



vscapView.h, vscapView.cpp - the view of the document

    These files contain your CVscapView class.

    CVscapView objects are used to view CVscapDoc objects.







/////////////////////////////////////////////////////////////////////////////

Other standard files:



StdAfx.h, StdAfx.cpp

    These files are used to build a precompiled header (PCH) file

    named vscap.pch and a precompiled types file named StdAfx.obj.



Resource.h

    This is the standard header file, which defines new resource IDs.

    Microsoft Developer Studio reads and updates this file.



/////////////////////////////////////////////////////////////////////////////

Other notes:



AppWizard uses "TODO:" to indicate parts of the source code you

should add to or customize.



If your application uses MFC in a shared DLL, and your application is 

in a language other than the operating system's current language, you

will need to copy the corresponding localized resources MFC40XXX.DLL

from the Microsoft Visual C++ CD-ROM onto the system or system32 directory,

and rename it to be MFCLOC.DLL.  ("XXX" stands for the language abbreviation.

For example, MFC40DEU.DLL contains resources translated to German.)  If you

don't do this, some of the UI elements of your application will remain in the

language of the operating system.



/////////////////////////////////////////////////////////////////////////////



---

### Post by tartarian on 2006-06-10
Hmmm..... I don't see anything there either. What exactly are you installing? Have you had a look in Synaptic Manager and tried installing it from there? What about the site you downloaded it off - is there any documentation/instructions on there??
Odd that there isnt an install.txt file :-?

---

### Post by maddbaron on 2006-06-10
i am looking for a screen captor/recorder that lets me select a part of a window to record. this program is called vscap20s i found it on google. the site said linux friendly and only had the source code in a zip file to download.

i tried synaptic and nothing either.

i really need a screen recorder that lets me record a select portion i have another but it only records the entire screen i cant pick an area.

in windows i have fastone and bullants screen recorder but those r exe programs.

---

### Post by tartarian on 2006-06-10
Do you have wine? You could try running the .exe prog with wine which might work. (the important word there being "might").

Could you not just take a screen shot and crop the image??? 

I just saw the word Microsoft in the ReadMe file.... :p

Apart from that I really dont know - theres nothing in Synaptic, theres no Makefile, its not an extension to another program. Could you post the site where you got it from???

---

### Post by maddbaron on 2006-06-10
sourceforge its called camstudio.

---

### Post by maddbaron on 2006-06-10
ok i give up on that program. i downloaded an aplet i followed the directions but i dont know what to do next..i got a stop message.

what do i type next to install or is it installed?

> maddbaron@alchemist:~$ cd /home/maddbaron/Desktop/wireless-applet-0.0.2
maddbaron@alchemist:~/Desktop/wireless-applet-0.0.2$ make
make: *** No targets specified and no makefile found.  Stop.
maddbaron@alchemist:~/Desktop/wireless-applet-0.0.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for APPLET... configure: error: Package requirements (glib-2.0 gtk+-2.0  libpanelapplet-2.0 gnome-keyring-1 hal dbus-glib-1) were not met:

No package 'glib-2.0' found
No package 'gtk+-2.0' found
No package 'libpanelapplet-2.0' found
No package 'gnome-keyring-1' found
No package 'hal' found
No package 'dbus-glib-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables APPLET_CFLAGS
and APPLET_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

maddbaron@alchemist:~/Desktop/wireless-applet-0.0.2$ make install
make: *** No rule to make target `install'.  Stop.
maddbaron@alchemist:~/Desktop/wireless-applet-0.0.2$


---

### Post by tartarian on 2006-06-10
I would be a very happy guy if I knew the answer to that - I'm getting pretty much the same error on a program I'm trying to compile. Only suggestions would be try running:
sudo apt-get upgrade
sudo apt-get update
sudo apt-get install build-essential

Apart from that I'm baffled!

(BTW - the other program you were trying to install was only compatible on windows -  It said on sourceforge: Compatible Operating Systems : Windows NT/2000/XP)

---

### Post by maddbaron on 2006-06-10
[QUOTE=tartarian]I would be a very happy guy if I knew the answer to that - I'm getting pretty much the same error on a program I'm trying to compile. Only suggestions would be try running:
sudo apt-get upgrade
sudo apt-get update
sudo apt-get install build-essential

Apart from that I'm baffled!

(BTW - the other program you were trying to install was only compatible on windows -  It said on sourceforge: Compatible Operating Systems : Windows NT/2000/XP)[/QUOTE]

do u think i would be able to download this applet from synaptic?

i am on gnome but i have kde programs also. 

i have the kubuntu desktop also. this is a kde program is shouldnt cause any problems right?

---

### Post by tartarian on 2006-06-10
It is possible to run a KDE program on a GNOME desktop environment. As long as you have the KDE libraries. The only problems I have ever heard of (not experienced) are the program not fitting in with the GNOME "look" and problems with drag and drop features. Thats it I think.

If the program you want is made specifically for linux then it should be in Synaptic. Just click search and type in the nameof your applet. If it's there then you should have no problems installing it - it does it for you.

---

### Post by maddbaron on 2006-06-10
ah ok cool thanks...i will give it a go

---

### Post by tartarian on 2006-06-10
Post any problems you have, or if you get it working! :d

---

### Post by maddbaron on 2006-06-10
didnt get it working....i downloaded it and now cant find it.....i tried the add to panel feature and got nuthin

---

