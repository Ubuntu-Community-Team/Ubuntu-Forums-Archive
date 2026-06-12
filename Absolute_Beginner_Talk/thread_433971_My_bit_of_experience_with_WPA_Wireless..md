---
title: "My bit of experience with WPA Wireless."
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by The_Marlboro_Man on 2007-05-05
Hello.

I just installed Ubuntu yesterday after fiddling with the liveCD for a couple of days... Setting it up (so far) has been extremely easy as I just had to do one thing: set up the wireless stuff. I figured out that I could share that bit with the rest of the community in case someone as new as me had the same problem as me.

I read in a lot of places that the Intel 2200 wireless adapter (usually comes with laptops, like the one I'm writing on right now) has problems with Ubuntu... Well, mine's had. My Ubuntu CD was "Edgy Eft" and I can say that I connected to the wireless while trying (actually the second time through): it never said what network I was in or asked for a key, it simply connected. Just after installing I could connect too but when I came home that night and started to set up my system for its usage it had a nasty surprise for me: no wireless. Even a clean install would leave me without a wireless and wireless connections were non existant on the liveCD.

This could be a good moment to say that my wireless connection has a WPA key applied to it: maybe it could have worked with simpler protocols.

I did some research on the Windows partition, read a lot but could never solve anything as most solutions asked me to download packs and stuff. That was yesterday. Today I got myself an Ethernet cable and got myself ready for solving the problem: just plugged the cable to my router and could connect to the "wired" net.

From there, the first thing I absolutely did was to upgrade from "Edgy Eft" to "Fiesty Fawn" (from 6.10 to... 7.whatever). It took a bit of time but when finished I had the same problem: no wireless.  Having a direct connection I could do some more research and read about the topic: I found out that I had to install two components: "GNome Network Manager" and "WPA_Supplicant". The Network Manager would allow connection using a graphical interface and the WPA_Supplicant would provide the system with means to use the WPA protocol... Or that&#347; what I think ;).

So, tried to install them both and it happened that I already had them installed. Tried a reboot but wouldn't work so I started searching again. I read a lot of things about updating drivers, firmware and more but I reverted to the WPA thought again: in the "Network Manager" I could clearly see my Wireless (and my neighbours') signal under the "ESSID" on the "properties" tab if that "Other" newwork app, the "Network Monitor"... It was just that it asked for a WEP key and mine's was WPA. 

Reading a bit more I found out that I had no WPA_Supplicant config file so I created my own and provided it with my ESSID and pass. Fiddling around with the "NetWork monitor" and trying it to ask for an WPA key was useless. Instead of that I tried rebooting to see if that WPA_Supplicant config file served any purpose. Next reboot and I was connected :). I still can't see any sign of WPA on the "Network Monitor" but the "Network Manager" shows them so I suppose the WPA_Supplicant doesn't affect the default app...

So, all I wanted to say is that the 2200 wireless interface is working in Ubuntu for me, it was just a question of reading and configuring (a lot of reading... I didn't even know how to copy a file to the etc directory!!). Still I have a long way to go getting mp3, mov and other media stuff to work along with a decent programming IDE but I guess it's all about getting into it. Wish me a nice start with Ubuntu/Linux/GNU!!!.

---

### Post by foresth on 2007-05-06
My bit of experience with WPA Wireless:

Be also aware of the fact that connecting with WEP key or WPA is not supported on some wireless cards if you try to make it work via **ndiswrapper**.

I was trying to set up this on my laptop wi-fi for days and eventually figured out that since some kernel version, WEP/WPA is not supported on my wireless card.

---

### Post by The_Marlboro_Man on 2007-05-06
I was about to do the wrapper thing that is read on the "How-to's" but fortunately I got it working before downloading any firmare or drivers or anything. For what I know my installation of Ubuntu shouldn't come with the ndiswrapper installed so it just got working without them :).

Again, my card is an Intel 2200m which I read, gives a lot of problems in Ubuntu.

---

### Post by joneil1000 on 2007-05-06
You know something though, some wireless cards even under Windows are crap, it's just that people do not either realize it or talk about it - at least the same was people do here.

   I have two laptops, and older Toshiba, a newer HP.  The built in card int he Toshiba never carried a signal just right from day one - it was always flaky.  Bought a new notebook card - wireless worked great.

   The built in wireless in my HP under windows works great, but always has issues connecting.  If th ecard is turned on when I book up (there is a physical off/on switch) then it detects networks, but never connects.   After  my machine is fully booted up and everything is running, I physically turn off the wireless card via hardware switch, turn it back on, and voila - connects instantly.   This is true for any kind of network -   open or secure.

   So when I hear various posts say "well this card doesn't work very well under Ubuntu", well, that may be very true - but there is a  lot of hardware out there that doesn't work 100% under Windows either.


  Anyhow, back to Ubuntu, try installing a little program called "Network Selector".  I think I installed it fomr Synaptic Package Manager - do a search.  Does a little applet on your top bar.  Seems to work great on my old laptop.   For some odd reason, my machine keeps looking for a network cable connection, even when there is none, so Network Selector seems to sort out issues with me.  

good luck
joe

---

