---
title: "Installing display drivers"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by deposition on 2007-03-31
I just installed Ubuntu and downloaded the "Display Drivers for XFree86 4.3" for my radion x1600. Im not sure how to install these. when try to open them it says  "Archive type not supported"

---

### Post by 67GTA on 2007-03-31
What did you download?

---

### Post by Maestro23 on 2007-03-31
> **deposition said:**
> I just installed Ubuntu and downloaded the "Display Drivers for XFree86 4.3" for my radion x1600. Im not sure how to install these. when try to open them it says  "Archive type not supported"

I have an X1600 as well, just installed the latest driver myself not to long ago. Get the ATI Driver Installer version: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

You can then follow this guide: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28ATI%29](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28ATI%29)

Goto section: "Installing Latest ATI driver from site".

Can also get the Evny script: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

You can also install the xorg-driver-fglrx from the Ubuntu repositories as well.  It is also explained in the link above.

Good luck.

---

### Post by deposition on 2007-03-31
nevermind i cant read

---

### Post by Maestro23 on 2007-03-31
Looks like you have another program open that handles packages.  Close Synaptic, Add/Remove, etc... and try the commands again.

---

### Post by PurplePenguin on 2007-03-31
Sounds like you have another instance of aptitude (or Add/Remove, or Synaptic) running at the same time.  If you don't have any other terminals or windows open (check all of your desktops!), there might be a package manager running in the background or stuck.  Try rebooting (there are other ways, but this is the easiest) and run sudo aptitude install etc. again from a fresh boot.

Edit: Maestro beat me by seconds. :D

---

### Post by Maestro23 on 2007-03-31
> **PurplePenguin said:**
> Sounds like you have another instance of aptitude (or Add/Remove, or Synaptic) running at the same time.  If you don't have any other terminals or windows open (check all of your desktops!), there might be a package manager running in the background or stuck.  Try rebooting (there are other ways, but this is the easiest) and run sudo aptitude install etc. again from a fresh boot.

[COLOR="Red"]Edit: Maestro beat me by seconds[/COLOR]. :D

Must be all the Killian's Irish Red I'm consuming tonight...:lolflag:

---

### Post by deposition on 2007-03-31
Thanks for the help guys

I followed the [https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28ATI%29#head-99489608eb537a1a0346cdd3ad34209d7887714a](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28ATI%29#head-99489608eb537a1a0346cdd3ad34209d7887714a)
guide to the bash ./ati-driver-installer.run --buildpkg Ubuntu/edgy part

and i get

brian@brian-desktop:~/Desktop/ATI_Drivers$ bash ./ati-driver-installer.run --buildpkg Ubuntu/edgy Created directory fglrx-install.pWi1o1
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.35.5.........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/edgy
./packages/Ubuntu/ati-packager.sh: line 57: dpkg-architecture: command not found
Error: unsupported architecture:
Removing temporary directory: fglrx-install.pWi1o1

So it doesnt create the files that I need for the next step.
Anyone know why the "command not found Error" has occured?

---

### Post by deposition on 2007-04-01
ok i reinstalled and now im past that. im to the very end of the guid where i type > udo module-assistant build,install fglrx-kernel and it says 

> brian@brian-desktop:~/Desktop/ati_drivers$ sudo module-assistant build,install fglrx-kernel
Build failed. Press Return to continue...

so i used the -f version like it says and it echos the same thing, > brian@brian-desktop:~/Desktop/ati_drivers$ sudo module-assistant build,install fglrx-kernel -f
Build failed. Press Return to continue...

---

### Post by deposition on 2007-04-01
and after the above it wornt shutdown or boot. I've reinstalled three times, followed the instructions exactly, and everytime the above happends and i cant shut down or boot.
Thanks for any help in advanced.

---

### Post by Maestro23 on 2007-04-01
> **deposition said:**
> and after the above it wornt shutdown or boot. I've reinstalled three times, followed the instructions exactly, and everytime the above happends and i cant shut down or boot.
Thanks for any help in advanced.

That guide is a little confusing to follow, I couldn't find the exact one I used until today.  Give this one a try.  It's a little easier to follow, and the one I used for my X1600.  Good luck man.

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by 67GTA on 2007-04-01
I took the easy way out and used Alberto Milone's Envy script for my x1600. If you are using Edgy you can use the gui version. It is the only way I could get mine to work. [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by deposition on 2007-04-01
I just wanted you guys to know after spending all yesterday and today trying everyway to install these drivers, all i needed to do was 3 little lines of code to do everything (even downloads the drivers)

sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial

---

### Post by Maestro23 on 2007-04-01
> **deposition said:**
> I just wanted you guys to know after spending all yesterday and today trying everyway to install these drivers, all i needed to do was 3 little lines of code to do everything (even downloads the drivers)

sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial

Glad you got it.  Believe that was Method 1 in the second guide I linked. There are a couple different ways to install drivers.  Some ways work well for some and not for others. Can you go back to your first post, edit it, and mark it RESOLVED under advanced.

---

### Post by deposition on 2007-04-01
Maybe i actualyl do have another problem lol

I installed Beryl and when I select beryl as my windows manager form the Beryl manager it goes back to the gnome windows manager. I typed > glxinfo | grep direct in the terminal and it says > Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirec

I know direct rendering should be on. How do I do this and will I need to do anything else to get Beryl to work? Thanks for the help in advance.

---

### Post by deposition on 2007-04-01
Looks like I had > Section "Extensions" 
    Option "Composite" "true"
EndSection in my xorg.conf so i changed the true to false and then 0 and both times when I restarted everything was really weird, windows didn't refresh themselfs and when I scrolled I didn't actually see the text i scrolled down to, the pane just stayed on what it originally displayed.

---

