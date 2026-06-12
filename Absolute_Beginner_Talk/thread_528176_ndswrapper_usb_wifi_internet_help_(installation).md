---
title: "ndswrapper usb wifi internet help (installation)"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by shadows123 on 2007-08-17
ok,
the instructions in here [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) were a bit i dunno i just couldn't find it out right..
it says to find a .INF to install the driver ? but which .inf? i searched in my windows and i found plenty of file .inf.. :(

Thanks again.
Shadows123.
i installed ndiswrapper and searched for the inf file to get it..
i got the .inf file from the driver for th exp version.. at topcom's site...
i just installed wicd after that and i was able to connect..
topcom wifi usb skyr@cer V2

---

### Post by thefoolisme on 2007-08-17
What USB adapter are you using?  Are you sure it's not supported by a linux driver?  You don't have to use NDISWrapper for all of them.  

Check the links on this page to see if yours is supported.  you may not need NDISwrapper.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28wireless%29](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28wireless%29)

---

### Post by jdfreshwater on 2007-08-17
You may also want to check the website for the card.  Many websites provide the drivers, and you are able to download and extract them to a linux folder for use.

---

### Post by shadows123 on 2007-08-17
i did check their website.. as i used their driver for xp.. they only have xp :(
i checked ur url ..

opcom
	

Skyr@cer wifi card 4054G
	

Maverick
	

no (ndiswrapper)
	

?
	

Yes
	

No
	

More info: [WWW] [http://www.oreillynet.com/pub/wlg/6917](http://www.oreillynet.com/pub/wlg/6917)
	

2006-01-11
	

PCMCIA 

think that's mine ( or atleast it's compatible with it )

---

### Post by shadows123 on 2007-08-18
Ok!
i got a lot of info now...
i got the inf file of my driver for teh ndiswrapper...
done, now there's a wireless thing in network.. but stil no internet..
i runned iwconfig in terminal :
> kevin@kevin-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   Sensitivity=0/3  
          Power Management:off
          Link Quality:0/100  Signal level:56/154  Noise level:160/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kevin@kevin-desktop:~$ 



Ok.

now, the problem is when in network thingy, there's wep ascII and another wep... the prob now is that my usb card doesn't use wep.. i had disable it.. ( it's secure enough already... )

another screeny : 
[http://i19.tinypic.com/540rhp2.png](http://i19.tinypic.com/540rhp2.png)
i had put essid to wlan0 as i thought that's the name of it.. after it i tried with it blank.. still same..

now how do i disable taht wep? :s

Thanks in advance,
- Shadows123.

---

### Post by ugm6hr on 2007-08-18
> **shadows123 said:**
> now how do i disable taht wep? :s


Easier to just tick the "enable roaming mode" box, then use the Network manager icon (2 computers between the speaker and GAIM icon top right) to connect (either left or right-click - can't remember which to bring up list of Networks, and select yours).

It should be pretty easy.

If that doesn't work - try Wicd (see the link in my signature).

---

### Post by shadows123 on 2007-08-18
ok i've put on roaming mode.. still not working..
i tried wicd it said it made a conflict with ndiswrapper :S

---

### Post by ugm6hr on 2007-08-18
> **shadows123 said:**
> ok i've put on roaming mode.. still not working..
i tried wicd it said it made a conflict with ndiswrapper :S

You have to uninstall Network Manager to use Wicd:
From Synaptic Package Manager, search for *network-manager *and *network-manager-gnome* and mark for removal, then uninstall them.

Then try using Wicd again.

Your problem may not be solvable, given that your USB card is not listed on ndiswrapper as working...

---

### Post by shadows123 on 2007-08-18
OMG!!!!!!
this is awesome man!!!
i have internet now!!!
:D
omg thanks a lot dude!!
ubuntu (&you as u helped me lol) are the best!!!!
that's awesome!

---

### Post by ugm6hr on 2007-08-18
Perhaps list your exact wifi card, with the relevant (relating to your wifi) ouput from:
```
lsusb
```

And add exactly where you got the .inf / .sys files from here.

Then mark the thread as solved.

That way, if anyone else with the same usb wifi card needs help to get it working, they will be able to search for this post!

---

