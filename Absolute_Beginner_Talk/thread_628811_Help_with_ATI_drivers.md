---
title: "Help with ATI drivers"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by gubemton on 2007-12-01
I have an ATI x1100 on my laptop @ 1280x800

I tried installing these drivers:

[http://linux.softpedia.com/get/System/Hardware/ATI-Radeon-Linux-Display-Drivers-6719.shtml](http://linux.softpedia.com/get/System/Hardware/ATI-Radeon-Linux-Display-Drivers-6719.shtml)

And I get this in the gedit thingy:

"gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

I press retry and it still does not work. Any suggestions?

---

### Post by overdrank on 2007-12-01
> **gubemton said:**
> I have an ATI x1100 on my laptop @ 1280x800

I tried installing these drivers:

[http://linux.softpedia.com/get/System/Hardware/ATI-Radeon-Linux-Display-Drivers-6719.shtml](http://linux.softpedia.com/get/System/Hardware/ATI-Radeon-Linux-Display-Drivers-6719.shtml)

And I get this in the gedit thingy:

"gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

I press retry and it still does not work. Any suggestions?

Hi and have you tried the restricted drivers? Also I viewed you link and I see no command that refers to the gedit thingy ?

---

### Post by gubemton on 2007-12-01
The link is the driver I downloaded. When I double click on the .run for the ATI driver, it shows that error in gedit.

---

### Post by gubemton on 2007-12-01
Hate to double post but I found this on how to use a .run file

[https://help.ubuntu.com/7.10/add-applications/C/install-file.html](https://help.ubuntu.com/7.10/add-applications/C/install-file.html)

it works fine till it says that I need to be a "Super User" in order to contiune.

Any help?

---

### Post by overdrank on 2007-12-01
> **gubemton said:**
> Hate to double post but I found this on how to use a .run file

[https://help.ubuntu.com/7.10/add-applications/C/install-file.html](https://help.ubuntu.com/7.10/add-applications/C/install-file.html)

it works fine till it says that I need to be a "Super User" in order to contiune.

Any help?

Ok and as I asked before have you tried the restricted drivers? and in the link you posted did you follow the instruction
Install .run packages

Sometimes you may need to install software (most often a game) which has been packaged as a .run file. These files contain the software and a small program to install the software.

Follow the procedure below to install software packaged in a .run file:

   1.

      Find the .run file in the File Browser
   2.

      Right-click the file and select Properties
   3.

      Under the Permissions tab, make sure that Allow executing file as program is checked and press Close
   4.

      Double-click the .run file to open it. A dialog box should appear
   5.

      Press Run in Terminal to run the installer
   6.

      A Terminal window will open. Follow any instructions on-screen to install the program

---

### Post by gubemton on 2007-12-01
I did do as that site instructed, but it says I need to be a "Super User"

I tried the restricted drivers but they do not allow me to use Desktop Effects.

---

