---
title: "Wireless issues on iBook G4 running Gutsy"
date: 2007-10-25
forum: Apple PPC Users
---

### Post by Madman68 on 2007-10-25
Hi,
I have been using Ubuntu for awhile now and have found that it is a great opertaing system. So I decided to upgrade to Gutsy and thats where the problem started. I upgraded the Ubuntu install on my Apple iBook G4 and now ther is no wireless or eathernet. After the install had finished and restarted I loaded up firefox and when I did a message came up that said I needed to install a restricted driver so that my wireless would work properly. It should be know that before I installed the restricted driver my wireless worked. I figured that it would be a good thing to install the driver it told me I needed to so I just did it the way it instructed me and thats when the problems started. After installing it the wireless and the eathernet both do not work. I decided to try to go into the Network manager to see if anything needed to be turned on or set up. when I tried to open Network manager it froze and I had to restart. Now it looks as though Network Manager is gone and I still can't get any type of internet to work on the iBook. I know that the wireless card isn't broken because the iBook dual boots Ubuntu and Mac OS X. Sorry if I rambled a little bit, or a lot, but I am really annoyed that I now cannot do anything with it. If anyone can help me it would be greatly appretiated.

---

### Post by superFerra on 2007-10-26
I had a similar problem.
Check if NetworkManager process is overloading CPU. I issued 
```

sudo top

```
I noticed that it was near 100% cpu usage. I've killed the NetworkManager process and configured my wireless adapter manually and worked fine.
I've removed NM and installer WICD. It's nice and works very well...

---

### Post by Madman68 on 2007-10-26
I did sudo top and it doesn't report that NM is using anything, it doesn't even show it in the list, but when I try to install WICD it gives me an error because it says NM is still installed, but it doesn't say it is in the Add/remove programs, any ideas what is going on?

Edit:
After making sure that NM was fully installed I got WICD to install. It finds the wireless network and says that I'm connected to it with 80% streangth signal. Yet when I open up Firefox and try to go to a website, it doesn't load. Firefox doesn't say it can't load the page, and it doesn't say there were any errors, it just keeps loading and loading and nothing ever happens.

---

### Post by superFerra on 2007-10-26
you mean fully unistalled?!
```

sudo apt-get remove NetworkManager

```
it will remove NetworkManager and NetworkManager-gnome
then you 

```

sudo apt-get install wicd

sudo /etc/init.d/networking restart


```

...
PS: You can try to disable and re-enable BCM43xx driver again ...

---

### Post by Madman68 on 2007-10-26
yea, I ment fully uninstalled. I tried what you suggested,superFerra , and it didn't work, I've spent a few hours trying a few thing that worked in previous versions but the problem is it isn't just the wifi that isn't working. The eathernet isn't working either, so I can't get anything.

---

### Post by Madman68 on 2007-11-21
Well, sorry to revive an old post but I still havn't gotton the problem fixed. As of right now when using Ubuntu I cannot connect to my wireless internet or connect to the internet by using an eathernet cable. So basically I cannot connect to the internet at all. I've tried many things to fix this and am really regreting upgrading. I have no idea what I should do as I am doul botting Mac OS X and Ubuntu. If you know, or even think you know of something that could help, let me know, thanks again.

---

### Post by ubuntubrian on 2007-12-19
Downgrade to Dapper? It's tough, I know, as I am using Dapper and have been scared away from further upgrades as PPC loses support. Gutsy has the cool graphics and is a prettier OS for sure. Bummer, I know

---

### Post by benlm on 2007-12-21
Try what this thread... 
[http://ubuntuforums.org/showthread.php?t=526901]("http://ubuntuforums.org/showthread.php?t=526901")
It may be helpful, at least it was for me.
Ben

---

### Post by gtcoffee on 2007-12-21
here is my experiences...
1) first time i installed the gutsy on my powerbook g4, i upgraded everything, and seemed working good. However, one day while i was browsing the website my whole screen was froze, and the network  was totally crash after i restart. 

2) So i reinstall the gutsy second time coz i couldnt find any solution. This time the network manager crash again after i upgraded everything, it realli pissed me off...i kept lookin for the solution, and i figured it out its about the "network-manager" package upgrade.

3) i reinstall the Gusty third time...i upgraded everything except  the "network-manager". Now the wireless won't work, but the wire was working, then i go to here "http://www.speedyshare.com/214793933.html" to download the wireless driver and install it. Now wireless is working with no problem. 

Hope this will help you.
** remember don't upgrade the "network-manager"

---

