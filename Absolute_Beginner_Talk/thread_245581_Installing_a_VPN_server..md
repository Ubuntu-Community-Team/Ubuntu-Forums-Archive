---
title: "Installing a VPN server."
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by netwizard on 2006-08-28
I just finished installing Ubuntu on my computer. My question now is how do I install a VPN server on Ubuntu? OpenVPN binaries are compiled for Fedora and RedHat. Any help would be great. Thanks!

---

### Post by steve.horsley on 2006-08-28
There are lots of different VPN servers. If you are happy with OpenVPN (an excellent choice in my opinion), then package openvpn is available in Synaptic, in the Universe repository. If a search for openvon doesnt't show it, then you need to enable the multiverse and universe repositories by choosing Settings->Repositories, click Add, and make sure all 4 boxes are checked. Click the Reload button to learn what's available in the new repos, and then search for openvpn again. There's a good HOWTO on the openVPN site that tells you how to configure it.

---

### Post by 1oki on 2006-08-28
Unfortunetly the howto that is on that site is alittle confusing... I tried to follow the directions (not word for word because it is a general linux howto) and got confused because their is no definition of where to look for files. For instance... I generated a static key, and dont know where it was generated. I did a whereis openvpn and went to all the folders. I did not find the key in any of them. Heck... I cant even find the config file!! ](*,)

---

### Post by bunnynuts on 2006-08-28
Have a look at this [link]("http://www.ubuntuforums.org/showthread.php?t=239219&highlight=openvpn"), I can greatly improve on it so let me know what questions you have and I'll see if I can answer them. Also, make sure you use this along with the HOWTO on the openvpn.net site.

---

### Post by 1oki on 2006-08-28
Thanks... I did install the openvpn from synpatic... but i cant even get to the cd /etc/openvpn/easy-rsa part... I dont have anything in the /etc/openvpn directory...

---

### Post by bunnynuts on 2006-08-28
As you can see from the openvpn site, the contents of the easy-rsa directory are quite necessary :).  My only suggestion would be to uninstall openvpn and then reinstall it via command line as opposed to synaptic manager.

---

### Post by JohnW on 2006-09-22
You want to copy into the /etc/openvpn directory the files in /usr/share/doc/openvpn/examples/easy-rsa

---

