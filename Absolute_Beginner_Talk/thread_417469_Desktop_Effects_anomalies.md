---
title: "Desktop Effects anomalies?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by DanFromWinterpeg on 2007-04-21
Hello,

I just finished a fresh install of Feisty today.  I love the new look and have had a lot of fun with it so far.    I had a heck of a time installing it though.  I have yet to have any success doing an upgrade from a previous release of Ubuntu.  So I have just resigned myself to backing stuff up and doing a fresh install every time.  Besides,  Although my only OS experience before Ubuntu has been several flavors of Windows  I have learned that existing problems tend to tag along after an upgrade so a fresh install is probably best anyway.

Well I have just started adding some new software using Synaptic after playing with the desktop effects and well now all of a sudden for no apparent reason all but one of my workspaces have vanished.  Now if I turn off the effects everything is fine.  When I turn them back on again Ubuntu eats my extra workspaces.  Do I have gremlins on my flashy new install already?  Has anyone else run into this peculiar and mildly annoying problem?

Thanks 

Dan

---

### Post by Happy_Man on 2007-04-21
This is a quirk of the effects; it's quite fixable and is not a bug. First off, go into Synaptic and install "gnome-compiz-manager." Then, go into its settings, and change the number of viewports in the Workspaces tab to whatever you like. Problem solved!

---

### Post by RomeReactor on 2007-04-21
Hi. I ran into the same problem upon doing a fresh install of Feisty; then I installed **gnome-compiz-manager** and fiddling with it's settings on its workspaces tab solved the issue.

**EDIT**: Damn you Happy_Man! I'll thwart you yet...

---

### Post by DanFromWinterpeg on 2007-04-21
Thanks a million.

That was easy.  This is SO COOL!  I am having way too much fun tweaking my new install.  I am a bit surprised I cannot get my refresh rate above 60 though.  Probably just need to play with the driver a bit.  Then again with the LCD I find this is not so much an issue anyway.

Thanks again.

Dan

---

### Post by Ricbuntu on 2007-06-10
I was looking to increase my number of available workspaces, and followed the above mentioned advice.

After downloading compiz, I was able to increase the number of workspaces, but a couple of things did happen:
a) When GL Desktop (compiz) was activated, all my windows were fully maximised. It was either that, or fully minimised in the taskbar. The title bar with the control buttons on the top right was not visible. Is there a way to disable this "feature" !? It'd be nice to control the window size of my windows...
b) I turned GL Desktop off, then turned it on again, and got a black screen. My mouse pointer was still active and visible, but thats all I could see. Hence I had to do a power off/on restart to get things back to normal. Anyone else had this issue ?

I'd prefer not to use compiz, so is there any other way of increasing the number of available workspaces without the use of compiz ?

Thanks :)

---

### Post by Ricbuntu on 2007-06-10
Okay I found the solution to my problem !

Right-click in the workspace areas, and choose Preferences... It has an option to increase the number of workspaces (and even give each one a unique name). Pretty cool !

---

### Post by PlainShane on 2007-06-10
Via synaptic package manager "gnome-compiz-manager" is not even a choice... Where do I get that? Also, should I be running all of this in Gnome +XGL session?

---

