---
title: "i did it, but im having some problems with my internet."
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by Stromham on 2006-06-25
ok so right as i type this im using ubuntu and its great! but i have to do a usb connection to get online, im having problems with my wireless card (linksys wpc45g) and  i have ndiswrapper and its utilitys on my comp, but the first time i did sudo ndiswrapper -i xxx.inf it worked and said the drive was installed and corrected, but my ubuntu did not install right and had some errors so i did another clean install booted up ndiswrapper typed the command again and then i typed sudo ndiswrapper -l to see the driver i just installed and it said it was a invalid driver. i uninstalled it and reinstalled it a few times now and i get the same thing. how do i get my wireless working??

---

### Post by Apple 101 on 2006-06-25
This method took about 2 minutes after I finished downloading the packages.  The instructions are for Ubuntu 6.06.

1. Find the Windows .inf and .sys files for your wireless card. Put them together in your home folder.
2. Install the ndisgtk package and open it from the System --> Administration --> Windows Wireless Drivers.
3. You'll need to locate the .inf file for the programme. It will install and recognise your wireless card (hopefully - you may need to find another version of them if it doesn't work).
4. Install the wlassistant package.
5. Open it from Applications -->Internet --> Wireless Assistant
6. Go through the options - graphically.

The assistant detects your network, strength, whether it has encryption, and lets you get connected even with password keys.

---

### Post by Stromham on 2006-06-25
i cant seem to find ndisgtk and what is my home dir?

---

### Post by Stromham on 2006-06-25
ok i have the drivers installed but when i click wireless assistant it says there is no wireless networks but my computer is sitting right next to it. i need help :(

---

### Post by Apple 101 on 2006-06-25
Oh sorry, I forgot, ndisgtk is currently only in Universe.  You can get the debian package from [Ubuntu Packages]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fn%2Fndisgtk%2Fndisgtk_0.6-0ubuntu1_all.deb&md5sum=820f3a749abd2cb2d097c362103cd07e&arch=all&type=main").  Double-click to install the package.

Your home folder is /home/<your username here>

Repeat this again:
1. Install the ndisgtk package and open it from the System --> Administration --> Windows Wireless Drivers. (If you haven't already done so).
2. You'll need to locate the .inf file for the programme. It will install and recognise your wireless card (hopefully - you may need to find another version of them if it doesn't work).  If it loads - click the Configure Networking box to check that the wireless card exists.
3. Open the Wireless Assistant.

---

