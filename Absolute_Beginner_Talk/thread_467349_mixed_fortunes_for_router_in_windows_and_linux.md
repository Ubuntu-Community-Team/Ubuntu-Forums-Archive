---
title: "mixed fortunes for router in windows and linux"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by jackyu on 2007-06-07
hi, 
Here's the situation.   I have a wireless router, a laptop with Windows and Ubuntu installed.  I can use the wireless when I'm using Windows.  However, I just can't get on the internet when in Ubuntu.  I can see that my network is detected, and I'm prompted to enter my WPA2 passphrase, but after entering it in, the icon only shows one green light, this goes on for ages while the other green light never shows.  And after a while, the swirling about the green light just stops.  Also, when I connect to the router through a wire, I still can't get on the network.  This only happens with this particular router at home, while everything works fine elsewhere.  

I'm a n00b, and have been struggling with for a long time; in fact, I have just switched from fedora core, in the hope of getting rid of this problem. :(  Can someone give me some help?  I'm really tired of having to switch between the two OS all the time.

---

### Post by ulli.winter on 2007-06-07
hi jackyu,
do you use the same settings for dynamic / fixed ip on both operation systems?

---

### Post by jackyu on 2007-06-08
> **ulli.winter said:**
> hi jackyu,
do you use the same settings for dynamic / fixed ip on both operation systems?

i think it's set to dynamic on both operating systems.

---

### Post by ulli.winter on 2007-06-08
perhaps you should check that ;)

---

### Post by Rocket2DMn on 2007-06-08
You can try enabling Roaming mode, this seems to fix a lot of networking problems.  You can do this from System->Administration->Networking.
Good luck!

---

### Post by jackyu on 2007-06-12
> **Rocket2DMn said:**
> You can try enabling Roaming mode, this seems to fix a lot of networking problems.  You can do this from System->Administration->Networking.
Good luck!

hi thanks.  But when i checked i was already in roaming mode.

---

### Post by jackyu on 2007-06-12
> **ulli.winter said:**
> perhaps you should check that ;)


How do check if i have static/dynamic ip setting in Ubuntu?
could you please give a brief explanation of what is meant by static and dynamic IP, and how/why they matter in my situation?  i remember having had choose between 'static' and 'dynamic' in the setting up my router, but I don't remember having to do anything like this for the operating systems, so maybe it's something to do with this.     

thanks

---

### Post by ulli.winter on 2007-06-13
there are two possibilities....
either the pc requests the static ip, or the router assigns one to the pc ("dynamic")
thats how it should work, but if the settings dont match it probably wont work ;)

you might find ubuntu settings under: system-administration-network-wlan->properties

router: check your manual ;)

good luck

---

### Post by jackyu on 2007-06-16
> **ulli.winter said:**
> there are two possibilities....
either the pc requests the static ip, or the router assigns one to the pc ("dynamic")
thats how it should work, but if the settings dont match it probably wont work ;)

you might find ubuntu settings under: system-administration-network-wlan->properties

router: check your manual ;)

good luck

hi 
in system-administration-network-wlan->properties, i disabled the roaming mode, and selected my ESSID and in the connection type i selected Automatic(DHCP) instead of Static IP or the other option; i presume this is what you meant by 'dynamic'?  However, under passphrase type, there's no WPA/WPA2, just WEP.  If I ignore this, and just cilick ok, the following happens.  A small window tells me the Interface Configuration is being changed.  After it's done, i get a 'manual connection', but it still doesn't allow me to do anything.  So i switched back to roaming mode again, and was prompted to enter the WPA passphrase, but this time the icon on at the topright actually shows that the wireless is connected.  This is also verified when i use iwconfig, where i can see my ESSID.  However, when I try to ping something, nothing happens still.  Any ideas?

---

### Post by imon9 on 2007-06-16
hi jacku,

i recommend you to install wicd ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)) which is helpful in wireless connection management! you have to uninstall the natwork manager used by ubuntu though...

(erm, as usual, experiment at your own risk)

most ppl i know install wicd and happy using it

---

