---
title: "Ubuntu 7.1 Gutsy Gibbon - OpenGL question"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by Exefurious on 2007-12-29
This question has been posted before - I've found many proposed solutions - but none of them work.  I think the reason is because the solutions I am reading have all been written for 7.04 Feisty.

I have 7.1 however, and when I try to run chess in 3D mode it tells me:

*Your system does not have the required software to enable 3D mode. Please contact your system administrator and ask them to install the OpenGL Python bindings and the GtkGLExt Python bindings.*

I followed the instructions given in the other posts, but to no avail...

I know I can run 3d, because I had vista on this same laptop, and ran the Aero DE and all the 3d games, including chess, just fine.

Also, I downloaded and installed brutal chess from the add/remove tool, and it works very slowly and choppy.  

Can someone assist me??


Also, I installed plugins via firefox to view flash, but it still doesn't work - still can't view flash.

---

### Post by doorknob60 on 2007-12-29
For the 3D, go to System>Administration>Restricted Drivers Manager and enable the 3D driver. For flash, download it from here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) because it can't install from the repositories right now. Get the .tar.gz installer and follow these instructions:
>    1.  Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.



---

### Post by Exefurious on 2007-12-29
> **doorknob60 said:**
> For the 3D, go to System>Administration>Restricted Drivers Manager and enable the 3D driver. For flash, download it from here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) because it can't install from the repositories right now. Get the .tar.gz installer and follow these instructions:


The flash business worked.  Thank you very much!

The only restricted driver listed is my for my wireless - which is enabled and working.  So I'm not sure what's happening with the 3d??

---

