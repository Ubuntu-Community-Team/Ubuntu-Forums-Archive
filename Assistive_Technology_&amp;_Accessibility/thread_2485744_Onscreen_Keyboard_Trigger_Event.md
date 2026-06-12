---
title: "Onscreen Keyboard Trigger Event?"
date: 2023-04-07
forum: Assistive Technology &amp; Accessibility
---

### Post by j630-io on 2023-04-07
Edit: This appears to be an issue on X11 only.  I am using X11 for a reason so please consider that thanks.

Hello, I am developing an assistive application that runs on Ubuntu Jammy.  I have disabled onscreen keyboard in accessibility.   A python/tkinter app that presents two buttons somehow triggers the onscreen keyboard to appear and I have no idea why or how to control it.

Do you have any recommendations beyond this setting below?  I added this to the shell script that runs the python/tkinter app and it still triggers onscreen keyboard when touch is enabled.

Any other suggestion to keep the onscreen keyboard suppressed?  This user and application will never need it.  

[COLOR=#A6ACCD][FONT=&amp][COLOR=#ffcb6b]gsettings[/COLOR] [COLOR=#c3e88d]set[/COLOR] [COLOR=#c3e88d]org.gnome.desktop.a11y.applications[/COLOR] [COLOR=#c3e88d]screen-keyboard-enabled[/COLOR] [COLOR=#f78c6c]false[/COLOR]

[/FONT][/COLOR]

If removing the onscreen keyboard modules isn't practical what can I add to the shell script or python/tkinter app to suppress it some other way??

Thanks

---

