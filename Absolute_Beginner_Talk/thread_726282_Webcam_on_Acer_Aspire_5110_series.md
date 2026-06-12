---
title: "Webcam on Acer Aspire 5110 series?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Nante on 2008-03-16
Just installed Ubuntu 7.10 on a Acer Aspire 5110. I bought it from work with no hard drive so I have no idea of what kind of drivers it may need, the webcam is built in and is the only thing that Ubuntu did not recognize upon install. I searched the archives and other online sources and could not find anything, anyone know what I might try?

---

### Post by linuxwizard on 2008-03-16
Post results of the command > lsusb

---

### Post by Nante on 2008-03-16
:~$ lsusb
Bus 003 Device 002: ID 0402:5602 ALi Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 001 Device 004: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000

---

### Post by linuxwizard on 2008-03-16
This is your webcam > Bus 003 Device 002: ID 0402:5602 ALi Corp > 

Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.
To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by Nante on 2008-03-16
Installed Ekiga, played around with all the settings under video and video codecs, no luck, it keeps saying no device found and the bouncing ball stays put.

---

### Post by linuxwizard on 2008-03-16
Ok that is what I wanted to know. Alot of webcams just work no need to install a driver. I like checking to see if they work first before installing the driver. I will look for the driver you need.

---

### Post by Nante on 2008-03-16
Thank you, I really appreciate it :)

---

### Post by linuxwizard on 2008-03-16
The driver is still in development. Go to [https://sourceforge.net/projects/m560x-driver/](https://sourceforge.net/projects/m560x-driver/) . Your cam is not going to work no driver yet for it.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/61669](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/61669)

---

### Post by Nante on 2008-03-16
Thank you, I bookmarked the links and will keep checking, driver dev is way over my head. I really appreciate your time, I googled for hours trying to find info on how to make it work, guess I should have posted here earlier :)

---

### Post by linuxwizard on 2008-03-16
You're Very Welcome Glad that I was able to help you. Just wished it was better news on the driver. Good Luck

---

### Post by pastormick on 2008-03-16
Hi Nante - I just gave the 5100 that had my Unubtu on it to my wife (after installing Windo$e on it for her *sigh*) I spent more than eight months trying to get the cam going in my 5100, it had the element in it that used the Bison driver. Got it to work (sorta...) with Ekiga once - for two photos. But nothing that even remotely resembled a permanent fix. I really hope you have better luck. As for me, I finally went out and bought a Logitech ball camera thingy; not quite as elegant, but then I'm not as inclined to forget that it's on and stream myself doing the 'Chicken Dance' to the internet...\\:D/

Mick

Hmmm... I wonder if a guy could use the Win drivers through ndiswrapper? (I wonder why I had this flash of inspiration after it's too late?!?)

---

