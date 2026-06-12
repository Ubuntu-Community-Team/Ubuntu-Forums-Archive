---
title: "need help! need wireless, and itunes!"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Dbyrd1985 on 2007-03-14
so i am new at this ubuntu and i have found it is harder than i thought, i cant get wireless on my laptop i installed several programs that show a signal but none will connect.

also i am trying to upload itunes on my comp.  i have wine, but i cant get quick time to load.

---

### Post by oilchangeguy on 2007-03-14
please advise what version of ubuntu you are using.

---

### Post by airencracken on 2007-03-14
What kind of wireless card do you have? What kind of wireless network are you trying to connect to?

iTunes will probably not work, but there are programs that provide most of the functionality of iTunes for linux.

---

### Post by Dbyrd1985 on 2007-03-14
i am on ubuntu 6.10

---

### Post by pillu on 2007-03-14
can you post the result of this command :
```
sudo iwconfig
```

Have you put the ESSID and the key in correctly? Wireless was slightly frustrating for me too in the beginning but I got it to work eventually. 

As for itunes, I don't know how you can access the store but if you just want to use your ipod with linux then amaroK works nicely. There are other programs like gtkpod too if you just want to interface your ipod

---

### Post by Skia_42 on 2007-03-14
iTunes is tricky, there are some exceptional audio programs such as Amarok that are worth checking out. The interface is very easy to get used to. I used to use iTunes, I have found Amarok to be more flexible and easier to use with large amounts of music.

---

### Post by Dbyrd1985 on 2007-03-14
> **pillu said:**
> can you post the result of this command :
```
sudo iwconfig
```

Have you put the ESSID and the key in correctly? Wireless was slightly frustrating for me too in the beginning but I got it to work eventually. 

As for itunes, I don't know how you can access the store but if you just want to use your ipod with linux then amaroK works nicely. There are other programs like gtkpod too if you just want to interface your ipod






right now it says that i have no wireless extentions, and i dont know how to find out what my card is, i just know that i am using a toshiba mx45 laptop

---

### Post by Dbyrd1985 on 2007-03-14
ok i found it, i have a intel pro wireless 2200bg

---

### Post by DynamicJ on 2007-03-14
yeah, his problem with the iTunes thing is that his iPod is locked, and he needs back in to iTunes to unlock it, that way he can use it again with amaroK

---

### Post by Dbyrd1985 on 2007-03-14
:bump:

---

### Post by pillu on 2007-03-14
If it is giving no wireless extensions on all your devices (eth0, eth1 etc) then my guess is that the driver is not installed. My intel wireless has always worked out of the box. But you might want to look into installing the drivers through ndiswrapper or this HowTo

[http://www.ubuntuforums.org/showthread.php?t=12270](http://www.ubuntuforums.org/showthread.php?t=12270)

In a previous post you mentioned that various softwares are able to see your wireless connections. If this is true then your wireless is probably correctly installed. Then I have no idea why iwconfig does not show anything. One thing to try is to disable all other networking like the ethernet card.

---

### Post by Ebacherville on 2007-03-14
Says it works in the wiki:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)

According to the wireless card compatability WIKI it gave this link
[http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)

Hope that helps
Ebacherville

---

