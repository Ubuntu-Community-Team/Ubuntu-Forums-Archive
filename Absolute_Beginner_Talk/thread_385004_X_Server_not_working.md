---
title: "X Server not working"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by showty on 2007-03-15
Hey all

Installed Ubuntu 6.10 today, I tried 6.06 previously but couldn't get wifi working, but 6.10 seem(ed) to run fine with my wifi, so I was pretty excited.

But after setting up everything minor (connected to the net, set my wallpaper, installed some small stuff like GTetrinet) I tried to install the Nvidia drivers.

Following some instructions someone told me, I installed the restricted package with Synaptic (which included the latest Nvidia drivers) and tried to edit my x config file, but it was read only.

So I rebooted anyway, and was greeted with a blue screen, telling me my X server wouldn't load etc etc.

I have a Leadtek GeForce 7800GT by the way, I hope someone can help (I know.. I'm an idiot.. :( )

While this awesome community solves that problem for me, could someone quickly explain to me how to bump up my res from 1024x768 to 1280x1024? It wont let me in the resolution settings. Thanks :)

Ubuntu rocks, I hope to relegate Windows to being just my gaming OS once I get Ubuntu up and running correctly :)

---

### Post by PartisanEntity on 2007-03-15
Assuming that you cannot load your x-server do the following:

Log in with username and password if you have not done so already.

This will allow us to open the xorg.conf file with the right permissions and to edit it:
```
sudo nano /etc/X11/xorg.conf
```

Move down (with the arrow keys on your keyboard, mouse wont work at this point) until you see:
```
Section "Device"
    Identifier     "NVIDIA Corporation xxxxxx? [GeForce xxxxx]"
    Driver         "nv"
EndSection
```

Change 'nv' to 'nvidia'

Then search for:
```
Section "Screen"
```

Make sure DefaultDepth is 24, if it isn't edit it to 24:
```
    DefaultDepth    24
```

Scroll down further until you see:
```
    SubSection     "Display"
        Depth       24
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
```

Now add your desired screen resolution to the start of the 'Modes' in the same manner as the already existing resolutions, so "1280x1024".

Then we need to save and close, so type CTRL+X, it will ask you:
```
Save modified buffer (ANSWERING "No" WILL DESTROY CHANGES) ? 
```

Type Y for yes and hit enter.

Now press CTRL+ALT+Backspace to restart the x-server and hopefully you should see the Nvidia splash screen and then you should be able to see the desktop log in window.

---

### Post by overdrank on 2007-03-15
> **showty said:**
> Hey all

Installed Ubuntu 6.10 today, I tried 6.06 previously but couldn't get wifi working, but 6.10 seem(ed) to run fine with my wifi, so I was pretty excited.

But after setting up everything minor (connected to the net, set my wallpaper, installed some small stuff like GTetrinet) I tried to install the Nvidia drivers.

Following some instructions someone told me, I installed the restricted package with Synaptic (which included the latest Nvidia drivers) and tried to edit my x config file, but it was read only.

So I rebooted anyway, and was greeted with a blue screen, telling me my X server wouldn't load etc etc.

I have a Leadtek GeForce 7800GT by the way, I hope someone can help (I know.. I'm an idiot.. :( )

While this awesome community solves that problem for me, could someone quickly explain to me how to bump up my res from 1024x768 to 1280x1024? It wont let me in the resolution settings. Thanks :)

Ubuntu rocks, I hope to relegate Windows to being just my gaming OS once I get Ubuntu up and running correctly :)

Hi you can reconfigure X. Terminal and enter  sudo dpkg-reconfigure xserver-xorg
and follow the questions and make sure that resolution is in the configure. Hope this helps. Good luck!:guitar:

---

### Post by showty on 2007-03-15
Thanks a huge bundle guys!

I got back into my PC and the drivers were working, and so was the higher res. I loaded up OpenArena, joined a server and started playing, but then I noticed connection problems randomly appearing every 5 seconds or so.

Seems my wifi is going nuts again, like in 6.06 :(
I have a Netgear WG311T wireless card, running in 54mbit mode (its a 108mbit card) on a WLAN requiring a WEP key. It connects fine in 6.10, like in 6.06, and also like in 6.06, it just randomly drops out (without actually saying its dropped out, connection signal strength remains at 70%ish) and the internet stops working along with network share file browsing.

Any ideas? Thanks :)

---

### Post by Kobalt on 2007-03-15
What method (drivers) did you use to set up your wireless card ?

---

### Post by showty on 2007-03-15
Default ones that loaded up with Ubuntu after installation.

---

### Post by Kobalt on 2007-03-15
I'm not an expert of Netgear hardware, but I can recall having read many threads on this forum about this specific WG311T being quite unstable, unfortunately... Maybe it'll get better in the next Ubuntu release, or maybe someone with more skills will be able to guide you on a possible fix up....
Sorry I can't be more helpful lad.

---

### Post by showty on 2007-03-15
If the WG311T is bad, what about the stripped down 311, with only 54mbit support (the WG311). I have one of them lying around, but I don't really want to bother putting it in if its going to have exactly the same problems.

---

