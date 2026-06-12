---
title: "Fixing network connection without restart"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Yellowbelly on 2008-01-17
I don't have a home network yet because I can't get my switch to cooperate with my isp basically so I have to switch cables from my computer to x360 when I want to change where the bandwidth goes. So say the modem is on and currently hooked up to the xbox and I need to use the internet on my comp. so I have to plug it in and it detects it but doesn't assign ip addresses and stuff (even after I restart the modem) so I have to restart the computer AND the modem to fix the connection. I know in XP, theres a button to fix or repair the connection and it does so without having to restart. Is there a piece of code that does this or some option that I haven't found yet? If not it should definitely be included soon.

---

### Post by jflarm on 2008-01-17
Try the command:
dhclient
It asks the dhcp server for new ip assigments.

---

### Post by freddyp on 2008-01-17
And

sudo /etc/init.d/networking restart

to restart network services

---

