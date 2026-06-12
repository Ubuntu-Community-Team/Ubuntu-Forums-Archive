---
title: "Dial-up"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by georgeca on 2005-12-10
As you may have guessed, I am new to Ubuntu, since I'm tired of Windows, and see no need for it since I only use my computer to go online and to type documents. I installed Ubuntu 5.10 on one of my desktops, and I only have dialup internet. (I live in a rural area) However, I can't find how to get Ubuntu to go online. I can't get Gnome-PPP from the list of programs on Ubuntu, because I need to be online to do that. So I went on my other computer, and downloaded the Gnome-PPP package from the Ubuntu website. I transferred it to the via the LAN (yes, I was able to get it networked with my Windows PC, but I don't know how to make them share the dialup internet connection, if possible. With Windows I share the connection with a proxy server, CCProxy, and they work fine. I tried doing that with my Ubuntu PC, but it won't go). Once I transferred the Gnome-PPP package to the Ubuntu PC, I can't get it to run. It says that that type of archive is not supported. Maybe I just don't know how to install those packages. So, after that, I went with PPPConfig using the Terminal, and it won't connect. The modem doesn't seem to try to connect, but the weird thing is that I checked under the Device Manager, and it seems to be installed. (It's a Conexant HSF internal modem) But when I went to the Network option where my Ethernet and Modem are listed, I put to Autodetect under what port the modem is under, but it said it didn't find it. I guess there's the possibility of it not being installed correctly.

Thanks in advance; I really appreciate any help. :)

---

### Post by az on 2005-12-10
You have a software modem who'se manufacturers do not cooperate with open source software.  They sell their linux driver for 15 USD.

You can buy it at linuxant.com.  Or you can buy another modem which offers better linux support.  (intel and lucent provide the same kind of non-open-source driver as conexant, but they give it away free)  Some intel modems have 100 per cent open source drivers.

Hardware modems do not need drivers.

---

### Post by georgeca on 2005-12-11
Okay, thanks.

I made Firefox on my Ubuntu PC get the proxy and connect to the Internet, and it works fine. But why won't the rest of the PC also connect to the Internet? For example, the Add Applications feature won't connect. I went to System, Preferences, and Network Proxy and put in the settings, but it still won't go. :(

One more question. I downloaded Gnome-PPP off the Ubuntu website. It's titled: gnome-ppp_0.3.21-1_i386.deb. How would I install it?

---

### Post by Gray. on 2005-12-11
```
sudo dpkg -i <package-name>
```
I think dpkg requires sudo

To get the Add Applications to work (maybe):
Go to your Epiphany Web Browser (Don't know it it's installed by default, so all this typing could well be in vain)
and then try to enter your proxy settings in there (since I THINK that the Add Applications uses Epiphany).
Hope it helps.

---

### Post by georgeca on 2005-12-11
[QUOTE=Gray.]```
sudo dpkg -i <package-name>
```
I think dpkg requires sudo

To get the Add Applications to work (maybe):
Go to your Epiphany Web Browser (Don't know it it's installed by default, so all this typing could well be in vain)
and then try to enter your proxy settings in there (since I THINK that the Add Applications uses Epiphany).
Hope it helps.[/QUOTE]
I tried that but it says it can't find it:

jorge@Jorge:~$ sudo dpkg -i gnome-ppp_0.3.21-1_i386.deb
dpkg: error processing gnome-ppp_0.3.21-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gnome-ppp_0.3.21-1_i386.deb

Is there somewhere I should locate the package at? I need help with installing packages...

---

