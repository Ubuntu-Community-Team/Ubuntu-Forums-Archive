---
title: "nm-applet picks the wrong wireless on bootup"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Ansible on 2007-12-11
I live in a condo, and there are about 10 wireless networks in my building.  Whenever I boot into ubuntu, nm-applet always connects to an unsecured 'linksys' network by default.  the problem is, that's not my router - I have to manually select the router every time.  

Is there some way of configuring the default wireless network?

---

### Post by PhoenixP3K on 2007-12-11
Right click of the nm-applet in the system tray and select manual configuration. This way you can type in the name of the SSID you want the wireless card to connect to. You input the WEP or WPA password and each time you boot your network should always go to the one you selected. This is not in roaming mode, so if you have a laptop and need it to roam the settings would have to be different.

---

### Post by Ansible on 2007-12-11
Roam eh?  Not sure what that means.  I do have a laptop though, and I want to be able to select the wireless network when I go to coffee shops and etc.  What I'd like is to have a default priority, so if it sees my network id that it uses that before other networks.  

I guess I could set it to manual, and then when I go other places I can change it to non-manual.  Then when I get home it will connect to linksys again and I'll set it to manual again.  Not really ideal, but maybe less hassle if I'm mostly using it at home.

---

### Post by floke on 2007-12-11
open gconf-editor, then go system/networking/wireless/networks and delete the one(s) you don't want to access.

---

### Post by Ansible on 2007-12-11
Does that mean I won't be able to access networks named 'linksys' from now on?

---

### Post by kernel tom on 2007-12-11
> **floke said:**
> open gconf-editor, then go system/networking/wireless/networks and delete the one(s) you don't want to access.

I don't think you would want to do that, it may not allow to connect to another "linksys" network.

But go into your network settings. Menu Applications/system/network  or whatever it is, and go to your wireless connection and click "Roaming Mode" or something to that effect.  

Now click on nm-applet and select Manual Configuration, enter the info for your network, including the passphrase/hex key/acii key and click connect.  The keyring should ask you for a password, so it can remember the network configurations for that network.  The password you enter for the keyring doesn't have to be your network password, just make sure it's one you remeber, cause it will be that same password for every addition to your keyring.

-kt

---

### Post by buntunub on 2007-12-11
This happens to me too, but only rarely when its unable to connect to my router upon initial bootup for whatever reason. It has something to do with initial setups, because from the first time I set everything up, it always tries to connect to my router by default, and then would kick to an unsecured router it saw if it couldnt connect to mine. Perhaps its the nm config file that needs to be looked at for settings like that. Im thinking something like /etc/networking/nm-config, or /etc/init.d/networking config or something like that.

---

### Post by floke on 2007-12-11
> **kernel tom said:**
> I don't think you would want to do that, it may not allow to connect to another "linksys" network.

Sure, you can just recreate one.

---

### Post by Ansible on 2007-12-11
i don't see where gconf-editor lets you delete a 'folder' of settings.  'linksys' is a folder that has four settings values in it.  I can right click on each of those and click 'unset', but the linksys folder as a whole doesn't show an option for delete.

I guess there is only a folder created if you actually connect to a network - when I first set up my machine I connected to linksys first.  After that I guess it assumes that linksys is the default.

---

### Post by HermanAB on 2007-12-11
Try WiFi Radar instead of Network Manager.

Cheers,

H.

---

