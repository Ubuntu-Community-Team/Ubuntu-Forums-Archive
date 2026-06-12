---
title: "Login screen - resolution"
date: 2005-05-29
forum: Absolute Beginner Talk
---

### Post by heltinde on 2005-05-29
Hi

I'm using a small monitor so 800*600 is optimal. But the login screen is 1024*768, and it makes everything so very small. Can I change that?

Lise

---

### Post by jobezone on 2005-05-29
[QUOTE=heltinde]Hi

I'm using a small monitor so 800*600 is optimal. But the login screen is 1024*768, and it makes everything so very small. Can I change that?

Lise[/QUOTE]
 I'm assuming you're using Ubuntu Hoary:

go to a command line and run:

```

sudo dpkg-reconfigure xserver-xorg

```

This, like the name of the command hinted, will reconfigure x.org, responsible for your graphic card, keyboard, mouse and monitor in linux.
Many question will be asked about your graphic card, mouse, keyboard. Just leave them as they are, so you don't change what already was automatically configured and detected for you. You'll eventually come up to a question:
"Select the video modes you would like the X server to use."
In this screen, deselect the resolution 1280*1024 , while keeping 800*600 .
Go on until it finishes.

You can also acess this reconfiguration screen using Synaptic. Choose a package that you have installed, and click on the menu Package->Configure . Not all packages have this configuration possibility, and a quick way to see which do would be to click Filters->"Packages with Debconf" .

Checkout [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by heltinde on 2005-05-30
Thanks Jobezone.

It's not exactly the solution I hoped for - I was thinking more of an easy way to switch between the installed resolutions, just like I can inside Gnome. I'm a bit surpised it didn't affect the login screen. If I end up using the small monitor permanently, I'll do it your way.

I have printed out your answer, because it contained so much nice information I can use for other purpuses. Now I suddently know what filters can be used for, and also what debconf means  :smile: 

Lise

---

### Post by jobezone on 2005-05-30
There is no graphical way to choose the resolution of GDM as such, and so I figured this would be the simplest method (that I know of).

Also, you could change the video modes like I said, and if you get a bigger monitor in the meanwhile, you would just re-run the configuration for xserver-xorg and choose more resolutions.

Yes, I also only discovered this in the last months with ubuntu. I was using debian before, but didn't use as much synaptic. But now, it seems to me to be a very powerfull tool. One can do all of the actions the package manager system allows us, like block a certain version of a package (so it doesn't get upgrade, ou removed), find orphaned packages (unecessary packages which were installed as dependencies of another package which has later been removed)(this filter isn't pre-configured, you have to install "deborphan" and create a new filter and check the option "orphan"), see the changelog of upgrades (changes between new and present version),etc. 
Have fun in linux, and if you have questions you can't work out for yourself and the unfortunately somewhat scattered documentation, you're free to ask  :)

---

### Post by heltinde on 2005-05-30
Again - thank's Jobezone. I really like the information you provide me with. I was beginning to think about all the extra packages I don't need on my system. It would have taken me about forever to figure out the word 'deborphan'  ;-)

---

### Post by jobezone on 2005-05-30
Well, you want more? 

You can reconfigure debconf itself. It allows you to change the kind of questions you made to you by packages (if you're new to linux, I would recommend leave the current option as it is, so you are not overwhelmed with questions. Or if you're curious, decrease the the level of questions being made to you), and how they are presented to you (Dialog is the default used, but you could use Gnome interface. If you set it like this, it uses a Gnome interface if it can, or goes to Dialog if no graphical screen is present, if, for example, you are in a Virtual Terminal (hint, press Ctrl+alt+F1 . To get back to the desktop, press Ctrl+alt+F7, or Alt+[left arrow] or Alt+[right arrow] some times until you reach it)).

---

### Post by eismann on 2005-06-14
[QUOTE=heltinde]Hi

I'm using a small monitor so 800*600 is optimal. But the login screen is 1024*768, and it makes everything so very small. Can I change that?

Lise[/QUOTE]I have had the same problem.
While installing Ubuntu, I added 1280x1024 for future use with my 19" TFT,
along with 1024x768, 800x600 and 640x480.

1280 became the inital resolution for the login screen and X11/Gnome Desktop.
I could easily change the Desktop resolution to 1024x768 using menu
system - preferences - resolution.
But the login screen kept on using 1280x1024. Which is far too small for my 
current CRT monitor.
And it would nice if the login screen would be in a reasonable resolution
for users with restricted sight, too.

I solved the problem by changing the order of the resolution in
 /etc/X11/xorg.conf Section "screen":

```
SubSection "Display"
    Depth  24
    Modes  "1024x768" "800x600" "640x480" "1280x1024"
EndSubSection
``` Regards
. . . Dirk Eismann

---

