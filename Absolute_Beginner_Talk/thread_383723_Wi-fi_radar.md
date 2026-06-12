---
title: "Wi-fi radar"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Jareth on 2007-03-13
Just a question of what goes where in Wi-fi radar.

I can see the network, when I ask to connect it wants a profile setup. The network is WPA-PSK encrypted, where do I put the network key?

[IMG]http://wifi-radar.systemimager.org/images/wifi-radar_profile.png[/IMG]

(Thats just off the wi-fi radar site)
This is the profile screen, when the encryption is off I don't need to put anything in, it just connects. I assume I just need to put the Network Key in there somewhere.

Any help? Ta!

---

### Post by jdfreshwater on 2007-03-13
You would put the key in the Key field, you may have to use the drop down to choose the secruity.

---

### Post by benfindlay on 2007-03-13
I am not entirely positive but i think the wpa supplicant config files still deal with your PSK and such like. You just need to direct wifi-radar to the relevant drivers you have installed. Hopefully someone else can verify this!

Hope this helps!

---

### Post by Jareth on 2007-03-13
what is that driver and how do I find it?

---

### Post by benfindlay on 2007-03-13
The package is called wpasupplicant I believe, just install it through Synaptic or with ```
sudo apt-get install wpasupplicant
```

As for config-
There's a Dapper guide here: [http://ubuntuguide.org/wiki/Dapper#How_to_enable_WPA_with_Ndiswrapper_driver]("http://ubuntuguide.org/wiki/Dapper#How_to_enable_WPA_with_Ndiswrapper_driver")

And an Edgy one here: [http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_enable_WPA_with_Ndiswrapper_driver]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_enable_WPA_with_Ndiswrapper_driver")

Theyre probably exactly the same, but its worth checking your exact version!

Hope this helps!

---

