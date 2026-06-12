---
title: "Screen Resolution Issues"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by kickstart on 2007-07-17
G'day,

This is, no doubt, the first of many posts i shall make here on the Ubuntu Forums. I'm grateful for a place like this, so thanks in advance.

As the thread topic implies, i am having certain screen resolution issues.

Before i get started explaining, you should probably all know that i am running 7,04 and am quite obviously a complete noob to linux. NB: I have a script called "Envy" installed, which as it seems, installs the NVidia drivers relevent to my graphics card. I am running a Geforce 8600GT on an Acer AL2216W (A 22 Inch Widescreen LCD, native resolution is 1680x1050).

Here is my issue:

The default resolution setting appears to be 1024x768, fair enough. I installed Envy, it seems to work fine. I go to System Places --> NVidia Settings --> Server Display Configuration --> 1680x1050 --> Apply --> 'Save to X Configuration File" --> a box appears "/etc/x11/xorg.conf" and a tick box labelled "merge with existing file" (this box is ticked). After clicking OK, i get the following message "Error message: Unable to remove old x config backup file '/etc/x11/xorg.conf.backup'

So that aside, the resolution does change to 1680x1050. MY ISSUE is that when i restart the computer, the resolution returns to 1024x768 as if, and quite obviously, that the setting has not been applied.

How can i fix this issue and ensure that my resolution remains 1680x1050 after a reboot?

Thanks.

---

### Post by _simon_ on 2007-07-17
from terminal:

sudo gedit /etc/X11/xorg.conf

Find the SCREEN section and check that 1680x1050 is listed, if not add it. if it is, try removing the others.

I also used the Envy script but have no problem with my resolution. 

Is your resolution listed in System -> Preferences -> Screen Resolution ?

Here is my SCREEN section:

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7900 GS]"
    Monitor        "Bel2225S1W"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection

```

---

### Post by jordanmthomas on 2007-07-17
You need to find out what command is run when you go to that menu option and run it as root:
right click on the nvidia settings icon and go to add to desktop
Then, right click on the icon on your desktop and look for the command line.
Then, press Alt + F2
type 
```
gksudo whateverthatcommandis
```
make your changes, and you should have permission to overwrite xorg.conf.

Alternatively, you could manually edit your xorg.conf

---

### Post by kickstart on 2007-07-17
This seems verty strange, but when i type the sudo gedit /etc/x11/xorg.conf command in terminal, the box where the file should be appears and in the corner it says 'loading xorg,conf' but then no text appears. Almost as if the file doesn't exit.

Any ideas?

---

### Post by jordanmthomas on 2007-07-17
could you do this in a terminal?
```
ls -l /etc/X11
```
and see if there's an xorg.conf

Also, you should use gksudo gedit instead of sudo gedit

---

### Post by kickstart on 2007-07-17
Thanks Jordan! That worked perfectly:D 

I'm trying to learn about Linux, so could you kindly please explain to me how and why that worked?

Cheers

---

### Post by jordanmthomas on 2007-07-17
Of course...I'll try.  :)
When you use linux you have very limited access to the filesystem.  You can read most things but not write them.  There's a user called root that can do whatever he wants and he owns most files.  You, a puny user, can't mess with his stuff.  However, you can gain access to his stuff by using sudo, su -, gksudo, etc.  These programs elevate your permissions and for a short while you more or less become root and so you own the files you're toying with.  So, when you ran gksudo someprogram, you had permission to edit /etc/X11/xorg.cong (which your user kickstart did not)

Does that help any?  If not, let me know and I'll try again.

---

### Post by _simon_ on 2007-07-17
> **kickstart said:**
> This seems verty strange, but when i type the sudo gedit /etc/x11/xorg.conf command in terminal, the box where the file should be appears and in the corner it says 'loading xorg,conf' but then no text appears. Almost as if the file doesn't exit.

Any ideas?

It's case sensitive. X11 is a capital X, not a lowercse x.

---

