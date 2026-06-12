---
title: "Setting up dial-up Connection"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by poloman2 on 2005-11-18
Hello:
here are a few newbe questions:
1) How do i find out that my modem(or any device) has been reconized by the OS (in windows device manager). when i had windows XP on the same laptop (Compaq Presario 1600) where i have ubuntu, i didn't need to install the drivers for the modem. Are there any chances that the same thing happend with the linux intallation

2) How do I set up my internet connection using dial up.

Thank you...

---

### Post by dalani on 2005-11-18
Try using the network configuration tool in under the administration menu. You'll to type in your root password and hopefully you should see your modem listed as a ppp connection.
If not, use the following instructions by Bruce147 from a previous thread 
This may be of help.

> Make sure your serial modem is turned on.
Install the gnome ppp dialup utility. It should appear on your menu bar.
Set the System/Networking utility to "deactivate" for your modem (mine already was, not sure if it must be deactivated during gnome ppp setup)
Using the gnome ppp GUI, fill in the required info... phone number, login info etc
Hit the connect botton to logon to your ISP (it probably won't work).
Close out then and open gnome pp to make sure all info is there. Close again.
Open a terminal and type sudo wvdialconf (This automatically detects your serial modem and silently creats a wvdial configuration profile, which had been lacking before.)
Finally, back on the main window, click on the red phone, the gnome GUI, and you should be ready to connect.

Here is what my terminal session looked like:
bruce147@ubuntu:/$ sudo wvdialconf
Usage: wvdialconf <configfile-name>
(create/update a wvdial.conf file automatically)
bruce147@ubuntu:/$


To see your detected hardware in general,  HAL, gnome hardware manager (in the administration menu), should list that information.

---

