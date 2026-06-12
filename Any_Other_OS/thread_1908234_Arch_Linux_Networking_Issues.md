---
title: "Arch Linux Networking Issues"
date: 2012-01-13
forum: Any Other OS
---

### Post by Zukaro Travon on 2012-01-13
I need some help with Arch Linux and I can't register on the forums as I can't solve the question "**What is the output of "date -u +%W$(uname)|sha256sum|sed 's/\W//g'"?**" which I need to in order to register.

(tried "echo "date -u +%W$(uname)|sha256sum|sed's/\W//g'" but it doesn't accept the output in the registration (I've heard it might be broken though))



So I'm asking here.


When I try to connect to my network I type:

iwconfig wlan0 essid "id" key s:word
ip link set wlan0 up
dhcpcd waln0

(my essid is not ID and my password is not word, just put those in as I don't want to give my actual pass or ID (also, this command is for connecting to a WEP encrypted router (I know WEP is terrible), my router is only WEP for my Nintendo DS (the old one) and I don't know how to connect to WPA in Arch Linux as of yet (I will figure it out soon though) (just letting you know :P))

Then dhcpcd just times out and I can't connect.  I don't know what the problem is; I could connect just fine while on the live-USB.  Currently the only way I can connect is by typing dhcpcd and then dhcpcd wlan0 a few times, and even then it doesn't always work.  I don't think it's a driver issue however (could be wrong of course).

My router is a D-Link router (not sure of the model or anything, if you need more info on my router just ask).

My netbook is an Acer Aspire One ZG5 (not sure if that will help).


I also need some help with the sound and possibly a few other things, but those don't matter right now and I can live without them (and probably figure out on my own).


Also, I do not have a GUI, just CLI (and I only want a CLI for the time being); so any fixed would require they work in a CLI only environment.




Thanks for your time.

---

### Post by lisati on 2012-01-13
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by dirtrider1 on 2012-01-13
Due to increasing spam Arch has implemented a more stringent registration process that is designed to be somewhat difficult but not overly burdensome. My only advise is try working out the commands one by one without the echo and you will get the answer relatively easily. IF you still are having problems afterwords pm me.

---

### Post by Toz on 2012-01-13
> **Zukaro Travon said:**
> "**What is the output of "date -u +%W$(uname)|sha256sum|sed 's/\W//g'"?**"

```

$ date -u +%W$(uname)|sha256sum|sed 's/\W//g'
8ffcf0e88bc3f267aa2e80bf0b9b5be544b4f7d2c21ef0e705f32e07e057c9cf

```

Strip the double quotes.

---

