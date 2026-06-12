---
title: "How to save wireless passwords"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by dinostabOMG on 2007-08-27
Does anyone know how to do this? It would be nice not to have to enter my WEP/WPA key every time I switch connections or start up my computer.

---

### Post by xopher on 2007-08-27
Im pretty sure network manager does this? If you don't have it installed, then install it ..

```
sudo apt-get install network-manager-gnome
```

---

### Post by dinostabOMG on 2007-08-27
Thanks for the reply. Actually, I am using network manager. I have a realtek 8180L and I am using ndiswrapper and wpa supplicant also.

I would think it would be a built in feature of network manager but it hasn't happened to store the passphrase. I get a popup box asking for the password and no checkbox or anything to store it.

Any ideas?

---

### Post by gubemton on 2007-11-02
i have network manager too with the same problem. can someone please help us??:confused::(

---

### Post by xinematik on 2007-11-18
The only thing you need to do, to save the wireless passphrase is open the **Keyring Manager** (Applications>System Tools). It will ask you permision to save the passphrase of the wireless networks.

---

