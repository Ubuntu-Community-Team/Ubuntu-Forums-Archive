---
title: "Wireless, of course"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by huzzak on 2007-03-23
So, I've tried to get Ubuntu to play nice with my wireless card, but it won't do it.  I have an HP Pavilion laptop and I think that the wireless card is an Intel sort.  I have a wifi network that uses WPA encryption and I can detect it with Wireless Assistant, but it lists it as WEP and no matter what I do it won't work.  I've tried to get the Network Manager dealie to work since that seems the prescribed method, but it won't open nor display the little icon on the taskbar.  Sometimes it will pop up a little dialog that says that it can't run because of inadequate resources or somesuch.

When I run iwconfig it says this:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6922   Missed beacon:0

sit0      no wireless extensions.


Any suggestions?  Thanks in advance.

---

### Post by Zzl1xndd on 2007-03-23
Im using network manager myself and it works like a charm it also worked on 2 other laptops that I set up so you might wanna look at that. Also I did need to restart one of them to get network manager to work.

---

### Post by huzzak on 2007-03-23
I installed the Network Manager with add/remove applications and restarted, but it still doesn't work.  My wireless card indicator is flashing like it is posessed but no information is transmitted over it and there is no way that I can see to actually open up the Network Manager and monkey with it.  I dunno.

---

### Post by Zzl1xndd on 2007-03-23
is there a computer Icon up in the top right of your screen?

---

### Post by huzzak on 2007-03-23
Yes, there is a little computer in the upper right hand corner of my screen.  It is actually two computers one behind the other.  I can click on it and get a little dialog box that has eth0 and lo as options.  If I type in eth1, it informs me that it is disconnected.  I don't think it is the Network Manager because it stays there even if I remove the Network Manager program.

---

### Post by Zzl1xndd on 2007-03-23
strange, I hate to suggest more software to toss at the program but how about wifi-radar?

---

### Post by martinw89 on 2007-03-23
I also remember reading somewhere that Network-Admin (System->Administration->Networking) and NetworkManager (the computers in the upper right) don't get along.  To remedy this, press alt+f2 and type```
gksudo gedit /etc/network/interfaces
```  In the file, place a "#" mark before every line except the following two lines:```
auto lo
iface lo inet loopback
```

So, for example, my /etc/network/interfaces looks like this:```
auto lo
iface lo inet loopback

# iface eth0 inet dhcp
# auto eth0
```

Adding the "#" comments out those lines, meaning the system will skip past them.  This allows NetworkManager to take over configuring the devices.

---

### Post by huzzak on 2007-03-23
I commented out the stuff in the interfaces file and rebooted, with no effect.  I took a screenshot of, perhaps, pertinent things.  Maybe just to serve as illustration.

[http://img.photobucket.com/albums/v101/Huzzak/wifi.png](http://img.photobucket.com/albums/v101/Huzzak/wifi.png)

I'll try the wifi radar thing.

---

### Post by huzzak on 2007-03-29
Well, I don't know what happened, but it started working.  Thanks a ton for the help.  I guess if you restart enough it is bound to turn on eventually.

I have another question, though, and it is also about wireless.  When my computer comes back from hibernating, without fail, the wireless won't work.  It is as if the card isn't even detected because the indicator on the body of my laptop doesn't flash and the wireless option doesn't show up at all in networking.  Any ideas?  Thanks!

---

