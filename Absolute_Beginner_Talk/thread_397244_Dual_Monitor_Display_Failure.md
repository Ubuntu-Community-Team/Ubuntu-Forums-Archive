---
title: "Dual Monitor Display Failure"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by theninthdimension on 2007-03-30
Hello,

	I am, as of this past Monday, new to actually having an installed Linux distribution. I am running Ubuntu 6.10 on a Dell Dimension 9200. I am having various small problems and one which I consider bigger. I have two Dell 2407WFP monitors running out of an NVIDIA GeForce 7900GS card on DVI connections, however, only one of the monitors functions (generally) correctly.

	When the computer boots up, both monitors display the BIOS boot process correctly as well as the initial Ubuntu start-up splash screen. However, once the process reaches the log-in stage whichever monitor is plugged into the left-most video card connector stops displaying 'real' graphics and displays a rapidly flashing background which cycles back-and-forth between light blue and burnt orange. Interspersed across this background are multi-colored rectilinear patches. If I were into psychotropic drugs, this would be awesome. Meanwhile, whichever monitor is plugged into the right-most video card connector exhibits a shrunken display, going from filling the approximately 52x33 cm display to having an approximately 43x33 cm display centered on the screen. I have switched both monitors around and turned them on and off at various times during the boot-up process and after boot-up. I have not tried using a non-DVI connection as the card only offers DVI and S-video hook-ups.

	My goal is to have the desktop display generally spread across both monitors, with one oriented in landscape and the other in portrait so that I can have editable graphics files spread out on one and text files on the other (is this called twin-view or dual-view?). Barring that, I would at least like to be able to have one of the monitors display across its entire screen.

	As near as I can tell, both monitors have fully updated firmware as does the graphics card. NVIDIA does offer some Linux-based drivers on their website, but I honestly do not know enough about this OS to know which (if any) I should try to install or am I simply missing an option already installed on here. I have been unable to locate help files on the Dell site, but have not yet tried contacting them directly.

	Please let me know if I need to provide additional information or if another part of the forum would be better suited to this problem.


Thanks,

Jeff.

---

### Post by ben.s on 2007-03-30
It sounds like you're using the open source "nv" driver -- it doesn't support dual output on a single card.  You'll need to download and install the "nvidia" driver, which supports TwinView.

---

### Post by charles.g.moore on 2007-03-30
First use envy to install the nvidia drivers or
[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)
then
[http://www.ubuntuforums.org/showthread.php?t=221174](http://www.ubuntuforums.org/showthread.php?t=221174)

---

### Post by bodhi.zazen on 2007-03-30
Yes, install envy.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

From the cli :

```
mkdir -p ~/src/envy
cd ~/src/envy
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu3_all.deb
sudo dpkg -i envy*
sudo apt-get install -f
sudo dpkg -i envy*
sudo envy -t
```

Then, in a terminal, type :```
gksudo nvidia-settings
```

Set up your monitors for twinview, set the resolutions, ect, then click the "save settings" button.

---

### Post by theninthdimension on 2007-03-30
Folks,

     Thanks for the help. I now have both monitors displaying and have them in the correct order (left on the left, instead of left and right mixed up). My last issue is figuring out how to get my "left" monitor to display in portrait instead of landscape. Any suggestions?

Thanks,

Jeff.

---

