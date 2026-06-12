---
title: "Oh Oh, erased most of/etc/network/interfaces"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by fattysfinest on 2008-01-07
I've been trying to get my wireless to work on my Acer travelmate 290 and I thought I could use the program "wicd" (guess I was barking up the wrong tree!)
The first instructions are as follows
Before you begin

    * Make sure that the only entry in your /etc/network/interfaces file is

          auto lo
          iface lo inet loopback 

So after running that command I proceeded to erase everything else.
Big mistake, Now I don't have any wired connection to the internet.
It did work until I tried to "fix" my wireless connection!
Any help as always is greatly appreciated.
I'm using 7.04, Ubuntu
thank you
Brian

---

### Post by bodhi.zazen on 2008-01-07
LOL

Always backup system files b4 you edit them.

Actually there is no need to delete lines, just comment them out with a #

Try adding these lines :

```

auto eth0
#iface eth0 inet dhcp
```

If the first does not work, try the second

After editing , 

```
sudo /etc/initd.d/networking restart
```

---

### Post by RomeReactor on 2008-01-07
Hi. Open a terminal (Applications->Accessories->Terminal) and enter:
[CODE}gksudo gedit /etc/network/interfaces[/CODE]
there, below these lines:
```
auto lo
iface lo inet loopback 
```
add the following (if you were using DHCP):
```
auto eth0
iface eth0 inet dhcp
```

Or, if you were using static:
```
iface eth0 inet static
address YOUR_ADDRESS_HERE
netmask NETMASK_HERE
gateway GATEWAY_HERE
```

Save the file and reboot.

---

### Post by fattysfinest on 2008-01-07
You guys/gals? are Great!
works like a charm.
Thank you both for your help. 
Now, any thoughts on getting my wireless working?
Should I repost as a new question?
It's a intel pro/wireless lan 2100 mini pc, I already downloaded ndwrapper incase I need it but I really don't know what I'm doing.
I'm looking for a good Ubuntu book if you have any suggestions.
Brian

---

### Post by bodhi.zazen on 2008-01-07
See if this helps : [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

In terms of books, why not start with the Ubuntu wiki ?

---

### Post by RomeReactor on 2008-01-07
> **fattysfinest said:**
> It's a intel pro/wireless lan 2100 mini pc

According to the [community documentation]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel"), your card should work out-of-the-box, so maybe the problem lies in the configuration. Can you scan for wireless networks (provided your router is set to broadcast)? we need to know the designation of your wireless card, so please run:
```
iwconfig
```
if you see there **wlan0** or **eth1** (basically anything that's not **eth0** or **lo**), you can run:
```
iwlist CARD_HERE scan
```
in my case, my wireless card is **wlan0**, so I would run:
```
iwlist wlan0 scan
```

---

### Post by fattysfinest on 2008-01-07
Ok, I tried what you suggested and heres what happened
@ :~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:off   
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

bb@ :~$ iwlist eth1 scan
eth1      No scan results
bb@ :~$

---

### Post by RomeReactor on 2008-01-07
You'll need to specify the ESSID in WICD (or Network Manager). Is your router using encryption--WEP, WPA?

---

### Post by fattysfinest on 2008-01-07
I dont have  a wireless router here, I'm hoping to conect at my sisters house when I'm there.
So do you think this will work when I get there and enter the WEP/WPA info?
 In windows I can just find a spot that has a good signal and no lock and borrow there net for a bit. can't i do that?
also I removed WiCD, Should I reinstall it?
As you can tell I'm a nooby in every sense.
  Brian

---

### Post by RomeReactor on 2008-01-07
It should work, though I don't know how well the ipw2100 (the driver you have) handles encryption. Since you removed WICD, you could reinstall Network Manager:
```
sudo apt-get install network-manager-gnome
```

If you can't get Network Manager to connect, you could reinstall WICD later; just remember that, to use WICD, you need to edit your /etc/network/interfaces file:
```
gksudo gedit /etc/network/interfaces
```
and comment out the lines about your interfaces by adding a **#** at the beginning of each line. For example:
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp
```

If you're going to use Network Manager, make sure the lines **are not** commented out.

> **fattysfinest said:**
> In windows I can just find a spot that has a good signal and no lock and borrow there net for a bit. can't i do that?

Yes, you can. Use either Network Manager or WICD to scan for the network once you're in range. You can also use the terminal to see if you can pick up a nearby connection:
```
iwlist eth1 scan
```
This will tell you if there are any networks close by, and the ESSID.

---

### Post by fattysfinest on 2008-01-07
so is is what  I shoud see? 
auto lo
iface lo inet loopback

 auto eth0
iface eth0 inet dhcp

and
bb@ :~$ iwlist eth1 scan
eth1      No scan results
 
I'm guessing the "no scan results" means no wireless available in this area?
Under windows wireless drivers I don't have anything listed is this ok?
Sorry to pester you but I've been trying to get htis to work for a couple weels now

---

### Post by RomeReactor on 2008-01-07
Right now, you only have your ethernet connection (eth0) listed; try adding the wireless (eth1) so it looks like this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```
As you said, "no scan results" means no wireless networks available nearby. There *may* be one or more networks around you, but they might not be broadcasting their ESSID, which means you would need to know it in order to connect, and if they're using encryption, you would need to know the key as well.

As for Windows Wireless Drivers, that's for using windows drivers through NdisWrapper, and as far as I can tell, your card already has functional native Linux drivers. Don't worry about asking questions; it's important that you don't have any doubts about how to connect wirelessly. I know it's somewhat difficult the first few times one configures a wireless connection, but it does get easier later on. ;)

---

### Post by fattysfinest on 2008-01-08
ok, Ive done as you suggested but still no wireless. there is a good strong signal on my potable wifi detector but nothing showing on my laptop.
In network settings under connections the wireless connection shows roaming enabled but the check box shows a - , and wont change to a check mark. I'm guessing it should as the wired connection is ticked.
Any thoughts? 

 also I got an error screen saying the following
Bad key or directory name: "/desktop/gnome/peripherals/keyboard/host- /0/numlock_on": ` ' is an invalid character in key/directory names
Bad key or directory name: "/desktop/gnome/peripherals/keyboard/host- /0/numlock_on": ` ' is an invalid character in key/directory names

This error did not show up on the wireless screen, I think it just popped up on the desktop screen.

---

