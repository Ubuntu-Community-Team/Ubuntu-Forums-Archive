---
title: "Alternate to Wifi-Radar and KNetworkManager"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-10-24
I was wondering if there is any alternative to these programs for wireless. I have trouble connecting to random places for some reason. I was wondering what are other good wifi programs besides these two? Thanks!

---

### Post by x64Jimbo on 2006-10-24
NetworkManager. Look in my sig.

---

### Post by amitroy5 on 2006-10-24
For some reason, Network Manager does not detect my wifi card. I remember using some program when I used Ubuntu a year ago and it was really nice. Are there any others? Thanks!

---

### Post by x64Jimbo on 2006-10-24
If network manager doesn't detect your card, you need to comment out its entry in /etc/network/interfaces. Just put a # before it.

---

### Post by amitroy5 on 2006-10-24
I don't find any mention of network manager in "/etc/network/interfaces". What should I do to get networkmanager to work?

---

### Post by x64Jimbo on 2006-10-25
You need to comment out your interface in that file. 
It will look like this:
auto wlan0
iface wlan0 inet dhcp
Change it to this:
#auto wlan0
#iface wlan0 inet dhcp

---

### Post by amitroy5 on 2006-10-25
Thank you so much for your help. That did the trick and I got wifi working!

---

### Post by kverde on 2006-11-06
Thanks, this helped me as well on a new Edgy install.  The problem it seemed is that if you use the network manager in gnome, then NetworkManager does not work. (Unless you comment out the interface as you said).  This is way better, and essential for my laptop.  Thanks for the help!

---

### Post by kverde on 2006-11-06
This is working great, but any way to make it not ask for password when it starts up?  (Actually, it asks for a password twice on startup so its doubly annoying).

Thanks for the help!

---

### Post by x64Jimbo on 2006-11-07
If you hibernate your system instead of shutting down, it will boot up faster, and it will remember your session in NetworkManager.

---

### Post by misha680 on 2006-11-07
Or try this howto (it involves a little compilation though so I'm not sure how easy it will be to follow, but it does work):

[http://www.ubuntuforums.org/showthread.php?t=192281&highlight=pam_keyring](http://www.ubuntuforums.org/showthread.php?t=192281&highlight=pam_keyring)

Misha

p.s. Also I always have my system on automatic login because I am the only one who solely uses it at home (you can set it up at System->Administration->Login Window, Security tab, check Enable Automatic Login, and select your user from the dropdown list). If you do it this way you do not have to even do the howto above, and will just have to enter your password once for networkmanager.

---

### Post by kverde on 2006-11-07
Actually, it's not the login to the desktop, its the keyring manager that seems to prompt twice for the password every time.  Seems like its a known bug with no workaround yet.

> **misha680 said:**
> Or try this howto (it involves a little compilation though so I'm not sure how easy it will be to follow, but it does work):

[http://www.ubuntuforums.org/showthread.php?t=192281&highlight=pam_keyring](http://www.ubuntuforums.org/showthread.php?t=192281&highlight=pam_keyring)

Misha

p.s. Also I always have my system on automatic login because I am the only one who solely uses it at home (you can set it up at System->Administration->Login Window, Security tab, check Enable Automatic Login, and select your user from the dropdown list). If you do it this way you do not have to even do the howto above, and will just have to enter your password once for networkmanager.

---

### Post by misha680 on 2006-11-07
I don't know my network manager only prompts for the key ring a single time on start up. Maybe it is the type of network or something.

Misha

---

