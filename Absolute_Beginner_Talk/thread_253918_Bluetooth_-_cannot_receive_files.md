---
title: "Bluetooth - cannot receive files"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by lorre on 2006-09-09
I have a mitsumi bluetootusb dongle. If I try to send a file using bluetooth in nautilus with 'send to' nautilus crashes, I have searched on this forum and it seems to be a known problem. 

After installing kbluetooth-manager I was able to send files using the Bluetooth OBEX client. Unfortunately I cannot browse my phone with this client but can only send files to the phone.

If I try to send a file or connect from my phone to my pc the phone gives a connection failed message.

What can I do to receive the files that are on my phone?

---

### Post by Fedz on 2006-09-09
I searched for the PCs bluetooth via the phone, then paired them (on the phone) using passcode 1234 and then it allows sending to the PC.

Hope this helps

---

### Post by lorre on 2006-09-09
If I search for devices using my phone I can see my PC. The only problem is when trying to connect it gives a connect failed error message. I don't get to the part where I have to give the pin.

Funny thing is that I am able to connect from my pc to my phone but only for sending files. I am wondering -since I can connect from pc to phone- if it's possible to browse and download files on my phone from my pc.

Does the obex client of kbluetooth-manger only support sending of files to other bluetooth devices or is it capable of browsing and receiving files as well?

---

### Post by Fedz on 2006-09-09
Depending on your phones model you goto bluetooth and then too paired devices > press search > then pair > asks for PIN (default on Ubuntu is 1234).
You don't actually send anything or whatever until you've paired as it'll say unable to connect as you say it does.

Have you opened a command window and typed **kbluetoothd** as that's how I started when I enabled bluetooth on Ubuntu, which by the sounds of it you've already enabled.

I then did as I said before and on my phone searched found the PC and paired > then phone asked for the PIN (Ubuntu default - 1234) and it paired.

I couldn't send files to the PC until I paired them both.

I am of the understanding browsing isn't allowed.

---

### Post by lorre on 2006-09-10
Hi,

The problem is when I search for devices on my phone it shows a list of found devices (nokia). The only option I have is to select a device from the list, and when I try to select my pc, it gives the connect failed error. I did not get a chance to enter the pin (so it's probably "press search > SELECT > then pair > asks for PIN")

---

### Post by Fedz on 2006-09-10
The only conclusion is that all my Nokia phones must have been different to yours!

I've always gone to connections, bluetooth, search for paired device, then pair, then PIN.

'Connect failed' (like you're getting) is what I get if I forget to pair first (as above).

Kind regards

---

### Post by bigken on 2006-09-10
take a look [here]("http://www.ubuntuforums.org/showthread.php?t=94713") this might help you :wink:

---

### Post by lorre on 2006-09-10
bigken; that howto unfortunately does not work for me, it fails when I select my pc as the target device (connection failed).

I did find this howto: [http://ubuntuforums.org/showthread.php?t=34740](http://ubuntuforums.org/showthread.php?t=34740) that made it all work. 

Anyway thnx for the hlp

---

### Post by Fedz on 2006-09-10
Pleased to learn you managed to get bluetooth working :D

I do it differently. I either type kbluetoothd in a command window OR (as I have done now) on Desktop, right click, create new launcher and use the following:
Name: Bluetooth | Generic Name: Bluetooth | Comment: | Command: kbluetoothd | Type: Application | Icon: locate the bluetooth icon

The all I do is double click the bluetooth icon on desktop to use it :)

Kind regards

---

