---
title: "How Do I know if xubuntu is actually connecting or not?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by ajskhan on 2007-06-22
I go to the network manager, input my essid, wep key, and DHCP...

how do I know if it is actually connecting?! i want to download the network manager for the gnome thingy, but i don't have ubuntu installed, just a fresh xubuntu!

and I don't have any internet connection at all, so how do I go about installing the network manager for gnome? it is very convenient?


-thanks

---

### Post by Edgeworth on 2007-06-22
I'm not as familiar with KDE as I am with Gnome, But most KDE programs run in Gnome, so I think It should work the other way. You could probably install the network manager through synaptic or something, using your install CD as a repository.

---

### Post by noobbutnotboob on 2007-06-22
yes that's it exactly... install the network manager by going to system -> admin -> synaptic. The net manager should be listed and installable from the cd-rom (so make sure it is in). Once you get it installed, go to system -> admin -> network and you should then get a box that shows wireless, wired, and modem connections (if you have all three possibilities. From there, you may have to manually configure the wireless by going to properties. If you continue to have trouble check out the wireless help guide for more specific help if you run into issues. [http://https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#connection]("http://https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#connection")

---

### Post by Xoanan on 2007-06-22
Hi ajskhan.

Go to the terminal and type in *ifconfig*
That should give you an ip address which should help you to determine if you have an internet connection

---

### Post by Sweet Mercury on 2007-06-22
> **Edgeworth said:**
> I'm not as familiar with KDE as I am with Gnome, But most KDE programs run in Gnome, so I think It should work the other way. You could probably install the network manager through synaptic or something, using your install CD as a repository.

I don't think he's running KDE, Xubuntu runs the Xfce4 DE.

From what I've read and my own experience, programs are directly portable between Ubuntu and Xubuntu.

OP, do you mean you have no internet connection at all at your home?

---

### Post by Edgeworth on 2007-06-22
> **Sweet Mercury said:**
> I don't think he's running KDE, Xubuntu runs the Xfce4 DE.


Sorry, got those two confused. :oops:

---

### Post by ugm6hr on 2007-06-22
The Xubuntu CD doesn't have Network Manager on it - and it's not possible to install it without internet access from the Xubuntu machine (because of it's dependencies being bi-directional - I tried to download all components from [http://packages.ubuntu.com/feisty/](http://packages.ubuntu.com/feisty/) - and it wouldn't work), unless you use a Ubuntu CD as a repository (I'm not sure if this is possible).

It's worth trying Wicd as an alternative in Xubuntu (I would recommend v1.2.9 - it was more stable for me in Feisty!):
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

The other upside is it doesn't use the GNOME keyring, or any GNOME dependencies.

This is a useful thread too:
[http://ubuntuforums.org/showthread.php?t=463118](http://ubuntuforums.org/showthread.php?t=463118)

---

### Post by ajskhan on 2007-06-22
OK: I have a router - no clue why it is not connecting (was before). I have no internet connection.

now, to fix this :)

---

### Post by ugm6hr on 2007-06-23
> **ajskhan said:**
> OK: I have a router - no clue why it is not connecting (was before). I have no internet connection.

now, to fix this :)
Are you referring to a wired or wireless connection now?  And do you have internet access available from anywhere else?

---

### Post by ajskhan on 2007-06-23
Wireless, and no other place...

also - installed wicd - and i went to apps>network>wicd, and nothing happened - do i need to reboot or something???

---

### Post by ajskhan on 2007-06-23
edit, got it - but it can't obtain ip address?

---

### Post by Xoanan on 2007-06-23
What is the result of the command *ifconfig?*

---

### Post by ajskhan on 2007-06-23
edit got it - awesome program

now how do i get it in the top right corner of my scrn???

---

### Post by ugm6hr on 2007-06-23
> **ajskhan said:**
> now how do i get it in the top right corner of my scrn???
In Xubuntu - to add to panel:
1. Applications->Settings->Autostarted Applications:
2. Add
3. Name: Wicd / Command: /opt/wicd/tray-edgy.py

---

### Post by ajskhan on 2007-06-23
ok, i have no clue what is going on

i was online for quite a while, then it just lost connection and it won't let me get it again?!

---

### Post by ajskhan on 2007-06-23
it says it is connected, but there is no way it is?!

---

### Post by ajskhan on 2007-06-24
got it

---

### Post by ugm6hr on 2007-06-24
Only problems with Wicd v1.2.9 for me - it doesn't resume from suspend properly (but I never suspend anyway) - and it doesn't allow you to disconnect from network (only choose a different network to connect to).

Glad you got it working.

---

