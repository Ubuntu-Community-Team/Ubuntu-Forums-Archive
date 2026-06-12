---
title: "Cant install audio/video codecs - conflict?"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by NeptuneUK on 2007-08-23
"This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."

I haven't installed any previous audio or video codecs as I cant play videos!

---

### Post by Daveth on 2007-08-23
what is the "this application" that gives you that message?

---

### Post by NeptuneUK on 2007-08-23
Any kind of codec or media player I select from the add/remove list

---

### Post by NeptuneUK on 2007-08-23
Just tried to install a game and got the same error, that's not normal!

---

### Post by eapache on 2007-08-23
No, it isn't normal. Please go into System>Admin>Synaptic and try and install the plugins. Then please post the more detailed error.

---

### Post by NeptuneUK on 2007-08-23
Example, I click  'gstreamer0.10-plugins-ugly' then I get:


Cannot install 'gstreamer0.10-plugins-ugly'

This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

---

### Post by eapache on 2007-08-23
Please switch to the synaptic package manager (under System>Administration>Synaptic Package Manager) and try to install the same package. It will tell you which programs are conflicting. Please list those programs here.

---

### Post by NeptuneUK on 2007-08-23
Says:

the following packages have unresolvable dependancies:


gstreamer0.10-plugins-ugly:
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable



I cant see why I have this issue on my current PC but not on my other installation upstairs :S

---

### Post by eapache on 2007-08-23
Please try and install both of those packages that it says are 'uninstallable' and post the more detailed error message you will get from trying to install them directly.

---

### Post by NeptuneUK on 2007-08-23
Ah, these packages seem to be missing from the package manager!  Hmm

---

### Post by eapache on 2007-08-23
Please go into System>Administration>Software Sources, and make sure that the universe and multiverse repos are enabled.

---

### Post by NeptuneUK on 2007-08-23
It seems they are enabled yes.
Might have to format and reinstall....... :\

---

### Post by eapache on 2007-08-24
Just one more thing to try. In Synaptic, press the 'reload' button in the toolbar, and take another look for the packages you couldn't find.

If that doesn't work, it would seem that something is corrupted. If you have the cd you originally installed from, please run the auto-verification option to see if that could be the case.

---

### Post by rase on 2008-03-03
Hi,

All you have to do is:
Synaptics Pakage Manager>Settings>Repositories>Downloadable from the Internet.
Make SURE everyone is added to be able to download from.
Then do the search: libid3tag0 and libmad0.
that it is!
enjoy!

---

### Post by juky on 2008-03-09
Thanks all for support. It worked for me!

---

### Post by Dylock3 on 2008-03-14
Thanks on my part too, worked for me!

Why is Synaptic conflicting with Add/Remove Applications?  I may not understand this right.  Theoretically it should be simplified for not so savvy users like myself.

---

