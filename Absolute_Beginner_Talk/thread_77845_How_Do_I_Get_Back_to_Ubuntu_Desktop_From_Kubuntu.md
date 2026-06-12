---
title: "How Do I Get Back to Ubuntu Desktop From Kubuntu?"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by screamingFit on 2005-10-17
Was following an instruction in the ubuntuguide to reset gnome-panel after installing an app (think it was : killall gnome-panel or something like that).  Well, I type that command in and lost all the gnome panels and they never came back.  Not really knowing what to do, I pressed CTRL+ALT+BACKSPACE to kill X.  Now, at the login, there's no option to choose a Gnome desktop other than "Failsafe" - and trying that brings up an error about Gnome not being found and it throws me into a terminal window.  I have tried every option from the login panel and they all throw me to KDE.

Is there anyway back?

---

### Post by Ampersand on 2005-10-17
Log in to KDE, and open Synaptic. If you install the ubuntu-desktop package, you should get Gnome back.

---

### Post by screamingFit on 2005-10-17
[QUOTE=Ampersand]Log in to KDE, and open Synaptic. If you install the ubuntu-desktop package, you should get Gnome back.[/QUOTE]

Thanks!  That worked!

Does anyone have a reason why this happened - a package (and a pretty important one!) being blown away like that?

---

### Post by poofyhairguy on 2005-10-17
[QUOTE=screamingFit]Thanks!  That worked!

Does anyone have a reason why this happened - a package (and a pretty important one!) being blown away like that?[/QUOTE]


ubuntu-desktop is not actually that important. But when you installed it it brought with it other important packages that fixed your machine. By itself it does nothing really.

---

### Post by ecobuntu on 2005-10-17
Yeah ubuntu-desktop is a virtual package.  That's why if you remove a gnome package ubuntu-desktop goes with it.

---

### Post by screamingFit on 2005-10-18
Well, I find that a bit crazy.  You kill a process and it takes the whole desktop with it permanently (well, until you reinstall it)?

Thank jeebus I still have my Macs to fall back on!

---

