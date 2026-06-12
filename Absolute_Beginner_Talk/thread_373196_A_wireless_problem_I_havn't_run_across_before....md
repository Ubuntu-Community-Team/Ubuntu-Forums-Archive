---
title: "A wireless problem I havn't run across before..."
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Amablue on 2007-03-01
I once again formatted my Ubuntu partition and went to reinstall wireless (the one thing I can't stand doing) and started by doing a search for broadcom chipset configuration how-tos. I tried one, it didn't do anything. I found a different method and started to try that one. Then I realized that my wireless doesn't appear on my networking menu. I don't know if it was like that before or if it was something I did from the first how-to (and I don't remember which guide I was following either :( )

Anyone know what's going on?

---

### Post by casaschi on 2007-03-01
So... you are asking here people to help you undo something but you dont know what you did in the first place? Funny :-)

Some wireless howto starts with "blacklisting" the kernel driver in order to use ndiswrapper with the winXP driver. If you are stuck there in the middle, you wont have any wireless interface listed.

Dont have ubuntu here, but you should look somewhere for a file like /etc/modules/blacklist and see if the wireless driver of your card is listed there, if it is, try to remove it and start again (taking note of which howto you follow).

---

### Post by Amablue on 2007-03-01
Okay, I found it by filtering through my history. 

[http://ubuntuforums.org/showpost.php?p=1189681&postcount=105](http://ubuntuforums.org/showpost.php?p=1189681&postcount=105)

I can't find any file called blacklist, or any directories that look like they contain it.

EDIT: Nevermind, found it.

---

### Post by casaschi on 2007-03-01
I referred to this part of your howto:

4.)UN@CN:~$ echo blacklist bcm43xx | sudo tee -a /etc/modprobe.d/blacklist
A.)Press the Return/Enter key

Have you done that?
If you did, try removing the line "blacklist bcm43xx" from /etc/modprobe.d/blacklist then reboot (or do a modprobe of the dirver and restart network, simpler to reboot)

---

