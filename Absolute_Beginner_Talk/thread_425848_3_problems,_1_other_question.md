---
title: "3 problems, 1 other question"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by schmidtbag on 2007-04-28
I've been frustrated with this for a while, and I can't figure out why I can't get my TRENDnet TEW-424UB wireless USB adapter to work.  I have Crossover (Wine expansion) and tried installing the adapter that way, but it didn't work.  I tried Win4Lin and tried installing the adapter through Windows - still no luck.  I did check everything related to networking in Preferences and Administration but only the ethernet shows up and for some reason dialup even though theres no modem.  I love Linux so far but if I can't get that to work then I have nearly no use for the OS.  I'd hate to go back to Windows.

My second problem relates to my video card.  I have an EVGA 7900 and I have no way of installing it because the CD that came with it doesn't support non-Windows OSes.  Ubuntu detects it but thats it.  How do I fix this?

My last problem is pretty minor it isn't a big deal to me, but I have an illuminating keyboard.  It lights up with the scroll lock key.  Unfortunately, Ubuntu disables it.  Is there any way I can turn it on or is my keyboard stuck being unlit?

My question is more about people who use Wine or Crossover.  I know this might sound like a stupid question, but will games that require the My Documents folder (in Windows) work correctly?


I do know all my hardware works fine, I just stared using Ubuntu yesterday.
Thank you for whoever is spending the time to read this and help me out.

---

### Post by crispy_420 on 2007-04-28
#1:

Native chipset for linux if your lucky but most likely a good ndiswrapper guide.

#2:

Look in forums for a good howto on nvidia drivers.

#3:

keyboard, can't start on where to start

#4:

Not sure about crossover but I now wine will allow you to setup "My Documents" via winecfg.

---

### Post by Najand on 2007-04-28
It is too early to get frustrated.
About number one, see:
[http://ubuntuforums.org/showthread.php?t=207414#9](http://ubuntuforums.org/showthread.php?t=207414#9)
About number 2, Feisty Fawn comes with restricted drivers for NVIDIA. Check it out if it has been installed or not.
About number 3, I cannot understand what you mean.
And lastly... About my document, I think there is no problem.

---

### Post by kvonb on 2007-04-28
Can you run the following commands from a terminal (menu->accessories->terminal) please?

To find out what device your USB network adapter is, type this:

lsusb

To find out what type of video card you have, type this:

lspci | grep VGA

Then copy and paste the output on this thread.

---

### Post by alienexplorers on 2007-04-28
You could try the Envy Script to load the video drivers.  The site is located at: > [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html).  I have used it and it works great.

---

### Post by schmidtbag on 2007-04-28
First of all, thanks a lot everyone for the instant feedback I wasn't expecting so much.  I think crossover is an expansion to Wine (it has more compatibilities and uses the Wine engine or w/e it is).

BTW, Envy doesn't work with 7.04.  I downloaded the Edgy version but still didn't work.


> **kvonb said:**
> Can you run the following commands from a terminal (menu->accessories->terminal) please?

To find out what device your USB network adapter is, type this:

lsusb

To find out what type of video card you have, type this:

lspci | grep VGA

Then copy and paste the output on this thread.


For lusb, it says my adapter is:
Bus 003 Device 004: ID 0457:0163 Silicon Integrated Systems Corp.
Bus 003 Device 001: ID 0000:0000

That is all that was said when I plugged in the adapter, it excluded those 2 lines when I took it out.


For lspci | grep VGA it says:
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7900 GT (rev al)

---

### Post by kvonb on 2007-04-28
OK, your video card is an Nvidia, congrats, you should be in luck :).

To install the driver, simply click on the main menu, and under System->Administration you will see a "Restricted drivers manager" icon, open that then simply select "enabled".

That will go off and download the correct driver and install it for you.

The USB network "dongle" is a bigger problem, all I can suggest is searching these forums and if that fails, google, for the device ID, ie: "0457:0163"

That is the universal ID code for the device, if it doesn't show up in System->Administration->Network, then you might be able to use the Windows driver by installing an app called "NDISwrapper".

Unfortunately hardware manufacturers are unhelpful when it comes to providing drivers or technical information to Linux, and you might be in for a rough ride there.

All the best, KEv :)

---

### Post by schmidtbag on 2007-04-28
After a full hour of research there was no hope in getting the wireless adapter to work.  I'll try using a friends' D-Link adapter and see if that works.  I guess I can sacrifice the keyboard's illumination feature, its not that important to me.  And if the video card will work how its supposed to when I get the updates then I think I should be satisfied.  Thanks all of you for the support, if you know for a fact that D-Link isn't supported please let me know.

---

### Post by Carl Foxmarten on 2007-04-30
I have the same problem you have with the keyboard, pressing the "*lock" keys (NumLock, ScrollLock, and CapsLock) doesn't change the state of the lights (though the six text terminals let them work just fine).
(and I also have a keyboard that lights up with the ScrollLock light, hence my interest here)

---

### Post by rich.bradshaw on 2007-04-30
With the wireless things, it's not the make but the chip inside that makes the difference.

ndiswrapper is what you will most likely need to use if it doesn't work out of the box. google ndiswrapper, or search this forum, there is plenty on it.

---

