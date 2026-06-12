---
title: "Working Netgear WG111v2 installation in 3 minutes!"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Orvar on 2007-10-19
There are many guides for installing WLAN out there. They all seem to involve writing a lot of code in the Terminal window. Using Ubuntu 7.10 this i completely unnecessary! The software has an excellent install program, so just simply let it do the work for you!
**NOT A SINGLE LINE OF CODE TO ENTER IN TERMINAL, not even ROOT login:**
You need:
**Ubuntu 7.10**. (Maybe also earlier ones will work, I haven´t tested.)
**WPA encryption** (WEP doesn´t seem to work) with a passphrase no longer than 16 letters/numbers.
**The .inf-file for Windows XP** that is on your Netgear CD. (/Driver/WINXP/net111v2.inf)

1) Have the CD in the CD compartment, and your Netgear WG111v2 plugged in.
2) From the System menu, click Administration, then the last entry: Windows Wireless Drivers.
You will be asked for your password. This is your normal password used for log-in, not any special ROOT password.
3) When the window opens, click "Install new driver".
4) Browse to the .inf-file location on your CD. click it and choose "open" and when you get back to the previous window, "install".

Now the installation itself is complete. And you haven´t even opened Terminal. But don´t close any window yet, you still have to configure your network to match your wireless router. 
This is done by clicking "Configure network".
"Hardware present" should read "Yes" and the box beside Wireless connection should be marked. If not, do so.
Double-click on "Wireless connection" (or click Properties) and...
Fill in your SSID (network name),
choose WPA Personal,
fill in your passphrase and...
choose Automatic configuration (DHCP). Click OK. That´s all. After half a minute or so, you are up and running!
No need to be a geek anymore, no code hacking in Terminal. No sudo, no ROOT login...

Best regards
/Orvar

PS -- I don´t usually visit these forums, so I will not be able to answer questions about this, but it really worked perfectly for me (who is a newbie, almost) so I see no reason for it not to work for anyone else.

---

### Post by wooly on 2008-02-22
> 2) From the System menu, click Administration, then the last entry: Windows Wireless Drivers.

I just installed 7.10 today, and I don't see the menu choice: Windows Wireless Drivers.
 
Is there a package I can install to get that option?

---

### Post by dcstar on 2008-02-23
> **wooly said:**
> I just installed 7.10 today, and I don't see the menu choice: Windows Wireless Drivers.
 
Is there a package I can install to get that option?

ndisgtk, but since 7.10 natively supports (at least one version of) the WG111v2 I don't know why you would bother.

Plug it in, in about a minute you should be able to access the Wireless networks from the tray icon, if nothing appears, then try the ndiswrapper option.

---

