---
title: "installing wireless card"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by i8santa4u on 2007-08-01
hello,
i am new to linux i just installed ubuntu onto a spare computer i had. it didnt have wireless so i baught a netgear wg311 wireless pci card. 
when i opened it up it told me to install the cd first. my computer couldnt read the cd. Is that because it is a windows cd in a linux computer?
so then i took the cd out and put the pci card in and started the computer up. it didnt recognize that either.
could anyone help me, i have no clue what to do.

i dont know if this matters, but it is a..
dell dimension xps t550
20gb hard drive 
i dont know how much ram but im pretty sure its enough

ANY help would be greatly appreciated

---

### Post by annda on 2007-08-01
i don't know your card but the community help docs could help you:
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

---

### Post by FurryNemesis on 2007-08-01
Ok, for a start Windows software generally doesn't work in Linux.
Secondly you might be able to get the card working using something called ndiswrapper, which allows you to use the windows drivers with Ubuntu and other linux distributions. 

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3]("https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3")

Not used this myself so not sure if this solution is applicable to you, but is a good place to start. Good luck.

---

### Post by SteveHoffmanUK on 2007-08-01
Could you be more specific about your Dell not "recognising" the card?

I have a 4-year-old used Dell Latitude and bought a Belkin Wireless G Notebook Network Card for it. I stuck it in and it worked straight away in Ubuntu (all versions) once I set it up.

For example, what happens if you click on System > Administration > Networking? Does it show a Wireless connection?

---

### Post by i8santa4u on 2007-08-01
> **SteveHoffmanUK said:**
> Could you be more specific about your Dell not "recognising" the card?

I have a 4-year-old used Dell Latitude and bought a Belkin Wireless G Notebook Network Card for it. I stuck it in and it worked straight away in Ubuntu (all versions) once I set it up.

For example, what happens if you click on System > Administration > Networking? Does it show a Wireless connection?

thats what i ment by not recognising it, when i go to System>administration>networking it doesnt show up.
oh and by the way, i have feisty fawn

---

### Post by SteveHoffmanUK on 2007-08-02
Found this advice for your card:
> When you do an "lspci" the card ID's itself as
Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

I couldn't find any drivers for Linux, but you can use the older Windows XP/2000 drivers under ndiswrapper and get it working. I followed the instructions in this wiki here:
[http://www.jimbo7.com/wiki/index.ph...11v3_LINUX_WIKI](http://www.jimbo7.com/wiki/index.ph...11v3_LINUX_WIKI)

It works perfectly now. 

The Wiki is written for Debian users, and since Ubuntu is based on Debian, the instructions should work without any problem in Ubuntu. Hope this helps

---

