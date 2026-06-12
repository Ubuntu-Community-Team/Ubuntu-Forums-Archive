---
title: "ndiswrapper wifi (auto load)"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by observ8 on 2008-01-09
i installed the ndiswrapper and i made the installation of the appropriate drivers form my wireless card

after that i managed to have internet through wifi card using the commands found in the forum
the problem is that every time i restart my pc i must run these commands to the terminal and configuring my wep settings for having wireless connection

i assume that if i write these commands in a bash script every time i run this script i will connect through wireless

is there an alternative way of auto load of wireless card with  ndiswrapper?

---

### Post by wieman01 on 2008-01-09
[LIST]
[*]Load new driver module (may not be necessary any longer, but does no harm either):
> sudo depmod -a
sudo modprobe ndiswrapper

[/LIST]

[LIST]
[*]Add the module to "/etc/modules" to have it load automatically:
> echo 'ndiswrapper' | sudo tee -a /etc/modules
[/LIST]

[LIST]
[*]Create alias directive:
> sudo ndiswrapper -m
[/LIST]

---

### Post by observ8 on 2008-01-09
thank you for the quick reply,  i'l try it at home tonight :)

is it posible to explain me what each command does
(sorry for my bad english)

---

### Post by wieman01 on 2008-01-09
The headers should be kind of self-explanatory. If not, please refer to:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29")

I could not explain it any better. :-)

---

