---
title: "Firefox 2 exits when there is a javascript [Resolved]"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by tony2 on 2006-12-18
Firefox 2 exits when 

1. after loging into gmail

3. i click on a page link which contains javascript say for example google videos, youtube etc..

How to rectify this?

No extension is used at present.

---

### Post by aysiu on 2006-12-18
I thought those videos were Flash and not Javascript...

Maybe this might help?
[Solution to flash-related Firefox 2 crash in Edgy](http://ubuntuforums.org/showthread.php?t=286069)

---

### Post by tony2 on 2006-12-18
> I thought those videos were Flash and not Javascript...

videos are flash but they are embedded using javascript.

even while i login to gmail firefox exits immediately. (may be due to the gtalk interface which uses javascript)

---

### Post by aysiu on 2006-12-18
Even though you're saying the problem appears to be Javascript related, these two threads seem to indicate the fix is the same as for the Flash problem:
[firefox crashes on gmail with edgy](http://ubuntuforums.org/showthread.php?t=295220)
[ Edgy Eft and Gmail](http://www.ubuntuforums.org/showthread.php?t=302349)

---

### Post by tony2 on 2006-12-18
the link that you gave doen't help. because they have mentioned to insert a line in the read only file. Though we can insert the code the file cannot be saved because it is a read only file.

how to change to 24 bit color bit ?

---

### Post by aysiu on 2006-12-18
Alt-F2 ```
gksudo gedit /etc/X11/xorg.conf
``` will allow you to edit it with root privileges.

---

### Post by tony2 on 2006-12-18
can you be more clear as to what I should do ?

i tried the gksudo and a text file opened. but could not do anything with it. psl be more specific. thanx.

---

### Post by aysiu on 2006-12-18
It's not an empty text file, though, right? If it's empty, pay attention to your case--it's /etc/X11/xorg.conf, not /etc/x11/xorg.conf.

The file should have a section (may be toward the bottom) related to the screen. Mine looks like this: ```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
**        DefaultDepth    24**
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
``` Notice how my default depth is 24?

---

### Post by tony2 on 2006-12-18
aysiu thanx firefox is now stable. it is only due to flash. i changed to 24 depth and it works well now.

---

### Post by CeeDub on 2007-01-15
My depth was already set at 24, there is no composite option in my x.org file, and I changed firefoxrc.
Javascript now works once per time I open firefox.  The second time a javascript page is opened, firefox crashes.  Any ideas on what I can do?

---

