---
title: "Error after entering password in keyring for wireless"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by trmiv on 2006-11-17
I'm using edgy, I have it setup on my laptop with an iwp2200 card.  When the system boots, the keyring manager comes up and asks me to enter my passwords so my saved wireless settings in network manager will load.  Well recently I moved my /home to a new partition and had a few problems.  I solved them, but now I get a new problem which is likely related.  After I enter my keyring password I get an error that says:

"The application nm-applet attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change.  Some of the settings you have selected may not take effect or may not be restored the next time you use the application." 

Clicking details reveals this error message:

```

Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/system/networking/wireless/networks/0016015818B6/essid' set in a read-only source at the front of your configuration path
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/system/networking/wireless/networks/0016015818B6/we_cipher' set in a read-only source at the front of your configuration path
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/system/networking/wireless/networks/0016015818B6/wpa_psk_wpa_version' set in a read-only source at the front of your configuration path
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/system/networking/wireless/networks/0016015818B6/wpa_psk_key_mgt' set in a read-only source at the front of your configuration path
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/system/networking/wireless/networks/0016015818B6/essid' set in a read-only source at the front of your configuration path
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/system/networking/wireless/networks/0016015818B6/we_cipher' set in a read-only source at the front of your configuration path
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/system/networking/wireless/networks/0016015818B6/wpa_psk_wpa_version' set in a read-only source at the front of your configuration path
Can't overwrite existing read-only value: Can't overwrite existing read-only value: Value for `/system/networking/wireless/networks/0016015818B6/wpa_psk_key_mgt' set in a read-only source at the front of your configuration path

```

---

### Post by trmiv on 2006-11-17
Nevermind, this was solved here: [http://ubuntuforums.org/showthread.php?t=299985&page=2]("http://ubuntuforums.org/showthread.php?t=299985&page=2")

---

