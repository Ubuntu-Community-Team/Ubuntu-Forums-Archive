---
title: "(First Experience) -- Problems with Gutsy"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Stinn on 2008-01-29
Hi all,

Last week I installed Ubuntu Gutsy Gibbon (7.10) from cd to my HP pavilion zv6000 laptop, using this guide:

[zv6000 Semi-guide @ Ubuntuforums.org]("http://ubuntuforums.org/showthread.php?t=53578").

Everything seemed to work fine, except some small problems I tried to fix, fixing these -beginner as I am- these problems grew out to major graphics problems :mad:, at the moment these are the problems I encountered:

**1.** The broadcom driver.
The guide says I should load the broadcom WiFi driver from Linuxant's website into ndiswrapper, when I do that I get a warning that says:
> 
'BROADCOM' vendor not found.
Hardware not found.

So I asked someone a pretty experienced for help, and he told me to stay away from ndiswrapper, so I installed the "Ubuntu Restricted Driver" called *bm43xx-fwcutter*.

This works fine, I have WiFi connection now, until... until I reboot.
After a shutdown/reboot the connection is gone, and I have to completely reinstall the driver via Restricted Drivers to get my connection back.

Is there any way I can fix this?

**2.** The Graphics driver.
Pretty simple story: X used 'indirect rendering' because the Ati Radeon Xpress 200 drivers weren't working, so I followed the steps in the zv6000 semi-guide, well, they didn't help me :(
Then I tried the 'official' guide from: [Ubuntu Gutsy Installation @ cchtml.com]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually")
the 'verifying' part made me think it was ok now, but it still says "Direct Rendering: NO".
Also, fglrxinfo states the Vendor is Ati, but  glxinfo says it's SGI.

So I used an other guide, I'm sorry for I can't find it anymore, but it wasn't a big deal: downloaded a file from ati.com, made a .deb out of it, unpacked and install it, and then some small changes in xorg.conf... and a reboot...
The result was rather shocking:
As soon as I boot Ubuntu, the login screen shows up fine, when I login, the upper and bottom bar are both just thick white lines, when I click on the part where usually the 'Places' button is, the places menu shows up for half a second, and then I see only one icon, maginified to about 1000%, as soon as I click anywhere else [b]the screen turns light blue, with flashing white é's, then it turns ubuntu-brown and the system powers off and reboots.
Also, Failsafe Gnome and Normal Gnome Crash and get me back to the login screen in 5 seconds.

Does anyone know how to fix that?

and then the last problem:
**3.** Slow boot
As soon as I press power on on the laptop, everything goes fine, it goes to the GRUB menu, from there I select either Ubuntu or WinXP, but when I select Ubuntu, the screen turns black for about 3/4 minutes, then it turns off, on, and shows the logon screen, why is it doing that? It takes REALLY long to boot this way, and it doesn't show anything like "Loading ...", just a black screen?

Anyone solutions?
Thanks in advance,
Stinn

P.S: This is my first post, if I am doing anything wrong, don't wait to tell me, I think I read anything that states 'read before posting' and the Terms.

P.S.S: Some information about the sytem is here, however, it is from before the second guide that made the graphics go crazy

[glxinfo]("http://pastebin.com/f610a43e6")
[xorg.conf]("http://pastebin.com/f904663"), some things are changed in here, the last section was deleted as the guide told me, and Driver is not at Xgl but ati.

---

### Post by philinux on 2008-01-29
For the slow boot problem click the link below - known bugs.

---

### Post by Stinn on 2008-01-29
> **philinux said:**
> For the slow boot problem click the link below - known bugs.

Thank you, I think I can fix that, problem 3 solved,
thank you very mutch \\:D/

---

### Post by bumanie on 2008-01-29
What type of video card are you running? When i installed gutsy with a fairly old vga card, I had to install via console after stopping x server.
OOps, missed the mention of the ati card. Sorry.

---

### Post by emarkd on 2008-01-29
For one of my installs with an ATI card, I wound up using the fglrx driver that Restricted Drivers installed and installing the xserver-xgl package.  Rendering is then handled by xgl.  It's not very efficient, but even on my older hardware it's quite acceptable.

---

### Post by Papa-san on 2008-01-29
I have a link in my signature  to ndiswrapper. I would suggest going that route.  Ndiswrapper will limit your connectivity speed by about 2% (IF that!) of what going the fwcutter route will get you. (IF you can make it work...And that's a BIG if!) Broadcom cards are notoriously finicky. The developers have made some great strides in making Ubuntu work well with it, but all of the bugs are not ironed out just yet. If you are new, I would strongly suggest going the ndiswrapper route. Follow the suggestions in that link, and I can offer the suggestion of downloading the drivers (bcmwl5.inf and bcmwl5.sys, as well as bcmwl5a. sys and .inf... You will have them both available, and when you get the right one installed, you can delete the others...) 

Additionally, I would suggest googling 'WICD' which is a very good wireless tool for connecting to whatever networks you have available. (Makes it simple to get connected at McDonalds or the hotel, etc...)


Enjoy learning about linux!

---

### Post by Stinn on 2008-01-29
today I didn't even touch my Ubuntu installation, but when I turned laptop on, I noticed it must be fully broken, not getting any GUI, just grey lines saying:

"No Screens Found"
"module Xgl not found"

and when I used Xgl to render, it was like worthless, because anything like typing fast would cause Xgl to use 100% CPU speed.

So today I'm doing a total reinstall, because I think I just messed up the installation.

---

### Post by Sethalos on 2008-01-29
I have the same laptop and I have had 7.10 installed now for a bit.  In order for me to get my Wireless driver and Video card driver installed I simply had to click on the restricted driver icon, and put a check mark beside each item.

After that it worked fine for me. I'm not sure if you've done this yet, so just in case give that a try.

-Seth

---

### Post by Stinn on 2008-01-29
> **Papa-san said:**
> I have a link in my signature  to ndiswrapper. I would suggest going that route.  Ndiswrapper will limit your connectivity speed by about 2% (IF that!) of what going the fwcutter route will get you. (IF you can make it work...And that's a BIG if!) Broadcom cards are notoriously finicky. The developers have made some great strides in making Ubuntu work well with it, but all of the bugs are not ironed out just yet. If you are new, I would strongly suggest going the ndiswrapper route. Follow the suggestions in that link, and I can offer the suggestion of downloading the drivers (bcmwl5.inf and bcmwl5.sys, as well as bcmwl5a. sys and .inf... You will have them both available, and when you get the right one installed, you can delete the others...) 

Additionally, I would suggest googling 'WICD' which is a very good wireless tool for connecting to whatever networks you have available. (Makes it simple to get connected at McDonalds or the hotel, etc...)


Enjoy learning about linux!

This makes me want to try ndiswrapper again, but there is NOWHERE I can find the driver files.
Linuxant provides them, but they are in a .exe file and I don't know how to extract them.

and:
You say ndiswrapper provides 98% speed, while fwcutter provides 100%? then what exactly is the reason to switch?:(

---

### Post by dstew on 2008-01-29
I think you can extract drivers in .exe packages with **cabextract**. Look in Synaptic.

---

