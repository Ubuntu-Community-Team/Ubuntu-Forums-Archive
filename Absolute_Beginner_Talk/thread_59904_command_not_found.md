---
title: "command not found"
date: 2005-08-25
forum: Absolute Beginner Talk
---

### Post by noam on 2005-08-25
Hello All,

Recent convert to the ubuntu scene. Having a problem that I could not turn up in the forums. 
I'm running Hoary and tried to install a few apps via synaptic.

Mondo,Konserve ,Kaffeine to be specific. Download and installation appeared to go ok. Usually apps install an Icon
or command in the menu or typing the name of the app
in a terminal will start it.  In my case neither. The response is "command not found". I'm sure there is a common factor aside from the obvious I don't know what I'm doing.

Any help would be appreciated.....thanks

---

### Post by cwaldbieser on 2005-08-25
[QUOTE=noam]Hello All,

Recent convert to the ubuntu scene. Having a problem that I could not turn up in the forums. 
I'm running Hoary and tried to install a few apps via synaptic.

Mondo,Konserve ,Kaffeine to be specific. Download and installation appeared to go ok. Usually apps install an Icon
or command in the menu or typing the name of the app
in a terminal will start it.  In my case neither. The response is "command not found". I'm sure there is a common factor aside from the obvious I don't know what I'm doing.

Any help would be appreciated.....thanks[/QUOTE]
The name is case sensetive (usually all lowercase) and must be an exact match.  Try typing the first couple letters and then hitting tab.

Alternatively, in synaptic, choose the package, press the Properties button, choose the Installed Files tab on the dialog, and then look for files that were installed in /bin, /usr/bin, /usr/local/bin, or /sbin.  One of them is probably the one you want to run.

---

### Post by Kyral on 2005-08-25
Looks like you need the Debian Menu. Its a nifty little "catchall" for the programs that aren't completely GNOME complient (*cough*KDE apps*cough*)

[http://www.ubuntuforums.org/showthread.php?t=32220](http://www.ubuntuforums.org/showthread.php?t=32220)

I'm sure those apps will show up SOMEWHERE in that menu (You gotta look. K3b showed up in the "System" menu)

---

### Post by noam on 2005-08-26
That did the trick.  thanks for the help guys........

---

