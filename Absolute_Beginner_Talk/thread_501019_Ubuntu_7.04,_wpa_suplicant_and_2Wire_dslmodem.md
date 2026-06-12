---
title: "Ubuntu 7.04, wpa_suplicant and 2Wire dslmodem"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-07-14
I've followed this link [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo) to try setup wpa on my wireless connection.  I use ATT/Yahoo dsl and it came with a 2WIRE dsl modem/wireless router.  I have no problem using it with WEP, but even in Windows I was never able to get WPA to work.  I also checked the posts on this forum that the "post" function came up with saying they matched mine, and there was no help there either.

I re-configured the modem to have WPA-PSK enabled and copied the key (used copy/paste) from the /etc/wpa_supplcant.conf file to it.

I also followed another link which showed me how to "clear" my keyring so it would ask for my password again.  When I selected connect to my wireless network it did come up saying it needed my WPA password, which I again copy/pasted into the line.  After telling it to "go", it justs sits there saying "Waiting for Network Key for the wireless connection " and my network name.

At the time it asks for the password, I notice it only allows WPA Personal but there is a line at the bottom that says default with another choice of tkip.  I have tried both but neither changes the result.

Now that I've described the problem, I'll give the information I hope is useful:

- my wireless interface is a Broadcom 4318 using ndiswrapper
- when I try the test shown in the how-to, I get this:

dave@dave-ubuntu:~$ sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dndiswrapper -wPassword:
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'eth1' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
ioctl[SIOCGIFINDEX]: No such device
ioctl[SIOCGIFINDEX]: No such device
ioctl[SIOCGIFINDEX]: No such device

dave@dave-ubuntu:~$ 

I'm sure my wireless is on eth1 - it fails to associate to wlan0 at boot saying the device is busy.  

Other than that, all I can tell you is that I am very new to Linux and Ubuntu, a novice's novice, so I hope I have provided enough information for help.:)

Thanks! :)

---

### Post by DSn0wMan on 2007-07-14
Here is the deal with Ubuntu 7.04 -- You don't need to mess with wpa_supplicant.conf at all. 7.04 comes with network manager installed by default and it supports WPA by default. 

I am not sure about the Broadcom 4318, but if it is working all you need to do is right click on the network manager icon in the task panel and activate your wireless network interface. After it is activated you simply click the network manager icon, and select your network. Network manager knows if you select a WPA enabled network, and will prompt you for the WPA passphrase.

---

### Post by anewguy on 2007-07-14
Thanks - I'll try that out and see how it goes!:)

---

### Post by anewguy on 2007-07-14
Well, I removed the /etc/wpa_supplicant.conf file that I created, then removed the entries from the /etc/network/interfaces file, connected via wire to my modem/router and changed the settings to WPA and put the passphrase in it, saved the changes and rebooted the modem/router.  When I tried to connect it asked for the passphrase which I copied and pasted from a file where I had saved it, and I'm back to the same thing.  The 2 little dots from network manager have the little circle going around them, and when I put my mouse over the icon it says waiting for network key.  I really don't understand at all.  I put it in the modem, and put the same one in when prompted for the passphrase.  Can anyone help an idiot?:)

---

### Post by anewguy on 2007-07-14
Anyone?

---

### Post by DSn0wMan on 2007-07-15
Is your router set up for WPA-PSK?

---

### Post by anewguy on 2007-07-15
I had put WPA-PSK and the copied the key I generated into the key field.  I even rebooted the modem/router (it's a 2WIRE dsl modem/wireless router all in 1).  After doing so, I can no longer connect with the WEP I had been using, so I assume it was updated to the WPA-PSK okay.  If network-manager-gnome is working the way I think it is (ouch, it hurts when I do that!), it is detecting it as WPA as it does ask me for ta WPA key.  It has some sort of option for "default" or "tkit" (?) and I have tried both with no luck.  Since I'm a novice, I'm probably just missing something stupid.  It seems like it should be straight forward - generate a key, set the wireless router up for WPA with that key, try to connect, and enter the generated key when asked.   However, I have learned one thing - when I assume something is simple, I'm usually making a mistake.:o

Thanks for your help!  Maybe we can figure out what I'm doing wrong yet!:):)

---

### Post by anewguy on 2007-07-15
I tried WICP as mentioned in another post about WPA.  That didn't work either.  I completely removed all of the wpasupplicant stuff, including wpasupplicant and network-manager-gnome, then re-installedmnetwork-manager-gnome.  I am now back to where I started - I can only get WEP to work on the wireless connection to my 2WIRE dls modem/wireless router.  I have a Broadcom 4318 Air Force One type wireless controller working with ndiswrapper.   Does anyone know if there is some sort of trick to doing this with the 2WIRE modem?

---

### Post by DSn0wMan on 2007-07-17
The setting on my wireless router is for WPA-TKIP thats what works for me.

---

