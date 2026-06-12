---
title: "fire wall problem"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by yimmmy on 2007-05-13
ok 
i have azures installed and torrent curently downloading i have a problem with the firewall i m pretty sure i dont have one but im not sure if there is a built in firewall if there is can some one tell me oh to disable it .
thanks

---

### Post by LE CHARBON on 2007-05-13
If It Is Feisty, The  Ports Are All Closed By Default. There Really Is No Firewall Per Se, As In A Windows Type Firewall.

---

### Post by oilchangeguy on 2007-05-13
the built in firewall is called iptables. why do you need to disable it?

---

### Post by mikewhatever on 2007-05-13
Use this how-to to open the port or ports used by Azureus
[http://ubuntuforums.org/showthread.php?t=331161](http://ubuntuforums.org/showthread.php?t=331161)

---

### Post by yimmmy on 2007-05-13
im not sure but the azures is downloading rellllly slow 
and the firewall thing worked im not sure how to do the port thing i dont think it worked

---

### Post by Pobega on 2007-05-13
The only firewall that comes with Ubuntu (Or any Linux distribution for that matter) is iptables, and that by default is almost never customized. The only way you activated it is if you spent two to three days doing research on the commands, and how to handle requests.

Otherwise you may have installed something like Firestarter, which is a graphical frontend to iptables.

As for forwarding ports, you may want to open the ports in your router (Assuming you are connected to DSL, FiOS, or something like that). Generally you have to point your browser to [http://192.168.1.1/](http://192.168.1.1/) and do it manually by logging in as your router's administrator account and forwarding the ports -

protocol: TCP
source: Any
destination: Port you want opened

---

### Post by mikewhatever on 2007-05-13
> **yimmmy said:**
> im not sure but the azures is downloading rellllly slow 
and the firewall thing worked im not sure how to do the port thing i dont think it worked

What do you mean it didn't work? Obviously, the port number given in that tutorial is different to that your Azureus is using. You'll have to find out which port is the right one in Azureus's settings.

---

