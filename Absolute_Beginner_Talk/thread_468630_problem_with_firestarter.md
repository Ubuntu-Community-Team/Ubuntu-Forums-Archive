---
title: "problem with firestarter"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2007-06-09
I'm using eth1 as my wireless connection.
Firestarter will alert me "eth 1 is not ready....." every time I login.
So, I have to type the password for the keyring 1st and I only can start the firewall after I made the connection.
Is there anyway that can make the wireless connect automatically so that eth1 is ready every time I login?

---

### Post by ggaaron on 2007-06-09
Probably yes. But I think that you must write a text config for it and add eth1 to start services. I'm not great at that - I use wlassistant and I don't think that programs like this can connect automatically.

If you really want it then maybe this can help:
[http://gentoo-wiki.com/HOWTO_Wireless_Configuration_and_Startup](http://gentoo-wiki.com/HOWTO_Wireless_Configuration_and_Startup)

---

### Post by oliviacond on 2007-06-09
i'm a noob. that one you showed me is gentoo, i donno how to apply in on ubuntu.

---

### Post by alienexplorers on 2007-06-09
Why do you need firestarter running.  Firestarter is just a gui frontend for iptables which runs all the time.

---

### Post by edm1 on 2007-06-09
People are so quick to jump in with with the "firestarter is just the gui frontend". I think the problem is a bug with Network Manager and not Firestarter. It's a bit crude but I fixed the problem by opening /etc/firestarter/firestarter.sh and commenting out the lines:

if [ "$MASK" = "" -a "$1" != "stop" ]; then
	echo "External network device $IF is not ready. Aborting.."
	exit 2
fi

so open a terminal and

> $ gksudo gedit /etc/firestarter/firestarter.sh

replace

> if [ "$MASK" = "" -a "$1" != "stop" ]; then
	echo "External network device $IF is not ready. Aborting.."
	exit 2
fi

with

> 
# if [ "$MASK" = "" -a "$1" != "stop" ]; then
#	echo "External network device $IF is not ready. Aborting.."
#	exit 2
# fi

hope that works for you.

EDIT: sorry didnt really read your post The fix above should make the firestarter daemon start properly. In order to stop networkmanager asking for keyring password have a look [here.]("http://ubuntuforums.org/showthread.php?t=192281") You may still have to do the above fix after sorting out your keyring thingy.

---

### Post by oliviacond on 2007-06-15
thanks a lot for your reply. :)

---

