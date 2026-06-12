---
title: "Omg, I hate wireless!"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-05-27
I am literally pulling my hair out. I still have no working internet connection on my linux machine.

I think that my problem is that my laptop isn't connecting to my access point. I have downloaded KWiFiManager. It says:
Searching for network: WANADOO-3EB4
Access Point: -no access point-
Local IP: unavailable
Access Point : N/A

So its definatley not detecting my access point. But I don't know whether linux is detecting my card either. I mean I definatley have the driver, but in Network Tools, Network device says "Unknown Interface (ra0)" which makes me wonder whether its actually detecting my card or not.

Please help. I'm on my knees :p

---

### Post by Super King on 2006-05-27
Are you using Kubuntu or Ubuntu? If you're in Ubuntu, go to System->Admin.->Networking, and see if your wireless card is enabled or not.

---

### Post by cowley on 2006-05-27
hi - are you using the inventel usb with this??  can you connect to other wireless networks(unsecured etc)  - i also have wanadoo livebox and think the issue may be there.

simon

---

### Post by tartarian on 2006-05-27
Yes my card is enabled - as ra0. It's all configured with the wep key entered, the network name and everything

---

### Post by tartarian on 2006-05-27
No, Im using the built-in wireless card with my laptop. so its not the usb dongle. grrr

Any other ideas PLEASE!!!

---

### Post by Ephemeral on 2006-08-16
I have a LiveBox, but no internet on my Ubuntu box, anyways,I am a noob, but this may help.
In the Terminal, type :
```
iwconfig
```
If you see your card, then it's good, if not, your card isn't configured with your Ubuntu PC.
If you have a USB key of some sort, or a CD-RW, try giving us the outcome of iwconfig.
Next, try :
```
iwlist scan
```
IF that shows NOTHING, try :
```
iwlist scanning
```
IF there are no scan results you may still have a problem.
COnsidering the fact you have a Livebox, use the PC that has access to it and enter it :
(usually 198.162.1.1)
and use username, admin and password admin.
Now, hoping you can make your LiveBox English, click the Wireless tab, there you should find the WIreless Network Setup.
Just for test purposes, turn the Security off, so that it is easier to get your card to access the LiveBox.
Next, find the mac address of your dongle/wifi USB key/whatever, which is a serie of numbers like :
00:00:00:00:00:00
Twelve numbers in total.
ANyways, you want to note that down and go to the link to edit the Mac filter list.
On the top, it should be : Permit only listed PC's.
You have to add the MAC address of your dongle there.
LiveBox is horrible and stubborn, you have to manually allow access which is a waste of time.
Now, in the Terminal on your wifi box, try editing some things, such as :
Your access point, with the command :
Before you do so, find the Mac address of your LIVEBOX.
sudo iwconfig ra0 ap MAC:ADDRESS:OF:YOUR:LIVEBOX
Then, when you do iwconfig, the access point should be the mac address of your livebox.
I can't remember ALL commands, but you should search forum for them.
Basically you want to get iwconfig ra0 to display everything you need.
I am a noob at this, but I recommend you talk to maniacmusician, he will be able to help you more.
Mark

---

