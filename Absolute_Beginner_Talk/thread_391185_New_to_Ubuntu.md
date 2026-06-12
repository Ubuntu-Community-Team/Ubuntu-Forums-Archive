---
title: "New to Ubuntu"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by F10AB/1B on 2007-03-22
Hello everyone.  This is my first post but probably not my last.  I became fascinated with Linux a while ago so I took the plunge and installed Ubuntu 6.10 on my Acer Aspire 3002LCi laptop as a dual boot system along with Windows Home.  Everything went very well indeed and now I have a functional dual boot system.
The first problem I encountered was that my built in wireless won't work with ubuntu but it still (and always has) works under Windows.  I read tons of posts on this site and it seems that there are as many ways to address the problem as there are users of ubuntu.  Also  most seem to involve typing in line after line of code and I (having only dealt with Windows before) break into a cold sweat at the thought of typing any code.
A really nice super user friendly instruction set for solving the wireless problem would be great.

---

### Post by Benchrest on 2007-03-22
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_consume_static_.28not_dhcp.29_wireless_LAN_.28WLAN.29_connection_.28KDE.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_consume_static_.28not_dhcp.29_wireless_LAN_.28WLAN.29_connection_.28KDE.29)

This is from the Edgy Guide. It has a lot of good stuff. The link here goes into how to set up wireless. Hope it helps.

---

### Post by bodhi.zazen on 2007-03-22
First Welcome to Ubuntu.

I understand, the terminal, or command line interface is intimidating at first.

See if this helps get you started :

[http://www.linux.com/article.pl?sid=06/09/05/2055232](http://www.linux.com/article.pl?sid=06/09/05/2055232)

To open a terminal 

Applications -> Accessories -> Terminal

To gain administrative privileges (root) use sudo in front of your commands, enter you log-in password.

Or if you are going to do multiple commands, ```
sudo -i
```

If you get stuck, let us know where you are.

---

### Post by F10AB/1B on 2007-03-23
Thanks for the reply.  There seem to be a lot of knowledgeable and helpful folks out there in Ubuntu land.  I am treading softly here but I think that I have overcome my initial fear of using the lines of code.  I thought that maybe I was too old a dog to learn new tricks but perhaps not.  I still haven't got my wireless working but there is hope!

---

### Post by joethenoob on 2007-03-23
I've just recently made the jump to linux as well, so I can relate.

I also had problems with my wireless. Have you tried installing NetworkManager? You can get it from the Synaptic Package Manager. The package manager has made my linux learning a lot easier.

Click System>Administration>Synaptic Package Manager. You'll be prompted for you system password. Once Synaptic is running, click Settings>Repositories. In the Repositories screen, check the box for (universe) and click close. You should get a warning telling you to reload your package list. Close that warning and click the Reload button. It will take a minute to update your lists.

Once the lists are updated, use the Search funtion and enter network-manager. Once you get your search results, right-click on network-manager and select Mark for Installation. You may be prompted that you also have to install additional packages that the network manager relies on. Go ahead and accept it. Now all you have to do is click the Apply button to get the install going.

Once the install is done, log off and log back on. You should see the NetworkManager icon up near your clock and sound controls. When I'm not using a wired connection (and I want to use my wireless card), all I do is right-click on the networkmanager icon and it shows me the available wireless networks. I selected mine, entered the WPA info and was off and running.

If any of this is off a bit, let me know and I'll fix it. Like I said, I'm new to linux as well and the Ubuntu crowd has been a great help. Just trying to do my part and help the next guy.

---

### Post by F10AB/1B on 2007-03-24
Hello again.  I have been reading forums and trying things until I have a headache and my eyes are crossed and still no wireless.  I did succeed in getting the wireless indicator light on the front of the laptop to come on but that is all.
I appears that I have the dreaded "BCM4318 AirForce One" version of Broadcom built-in wireless so maybe that is part of the problem.  This thing worked virtually automatically with Windows XP so why must it be such a problem with Ubuntu?

---

### Post by F10AB/1B on 2007-03-31
Hello, its me again.  I have been trying all sorts of things to get this wireless working to no avail.  I thought I had found the Holy Grail in the form of "floppyjoes.homeip.net" and I followed the instructions therein (at least I think I did) but, alas, no cigar.  I have my wireless light on the front of the laptop on and it shows both the hardware and driver installed and the wireless is activated (checked) but nothing!  Abject frustration-ugh!  Also I do not have a wireless icon by my clock-there is one for wired network but not for wireless.

---

### Post by brownknight on 2007-03-31
Hi. I'm a noob too. I found this thread with people having the same laptop as yours and same wireless problem. Check this out maybe it can help.

[URL="http://www.linuxquestions.org/questions/showthread.php?t=348619"]http://www.linuxquestions.org/questions/showthread.php?t=348619
[/URL]

 I cant explain this as Im a noob too. Im just trying to help with your search for an answer.

---

### Post by Floppyjoe on 2007-04-09
> **F10AB/1B said:**
> Hello, its me again.  I have been trying all sorts of things to get this wireless working to no avail.  I thought I had found the Holy Grail in the form of "floppyjoes.homeip.net" and I followed the instructions therein (at least I think I did) but, alas, no cigar.  I have my wireless light on the front of the laptop on and it shows both the hardware and driver installed and the wireless is activated (checked) but nothing!  Abject frustration-ugh!  Also I do not have a wireless icon by my clock-there is one for wired network but not for wireless.

It sounds like you may be using Network-Manager here by the description of the Icon by the clock. For that to work properly in Ubuntu 6.10 Edgy Eft you have to disable all your network interfaces in System/Administration/Networking(This is not the case in Feisty)

---

### Post by mshale on 2007-04-09
f10ab, Hi, I'm newish to linux now.  try and download 7.04(beta) release.  It's called Feisty. It's officially released in like 10 days so its not all that "beta".  Burn that to a disk and boot to that LiveCD and try it out.  you can see if that helps your wireless situation.  See, in Edgy, you had to know the name (SSID) of your router before you could connect to it.  In Feisty, it's different.  I suggest you give it a go, after all, you wont break your system by trying it, cuz it's a LiveCD, so no existing files are overwritten!

Enjoy! :popcorn:

---

### Post by F10AB/1B on 2007-04-25
Hello again.  Things are looking better.  I upgraded to Fiesty a few days ago and I finally got my wireless working!  Now I have another question for all you nimble minds out there.  My laptop has a Synaptics (I think I have the name right) touch pad device that serves as a crude mouse.  My laptop is a dual boot system with WinXP and when I am using windows I can control the properties of this device.  I cannot find a way to do the same with Ubuntu.  Particularly irksome is having a tap on the pad act the same as a left mouse click-I would like to disable this as I did with WinXP.  I usually use a wireless mouse with the laptop anyway.  When I type my thumbs get in to trouble with the touch pad!

---

