---
title: "Having trouble installed firefox2"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by synt4xerr0r on 2006-12-09
I am a n00b in linux i got ubuntu 2 days ago and i am not dualbooting bcuz i hate micro$hit

Can any1 explain to me how to install firefox2 i am using dapper 6.10

---

### Post by Frak on 2006-12-09
It should come preinstalled on Edgy (6.10)
EDIT
Or use the instructions [here]("http://psychocats.net/ubuntu/firefox"). (Thank Aysiu for those)

---

### Post by synt4xerr0r on 2006-12-09
> **Frak said:**
> It should come preinstalled on Edgy (6.10)
EDIT
Or use the instructions [here]("http://psychocats.net/ubuntu/firefox"). (Thank Aysiu for those)

thankyou so much!

and for those to lazy to click on the link here :D 

>  Installing Firefox on Ubuntu

Methods for Installing Firefox
Firefox comes standard as the default browser on Ubuntu and Xubuntu. If you're using Kubuntu, you can install Firefox using Add/Remove Programs, Adept, or this terminal command:
sudo aptitude update && sudo aptitude install firefox

If you want the newest Firefox, you have several options:

   1. Stick with the regular Ubuntu version of Firefox. Patches usually come in a few days or a week after being released by Mozilla.
   2. Install a helper program called Automatix that helps you easily install Firefox and a whole bunch of other popular programs, plugins, and other goodies.
   3. Install the Mozilla version of Firefox (which is self-updating) manually, following these instructions
   4. Download this [script]("http://pykeylogger.sourceforge.net/installnewfirefox.sh") to your desktop and paste these commands in the terminal:
      cd ~/Desktop
      chmod +x installnewfirefox.sh
      ./installnewfirefox.sh

What's so special about the script?
A very basic version of the script was created by Ubuntu Forums member aysiu as just a collection of the commands available through the third method--in order to save some copying and pasting.

Ubuntu Forums member nanotube then added a successive number of sophisticated changes to the script (which aysiu helped to test). In its current incarnation these are its features and improvements:

    * Automatically downloads whatever the latest version of Firefox is that's available
    * Allows you to choose which locale you want, based on your geographic location and language of choice
    * Verifies the integrity of the download
    * Integrates with the plugins you install through Synaptic, Adept, or aptitude; also checks what version of Ubuntu you have in order to use the proper path to the plugins
    * Exits if a command was not completed successfully
    * Makes a date-stamped back-up of your Firefox preferences before installing the Mozilla build of Firefox 

Removing Firefox
If you used the third or fourth method to install Firefox and now want to uninstall the new Firefox (revert to the old version), download this script to your desktop and paste these commands in the terminal:
cd ~/Desktop
chmod +x removenewfirefox.sh
./removenewfirefox.sh

---

### Post by helmeteye on 2006-12-09
synt4xerr0r.  Is that all you have to do, is download that script and paste those commands in the terminal?  I did that but have no idea that it has done anything.  I am sure I had the latest version, but, I wanted to see what would happen doing it that way.  On a side note, what is up with swiftfox?  Is swiftfox better than firefox.  Is SF made as a linux version of firefox or what?  What is the deal and what is the difference?

---

### Post by Frak on 2006-12-09
Swiftfox is a version of Firefox made JUST FOR the Processor Archetecture you are using, IE, I have a P4 HT, so when Swiftfox installed, it installed a P4 HT Firefox Core, swiftfox runs off of the firefox you currently have on your system, but uses the parts of FF that will make it go faster, not slower, this effect may be felt on some computers not all, if your computer is already fast, (like a wild dog, system76 computer) you don't need swiftfox, because FF is already running as fast as possible.

If that did not clarify as an answer please post again, so I can explain more if needed.

---

