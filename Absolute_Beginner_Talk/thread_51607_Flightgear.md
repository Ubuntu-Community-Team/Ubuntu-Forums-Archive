---
title: "Flightgear"
date: 2005-07-24
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-07-24
Hi!

I've ticked and let Synaptic install Fightgear. Yet when i run flightgear from 'RunApplication' what i get back is Error Cannot display location 'file://flightgear'

Details: There is no default action associated with this location

Can anyone explain this to me and its implication?

From command line i have gone:

conrad@x1-6-00-0b-6a-16-78-f0conrad:/usr/share/doc/flightgear$ ls
AptNavFAQ.FlightGear.html  README.fgjs           README.protocol
AUTHORS                    README.gui.gz         README.running.gz
changelog.Debian.gz        README.introduction   README.SimGear
changelog.gz               README.IO.gz          README.sound
copyright                  README.IRIX           README.src
FlightGear-FAQ.html        README.Joystick       README.TerraSync
NEWS.gz                    README.JSBSim         README.uiuc.gz
README                     README.jsclient       README.Unix
README.autoconf            README.Linux.gz       README.Win32-X
README.commands.gz         README.logging        README.xmlhud.gz
README.conditions.gz       README.MacOS          README.xmlpanel.gz
README.Cygwin              README.MSVC           README.xmlsound.gz
README.Debian              README.multiplayer    README.xmlsyntax.gz
README.electrical.gz       README.plib           Thanks.gz
README.extensions          README.properties.gz


but i don't know how to access any of these READMEs or how to make sense from it,

any help/advice appreciated,

sophtpaw

---

### Post by charlieg on 2005-07-24
To access the READMEs is easy, either use 'less' (or another console tool) to read it in a terminal by doing 'less path/to/README' or open up GEdit or your favourite desktop editor and load a README by browsing to the directory and selecting it like any other file.

It seems like the menu entry isn't configured correctly.  What happens if you run flightgear from the console?  The command to load it is probably just 'flightgear' although, if not, should be listed in /usr/games/bin - you already know how to use 'ls'. ;)

---

