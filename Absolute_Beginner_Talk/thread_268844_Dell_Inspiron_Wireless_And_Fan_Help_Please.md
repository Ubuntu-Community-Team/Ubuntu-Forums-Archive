---
title: "Dell Inspiron Wireless And Fan Help Please"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2006-09-30
I recently installed Kubuntu and I love it. But I am having two problems.

1. My fan is not turning on. I got gkrellm and it manages it, but how can I make it run at start up and take care of the fan situation?

2. My Wireless is not working. I downloaded the Wireless Network Drivers Program. What else do I need to do?

3. What do I need to make the volume buttons work properly. (They aren't working at all.) I know I need some kind of hotkey program, but I don't know what. The volume is accessed through the Fn+PgDown,etc function.

Thanks in advance.

---

### Post by onioneater36 on 2006-09-30
what kind of wireless card do you have?  Do you know what chipset your wireless uses?  For example, I have a WG511T netgear card that uses the "atheros" chipset.  For "atheros" chipset wifi, you use the "madwifi" driver which is included in Ubuntu and should be pre-setup for you.

Here are some terminal prompt commands that help out alot...

"ifconfig" will list all your network interfaces (eth0, ath0, lo, etc) and show you what IP address they have, etc.  If you want to see the settings for just one of these interfaces, you can type in "ifconfig ath0" for just the atheros card.

"iwconfig" will show you which one of these devices support wireless, what the current state of the wireless is.

"iwlist ath0 scan" will show you a list of all the access points you can hear and how good the signal quality is.

"iwevent" will monitor the wireless interface and post any error messages when the network drops or anything bad/unexpected happen (useful for debugging).

I still don't have mine working 100%, but I am really close.  I have been getting a lot of help from...

[http://www.ubuntuforums.org/showthread.php?t=263136]("http://www.ubuntuforums.org/showthread.php?t=263136")

What kind of security do you have setup in your router (WPA, WEP, etc).

---

### Post by tdrusk on 2006-09-30
According to what you told me to do, my wireless card is a Broadcom 4318.
Kubuntu isn't even allowing me to enable the card. That specifies a driver issue correct?

---

### Post by Scheater5 on 2006-09-30
I also have a dell Inspiron, and I had wireless troubles, too.  I couldn't get a wireless driver native to Linux to work, but I had a Windows install on another partition with Intel Proset on it.  (As far as I know, all the Inspiron laptops can use Intel drivers - so you should be able to do the following as well)  So I made a copy of those drivers and moved them to my Ubuntu file system (you could probably leave it there and just mount the drive - assuming you still have your Windows copy, otherwise you'll still have to get a copy of Proset.  It's avaiable for download on Intel's site).  Then I got a program called "ndisgtk" which is in the repositories I think, but I'm not sure which one.  You can then load the Windows driver up and use it in Linux.  I'm afraid I'm not sure I could do it again myself, much less give you detailed more instructions - but if you think this is a viable solution, perhaps someone else can give you more detail.  Good luck.

---

### Post by LookTJ on 2006-09-30
I have Dell INSPIRON 600m and i have intel 2200BG wireless, no issues

---

### Post by tdrusk on 2006-09-30
Okay. Does anyone know how I can get a program (gkrellm) to start running at startup? I need it so my computer doesn't overheat.

I am going to work with my router tommorow. I think the WEP is the problem.

---

### Post by onioneater36 on 2006-09-30
fuzzyhair...

What Scheater5 is referring to is using ndiswrapper methods to get your drivers working.  If you search for "ndiswrapper ubuntu wireless broadcom" in google or on the forums, you should be able to turn something up.

Check out...

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

for compatibility information regarding your card.  I don't see the 4318, but I do see the 4306 and it looks like someone else was using ndiswrapper drivers too.

Good luck and I hope someone more familiar with your hardware chimes in to help you.

---

### Post by onioneater36 on 2006-09-30
Regarding gkrellm starting up automatically, I am assuming you are using UBUNTU with GNOME desktop.  Go to SYSTEM > PREFERENCES > SESSIONS and then to the STARTUP PROGRAMS tab.  

Click the add button and then type gkrellm and it should add it to the startup programs.

---

### Post by Scheater5 on 2006-09-30
Onioneater - fuzzyhair mentioned he was using Kubuntu.  In which case you could try going to System Settings under the K Menu.  System Settings > KDE Components > System Session has an option to "restore previous setting" - which would get the result you want if you close all programs *except* gkrellm before shutting down every time.  You could also save a session with gkrellm being the only program active, which would also yield the same results.  As for setting gkrellm to automatically start up everytime, regardless of your saved session, that I don't konw how to do.

---

### Post by Frak on 2006-09-30
If you read his first post it said *KUBUNTU*.

---

### Post by tdrusk on 2006-10-01
Is there any chance the new Beta will work with my card?

---

