---
title: "Auto connect to wireless as stopped"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by aaronbridge on 2008-02-25
At one time I was able to just connect to my wireless network once and it would stick. If I restarted my computer it would reconnect without problem. Some how I have changed something. In order to reconnect to my wireless network I have to go to manual network configuration and re-enter my WPA2 key. How can I make the settings "stick" so I don't have to always manually enter the key?

---

### Post by Sam Lars on 2008-02-25
Do the settings appear in
```
/etc/network/interfaces
```

---

### Post by incen on 2008-02-25
Hi, i have some similar question, too. Typing the key every time is ok, however, the keyring is really annoying. I posted this thread but no one helped me yet.
[http://ubuntuforums.org/showthread.php?t=707882](http://ubuntuforums.org/showthread.php?t=707882)

By the way, if there's a way to help stored the key, I would love to know too! Last time I followed Ubuntu instruction doing manual configuration, but the wireless stopped working right after I selected 'DHCP'. Weird... :(

---

### Post by Sam Lars on 2008-02-25
Is DHCP how you have the router set up?

---

### Post by incen on 2008-02-26
I guess so... I have no idea though. The router was not set up by my Xubuntu. I got it from some friend and they just provided me the key to it. It works totally fine in Windows XP. Now, the connection works ok for Xubuntu, too. However, I just cannot manual configure the wireless connection. Either picking up DHCP or IPv4... it just didn't work at all. I tried all the steps of troubleshooting in Ubuntu site. However, no luck at all.  :(

---

### Post by badmedic on 2008-02-26
Network Manager will not automatically log onto networks that use WPA. There is a way to do this though using libpam-keyring. You can read a thread about it here:
[http://ubuntuforums.org/showthread.php?t=463621](http://ubuntuforums.org/showthread.php?t=463621)

The only limit seems to be that it relies on you logging onto your system... you cant have your system automatically log on. 

I use this on my laptop and it works great!

---

### Post by incen on 2008-02-26
I'm not sure if this is the solution though. I meant... it seems it only works when the key to wireless is the same as the key to login my Xubuntu. Am I right? If it's the case, then it seems it cannot work for me since I cannot change the key to the router.
However, I'm so wondering why it just doesn't work even I followed the Ubuntu instruction! :roll:

---

### Post by badmedic on 2008-02-26
Read through it... It relies on the act of logging in, not the password itself. My login password is different from my WPA password.

---

### Post by Sam Lars on 2008-02-26
Could you ask your friend what type of encryption it has enabled?
If Windows works automatically, then it's probably DHCP.  Try typing in the key as each type of encryption and seeing if it will work...
My router at least is reachable by IP, so if my IP address is 192.168.1.101, then the router is 192.168.1.1.  Can you get there in a browser?

---

### Post by incen on 2008-02-26
Mine is WEP. I know it's such a low-security one... well, I don't have a way to change it though. :p

I tried to type in the password in every key type (with WEP): ascii, hex... and only hex works.
Right now I'm at school. I'll try again at night. Thanks anyway! ^^

---

### Post by Sam Lars on 2008-02-26
Well if it's a hex key, it's a hex key... you may be able to convert the hex back to ASCII, but as long as you have the key...

---

