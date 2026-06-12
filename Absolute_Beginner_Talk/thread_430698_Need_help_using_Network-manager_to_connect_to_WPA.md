---
title: "Need help using Network-manager to connect to WPA"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Diversion on 2007-05-02
Hi guys,

I really need some help. I've been following the exellent step-by-step guides fromhttp://ubuntuguide.org/wiki/

I'm now trying to set Ubuntu up to work with my WPA network. 

After some research I found out I needed the Wpa-supplicant and the Gnome-Network-manager.

After installing both and discovering the Network-manager Icon in the top right, I got stuck on the following part:

**"click on the NM icon in the notification area (default is at the top right of Ubuntu/Gnome). Choose your network, then enter your passphrase. Type a password for the keyring, and you're set. "**

When trying to click the NM icon i get the following message:**" No network devices have been found".**

weird thing is i'm using a Intel 3945 wireless adapter which worked out-of-the-box without problems. Connecting to non-secured or WEP-networks works fine.

I don't really get why this is happening and can't seem to solve this,
Any help would be greatly appreciated!

---

### Post by Kobalt on 2007-05-02
If you had configured your network before then it's possible you edited the /etc/network/interfaces file which actually needs to be almost blank for Network-Manager to work properly. What you need to do is comment (put a # at the beginning of each line) anything in this file apart from the 2 lines of you local interface : > auto lo
iface lo inet loopback

---

### Post by Diversion on 2007-05-02
That did the trick!

Finally connected to my own network!

thank you for helping me out, days are hard being new to linux :)

---

### Post by Kobalt on 2007-05-02
You're welcome.

If the early days of linux are hard I think the more you spend time sticking to it the more you love it. The opposite of any other OS in other words...

---

### Post by Diversion on 2007-05-02
I hope so.
Been trying out linux before but never pushed myself into it.
Everytime it gave me a hard time I just ran away from it.

Really pushing myself to use it this time, cause I need and want to know how it works.

---

