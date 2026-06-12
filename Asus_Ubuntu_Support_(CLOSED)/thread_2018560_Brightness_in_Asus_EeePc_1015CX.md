---
title: "Brightness in Asus EeePc 1015CX"
date: 2012-07-06
forum: Asus Ubuntu Support (CLOSED)
---

### Post by daniwaber on 2012-07-06
Can anyone tell how to reduce the brightness in Asus EeePc 1015CX in Ubuntu 11.04. Note that function keys for brightness are not working but for sound are working. Brightness function keys work in ubuntu 9.04 live cd.

---

### Post by LonelyStar on 2012-07-07
On my asus r052c I have to type

sudo setpci -s 00:02.0 f4.b=80

where 80 is the brightness level.
Does that work?

---

### Post by daniwaber on 2012-07-07
Thanks. It is working. but the setting is not saved when you boot again. Is there any way to save settings.

---

### Post by daniwaber on 2012-07-14
EDIT:
Now you no longer need Gambas. Just Download the rapidshare link and extract all files in folder called "Final" to a new folder named ".bright" in home. Then add a startup refrence to the file called "start". You may need to fix permissions for the file (Right click, click on Permissions and allow the file to be run as executable)
The startup command must run as follows:
**./.bright/start**
If you need password to use any sudo command (if you are not root by default), then run **"sudo visudo"** in terminal and add the bold line at the position indicated.
```
%sudo ALL=(ALL:ALL) ALL
**%YOURGROUP ALL=(ALL:ALL) NOPASSWD:/usr/bin/setpci**
```
Replace YOURGROUP by your group name.
Now you can adjust brightness by running **"./.bright/adjust**" in terminal or by running the "adjust" file.
Link:[ http://rapidshare.com/files/4244361567/setpciBrightDaniwaber.zip]("http://rapidshare.com/files/4244361567/setpciBrightDaniwaber.zip")
Tested to be working on Xubuntu 13.04 on Asus EEE Pc 1015 CX

> OLDER:
Okay I have finally figured it all out:D
**This is the total solution for any Asus Eee Pc 1015 CX for Brightness Problems.**
Download the attachment and install **Gambas Runtime** (Preferably **2.21**)
To install Gambas, either search for it in **Ubuntu Software Center** or **Synaptic Package Manager** and install it from there **(Easier)**
If Software Center or Synaptic does not list it, go to  [http://gambas.sourceforge.net/](http://gambas.sourceforge.net/)

If you need password to use any sudo command (if you are not root by default), then run **"sudo visudo"** in terminal and add the bold line at the position indicated.
```
%sudo ALL=(ALL:ALL) ALL
**%YOURGROUP ALL=(ALL:ALL) NOPASSWD:/usr/bin/setpci**
```
Replace YOURGROUP by your group name. After that, keep the attached .gambas file in your home folder somewhere and add a refrence in startup to it with the command as the full path to the file.
For Example, if my username is **uuser** and I have kept my attachment in my home folder then the command must be:```
/home/uuser/BrightnessApplet.gambas
```
After this, every time you start up, the icon will show up in the top panel. Click the icon and you can slide to adjust brightness and it will remain that much at every boot.
**This works definitely with *Ubuntu 11.04* **
*Thanks to _**LonelyStar**_ for the command*:D

---

