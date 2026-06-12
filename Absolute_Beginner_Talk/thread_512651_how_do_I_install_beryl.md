---
title: "how do I install beryl?"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by cygnis1 on 2007-07-29
I followed the instructions to install Beryl on my Feisty laptop.  Everything went well until I typed "beryl-manager" into the terminal.  I received this message in the terminal:

Detected xserver                                : AIGLX

Checking Display :20.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

What is a composite extension? and where do I get it?  Can I find it in synaptic?
Thanks,
Cygnis1

---

### Post by BlahMan_of.Doom on 2007-07-29
What kind of video card do you have? And are you running i386 or AMD64?

---

### Post by Immolatus on 2007-07-29
Open synaptic and search "beryl" (without the q-marks. Then look through the results. Beryl manager is a separate package so you'll have to select it. AIGLX is installed and running by default in feisty, So you wont have to install it.

Just make sure you have Beryl and beryl manager installed. You will find the manager under
Applications-->system tools.

Note: you can also install Compiz without bothering Beryl any, and it will be selectable in the Beryl manager. Just right click on the manager icon, it will be in the drop down under "select window manager".

---

### Post by FleetAdmiral74 on 2007-07-29
The correct answer is do not install Beryl. Please try Compiz Fusion, as it is more stable. Beryl is not even activily developed anymore.

---

### Post by cygnis1 on 2007-07-29
My machine is i386.  My video card is an ATI.  AIGLX is installed.  Should I use Synaptic to install all the packages?  What is the Xcomposite extension?  Should I use Synaptic to install Compiz?  Will that get the 3d effets to work?  I have the beryl manager and tried to use it but it doesn't change anything.
Thanks,
Cygnis1

---

### Post by Immolatus on 2007-07-29
Yes use synaptic. beryl is an xcomposite extension, so it's telling you that it is not installed. It sounds like you just installed the beryl manager without beryl itself. So, open synaptic and search for beryl and install beryl. It should work fine bu you might have to play with the drivers for that ATI card.

---

### Post by sailor2001 on 2007-07-29
1st check system/administration/restricted drivers.........after clicking everything in synaptics...try fusion...... in terminal:       compiz --replace c- emerald &

---

### Post by cygnis1 on 2007-07-29
I tried both of these things without success.  When I used the terminal I received this message:

john@r3-mobile:~$ compiz --replace c- emerald &
[1] 12131
john@r3-mobile:~$ /usr/bin/compiz.real: No composite extension
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

How do I replace the current window manager, and with what?

Thanks,
Cygnis1

---

