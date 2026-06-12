---
title: "awn stack applet problem"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by rimi on 2008-03-02
Hi everybody,
                    I installed AWN in my ubuntu linux without any problem. But it does not load stacks applet on the pent showing the following error,

LOADED : /usr/share/applications/gcalctool.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/main-menu.desktop
APPLET : /usr/lib/awn/applets/stacks.desktop
python: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
Please inform the developer(s) of the applet 'Stacks Applet' that the .desktop file associated with their applet need to be updated per the Applet Development Guidelines on the AWN Wiki

Can anybody please help.


Thanking you in ahead
Rimi:(

---

### Post by igknighted on 2008-03-02
Did you try installing the library it is asking for (libstdc++)?

---

### Post by rimi on 2008-03-02
Hi 
Thanks for the reply. I checked with synaptic managet I have alreadi libstdc++6 installed in the system.

---

### Post by igknighted on 2008-03-02
do you have libstdc++-5? There are a whole bunch of these compatibility libraries.

---

