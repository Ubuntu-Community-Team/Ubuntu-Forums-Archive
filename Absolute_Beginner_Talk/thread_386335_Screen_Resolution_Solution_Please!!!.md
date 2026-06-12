---
title: "Screen Resolution Solution? Please!!!"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by ibuntutoo on 2007-03-16
I recently installed Ubuntu in an old pc I had around. It was a 1 Ghz AMD PC with 256MB of ram. It ran well but crashed frequently. While rummaging through my extensive collection of computer odds and end I ran across two 512 dimms compatible with the computer. It booted up and ran sweet! Gone are the crashes. In the spirit of this last victory I began to search again for an aAPG card since the system had a on-board video card. I found one, probably with the same 64mb that the system had been using with shared memory, but it has been my experience that removing the load on the CPU can account for a significant overall improvement in performance. When I tried to boot it gave me an error loading X. I tried rebooting a couple of times but eventuly gave up.

Now here is my Boo-hoo!! Now that I am back to my old on-board video card my pre-APG resolutions and refresh rates are gone! I would know what to do on a windows system, where it would seem to be a driver problem, but in linux I've haven't a clue where to begin. HELP! :confused:

---

### Post by Scunizi on 2007-03-16
First, What kind of built in video card is it?  Also, what kind of AGP card did you try?

---

### Post by ibuntutoo on 2007-03-16
The truth is that I am not sure what kind of chipset is in build in card. The other card is an ASUS card APG-V7100 if I had to guess probably an old Gforce chipset. I haven't used these parts in years.

---

### Post by Scunizi on 2007-03-16
Find the terminal under Applications/Accessories and open it.  Next type (without the quotes) "sudo dpkg-reconfigure -phigh xserver-xorg" <enter>.  This will reconfigure your video for you and ask a couple of questions.  After that is done use the Linux 3 finger salute to restart X (the gui).  Ctrl Alt Backspace.  Log back in and see if that fixes it.  If it doesn't you can also look at your driver settings by typing "sudo gedit /etc/X11/xorg.conf" and see if the values you need for your system are listed correctly.  Sometimes you need to add the right resolutions and or refresh rates, sometimes you need to change to the generic driver (vesa).   Try the auto method first.

---

### Post by ibuntutoo on 2007-03-16
Thank you so much. The Linux 3 Finger Salute was worth reading you post alone. You can't imagine how many times I have gone for the ctrl-alt-del since installing Ubuntu. Now I know how. I am currenly trying to install Fedora on another frankestine system, but as soon as I can get back to the one with Ubuntu I will try out your sugestion and post my results. 
**I am loving Linux. **

---

### Post by Scunizi on 2007-03-16
If you've got a frankinstein sys you should try xubuntu.  It's light weight, fast and fun.

---

### Post by ibuntutoo on 2007-03-16
It's a very capable Frankestain. Duron 1.8 Ghz with 512 Ram. I have an old 266 mhz petium  laptop with 256mb of ram that belonged to my father-in-law. Does that sounds like a good candidate for xubuntu?
Linux has become like a good Ice Cream Shop, I just want to taste all the flavors. But then again like Ice Cream and girls it always comes back to your first love; Ubuntu?

---

### Post by metroknight on 2007-03-16
> **ibuntutoo said:**
> It's a very capable Frankestain. Duron 1.8 Ghz with 512 Ram. I have an old 266 mhz petium  laptop with 256mb of ram that belonged to my father-in-law. Does that sounds like a good candidate for xubuntu?
Linux has become like a good Ice Cream Shop, I just want to taste all the flavors. But then again like Ice Cream and girls it always comes back to your first love; Ubuntu?

I had Xubuntu running on an old Gateway Solo. It had a 333mhz with 288 ram until the harddrive (6gig) died on it.

---

### Post by Scunizi on 2007-03-17
I looked up your old card on google and found it's a nvidia gforce2 mx400.  Probably a better card than what was built on the motherboard.  You might try sticking it back in and redoing what I mentioned in the previous posts.  Once things are running correctly, go to synaptic and download the nvidia-glx drivers then .... once again.. back to sudo dpkg-reconfigure -phigh xserver-xorg and when thats done.... sudo gedit /etc/X11/xorg.conf and look for the "driver" line and change the contents to nvidia.  Save. Three finger salute and you should be rocking and rolling.

---

### Post by ibuntutoo on 2007-03-17
I'm back from my excursion to fedora. I will be installing Ubuntu on that system as well. Installation was more complicated than anticipated and gui nothing better than i get with Ubuntu. 
Ok, so I come back to Ubuntu and guess what? My resolution is back to what I wanted. Can someone explain to me how it happends. I did not do anything different. I just turned it off  while I delt with the other PC and when I rebooted, Walah. 
I will try to install the other card. I am still not exacly sure what to do when I get the very colurful screen of death, telling me the computer can't open x.

---

