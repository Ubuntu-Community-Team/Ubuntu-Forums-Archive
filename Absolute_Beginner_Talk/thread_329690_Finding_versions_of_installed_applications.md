---
title: "Finding versions of installed applications"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-01-02
Back again for a little more help. How do I find out what version of Firefox is currently running on my comp? I downloaded the tar for 2.0, extracted the files and ran the mozilla-firefox.sh exe file, but nothing seemed to happen. Just trying to see if it installed and I just didn't know it. Also I downloaded the Debian menu with Automatix, but can't seem to find it anywhere. Does it automatically install in the overhead toolbar of do I have to put it there manually. thanks again ladies and gents--so far a very exciting and smooth experience with Ubuntu.

---

### Post by MkfIbK7a on 2007-01-02
start firefox go to "help" menu and choose "about firefox"

---

### Post by riven0 on 2007-01-02
That'll work, or you can open the terminal and type **firefox -v**

---

### Post by ciscosurfer on 2007-01-02
> **jerrynewt said:**
> Back again for a little more help. How do I find out what version of Firefox is currently running on my comp? I downloaded the tar for 2.0, extracted the files and ran the mozilla-firefox.sh exe file, but nothing seemed to happen. Just trying to see if it installed and I just didn't know it. Also I downloaded the Debian menu with Automatix, but can't seem to find it anywhere. Does it automatically install in the overhead toolbar of do I have to put it there manually. thanks again ladies and gents--so far a very exciting and smooth experience with Ubuntu.Hmm.  If you downloaded FF2.0, then I would assume the version you're running is...2.0 ;)

---

### Post by jerrynewt on 2007-01-02
Thanks for the quick replies. Got so involved in the terminal aspect of this system I forgot about the help tab in firefox (duh). Anyway- any ideas on the Debian menu or is this another obvious solution that I have overlooked? Thanks again

---

### Post by riven0 on 2007-01-02
> **jerrynewt said:**
> Thanks for the quick replies. Got so involved in the terminal aspect of this system I forgot about the help tab in firefox (duh). Anyway- any ideas on the Debian menu or is this another obvious solution that I have overlooked? Thanks again

Okay, go to System >> Preferences >> Menu Layout

Make sure Debian is checked off there.

---

### Post by jerrynewt on 2007-01-02
When I go to System > Preferences there is only Menu and Toolbars, no Menu layout.

---

### Post by riven0 on 2007-01-02
> **jerrynewt said:**
> When I go to System > Preferences there is only Menu and Toolbars, no Menu layout.

:confused: :confused: Alright, how about GNOME Control Center? Can you find it there?

---

### Post by jerrynewt on 2007-01-02
Ok how do I get to the Gnome desktop?

---

### Post by riven0 on 2007-01-02
> **jerrynewt said:**
> Ok how do I get to the Gnome desktop?

No, no, I meant System >> Preferences >> GNOME Control Center


Otherwise, do this to make sure it's really installed:

Go to Terminal: Applications >> Accessories >> Terminal

Copy and paste this: > sudo apt-get install menu

---

### Post by jerrynewt on 2007-01-02
There is no Gnome Control Center under System>Preferences, and it says menu is already latest version.

---

### Post by jerrynewt on 2007-01-02
Not showing Gnome Control Center under System>Preferences so I used the sudo command you gave me--it says "menu is already latest version".

---

### Post by riven0 on 2007-01-02
Oops! I forgot about the easier way. Sorry about that. Just right-click on Applications and choose Edit Menu. It should bring up the menu editor.

---

### Post by jerrynewt on 2007-01-02
Ok it shows the Debian icon on the left side but when I single click on it nothing shows up in the right information  pane.

---

### Post by riven0 on 2007-01-02
> **jerrynewt said:**
> Ok it shows the Debian icon on the left side but when I single click on it nothing shows up in the right information  pane.

Check of the box next to Debian on the *right* pane. Does it show up in your Applications?

---

### Post by jerrynewt on 2007-01-02
Ok checked the box (large info box) to the right of the Debian icon, after selecting Debian, and still nothing in the  pane.

---

### Post by riven0 on 2007-01-02
I don't have Debian menu installed, so I really don't know if any applications are supposed to show up under the menu editor... but when you go to Applications? Is it there?

EDIT: I mean Applications on the top panel of screen.

---

### Post by jerrynewt on 2007-01-02
No nothing under applications regarding Debian at all.

---

### Post by riven0 on 2007-01-02
:confused: Alright, next thing to try. Hit CTRL + ALT + Backspace to log out. Then log back in and check again. Make sure to save any work left open!

---

### Post by jblebrun on 2007-01-02
Assuming that all of your software is installed using a package manager, you can also use synaptic or aptitude to find out what version of a program you have installed. Simply search for the program of interest. Both programs will show you both the installed version and the latest version available. 

Of course, if you are installing things from source, binary installers, or other package types, this method may be inaccurate.

---

### Post by jerrynewt on 2007-01-02
Ok logged out and back in and still no Debian menu under applications.

---

### Post by riven0 on 2007-01-02
Hmm, I just went and did the whole process myself now. I even did **sudo alacarte** and choose Debian through there. You're right; it doesn't show up. All I can think is that there is a bug in the program. 

Otherwise, there is an important step I'm overlooking... anyone?

---

### Post by riven0 on 2007-01-02
*smacks forhead* I'm sorry; there is nothing wrong with Debian. The problem is, you're going to have to manually add in the programs yourself... much different from when I last used it.

So go back to the menu editor, click on Debian, then click add New Item. Add your programs through there.

---

