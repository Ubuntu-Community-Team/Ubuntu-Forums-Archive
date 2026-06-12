---
title: "How do I change passwords for network manager?"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by yasoumalaka on 2006-09-28
I've changed my wpa password now I can't login to my network because I can't change the password.

---

### Post by njohn858 on 2006-09-28
I had the exact same problem last night. I got connected, then I changed the WPA key in the router, then I couldn't connect or change the key on my laptop. I did a bunch of searching and didn't turn up anything.](*,)  I deleted the .xml file in ~/.gconf/system/networking/wireless/networks/SSID but still couldn't change the WPA key. I shut down my laptop and this morning when I turned it on and tried connecting, it asked me for the WPA key. So it sounds like it is fixed, but I am not sure if what I did solved it (I am a noob) If anybody can give more detailed information that would be great!

---

### Post by yasoumalaka on 2006-09-28
Ok I figured it out. It was just something us newbs easily overlook. There is a keyring manager and you need to install it then it will show up in administration. start it and delete the old key,then you can enter the new one.

---

### Post by njohn858 on 2006-10-02
What is the name of the keyring manager?

---

### Post by joemastro67 on 2006-10-14
The name is just that "Keyring Manager"

Do a search in synaptic for keyring. Install the gnome-keyring-manager

Good Luck

---

