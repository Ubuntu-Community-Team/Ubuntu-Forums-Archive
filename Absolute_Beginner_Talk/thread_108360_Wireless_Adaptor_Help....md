---
title: "Wireless Adaptor Help..."
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by bigeyedphish4134 on 2005-12-25
I am very new to any Linux OS, in fact I just installed it for the first time about an hour ago.  I have clearly have much to get used to and figure out for myself, but the one topic i seemed to have reached a dead end on is my wireless adapter.  I have Ubuntu 5.10.  

My wireless adaptor is a D-Link DWL-G510.  I searched these forums, which lead me to search the manufactures website which listed a drivers that were not endorsed/supported by the manufacturer.  Luck have it, my adaptor is one that appears to not have a linux driver.  Now i am currently trying to figure out if there is a program that will read my "windows" version of the driver and convert it to somehting linux can use.

I would appreciate any help you guys could throw my way.

Thanks!!

-Greg

p.s.   I saw a few threads similar, but they seemed to be pretty specific

---

### Post by Lambert on 2005-12-25
This should just work as the g510 has an atheros chipset supported by the madwifi driver which is part of breezy. You may need to install the linux-restricted-modules. If you click on the life preserver in the top panel there are instructions there on how to install apps. the linux-restricted-modules are on the install cd.

go to system>administration>networking

card should be in the list. highlight, set properties, then activate.

If you use wep post back details (not personal data) of the settings as an edit might need to be done.

if you use wpa go to the ubuntu wiki (ubuntu.wiki.com) and search wpa. There's a guide there to work.

---

### Post by fuscia on 2005-12-25
you can install ndisgtk from the synaptic package manager. if you have the windows driver, the rest is super easy.

---

### Post by bigeyedphish4134 on 2005-12-25
Thanks!  it now says "The interface ath0 is active"...im sure this is a step in the right direction.  I am still not able to connect to the internet.  I did not do the first step you mentioned (installing some files located on the Install CD)  I was not able to find where exactly to look once I clicked on the life preserver - I don't really know what category I should be looking under.  (is this even neccesary now that the interface is active?)
I appreciate the help!

---

### Post by bigeyedphish4134 on 2005-12-25
> you can install ndisgtk from the synaptic package manager. if you have the windows driver, the rest is super easy.

hmm...did a search for that and it turned up stuff for Debian....any recommendations of places to get this?

---

### Post by Lambert on 2005-12-25
You won't need ndis. It's an app used to make unsupported devices work in linux. Your device has a native linux driver. 

Post output of these commands  

```

iwconfig

ifconfig

```

Also are you using wep or wpa?

---

### Post by bigeyedphish4134 on 2005-12-25
[QUOTE=Lambert]You won't need ndis. It's an app used to make unsupported devices work in linux. Your device has a native linux driver. 

Post output of these commands  

```

iwconfig

ifconfig

```

Also are you using wep or wpa?[/QUOTE]
i have yet to find the command prompt....

and i am using a wep key

---

### Post by Lambert on 2005-12-25
applications>accesories>terminal

are you using an open or shared/restricted key
are you using ascii or hexadecimal key

---

### Post by bigeyedphish4134 on 2005-12-25
ok for the iwconfig i got...

lo                       no wireless extensions

eht0                    no wireless extensions

ath0                   IEEE 802.11   ESSID: "   "
                         mode: managed  frequency:2.417 GHz
                             *there some more to this message that i can type if you need it*

sit0                      no wireless extensions

---

### Post by bigeyedphish4134 on 2005-12-25
ifconfig:

ath0       Link encap: Ethernet     HWaddr:  00:11:  **more numbers**
                      **more info, this is the stuff that looks important...**
                  errors: 338          dropped:0
                collisions:0     txqueuelen:200

lo           Link encap: Local Loopback
             inet addr:  127.0.0.1      Mask:  255.0.0.0
             **more stuff**
              RX packets: 1334    **more stuff**
               TX packets : 1334      **more stuff*
                    *more stuff*




sorry...i can't copy/paste because I am on another computer
thanks!

---

### Post by bigeyedphish4134 on 2005-12-25
[QUOTE=Lambert]applications>accesories>terminal

are you using an open or shared/restricted key
are you using ascii or hexadecimal key[/QUOTE]

and that would be a restricted key (just my home network)
and ascii I think.....numbers and letters...i figure hex is just numbers

---

### Post by Lambert on 2005-12-25
Looks like you're dual booting so save the key strokes. I'll expain what I'm looing for.

for iwconfig I'm looking for the access point: I want to make sure it doesn't look like this 00:00:00:00:00:00 should be alpha numeric characters

for ifconfig I'm looking for inet addr: should have an ip address after this. Checking to see if an ip address is assigned to the device. (not the inet6 addr line)

I'm checking out so maybe someone else can step in or I'll be back tomorrow. There's a link in my signature WTG which you can see if it helps you get set up.

If you're running restricted key wep then after you activate you need to run this command.

sudo iwpriv ath0 authmode 2 (if open key then don't worry about this)

edit: running restricted key I know you can't connect unless you run the iwpriv command above. hexadecimal keys are actually 0-9 a-h

you will need to set up a configuration file so it does this automatically on boot

```
sudo gedit /etc/network/interfaces
``` 
in the editor you should see something similar to this. Edit it so it looks like this.

iface ath0 inet dhcp
wireless-essid xxxxx
wireless-key xxxxxxxx
wireless-mode managed
pre-up iwpriv ath0 authmode 2
auto ath0

if you figure you're using ascii key then make the wireless-key look like this.

wireless-key s:xxxxxxx

of course replaces all the xxx's with your actual essid and keys.

---

### Post by bigeyedphish4134 on 2005-12-25
[QUOTE=Lambert]Looks like you're dual booting so save the key strokes. I'll expain what I'm looing for.

for iwconfig I'm looking for the access point: I want to make sure it doesn't look like this 00:00:00:00:00:00 should be alpha numeric characters

for ifconfig I'm looking for inet addr: should have an ip address after this. Checking to see if an ip address is assigned to the device. (not the inet6 addr line)

I'm checking out so maybe someone else can step in or I'll be back tomorrow. There's a link in my signature WTG which you can see if it helps you get set up.

If you're running restricted key wep then after you activate you need to run this command.

sudo iwpriv ath0 authmode 2 (if open key then don't worry about this)[/QUOTE]
ok, thanks a lot for your help!
I'm sure I'll cya around

merry xmas/happy holidays!

---

