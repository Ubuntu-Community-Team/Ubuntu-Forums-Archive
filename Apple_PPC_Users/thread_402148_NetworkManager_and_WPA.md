---
title: "NetworkManager and WPA"
date: 2007-04-05
forum: Apple PPC Users
---

### Post by kugn on 2007-04-05
a lot has been said about feisty being really easy for those connecting to wireless networks, but this seems to have eluded me...

i've been installing the herds and the beta versions, but i've never gotten NetworkManager to play nice with my WPA connection at home. after cutting out the firmware for the broadcom chip on my ibook g4, NetworkManager sees the wireless connections just fine, but just wouldn't connect to the WPA ones. 

in ubuntu, trying to connect to the WPA network will get me a prompt for the password, but then fails to connect.

in kubuntu, there wouldn't even be a prompt for the password.

i get all these on fresh installations on ubuntu, default settings, without messing with any other network configurations.

if i were to manually configure wpa supplicant, connecting to the WPA network works just fine, so it shouldn't be that there's missing firmware or driver or anything of that sort.

is this a bug? or am i doing something wrong?

---

### Post by kapatp on 2007-04-06
> **kugn said:**
> a lot has been said about feisty being really easy for those connecting to wireless networks, but this seems to have eluded me...

I couldn't agree with you more... WPA just didnot work. I switched to WEP for my home... 

> 
in kubuntu, there wouldn't even be a prompt for the password.

same here.... KDE's Wireless Assistant doesn't work either. I had tried, wifi-radar in between.. even that didnot work...

> 
if i were to manually configure wpa supplicant, connecting to the WPA network works just fine

Could you post what exactly you are configuring for wpa supplicant?

pk

---

### Post by kugn on 2007-04-06
I'm glad I'm not alone in this. :)

I don't quite remember how i exactly configured wpa supplicant, but i did read this wiki [https://help.ubuntu.com/community/WifiDocs/WPAHowTo]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo"), amongst other guides.

After setting it up, i had to ```
/etc/init.d/networking restart
``` everytime i booted my computer to connect to network.

I do, however, remember that when i configured wpa supplicant, the driver used was 'wext' and not 'bcm43xx'. Perhaps the problem is that the bcm43xx driver doesn't work with WPA, and so NetworkManager, using the bcm43xx driver, cannot connect to WPA? If this is so, how can we make NetworkManager use the 'wext' driver instead?

I've also just found a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/101857"), which seems to be the exact problem we're having.

---

### Post by ditsch on 2007-04-08
If you use Networkmanager and WPA, you probably have trouble with [this bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/52922"). So you have to convert your passphrase to hex and enter this hex passphrase into the Networkmanager password prompt. 

To convert it, simply enter ```
wpa_passphrase ssid
``` in a terminal and enter your passphrase. Then you should be shown a line beginning with *psk=*. Copy the hex passphrase (the weird code after the equals sign) into the password prompt and get connected!

---

### Post by kugn on 2007-04-09
Thanks dittsch, it works!! As it is, I'm typing this in Kubuntu.

KNetworkManager still doesn't prompt for a password, so I has to 'Connect to other Wireless Network', but i guess that's a different bug.

Thanks again :)

---

