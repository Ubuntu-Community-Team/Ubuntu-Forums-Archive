---
title: "wireless internet problem"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by el_tuki on 2008-04-09
i just started using ubuntu so i dont know much about how to use it. i have been trying to log on to my school's wireless internet but it just wont connect. i have my computer partitioned so i still have windows and when i log on to windows i can connect through the wireless. i am putting the right user name and password so i have no clue why it is not working. if anyone can help i would really appreciate it.

---

### Post by DK-420 on 2008-04-09
A little more information would be helpful.

Is your school network DHCP or is it Static?

Also, if it is a static IP, are you inputting the IP address correctly and also adding the proper Primary and Secondary DNS?

---

### Post by el_tuki on 2008-04-09
to tell you the truth im not sure but i wasn't putting anything else besides by user name and password. on windows thats all i needed. i dont know how to find that information though.

---

### Post by DK-420 on 2008-04-09
In Windows, if you go to the Network Connections Settings in your Control Panel, you can right click your Wireless connection and go to Properties. 

Find the Internet Protocol in the white box, and click Properties.

 If you see the radio button that says Obtain IP Address Automatically and it's ticked, you're IP address is given dynamically. If the other radio button is ticked that says "Use the following IP Address" then you know you have to put your IP address in statically. Below there will be the Primary(Preferred) and Secondary(Alternate) DNS settings

Start there, and see what it says.

If it is set to static, then you have to manually add that information into Ubuntu Network Manager in order to connect to the internet.

---

### Post by el_tuki on 2008-04-09
ok so the radio button that says Obtain IP Address Automatically was ticketed so its not static.

---

### Post by lackofcreativity on 2008-04-09
Is it using WEP or WPA encryption? If so, is the key put in right? Double-check your spelling, I wish I had done that before... I learned the hard way :mad:.

---

### Post by |{urse on 2008-04-09
open up your terminal (located under Accessories in the menu)
type in 

sudo iwconfig

you should now be able to determine the name given to your wireless connection

usually its something like eth0, ath0, wifi0, wlan0 etc. but not lo (thats just the loopback)

type in

man iwconfig

this will give you the full manual for iwconfig which is an immense help sometimes. Just follow the instructions for specifying the mode (sudo iwconfig mode eth1 Managed for example would be the command to set your connection to a managed wireless connection) then set the correct essid and wep key etc.

now you said something about a username and a password, well, if its wpa psk/tkip encryption that should be tons of fun and i wish you the best of luck.

also make sure your respective connection is actually up 
for example

sudo ifconfig wlan0 up

---

