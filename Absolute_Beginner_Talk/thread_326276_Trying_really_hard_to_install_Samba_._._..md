---
title: "Trying really hard to install Samba . . ."
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2006-12-27
Hey all. I'm trying to set up a shared network between my father's office computer and my own. Both are plugged into a router. His runs on XP, and mine runs on Dapper . . .my dilemma is that no matter which way I read on how to install Samba, it doesn't work . . .I have it downloaded and extracted, but I can't find out what to do next . . .any thoughts?

---

### Post by meborc on 2006-12-27
so... the two computers ar on LAN (local area network) or not? it makes a big difference :)

also try [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by KenSentMe on 2006-12-27
Have you tried searching the wiki pages?

Start here: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Tell us what errors you get, what you've done, how you've done it and what exactly doesn't work.

---

### Post by CheshireMac on 2006-12-27
> **meborc said:**
> so... the two computers ar on LAN (local area network) or not? it makes a big difference :)

also try [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

How do I tell if it's on a LAN or not? I think it is, but I wouldn't know . . .

---

### Post by lift_test on 2006-12-27
Try SYSTEM - NETWORK SETTINGS
You should see by default the connections tab,. which should show your ethernet connection as etho0 is active.  If this is the case then you have a working lan card.
Click general tab, make sure you have a Hostname, make a note of this you will need it later.  Leave domain name empty (if you need this it is beyond my knowledge)

Go to windows machine START - My Network Places.
Click on SEARCH and type in the name you found/typed in above.
If things are working you will be asked for a password. You will probably not be able to go beyond that because the password is not your logon PW.

Go back to your machine and click on Places - Network servers.
You should see a windows workgroup name eg DELLBOYLTD.
If you don't see this then Samba is not working.
If you do see this but you get a message saying that you do not have permission then the problem is probably MacAffe/Norton or similar.  To check try temporarily disableing.

---

### Post by jonathan.lees on 2006-12-27
You could also:

To find out if your on a LAN, in your dapper open up a terminal and type ifconfig and look for the line that reads inet addr:

for example mine reads:
inet addr:192.168.1.32  

Now make a note of that address and go over to the XP machine. Open up a command prompt, you can do this by clicking on Start and then Run, type cmd and press enter.

In the command prompt, type ping (the inet addr you made a note of)

For example: ping 192.168.1.32

Now if you get a response then you are on a LAN and you can continue with your Samba installation, if you don't get a response then you need to create a LAN before you can configure Samba.

---

### Post by Irony on 2006-12-27
Install samba via synaptic.

---

### Post by edbuntu on 2006-12-28
As a noob, I was ready to tear my short hairs out while trying to install Samba ](*,). I finally stumbled upon fabioleitao's advice to check the router's firewall setting and goshdangit that was it \\:D/ ... I could be wrong but check that port 901 is open in your router's firewall.

---

### Post by halitech on 2006-12-28
if you are sharing internally on a LAN, you shouldn't need to open any ports on your firewall/router. I have 3 systems on my LAN and I don't have any holes punched in my firewall.

---

