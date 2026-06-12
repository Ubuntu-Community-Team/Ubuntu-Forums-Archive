---
title: "Sound in Ubuntu (Creative X-FI)"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by flightrecorder on 2007-12-05
I'm trying to get sound to work on ubuntu - i just installed a dual boot with windows on a dell xps 600.  i have a creative x-fi sound card, but ubuntu isn't playing nice with it. there does seem to be a beta driver from creative for it, but i have no idea whether it is safe or how to install it. suggestions? I can't seem to find an answer on google.
thanks.

---

### Post by KhaaL on 2007-12-06
There X-Fi beta driver- which is more of a pre-alpha driver IMO - is a hassle to install since it requires a 64bit OS and a kernel compiled with a older version of gcc. Which makes a lot of people think that this is a driver they've had worked on previously and now are throwing out publicly in order to show that they're doing something for supporting their soundcards on linux.

X-Fi cards might take a while til' they work on Linux. My recommendation is either to use the onboard soundcard, or purge the creativeness from your computer and replace it with something else.

---

### Post by flightrecorder on 2007-12-06
how do I use the onboard soundcard? i've tried looking in the device manager and sound preferences.

---

### Post by KhaaL on 2007-12-06
It should work out of the box. Do you have your wires connected to it? whats your motherboard - or if you know what chipset does it use for sound?

---

### Post by flightrecorder on 2007-12-06
everything's connected - it works fine in windows. my chipset is Nvidia nForce4 SLI X16 MCP.

---

### Post by KhaaL on 2007-12-06
According to nvidia ( [http://www.nvidia.com/object/linux_nforce_1.23.html](http://www.nvidia.com/object/linux_nforce_1.23.html) ) there is drivers and it's included in the kernel by default. Since I'm not too familiar with nForce chipsets I'm unable to help you further... 

Make also sure that your audio is enabled in your mixer.

---

