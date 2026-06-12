---
title: "Install from RPM"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by BigNeonGlitter on 2005-09-27
I am a newbie to Linux, and when I say newbie, I mean newbie. I have downloaded software from IBM that runs on Linux, and it's an RPM file. How do I go about installing the software from this file type? Do I have to download some sort of RPM packager utility?? 

Thanks in advance for any feedback ..

---

### Post by matthewv on 2005-09-27
The easiest way to install an RPM is to ensure, using synaptic, that you have alien installed. Once alien is installed, open up a terminal and navigate to the folder where your RPM is located. Type in "sudo alien [name of your RPM]" and press enter. This will create a file with a .deb extension. Run "sudo dpkg -i [name of .deb file]" to install the .deb file. Your software will now be installed.

---

### Post by SilentCacophony on 2005-09-27
Also, from what I remember of alien, it can't do much about dependencies, so you'll have to sort that yourself. In any case, dpkg will spout the packages which a .deb expects, if they are not there.

---

### Post by brentoboy on 2005-09-27
before you go there, you should spend the 13 seconds it will take to make sure there is nothing in the "universe" or "Multiverse" area's of the ubuntu repositories for the same software you have as an rpm.

If it is in there, that version is favorable from an "alien" installer.

I say that becuase the binary will be compiled specifically to match your kernel if you get it from the ub repository.

---

### Post by BigNeonGlitter on 2005-09-27
Thanks for the replies .. I attempted to launch the Synaptic Package Manager and the cursor changes for a second or 2 as if it's about to do something, but then just stops and nothing happens. I have 1GB of RAM and the only other thing running is Evolution and Firefox ..

---

### Post by brentoboy on 2005-09-27
sounds like it is crapping out when it trys to run the app as su.

open a terminal and run 
sudo synaptic

it will ask for your password, and then it will open synaptic.
Dont close the terminal until you are done though, becuase synaptic will be attached to it (kill the mother, loose the baby).

if there is a problem running it from a terminal, at least you will have an error message instead of ... ...

---

### Post by BigNeonGlitter on 2005-09-27
I must be really clueless .. I did as you said, I launched terminal and typed "sudo synaptic". It asked for my password and when I gave it, it just went back to the prompt.

---

### Post by BigNeonGlitter on 2005-09-27
I think I have discovered that my user account didn't have the necessary priviledges. I'm going to try it now ..

---

### Post by matthewv on 2005-09-27
If you only need synaptic to install alien, you can also install alien by typing at the command prompt: "sudo apt-get install alien"

---

