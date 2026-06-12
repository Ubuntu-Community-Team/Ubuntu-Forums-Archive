---
title: "i want to understand how to fix broken packages"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by girard on 2007-07-07
hi. i understand a little that whenever there are broken dependencies, that means that you are lacking something in your system. but just how exactly do i figure out how to get those.

this is coming from my attempt to install skype using apt. i saw a guide on how to do it via synaptic, but i'd like to learn how to do it on the terminal.

i get this

> 
 sudo dpkg -i skype-1.4.0.74.deb
Selecting previously deselected package skype.
(Reading database ... 107738 files and directories currently installed.)
Unpacking skype (from skype-1.4.0.74.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libasound2 (>> 1.0.12); however:
  Version of libasound2 on system is 1.0.11-7ubuntu3.
 skype depends on libqt4-core (>= 4.2.1); however:
  Version of libqt4-core on system is 4.2.0-1ubuntu6.
 skype depends on libqt4-gui (>= 4.2.1); however:
  Version of libqt4-gui on system is 4.2.0-1ubuntu6.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype


i understand that i don't have the new version of the lib* mentioned. how do i get them? example:

should i simply apt install libasound2 and that's it? simply include in the command everything before the parentheses? how do i know which numbers to include? should it be like libasound2_1.0.12? meaning i just add the "version"?

i also tried to install libqt3-mt

> 
 sudo aptitude install libqt3-mt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  skype 
The following NEW packages will be installed:
  libqt3-mt 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3138kB of archives. After unpacking 8921kB will be used.
The following packages have unmet dependencies:
  skype: Depends: libasound2 (> 1.0.12) but 1.0.11-7ubuntu3 is installed.
         Depends: libqt4-core (>= 4.2.1) but 4.2.0-1ubuntu6 is installed.
         Depends: libqt4-gui (>= 4.2.1) but 4.2.0-1ubuntu6 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
skype

Score is -299

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.


got scared so i aborted it. (i have work on this pc... hehe)

can anyone explain this for me please.  or a nice, short tutorial to understand how this works would also be nice. 

i know i can research this, but help would make it faster and not so overwhelming. thanks a lot!!! :)

---

### Post by robertc36 on 2007-07-07
I think skype is avaible through automatix and that should sort any dependencies.
Kudos for compiling.
You can search in the terminal
>  sudo apt-cache search 
 other command is > sudo apt-get install 

---

### Post by girard on 2007-07-09
got it already. i was able to install it but with broken dependencies. can't remember them all but they were something like libqt3, etc...

it worked well after i upgraded to fiesty fawn. maybe because i got the new skype and the dependencies weren't available for edgy... i dunno really. but i'm using it now!!! thanks. now i can stay on the desktop instead on the notebook!

---

