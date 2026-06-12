---
title: "wireless help"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by imacbo on 2007-03-21
ok i have a Broadcom 802.11 b/g wlan card this is the only way i can get online what do i need to get ubuntu to work?

---

### Post by sad_iq on 2007-03-21
Please paste the response of this comand: **lspci | grep Broadcom\ Corporation**

---

### Post by hfranco on 2007-03-21
Open a terminal and become sudo.  Type iwconfig and see if there are any interfaces available.  You might see something like:

hfranco@Linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

If you do have a wireless extension the you supply iwconfig with the necessary parramaters like:

hfranco@Linux:~$ iwconfig eth0 essid THISISYOURSSID key THISISYOURKEY

Or if you're lazy just right mouse click on the network icon by the clock on the right hand side.

---

### Post by oilchangeguy on 2007-03-21
let's make this real simple. non of this un-needed command line stuff. just go to system, admin, networking. what's listed?

---

### Post by imacbo on 2007-03-21
it shows a card but i cant seem to get it to work. the light on my computer for my wireless will not come on. also is there someway to get the WEP key from my windows over to the Ubuntu? I dont know the key. I am in Kuwait and the Army is the one that supplies the key so if I cant get the key from windows i will have to wait untill tomorrow to get it. Also I did not see when to enter the WEP key

---

### Post by oilchangeguy on 2007-03-21
define, it shows a card. you should see three things. your ethernet card, eth0, your wireless connection, wlan0, and maybe the phone modem. the two network connections should show as active. and no you can't get the wep key from windows. even if you could it would look like this **************. so it would be useless.

---

### Post by brontosaurus on 2007-03-21
Broadcom has not opened up its cards to have official Linux drivers made for them, so you're going to have to use reverse-engineered drivers.  Instructions for getting these installed can be found here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx).

---

### Post by oilchangeguy on 2007-03-21
and STOP creating multiple posts on the same subject! [http://www.ubuntuforums.org/showthread.php?t=390315](http://www.ubuntuforums.org/showthread.php?t=390315)

---

### Post by imacbo on 2007-03-21
ok i am having some trouble. i have a broadcom 4318 card and everything i have found about getting the firmware involves being able to connect with ubuntu. this i can not do. so can someone help me out and get the needed firmware or something so i can save it to my portable hard drive so i can then put it in ubuntu

---

### Post by imacbo on 2007-03-22
I tried all of the links and I can not get it to work. iwconfig lets me know its there and that it is a broadcom 4318 card. the only way I can connect to the internet is in windows and i need to find somewhere to get the firmware and then download it to my portable hd and then boot in unbuntu to install it. I am way to new to unbuntu to know what I am doing so can some one please help me

---

### Post by brontosaurus on 2007-03-22
Could you give more details about your internet connection?  If you have a wireless router, what you have to do is unplug it and plug into the ethernet port- hardwiring into the internet.  Otherwise, I'm not sure.

---

