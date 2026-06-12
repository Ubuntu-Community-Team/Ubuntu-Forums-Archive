---
title: "WPA access. Please help. URGENT!!!!"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by parry_mathur on 2007-07-08
Feisty fawn is running usecured wireless networks fine, but is having trouble connecting to WPA enabled security wifi networks. At work, I tried to connect to a network and entered the key. It kept asking for the key again and again(which was correct, since it worked in Vista). I did not realise that the WEP option was enabled and there was no WPA option in the dialog that asks for the key. So I chose the hexadecimal encryption option insteadof WEP. It asked me for the key, and accepted it. Next, it asked me a password for the keyring. I entered one. It connected, but no web page was opening. After I pinged yahoo.com, there was a response after about 30 seconds, and constant responses thereafter. I opened firefox and ran yahoo, which loaded in about 60 - 120 seconds. Google never loaded. 
Now that I've enabled the WPA key option after finding a tweak, I want to change the setting for this connection from the hexadecimal thing to WPA, but Ubuntu keeps connecting to this network using the settings I specified initially and I cannot get in to the dialog box, which asks for the key anymore. Is there any way I can reset this key so that I can switch to WPA? I'm not sure it'll work that way, too, though. Why is it that Ubuntu has this problem of not connecting to security enabled networks? Does anybody out there have a step-by-step solution?

---

### Post by BL00dFox on 2007-07-08
Hi

Ubuntu is renowned for its easy installation of wireless networks. Try clicking your wireless icon and going to "manual configure". Then you should be able to reconfigure your wireless settings. Always choose your correct encryption type and it should work.

---

### Post by ugm6hr on 2007-07-08
In Terminal:
```
rm ~/.gnome2/keyrings/default.keyring
```

This will remove all the preset GNOME keyring passwords, so that it has to ask you again (when you restart).

---

### Post by gridsleep on 2007-07-14
WPA is not going to work on your office network if it is set for 128-bit hexadecimal WEP.  WEP and WPA are alternate, incompatible encryption techniques.  You have to use WEP at the office unless your company adopts WPA as its encryption, and they will only do that if all the users' machines are WPA enabled.  Some people use older hardware or software, 802.11b for example, that can only use WEP encryption.  Your company will continue to use WEP in order not to exclude those users from the network.

---

