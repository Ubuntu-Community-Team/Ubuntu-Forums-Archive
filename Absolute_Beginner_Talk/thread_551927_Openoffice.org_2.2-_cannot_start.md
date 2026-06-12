---
title: "Openoffice.org 2.2- cannot start"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by MasterRoshi on 2007-09-15
hey guys. everytime i try to open openoffice, it says "The application cannot be started. An internal error occured."

i tried to run a terminal line of "openoffice" and it said this:

root@me-Laptop:/home/brad# openoffice
The program 'openoffice' is currently not installed.  You can install it by typing:
apt-get install openoffice.org-common
bash: openoffice: command not found

i then went and ran that line. it told me that it had installed, and everything went well. i rebooted, and ran the terminal line again. it said the same error listed above. i went into synaptic, installed all the things that were previously installed, and then rebooted. it gives me the same error, like a cycle. 

anyone have any ideas? ive read a few forums and couldnt find anything on it...

thanks!

---

### Post by Maestro23 on 2007-09-15
Open terminal and try:

> soffice

---

### Post by crmccreary on 2007-09-15
From the terminal you can execute the openoffice suite with soffice (harks back to when it was called star office).  Is Openoffice in your Applications/Office menu?

---

### Post by MasterRoshi on 2007-09-15
it is in my aps menu. when i type soffice in, this is the error message that comes up:

root@me-Laptop:/home/me# soffice

(process:5976): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:5976): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:5976): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:5976): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:5976): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:5976): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:5976): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:5976): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed


any ideas? this is a problem. i wish i knew what was going on...it doesnt do this to me on my desktop...and typing "soffice" is the only way it will open. ='(

---

### Post by Hagar Delest on 2007-09-16
Try to rename or delete your OOo user profile : ~/.openoffice.org2

---

### Post by MasterRoshi on 2007-09-17
> **Hagar de l'Est said:**
> Try to rename or delete your OOo user profile : ~/.openoffice.org2

sorry i didnt say i was kinda new to this...

call me a n00b but how? lol

wow. probably something right in front of my face and i cant even see it. i dont think i even MADE an OO profile on there...but in synaptic i did the "complete" removal of all packages. if that means anything.

uhh...yea. is there a terminal line or what?

i feel lame lol. thanks for the help
=]

---

### Post by Hagar Delest on 2007-09-17
Open Nautilus, show the hidden files and delete the folder called .openoffice.org in your home directory.

---

### Post by tonymoloney on 2007-09-17
I was having a problem with 2.2 in that the splash screen would come on and then the application would hang. When I went to shut down the system, the splash screen would be the last thing to go.
I fixed this by going to Add/Remove Programs and installing the latest version.
This now comes up as 2.x Developer Snapshot, but everything works.

---

### Post by MasterRoshi on 2007-09-20
alright i did the OOo profile thing under nautilus (As root), and rebooted. then i reinstalled OO in Add/Remove as suggested above. still the same error. this is really weird..

think i should try just downloading a tarball from openoffice.org?

---

