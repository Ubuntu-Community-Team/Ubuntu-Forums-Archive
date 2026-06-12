---
title: "[SOLVED] Installing Nvidia Drivers"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by BrettA on 2007-11-22
Hello, 

I have recently built myself a new computer and was planning to install Ubuntu onto it. I've managed to do the trivial things; but I'm having real problems when installing my video drivers.

I have an EVGA 320MB 8800GTS Nvdidia Graphics card and have tried numerous methods of installing the drivers. I will list the results below:

(Operating System: 7.10 Gutsy)

1 - Restricted Drivers

I tied using Ubuntu's built in method of installing the nvidia drivers. When I check the box to enable the nvidia driver for 3D desktop effects it installs the driver and tells me I need a reboot. I reboot the machine, and when it boots up I get a lovely black screen. Joy.

2 - Envy

After traulling these forums I heard some people recommend Envy. It wanted me to install xserver-xorg-dev and module-assistant (Which I think I did correctly using .deb packages), and then I ran the Envy script. This seemed to run fine, download the relevant driver and install it. Once again requiring me to do a reboot. So I do a reboot, and the same black screen welcomes me.

3 - Manually downloaded driver

I downloaded the driver. Installed some packages and then when it let me run the driver (via sudo sh nvidia-package-blah.run) and it wanted me to close Xserver. So I close Xserver with that /etc/something/stop command (I found from these forums) and run the script again. Again, it seems to install but after a reboot I get the black screen of death.

After doing this a few times and reinstalling Ubuntu a few times I tried loading in Low Graphics mode from the CD. When it was booting up I got the *Running local scripts (something.something) and my screen kept flickering. Then I got some message saying that Xserver has restarted 6 times in the last 90 seconds and something bad had probably happened. (Thats what the GUI thing said on boot)

If anyone has some information / guidance on this issue it would be much appreciated. Also if anymore information is required (such as terminal outputs - altho I don't think that would help since I can't get into terminal after install) let me know.

Thank you.

---

### Post by Rowdy73 on 2007-11-22
Also a victim of that black screen of death (Nvidia EN7900GTX video card user).
Subscribing to this one...

---

### Post by overdrank on 2007-11-22
HI I can only offer some ideas, when you use Envy you should uninstall the restricted drivers first. Then use Envy to install your drivers. If you get a black screen after using Envy then you can use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hopefully this will return you to the desktop.

---

### Post by BrettA on 2007-11-22
Thank you Overdrank for your reply. Just to clarify...

When you say "Uninstall the restricted drivers" do you mean remove the (I imagine) default graphics driver Ubuntu has installed?

When I open my Restricted Drivers I am presented with 2 drivers:

 - Atheros Hardware Access Layer (HAL) -> Enabled at present
 - NVIDIA accelerated graphics driver (latest cards) -> Diabled at present

If you mean remove the HAL driver, how would I go about doing this & then still running Envy (I presume this would disable my GUI & I'd be left with Terminal again)

If you were referring to previous attempts at installing the drivers, I am on a fresh install (Cause I tend to panic when I get black screen of death & just start again lol)

Many thanks

Brett

---

### Post by overdrank on 2007-11-22
> **BrettA said:**
> Thank you Overdrank for your reply. Just to clarify...

When you say "Uninstall the restricted drivers" do you mean remove the (I imagine) default graphics driver Ubuntu has installed?

When I open my Restricted Drivers I am presented with 2 drivers:

 - Atheros Hardware Access Layer (HAL) -> Enabled at present
 - NVIDIA accelerated graphics driver (latest cards) -> Diabled at present

If you mean remove the HAL driver, how would I go about doing this & then still running Envy (I presume this would disable my GUI & I'd be left with Terminal again)

If you were referring to previous attempts at installing the drivers, I am on a fresh install (Cause I tend to panic when I get black screen of death & just start again lol)

Many thanks

Brett
Hi and no if the restricted driver for nvidia is disabled the that is fine. I was just stating that if you tried the restricted drivers then be sure to remove them before installing with Envy.

---

### Post by BrettA on 2007-11-22
Oh dear, seems I've taken a step back.

Installed Ubuntu, updated the operating system with the 88 or so updates on the Update Manager.

Downloaded Envy, ran the script (seemed I didn't have to install the 2 dependies I did before for some reason)

Output from the terminal on running of the script (for a 2nd time cause the first one hung in the same place & I wanted to re-run it)

debconf: Unable to initialise frontend: Dialog
debconf: (Dialogue frontend will not work on a dumb terminal, an Emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
Selecting previously deselected package linux-libc-dev.
(Reading database ... 88927 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.22-14.46_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.6.1-1ubuntu10_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-16ubuntu2_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.2-9ubuntu2_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../p/patch/patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.5ubuntu16_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3build1_i386.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.16.1-2ubuntu3_i386.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.9_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_5.0.51ubuntu3_all.deb) ...
Selecting previously deselected package dh-make.
Unpacking dh-make (from .../archives/dh-make_0.43_all.deb) ...
Selecting previously deselected package dpatch.
Unpacking dpatch (from .../archives/dpatch_2.0.25_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.7.1ubuntu1_i386.deb) ...
Selecting previously deselected package gcc-3.3-base.
Unpacking gcc-3.3-base (from .../gcc-3.3-base_1%3a3.3.6-15ubuntu2_i386.deb) ...
Selecting previously deselected package libstdc++5.
Unpacking libstdc++5 (from .../libstdc++5_1%3a3.3.6-15ubuntu2_i386.deb) ...
Selecting previously deselected package module-assistant.
Unpacking module-assistant (from .../module-assistant_0.10.11_all.deb) ...
Selecting previously deselected package xserver-xorg-dev.
Unpacking xserver-xorg-dev (from .../xserver-xorg-dev_2%3a1.3.0.0.dfsg-12ubuntu8_i386.deb) ...
Setting up linux-libc-dev (2.6.22-14.46) ...
Setting up libc6-dev (2.6.1-1ubuntu10) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.5ubuntu16) ...
Setting up html2text (1.3.2a-3build1) ...

Setting up gettext (0.16.1-2ubuntu3) ...

Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.9) ...
Setting up debhelper (5.0.51ubuntu3) ...
Setting up dh-make (0.43) ...
Setting up dpatch (2.0.25) ...
Setting up fakeroot (1.7.1ubuntu1) ...

Setting up gcc-3.3-base (1:3.3.6-15ubuntu2) ...
Setting up libstdc++5 (1:3.3.6-15ubuntu2) ...

Setting up module-assistant (0.10.11) ...
Setting up xserver-xorg-dev (2:1.3.0.0.dfsg-12ubuntu8) ...
Setting up libstdc++6-4.1-dev (4.1.2-16ubuntu2) ...
Setting up g++-4.1 (4.1.2-16ubuntu2) ...
Setting up g++ (4:4.1.2-9ubuntu2) ...

Setting up build-essential (11.3ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package envy.
(Reading database ... 91598 files and directories currently installed.)
Unpacking envy (from .../envy_0.9.8-0ubuntu13_all.deb) ...
Setting up envy (0.9.8-0ubuntu13) ...
(Reading database ... 91971 files and directories currently installed.)
Preparing to replace envy 0.9.8-0ubuntu13 (using .../envy_0.9.8-0ubuntu13_all.deb) ...
Unpacking replacement envy ...
Setting up envy (0.9.8-0ubuntu13) ...

Sorry! :P

---

### Post by BrettA on 2007-11-22
Update:

Sorry about all this but there have been some developments on the driver installation front, but with those come other problems. 

I have managed to install & run Envy; which installed my Nvidia drivers. So now when I open Restricted Drivers I see

Atheros Hardware Access Layer (HAL) <Enabled> In use
NVIDIA accelerated graphics driver (latest cards) <Disabled> In use

( The <> are check boxes)

Whenever I reboot I still get the black screen of death (Well my monitor says no Signal) when I check the box & reboot. 

I did those commands and got back into the GUI but when I return the NVIDIA is always diabled. (Or not enabled)

Thats about it, any ideas chaps?

Brett

---

### Post by offroad64 on 2007-11-22
Did you remove the old drivers first ???
Boot in to recovery mode and run envy
sudo envy -t
Worked for me:)

---

### Post by BrettA on 2007-11-22
Thanks alot overdrank for your help. Without those commands I'd be reinstalling all night. I have written them down :D

Rowdy73 - For your information I managed to enable the driver after having installed the driver with Envy doing sudo nvidia-xconfig in terminal.

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

Was the terminal output and when I went to Restricted Drivers it was enabled. Magic!

---

