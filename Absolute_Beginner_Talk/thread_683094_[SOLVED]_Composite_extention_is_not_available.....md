---
title: "[SOLVED] Composite extention is not available.... ???"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by toastysquirrel on 2008-01-30
I've been trying to install AWN, or rather I've been trying to **run** AWN, but to no avail.  From looking around the forum it seems like it has something to do with Compiz.  Again, I looked around the forum and found a thread that pointed someone else to [this guide here]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion"), and I installed the [COLOR="Blue"]compizconfig-settings-manager[/COLOR] and dependencies, but I'm still getting the Composite Extension is not Available.  I'm using the restricted vdieo drivers for my ATI card if that makes any difference.

Any ideas?  Again, my ultimate goal is to get AWN up and running.  The AWN manager works, but not the app itself.

Thanks everyone!

---

### Post by jan quark on 2008-01-30
you have to install

xserver-xgl

from the synaptic package manager

then you have to log out and select the xclient session

of course you have to have compiz installed too

after installing the things above you should be able to install the awn

---

### Post by toastysquirrel on 2008-01-30
> **jan quark said:**
> you have to install

xserver-xgl

from the synaptic package manager

then you have to log out and select the xclient session

of course you have ti have compiz installed too

after installing the things above you should be able to install the awn
Thanks for the info Jan :)

[COLOR="Silver"]-Check on xserver-xgl. [/COLOR]
-As for Compiz, do you know what the package name for that is, or how I would tell if it's already installed?
-XClient...? Is this something I'll have to change every time I log in? I'm (currently) totally unfamiliar with it.

---

### Post by jan quark on 2008-01-30
dont mention it
tell me rather if everything works fine :lolflag:

---

### Post by tangibleorange on 2008-01-30
Hey there,

I originally had this problem with the ATI restricted drivers and the composite extension error message when I was trying to enable desktop effects. My solution was to edit my xorg.conf file:

> sudo gedit /etc/X11/xorg.conf

Scroll down until you find these two lines (there might be more):

> Section "Extensions"
   Option	"Composite" "0"

And change the "0" to "On". The "0" might say "Off" I don't know. Anyway good luck as that worked for me!

---

### Post by toastysquirrel on 2008-01-30
Is this the [compiz ]("http://packages.ubuntu.com/gutsy/x11/compiz-core")that I need?  If not, how can I tell? :)

---

### Post by tangibleorange on 2008-01-30
Compiz Fusion is already installed in Gutsy by default. I think you can check by going into Synaptic, searching for "compiz-core" and it should come up as already installed...

---

### Post by jan quark on 2008-01-30
yes stupid me
compiz is pre installed

just install the xserver-xgl as mentioned above

---

### Post by toastysquirrel on 2008-01-30
> **tangibleorange said:**
> Hey there,

I originally had this problem with the ATI restricted drivers and the composite extension error message when I was trying to enable desktop effects. My solution was to edit my xorg.conf file:



Scroll down until you find these two lines (there might be more):



And change the "0" to "On". The "0" might say "Off" I don't know. Anyway good luck as that worked for me!
Okay, I seem to be making *some* progress.  I changed "0" to "On" and now I get a message "Desktop Effects could not be enabled" after the system sits and things for about 3-5 seconds. (I also tried changing the value to "1", which gave me the same result).

---

### Post by jan quark on 2008-01-30
did you installed xserver-xgl as I have mentioned above ?
and changed the session to xclient?

---

### Post by toastysquirrel on 2008-01-30
> **jan quark said:**
> did you installed xserver-xgl as I have mentioned above ?
and changed the session to xclient?
Yessum.  xserver-xgl was already installed (and I just double-checked to make sure).  then I logged off, at the logon screen I clicked on "Options // Session // "Run xclient script"" then logged on and once again tried to enable visual effects.  That's when I get the "Desktop effects could not be enabled" :-k

---

### Post by toastysquirrel on 2008-01-30
Okay, I think I may have narrowed down the problem, though I'm no closer to actually solving it.  I lurked around the forum some more and I found a reference to the command "compiz --replace".  I ran that from terminal and I got the output:

```
Checking for Xgl: not present
No whitelisted driver found
Aborting and using fallback: /usr/bin/metacity

```
I checked in Synaptic and "xserver-xgl" is present.  I even manually reinstalled the package, rebooted, but still ran into the same issue.  My Ubuntu box is offline so I do all my installs via Nonetdebs which has an up-to-date version of my "status" file.  However when I plugged in xserver-xgl, in stead of telling me that it was already installed, it gave me a link to download it, and its two dependencies (which I already have installed).

```
http://archive.ubuntu.com/ubuntu/pool/main/g/glitz/libglitz1_0.5.6-1_i386.deb
http://archive.ubuntu.com/ubuntu/pool/main/g/glitz/libglitz-glx1_0.5.6-1_i386.deb
http://archive.ubuntu.com/ubuntu/pool/universe/x/xserver-xgl/xserver-xgl_1.1.99.1~git20070727-0ubuntu3_i386.deb
```

Maybe this will help out a bit.  :confused:

---

### Post by tangibleorange on 2008-01-31
Hey again,

Good to see we've made some progress. I seem to remember also getting this error, and the problem was again down to that damned xorg.conf file! I think it was trying to use the wrong driver:

> sudo gedit /etc/X11/xorg.conf

Locate these two lines:

> Section "Module"
	Load		"fglrx"

And make sure that says exactly "fglrx". I seem to remember this was causing the problem last time.

Good luck!

---

### Post by toastysquirrel on 2008-02-01
> **tangibleorange said:**
> Hey again,

Good to see we've made some progress. I seem to remember also getting this error, and the problem was again down to that damned xorg.conf file! I think it was trying to use the wrong driver:



Locate these two lines:



And make sure that says exactly "fglrx". I seem to remember this was causing the problem last time.

Good luck!
Unfortunately no luck, though I did have to change it.  Initially Load was set to "glx", so I changed it, saved the document, and restarted Gnome (ctrl-alt-backspace) to no avail.  When I set the Visual Effects to "normal" or anything else, it pauses, thinks about it, looks like it's about to accept it, then spits out the same effort "Desktop effect could not be applied".

Any other ideas <asks hopefully :) >

---

### Post by tangibleorange on 2008-02-07
It says there the driver is blacklisted. You could try editing your compiz file:

> sudo gedit /usr/bin/compiz

Find the lines with this text on:

> # Driver whitelist
WHITELIST="fglrx"

And check (again) that it says exactly "fglrx". You never know, it just might work!

---

### Post by toastysquirrel on 2008-02-08
It appears that the problem with getting the effects to work is now behind me; so it seems.  I got the idea from another thread to spontaneously re-enable XGL (something that before had been causing my systems rendering of *anything* to take forever) and it seems to have fixed everything.

:confused:

I really don't get it because as far as I can tell, I haven't done anything different then the previous times I was using fglrx and enabling XGL... although now I do have compiz installed so maybe that allowed fglrx and xgl to work peacefully?  <shrug>  Well, it's working, for now.

Thanks for you help everyone, especially you Tangible; I really appreciate it (!!).

---

### Post by tangibleorange on 2008-02-08
Glad to be of help! Glad you got it working :).

---

