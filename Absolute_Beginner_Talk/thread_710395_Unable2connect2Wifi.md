---
title: "Unable2connect2Wifi"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by NautTboy on 2008-02-28
I have:
Compaq C500T Notebook
1gb RAM
20Gb to work with
Linksys router

Does Ubuntu has what XP/Vista offer?  Autodetect wifi in range?  I'd try to connect to my wireless router but not successful.

network name: name i have for my homenetwork
I chose 64/128bit hex encryption: 26 characters
I chose open wep

What am I doing wrong?

I even tried the phrase encryption which i have 8 character.

---

### Post by TeoBigusGeekus on 2008-02-28
[http://ubuntuforums.org/showthread.php?t=705391]("http://ubuntuforums.org/showthread.php?t=705391")
Perhaps?

---

### Post by anewguy on 2008-02-28
It is quite possible (even more likely) that you need a driver for your wireless before you can use it.  If you click on the network icon on the top bar does it show any wireless networks?  Please do the following and post the results back here so we can help:

open a terminal window (Applications/Accessories, over and down to Terminal)

type:

lspci and press the enter key

post the output back here.  

This command asks Linux to list (ls) the pci (lspci) devices.  Your wireless adaptor will probably show there and then we can work on getting you to the driver.


:)

---

### Post by NautTboy on 2008-02-28
I'm at work now, but i will surely try that when i get home.

I noticed tho, upon loading it said something like can't locate pci source 7 and 8 or something like that.  Is that the driver for wifi card?

---

### Post by stchman on 2008-02-28
> **NautTboy said:**
> I have:
Compaq C500T Notebook
1gb RAM
20Gb to work with
Linksys router

Does Ubuntu has what XP/Vista offer?  Autodetect wifi in range?  I'd try to connect to my wireless router but not successful.

network name: name i have for my homenetwork
I chose 64/128bit hex encryption: 26 characters
I chose open wep

What am I doing wrong?

I even tried the phrase encryption which i have 8 character.

If you hide your SSID(at best a complete waste of time) I have found that Network Manager has problems connecting.

Network Manager will have an icon and when you click on it there will be a list of available wireless networks just like XP and Vista.

What kind of wireless card are you running?  Post an lspci output here please.

If your router and wireless card supports it use WPA or WPA2.  WEP is pretty weak.

---

### Post by NautTboy on 2008-02-28
> **stchman said:**
> If you hide what you mean by hide>  your SSID(at best a complete waste of time) I have found that Network Manager has problems connecting.

Network Manager will have an icon and when you click on it there will be a list of available wireless networks just like XP and Vista.

What kind of wireless card are you running?  Post an lspci Sorry, what is lspci>  output here please.

If your router and wireless card supports it use WPA or WPA2.  WEP is pretty weak.

I have just regular 128 Wep encryption and home network which i name after my last name.

---

### Post by myddewji13 on 2008-02-28
hit alt-f2 ...type in 'gnome-terminal' -->run---> type in lspci ...hit enter... post output...

---

### Post by stchman on 2008-02-29
> **NautTboy said:**
> what you mean by hide Sorry, what is lspci

I have just regular 128 Wep encryption and home network which i name after my last name.

I recommend you use WPA instead of WEP and don't disable SSID broadcast.

---

### Post by NautTboy on 2008-02-29
Here is what I gather up. I was trying to capture the popup when i put my mouse over the connection icon but didn't work. Only work via the accessories-screen capture

stchman, are you saying you want me to reset and redo my linksys router and of course 2-3 other laptop that uses this wifi?  I hate to fix what's not broken.  Or do you mean WPA setting on this laptop?

screen capture included after lspci

---

### Post by Moop on 2008-02-29
You change the wireless security settings on the router. WEP isn't secure and that's why it's suggested that you use WPA. 

There's really not much involved in getting all your PC's to work with WPA. XP and Ubuntu will see the network and ask for the password. 

If you have problems it's easy enough to switch the router back to what works for you.

---

### Post by NautTboy on 2008-02-29
Thanks, but right now I dont think it's my router.  My pc just won't see any signal at all.  As with windows, there's severals that would pop up.

I'll worry about the WPA later after I get connected.

---

### Post by NautTboy on 2008-02-29
it's been 11 hours, anyone?
Asked me to post my result and I did.

Is it my mistake to get rid of vista and load ubuntu?

---

### Post by stchman on 2008-03-01
> **NautTboy said:**
> it's been 11 hours, anyone?
Asked me to post my result and I did.

Is it my mistake to get rid of vista and load ubuntu?

According to the lspci output you have a Broadcom 43xx card.  If you are using Gutsy follow this procedure to get that card enabled.

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver)

Hope this helps.

---

### Post by NautTboy on 2008-03-02
Ok, I'd tried to follow the directioin given from that site.  Here's the capture of the screen.  I did not get the same as the procedure said. I got lost on the next step.  All this time, am i suppose to be connected to internet so that i can get to the repository?

---

### Post by ugm6hr on 2008-03-02
You have a Broadcom wifi card, as stated in lspci output.

Generally, ndiswrapper is recommended for this card (for better stability):
[http://ubuntuforums.org/showpost.php?p=3565453&postcount=112](http://ubuntuforums.org/showpost.php?p=3565453&postcount=112)

If you don't have a wired internet connection to do this with, replace the 1st 2 commands with the following:
[http://packages.ubuntu.com/gutsy/mis...pper-utils-1.9](http://packages.ubuntu.com/gutsy/mis...pper-utils-1.9)
[http://packages.ubuntu.com/gutsy/mis...wrapper-common](http://packages.ubuntu.com/gutsy/mis...wrapper-common)
Just double click on the .deb files to install.

And extract the .exe driver in Windows (and then find the correct .inf and .sys files)

---

### Post by NautTboy on 2008-04-20
I finally got a chance to get back to my funfinish gutsy. I was try to follow the link provided about and I dont understand when it means to :

vi /etc/modprobe.d/blacklist - append "blacklist bcm43xx" to the end

> 
sudo aptitude install ndiswrapper-common
sudo aptitude install ndiswrapper-utils-1.9
sudo modprobe -r bcm43xx
vi /etc/modprobe.d/blacklist - append "blacklist bcm43xx" to the end
- Get proprietary driver from the HP-site: sp34152.exe
cabextract -a ./sp34152.exe
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo echo ndiswrapper > /etc/module





---

### Post by ugm6hr on 2008-04-21
> **NautTboy said:**
> I finally got a chance to get back to my funfinish gutsy. I was try to follow the link provided about and I dont understand when it means to :

vi /etc/modprobe.d/blacklist - append "blacklist bcm43xx" to the end

This means just add that to the bottom of the file.

This can be done with the following commands:
```
sudo cp  /etc/modprobe.d/blacklist  /etc/modprobe.d/blacklist.bkp
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

You should now be ready for the next step.

PS: the first command makes a backup of the original blacklist file.

---

