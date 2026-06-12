---
title: "Acer 5920G Help"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by chirpilittle on 2008-03-08
I've installed Ubuntu on an Acer Aspire 5920G and was wondering if anyone could help me with the sound. At first I couldn't hear anything, but when I used the terminal to go into the alsamixer settings, I could adjust volume from there. My problem is that the sound wheel on the front of the laptop is useless for sound. A screen pops up to show that sound is increasing or decreasing, but the volume never changes. Is there anyone who can help me out? 

I also had a question about Ubuntu on Laptops. Is it really true that a patch is needed for when the laptop is not plugged in and is running Ubuntu on just battery power? If so where can I find this patch?

Help is very much appreciated.
Thanks 
chirpilittle

---

### Post by JeffoOfMetal on 2008-03-08
No, you don't need any patch to run your laptop on battery. I run mine on battery with Ubuntu and there are absolutely no problems.

As for the sound, I found this worked: Go to the volume control and open the mixer. Turn up and unmute Surround if it is there. That's what has worked for me...

---

### Post by EnergySamus on 2008-03-08
I have an Acer Aspire 3690 laptop that does the same. My volume buttons on my Keyboard won't work... Maybe it is an Acer thing:lolflag:

EnergySamus

P.S. That Gemstone Design rocks:lolflag:

---

### Post by spegru on 2008-03-09
The 5920 is different becuse there is a physical control wheel on the front edge for volume. The machine does react to the wheel, with a little volume graphic popping up. However it only goes from zero to about 15% and anyway the sound level doesnt change.
Seems it's almost working - must be easy to fix.....

any ideas out there?

spegru

---

### Post by igknighted on 2008-03-09
> **spegru said:**
> The 5920 is different becuse there is a physical control wheel on the front edge for volume. The machine does react to the wheel, with a little volume graphic popping up. However it only goes from zero to about 15% and anyway the sound level doesnt change.
Seems it's almost working - must be easy to fix.....

any ideas out there?

spegru

Right click the volume applet in the panel (the one that looks like a speaker), then select preferences.  Choose the audio channel you want to control (usually main), and turn the others up (in the mixer) to a consistant level so that you can use main to do the adjustments.

---

### Post by EnergySamus on 2008-03-10
I just booted into Ubuntu and my sound is now working! Maybe it was a small glitch or something... I hope that your sound controls work soon!

EnergySamus

---

### Post by spegru on 2008-03-12
I reinstalled alsa to the latest version and almost everything is now fine
Volume control works properly

only other thing is that the built in mic is too quiet even with 20dB boost on.....

---

### Post by chirpilittle on 2008-03-15
Thanks for all the help but I still can't seem to make the wheel react. As for the built in mic, check the recording levels. There could be a setting you missed.

---

### Post by AndyWaRoll on 2008-03-16
Hello !

First, sorry for my bad English, I am French. ;-)

Just to tell you that I also have a 5920G and I just found how to get the wheel working !

You need to go to System/Preferences/Sound, and then in the first tab (I don't know its name in the English version), check "Front" and "Surround" in the list at the end (hold shift to check more than one thing). Then close the Sound window.

Your wheel should work perfectly fine now !

Maybe you should help me with one of my problems, I am experiencing trouble with the wi-fi, even after installing the acer-acpi package (although it helped). Did you do anything more to make it easier ?

Seeya !

Kenny

---

### Post by chirpilittle on 2008-03-17
> **AndyWaRoll said:**
> Hello !

First, sorry for my bad English, I am French. ;-)

Just to tell you that I also have a 5920G and I just found how to get the wheel working !

You need to go to System/Preferences/Sound, and then in the first tab (I don't know its name in the English version), check "Front" and "Surround" in the list at the end (hold shift to check more than one thing). Then close the Sound window.

Your wheel should work perfectly fine now !

Maybe you should help me with one of my problems, I am experiencing trouble with the wi-fi, even after installing the acer-acpi package (although it helped). Did you do anything more to make it easier ?

Seeya !

Kenny

THANK YOU SO MUCH! my wheel is working perfectly now!

What sort of trouble are you experiencing with wifi?
Mine automatically detects any wi-fi activity and I didn't need to install anything.

---

### Post by AndyWaRoll on 2008-03-17
> **chirpilittle said:**
> What sort of trouble are you experiencing with wifi?
Mine automatically detects any wi-fi activity and I didn't need to install anything.

Well, before I installed the acer-acpi package, I couldn't even connect to my own wi-fi network. Now, it works, but not every time. Sometimes he just waits to be connected, and if I push it to its limits, the nm-applet application (the little icon in the bar) closes and I have to restart it. The only solution I found was to reboot and hope that it works again...

Kenny

---

### Post by natirips on 2008-03-17
> **AndyWaRoll said:**
> Well, before I installed the acer-acpi package, I couldn't even connect to my own wi-fi network. Now, it works, but not every time. Sometimes he just waits to be connected, and if I push it to its limits, the nm-applet application (the little icon in the bar) closes and I have to restart it. The only solution I found was to reboot and hope that it works again...

Kenny

I had the same problem on my 5520G (it wouldn't always connect to my wlan network at home, but it could always connect to any other wlan network in range <doh>). Check the name of your driver (right-click the network icon in the tray, and then check information about the connection), then go to console and reload the driver:```
sudo modprobe -r drivername
sudo modprobe drivername
```.In my case the driver is "ndiswrapper" so it is ```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```. It always works after that (note that it takes about half a minute for the card to detect your network after this).

See "man modprobe" in console if you're curious of what modprobe does. And just in case you don't know, use Q key to exit the MANual.

Edit: I later noticed it doesn't ALWAYS work, if it doesn't work just repeat the pattern a few more times, it just might work out...

---

### Post by rishubhai on 2008-03-18
hi andy,
thanks a ton for the resolving my volume issue.
i did nothing for my wifi. 
it has always been working fine.

---

### Post by errenay on 2008-03-18
> **AndyWaRoll said:**
> Hello !

Just to tell you that I also have a 5920G and I just found how to get the wheel working !

You need to go to System/Preferences/Sound, and then in the first tab (I don't know its name in the English version), check "Front" and "Surround" in the list at the end (hold shift to check more than one thing). Then close the Sound window.


Maybe someone knows how I could do this in Kubuntu?
In Kubuntu there is nothing like menu mentioned above and in Kmix I could select only one "main channel" :(

---

### Post by chirpilittle on 2008-03-31
sorry I don't know what to do in Kubuntu, but why don't you try opening the volume using the terminal and testing the wheel, apparently it's all you have to do according to a friend of mine. I would try to specify more but I don't know the exact steps, sorry.

---

