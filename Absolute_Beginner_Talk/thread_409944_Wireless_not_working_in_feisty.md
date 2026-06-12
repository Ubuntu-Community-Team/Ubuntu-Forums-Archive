---
title: "Wireless not working in feisty"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by wehttamb on 2007-04-15
Hi

I have just installed ubuntu 7.04 (feisty) beta on my computer. I used to have 6.10 (edgy) and the wireless network worked fine. I would just go into the network manager thing and put in the network name and key and it would conect to my network. Now on feisty i have tried putting them in the same way as i used to and i have tried using the other icon thing up the top of the screen but it just will not conect to the modems wireless conection. The light on my modem for wireless doesnt even light up at all.

Please help!!!

wehttamb

---

### Post by zvacet on 2007-04-15
Did you configured your network with system>administration> networksettings?Look if your /etc/network/interfaces are right.You can do this
> disabling network manager in the sessions/startup bit, and typing 

sudo ifup eth0
sudo ifdown eth0
sudo ifup etho


Replace eth0 with ath0 or whatever you use for wireless.

---

### Post by wehttamb on 2007-04-15
i found a topic that sounds like it might be the same problem so im going to try it. the link is:
[http://ubuntuforums.org/showthread.php?t=329299&highlight=wireless+feisty+netgear]("http://ubuntuforums.org/showthread.php?t=329299&highlight=wireless+feisty+netgear")

---

### Post by wehttamb on 2007-04-15
Hi

I have installed the driver and the wireless detects my network and say that there is a connection and when the conection gets to 60% it asks me for a passphrase or key. I set the setting to HEX and enter my key (i think it is meant to be hex, all of the characters in it are hexadecimals) and then the neywork meter thing will go down to 0% thenwen it gets to 60% again it will ask for the network key. 
What is wrong???

thanks

wehttamb

---

### Post by wehttamb on 2007-04-15
It shows the network as available and it also show the strength of the wireless network so it is sort of working now.

---

### Post by wehttamb on 2007-05-12
i just recently reinstalled ubuntu and then installed the driver again with ndiswrapper. last time when i got the wireless to work it would only work when there was no encryption. i now have no encryption on the modem still but i cannot conect to my wireless network. when i click the icon up the top right then it lists the networks name and has a meter showing the strength of the connection but when i click on the name of the network it wont connect. Could someone please tell me how to connect to my network.
Thanks

---

