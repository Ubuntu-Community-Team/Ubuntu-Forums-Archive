---
title: "REPOST: Wireless Issues"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by kevinmedina on 2007-06-14
This is a minor problem, but an annoyance nonetheless.

In the beginning, when I ran Ubuntu off the live cd, I would see my network connections icon in the top right hand corner and be able to click on it to see all the available wireless connections and switch without a problem. Now however, after installing Ubuntu via Wubi, when I click on the network connections icon it jumps right to the connection properties. Then, to choose another network connections I have to click on the properties for the wireless connection, input my root password, and click on the drop-down menu for the network name. This usually doesn't even yield all the available wireless networks I would usually see in Windows XP, and I would have to manually input all the network information instead in order to connect to my usual networks (work, university campus, home, girlfriends)

Can anyone help me get my network connections settings back to the way they are on the Ubuntu Live CD??

---

### Post by shearn89 on 2007-06-15
you may have to install network-manager:
[https://help.ubuntu.com/community/WifiDocs/NetworkManager]("https://help.ubuntu.com/community/WifiDocs/NetworkManager")

Once installed, it should run automatially (if not, type nm-applet into a terminal), and then you can just click on it to see available networks.

---

