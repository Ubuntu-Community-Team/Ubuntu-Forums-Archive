---
title: "&quot;totem-gstreamer-firefox-plugin&quot; not in Universe"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by BadDolphin on 2006-09-09
I just finished my first linux install (I've used linux to some degree via command line, usually just admin'ing Apache and stuff at work), and have been spending time reading the documentation.  The first thing I did was to add the Universe repository, then I reloaded.  

Next up, I decided to make the browser work with multimedia.  The documentation (4.4.1 on page 40) says to install "totem-gstreamer-firefox-plugin" from the Universe repository.  It points back to section 2 where it tells how to add from the Universe repository. 

However, there's no such thing listed among the many packages that show in the Universe repository.  They're in alpha order, and I checked in the t's and the g's and it's simply not there.
-----
PS...  I installed XChat, figuring I'd lurk in an #ubuntu channel somewhere, but the documentation is in error on that too.  It says that "Ubuntu Servers" is listed among the list of IRC servers, but there's no such thing listed.  I eventually found a server with an active #ubuntu, but I'm slightly dismayed to find such GREAT documentation specifically for 6.06 and yet find it... apparently just plain wrong.

---

### Post by deadgobby on 2006-09-09
You may want to install extra repos
[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)
 That may be the pill you need to solve you head ache.
Gobby

---

### Post by BadDolphin on 2006-09-09
I went back into System, Administration, Software Prefs, and checked EVERY possible thing there is, to assure I can see all packages.  I then get an error:

W: Duplicate sources.list entry cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060807.1) dapper/main Packages (/var/lib/apt/lists/Ubuntu%206.06.1%20%5fDapper%20Drake%5f%20-%20Release%20amd64%20(20060807.1)_dists_dapper_main_binary-amd64_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060807.1) dapper/restricted Packages (/var/lib/apt/lists/Ubuntu%206.06.1%20%5fDapper%20Drake%5f%20-%20Release%20amd64%20(20060807.1)_dists_dapper_restricted_binary-amd64_Packages)

Thanks for the help... I'll try the commands on that site at the command line and see what happens...

---

### Post by BadDolphin on 2006-09-09
Okay, I ran those commands and copied/pasted the content into the file that the second command opened.  Still no "totem..." ... it jumps from Tomboy Notes to TuxMath (the packages are in alpabetical order... I've scrolled through in case it's been renamed, but see nothing like this).

And I still get the error

W: Duplicate sources.list entry cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060807.1) dapper/main Packages (/var/lib/apt/lists/Ubuntu%206.06.1%20%5fDapper%20Drake%5f%20-%20Release%20amd64%20(20060807.1)_dists_dapper_main_binary-amd64_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060807.1) dapper/restricted Packages (/var/lib/apt/lists/Ubuntu%206.06.1%20%5fDapper%20Drake%5f%20-%20Release%20amd64%20(20060807.1)_dists_dapper_restricted_binary-amd64_Packages)

I remember years ago installing from .tar.gz files and never had this kind of crazy difficulty.  At least it was POSSIBLE to add software.

---

### Post by BadDolphin on 2006-09-09
Well, I finally just totally reinstalled Ubuntu.  And tried again, and at least I'm now 100% certain that I've found an error in the documentation for Ubuntu.

The error is on pg 28 of the instructions, where it says to do this:

1. Open System->Administration->Software Properties.
[no problem]

2. Select Add.
[no problem]

3. To enable the Universe repository, check the Community Maintained (Universe) button.
[done, still no problem]

4. To enable the Multiverse repository, check the Non-free (Multiverse) button.
[done, still no problem]

5. Click Close to save your changes and exit.
**[PROBLEM: there is no "close" to click.  The only buttons are Custom, Cancel, and Add.  So of course I click the X at the top right of the window, the closest thing to "close" there is.  That takes me back to a window where there is, in fact, a button labeled "close" so I click it.]**

6. To apply your changes, select Reload.
**[PROBLEM: There is no "reload" to click.]**

So next I go back and at Step 5 I instead click "Add."  Then, having no "OK" button or similar, I click "Close."  Now I do, in fact, get a "reload" button, which I click.  That leaves me with a totally grayed out window, which eventually closes on its own.  *_**However, if you go back to Step 1 to make sure the changes are recorded, both the boxes checked in steps 4 and 5 are back to being unchecked.**_*

But that wasn't the cause of the problem anyway.  When I go into Applications->Add/Remove->Advanced (clicking Advanced was what I missed), I can find it, but now get a dependency error (isn't that what this was designed to avoid?) saying 

[B]totem-gstreamer-firefox-plugin:
  Depends: totem-gstreamer (=1.4.1-0ubuntu4) but 1.4.3-0ubuntu1 is to be installed[/B]

I have no idea what that means, and it gives no further clues, but at least it at least gives me something new to google.

---

