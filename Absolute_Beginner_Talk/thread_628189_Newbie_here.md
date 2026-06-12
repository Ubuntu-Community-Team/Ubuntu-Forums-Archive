---
title: "Newbie here"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by nimbus2000 on 2007-12-01
Hi everyone
Just joined the ubuntu users community and started with gutsy gibbon. Have an Acer 5570Z and there are quite a few threads dealing with installation issues on this particular machine. Have been able to sort out quite  a few issues from posts here thanks to you guys. Only the wireless remains. Following the posts here i have installed NDIswrapper and the windows driver for the AR5007EG controller. My machine recognises my wireless network. It even conects to the network through WEP (The graph on the top right hand corner shows the strength of the signal. Thats about it. Firefox simply refuses to connect. Pinging doesnt work and to top it all if i use roaming mode it prompts me for the passkey every 3 minutes or so. can someone help please.
bye

---

### Post by vikram on 2007-12-01
probably a stupid question but did you get an ipaddress ? whats the output of the command below may provide a clue. 

sudo ifconfig


if you dont have an ipaddress try running the dhcp client. i think the command is  dhclient.

---

### Post by fineas on 2007-12-01
> **vikram said:**
> 
if you dont have an ipaddress try running the dhcp client. i think the command is  dhclient.

Actually, It is
sudo dhclient

---

### Post by bobyy on 2007-12-01
>HY TRY >> [http://ubuntuforums.org/showthread.php?t=512828&highlight=AR5007EG](http://ubuntuforums.org/showthread.php?t=512828&highlight=AR5007EG)
>ENJOY :)

---

### Post by nimbus2000 on 2007-12-02
hurray its working.
after a lot of reading i uninstalled network manager and installed WICD instead. wonderful. it connects.

---

