---
title: "Internet connection problem"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by wolfshark on 2006-05-21
Hi, this is my first post. Please excuse me about the bad english.
I had ubuntu 5.10 and i didnt find a way to configure my internet connection. It's a broadband connection that requires username and password. Now i am with ubuntu 6.06 and I still can't configure it. I tried pppconfig but that is for a phone modem, so it didn't work. I don't know what to do, please help me :(

---

### Post by bikeboy on 2006-05-21
What sort of broadband is it, xDSL? How is your computer physically connected to the modem, usb or ethernet?

With a bit more info it should be simple to help you.

---

### Post by wolfshark on 2006-05-21
It is conected via Ethernet and I think that is PPPoE. I am newbye so i don't know how to explain it. If you want i can explain it how I configure it in Windows :mrgreen:

---

### Post by bikeboy on 2006-05-21
When connected by ethernet you would normally go to System > Administration > Networking, type in your normal password. Click on your ethernet card and go to Properties, make sure it's setup right, asssign an IP address if you're not using dhcp. The gateway address is the address of your modem/router if you have one. Also add the dns server of your isp.

When networking is setup correctly you should be able to get internet access because your modem will take care of the rest, there is no need to configure PPPoE or anything in Ubuntu itself if you're connected via ethernet.

If I'm wrong about you're situation then yes it would be useful to tell us how you do it in windows.

---

### Post by wolfshark on 2006-05-21
My IP isn't static and i don't know the dns server of my isp. My connection REQUIRE username and password.
In windows it is something like this:
Connect using a broadband connection that requires username and password

---

### Post by jorn on 2006-05-21
If you open: System> Administration> Networking
Do you see:Ethernet connection :The interface eth0 is active?
Click Properties. Is Dchp activated?
Im not shure it leads to solution. Just trying to help.

---

### Post by wolfshark on 2006-05-21
[QUOTE=jorn]If you open: System> Administration> Networking
Do you see:Ethernet connection :The interface eth0 is active?
Click Properties. Is Dchp activated?
Im not shure it leads to solution. Just trying to help.[/QUOTE]
Yes, there is eth0 and it is active. In the properties Dchp is activated. How to enter my username and password for the connection???

---

### Post by bikeboy on 2006-05-21
Hmm I see. Try opening up Synaptic and searching for packages names pppoe. I have 2 listed, pppoe the driver (not installed) and pppoeconf. I'm guessing you need both of those installed.

Once they are, open up a terminal and type ```
sudo pppoeconf
``` to start the config wizard. It's not fancy but it might be what you need.

---

### Post by wolfshark on 2006-05-21
[QUOTE=bikeboy]Hmm I see. Try opening up Synaptic and searching for packages names pppoe. I have 2 listed, pppoe the driver (not installed) and pppoeconf. I'm guessing you need both of those installed.

Once they are, open up a terminal and type ```
sudo pppoeconf
``` to start the config wizard. It's not fancy but it might be what you need.[/QUOTE]
YES! That worked. THANK YOU VERY MUCH!

---

### Post by jorn on 2006-05-21
What happens if you open your browser? I remember once I had to type an internet site into the browser to get online and then where asked for password.
Did't you get some information from your ISP?
Edit:  ok you got the correct help. That's good.

---

### Post by bikeboy on 2006-05-21
[QUOTE=wolfshark]YES! That worked. THANK YOU VERY MUCH![/QUOTE]

Awesome, I learnt something myself there too.

---

