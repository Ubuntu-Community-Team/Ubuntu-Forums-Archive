---
title: "getting online with ubuntu 6.10"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by arep on 2007-03-15
hello all, i just installed ubuntu 6.10 and it does not detect dhcp and asked for url instead. i did not entered any url since i dont think that i have url because im using ubuntu for personal uses and educational purposes
anyway, i managed to install ubuntu and im trying to get online using ubuntu however i cant get it online. i read a few threads mentioning that i have to change the some settings in the /etc/network/interfaces file and by using dhcp settings. i also tried using the networking tools to ping my router with static IP and it shows 100% packet loss but with dhcp, the networking tools does not even ping the router. I then tried to configure the devices in my computer using the device manager:- it does detect my mouse and sound card, but freezes when the device manager tries to detect the network card.
the question here would be should i update my network card's driver, or is there any mistake that i have done while installing ubuntu in the first place?
thank you for your time and co operation

---

### Post by xyz on 2007-03-15
For a start...hi and Welcome!
Try this: Go to Applications > Accessories > Terminal
You'll see something like this: th@luser:~$ 

Copy/paste this into the terminal:

```
sudo /etc/init.d/networking restart
```
type your password.
See if it works....

---

