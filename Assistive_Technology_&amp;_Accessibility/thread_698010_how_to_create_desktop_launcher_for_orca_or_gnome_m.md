---
title: "how to create desktop launcher for orca or gnome magnifier"
date: 2008-02-15
forum: Assistive Technology &amp; Accessibility
---

### Post by RoBo5050 on 2008-02-15
Hello forum members,
 
 I would like to know what commands are necessary to create
a desktop launcher for orca or gnome magnifier??:confused:
I need to know what folder the orca or gnome magnifier reside in.

Thanks in advance for a reply!

---

### Post by Sef on 2008-03-15
> I would like to know what commands are necessary to create
a desktop launcher for orca or gnome magnifier??
I need to know what folder the orca or gnome magnifier reside in.


They would be located in the Universal Access folder under Applications.  Just highlight the program what you want, right click, and the second option is Add Launcher to Desktop.  If you do not have the Universal Access folder under Applications, then click on **Main Menu, highlight Universal Access and click on the program you want**.  It will show up under the Appllications Menu under Universal Access.

Also you may need to go to **System > Preferences > Universal Access > Assistive Technology Preferences** and click on enable assistive technology preferences.

---

### Post by RCC2k7 on 2008-04-02
You can create your own desktop launchers. Right-click on the desktop (Shift+F10 when the desktop has focus) and select Create Launcher.

For Orca fill in:
**Type:** Application.
**Name:** Orca
**Command:** orca
(Note that the command field should be entered in all lowercase, but the Name field can  be capitalized so it looks professional.)
**Description**: Orca screen reader and magnifier.

For the Gnome Magnifier fill in:
**Type:** Application
**Name:** Gnome Magnifier
**Command:** magnifier
(Note that the command field should be entered in all lowercase, but the Name field can  be capitalized so it looks professional.)
**Description:** Gnome screen magnifier

Note that for Orca, you can force magnification, speech and or braille to be on or off when you start the program from the launcher, For example, the command "orca -d braille" will cause Orca to launch always with braille support turned off, while the command "orca - e magnifier" will cause Orca to always enable magnification on startup. This means,nothing is stopping you from creating more than one desktop launcher such as "Orca - Speech Only" and "Orca - Everything Enabled" if desired.

---

