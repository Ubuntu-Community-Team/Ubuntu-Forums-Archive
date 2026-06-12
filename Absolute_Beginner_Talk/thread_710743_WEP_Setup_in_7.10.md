---
title: "WEP Setup in 7.10"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by mrobinson_sr on 2008-02-28
This has most likely been covered somewhere, but after hours of searching I cannot find it.  

I have my wireless up and running fine (with help from the forum) with no encryption.  My router is normally setup to run WEP in 64 bit encryption, it is currently turned off, I have tried for hours to set the WEP encryption through the: System settings, Network settings, entering administrator mode, clicking on Wlan0, click configure, enter WEP key and change to hexidecimal, click OK, click Apply, network refreshes, and nothing.  What's odd is when I go back into the Wlan0 it doesn't hold the settings, sometines it changes to ASCII, and sometimes it deletes the WEP password.  Also, I thought there was somewhere I saw that I could change to 64 bit encryption, but for the life of me cannot find it again. 

Anything I'm missing, or is there an alternative method to do this?????????

Thank you.

---

### Post by wesleybailey on 2008-02-29
I had the same problem when I upgraded to Gutsy Gibbon 7.10.  I wrote an  [article]("http://wesleybailey.com/blog/2007/11/01/wireless-with-wicd/") to show how to install an alternative connection manager WICD.

It can be installed with an easy sudo apt-get install command, it saves your settings, and it can connect automatically at boot.

---

### Post by snoop001 on 2008-02-29
hi ! 

Have the same problem like mrobinson. I've instaled the WICD manager but cant c]onnect to my network. ive put the wpa  key to the window . its connecting 1-2 minits and thats it . not  connected:confused::confused::confused: .

and now if im on the net with the network manager after every trying with the WICD i have to put the wpa key to the network manager because the connection is gone

---

