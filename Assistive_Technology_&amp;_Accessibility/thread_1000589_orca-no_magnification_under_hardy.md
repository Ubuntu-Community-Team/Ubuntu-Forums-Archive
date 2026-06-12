---
title: "orca-no magnification under hardy"
date: 2008-12-03
forum: Assistive Technology &amp; Accessibility
---

### Post by glaux on 2008-12-03
Hi,

I am visually impaired, and I would like to use ubuntu/orkca for my web programming needs.
I installed ubuntu 8.04, screenreader is working fine, but there are 2 problems:

1. Magnification doesn't work for me under ubuntu hardy.
If I enable mag and click apply, the screen flashes for 1 second, than remains as before.
I checked xdpyinfo (see below) and extension composite is present.
lshw shows my intel 82G33/G31 Express Integrated Graphics Controller.(see below)
Everything seems to be correct.
Any ideas to get magnifier working?
I atached the output files xdpyinfo and video..

2. I followed the instructions for sys admin in Orca docs 
(create an orbitrc file for root), the file is present in /root directory of root@computer, I checked its content.
But if I enter sudo synaptic in the terminal, the Synaptic window opens and the speach stops until I close the window.
sudo apt-get is working fine with speach. 
Is it possible to get the GUI system tools to work?

Thanks so much glaux

---

### Post by drbongo on 2008-12-04
The magnifier problem sounds like you have compiz enabled - open the appearances window, navigate to the desktop effects tab and disable desktop effects. Orca magnifier should now work.

In order to get the Gui admin tools to work you need to either log in as root (disabled in Ubuntu by default) this can be enabled in the login manager screen but you need admin rights to enable it so it won't work with speech (catch 22). The other way is to stop orca, restart it in the --no-setup mode open the gui using sudo and making the changes.

e.g in a terminal type

sudo pkill orca
(enter password)
sudo orca --no-setup 
sudo (name of admin gui app)

afterwards I recommend you restart the computer to regain normal service.

hope this helps - I am working on a solution to this and will include it in the next version of Vibuntu.

drbongo

---

### Post by glaux on 2008-12-06
Hi drbongo,

thank You very much for the hint. Disabling visual effects is the solution for my magnification problems.
Not only all mag-fetures are now working fine, but speach is working better too (more system ressources available?).
May be this hint should be added to the [http://live.gnome.org/Orca/Magnification](http://live.gnome.org/Orca/Magnification) page.

sysadmin with orca now works after editing the sudoirs file. I forgot to do this.
But some userrs may like to use the GUI-menu to open admin-tools, because they don't know the command line names.
A solution for this problem would be great for the next vibuntu-version..

Thanks again 
glaux

---

