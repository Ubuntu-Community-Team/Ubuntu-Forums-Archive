---
title: "Installation woes on mac with ati x800 xt"
date: 2007-04-04
forum: Apple PPC Users
---

### Post by dafriis on 2007-04-04
Hi,

I will try to explain this as well as possible. I haven't used Linux for that long and I've had so many errors along this path that it's hard to remember them all.

I have a dual 2.5 GHz ppc with an ati x800 xt card. I've tried to install 6.10, both regular and alternate and the beta feisty too (no alternate version what I've seen).

When installing I don't get that nice brown theme but some white text on a black background. I've tried every boot option there is and the one that worked was (on 6.10 alternate) live-nosplash video=ofonly.
Any other option gave me a black screen and after a while my monitor turned off and the fans started roaring.

After rebooting the monitor dies again after a few seconds. I've seen in a lot of forums that there's problems with ati cards and I've tried every solution I've found here and on google.
I have switched "ati" in xorg.conf to "radeon" and "flgrx". Radeon didn't work at all and if I set it to flgrx it complained about the module not being installed. I can't install flgrx either since it says the package can't be found. (using apt-get).

Some people says they have had better luck with 6.10 and some with 7.04. None of the versions have worked for me. 6.10 could be installed but the monitor is just black. 7.04 can't even be installed.

After having browsed my fingers numb I'm wondering, CAN ubuntu be installed on a mac with an ATI card, and shouldn't an untouched system work and not complain about not being able to retrieve apt-get packages?

I've seen lots of people complaining on ATI for this situation but I HAVE seen other OS's being able to use their cards....

---

### Post by ZoiaGuyver on 2007-04-06
I can tell you of some of the problems to do with ATI cards is mainly the DRI setting in xorg.conf, ive found none of the ubuntu varients can install a desktop with this enabled but there are workarounds for it after you get a working xorg.

The reason apt-get cant or wont install the flgrx module is simple there isnt one for the PPC arch only x86 arch's so although apt lists it, its not for PPC. This is ATI's fault as with it being a closed source driver noone can rebuild it for PPC. 

That leaves you only 2 choices really fbdev should work but will give you no 3d acceleration and very slow performance (ive found anyways), or the open source ati driver (which is what loads the radeon driver) basically the ati is just a probe driver that locates and installs the correct module, in your case "radeon".

If you can do a cli install and see if that works cleanly without problems (you can do this by typing "cli-powerpc" at the boot prompt on install. This will leave you with a base command line system that should work without issues. Ive heard of problems with the fans on G5's in anything before Feisty so i would suggest a Feisty cli install.

After this you can then try doing the setups properly using these commands.

sudo apt-get update

sudo apt-get upgrade (to make sure you have the latest software)

sudo apt-get install xorg xserver-xorg-dev (should install all the packages needed)

This should leave you with a basic Xserver (ugly as hell)

Then try

startx (if this works it means it will create a base xorg.conf file for you)

Then if it does work press ctrl-alt-backspace to kill the xserver, edit the xorg as required but at the moment do not change the section for the graphics card.

Then do 

sudo apt-get install ubuntu-desktop or kubuntu-desktop or xubuntu-desktop depending on your preference for gnome, kde or XFCE

After this try typing gdm or kdm (depending on your choice of gnome or kde)

This should if all is well take you to a login screen from here on out we know we have a working base so you can then edit the xorg file knowing you have a working base incase things go wrong.

If it works hit ctrl-alt-f1 to go back to console and from the command line type 

sudo killall gdm or kdm (this will kill the xserver again)

From here we can try to edit the xorg.conf to get you a working ati card.

Type 

sudo nano /etc/X11/xorg.conf

look for the line in the device section relating to the driver (should be "fbdev" and change this to read "ati")

After this is done again type gdm or kdm at the prompt

This if all has gone well will give you a login screen again (but this time using the ati driver).

I hope this helps a little. If you have more problems post here and we will try and help you out as much as possible.

---

