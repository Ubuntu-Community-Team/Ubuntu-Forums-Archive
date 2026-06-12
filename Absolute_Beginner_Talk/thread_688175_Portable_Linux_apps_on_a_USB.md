---
title: "Portable Linux apps on a USB"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by AAM on 2008-02-05
I am looking at a project to develop a solution for medical practitioner use. Becasue of the wide availability of Firefox and its XUL language, I was intending to focus on using Firefox with a custom extension. 

I thought of having 3 folders containing:
[LIST=1]
[*]a Windows executable (Portable Firefox)
[*]a linux version of Firefox
[*]a MacOS version of Firefox[/LIST]with the extension and data components housed within the OS-agnostic tree structure of Firefox, so that all OS version use the same chrome directories while running natively within the resident OS. Don't want to use WINE.

Is this possible? Do Autopackage or Klik have any potential in this?

---

### Post by LowSky on 2008-02-05
the mac and linux version might run simular but the windows version has different file parameters. its the only snag i can see

---

### Post by MasterXandrex on 2008-02-05
There is a portable version available already for Windows that you might want to try. I don't suppose it would be that difficult to do yourself. Check this FAQ: [http://www.mozilla.org/support/firefox/profile#move]("http://www.mozilla.org/support/firefox/profile#move")

Anyway the Windows version of Firefox is available at [http://www.portableapps.com]("http://www.portableapps.com"). I currently use it on my flash drive with no problems -- auto-updates just like the normal version.


Xan

---

