---
title: "installed ubuntu THEN added airport card - cant see"
date: 2006-07-10
forum: Apple PPC Users
---

### Post by printmkr on 2006-07-10
I did a total install of Ubuntu on an old iBook (no OS X on the drive). I then added an airport card. But the card does not show in the Networking settings... I won't have to do a total reinstall or anything will I? Should Ubuntu see the card automagically after I added it or am I missing something I have to install? I tried a few tricks from the forums, but it is still not showing up. even with lspci...

---

### Post by rasec on 2006-07-10
What does "ifconfig -a" show? If it shows an eth1 or wlan0 than you might need to go into your /etc/network/interfaces and copy the entry for eth0 for eth1/wlan0, replacing all instances of eth0 with eth1/wlan0.

If that doesn't work, than maybe the kernel modules isn't loaded. Try "sudo depmod -a; sudo modprobe orinoco_cs" and that should load the driver. I don't have an airport card in my powerbook, I have the extreme version, so I don't know for sure if the original airport card uses the orinoco_cs drivers. Hopefully someone else with an airport card will tell you which driver their using. After you load the driver do a dmesg to see if any new ethernet devices were found. If the card was detected, you should be set, otherwise you may need to add an entry for the card in your interfaces file as I mentioned above.

If the card wasn't detected, than I either told you to load the wrong driver, or your airport card is dead or was installed wrong.

---

### Post by printmkr on 2006-07-10
Thanks for the help! ifconfig -a did not show an eth1 or wlan0, just an eth0, lo and sit0. I tried the depmod -a but it kept on giving me "WARNING: Module " yaddah yaddah"ignored, due to loop." 

I swapped out this airport card and it works on another machine, so it is not the card. It could be this particular machine, though... looks like I am going to have to re-install OSX on this HD to see if the card works from there.

---

### Post by printmkr on 2006-07-11
Alrighty then... reinstalled OSX (alas had to wipe Ubuntu) and yes my Airport card works fine on this machine (iBook G3 500 mhz) under OSX. I'm reinstalling Ubuntu from scratch now, this time with the airport card installed from the start, so perhaps there will be some love from Ubuntu this time around.

---

### Post by printmkr on 2006-07-11
Huzzah! Ubuntu goodness! My airport card shows up. Now to getit up and running, but the battle is half won!

---

### Post by printmkr on 2006-07-12
Not that I am enjoying having a conversation with myself or anything, bt I figure maybe this thread may be of use to someone else! Once the Airport card was recognized, it was no problem getting WEP and the card working with my original airport base station.

---

### Post by brian.reading on 2006-07-14
Well.. Now I have this problem, and I'd really rather not solve it by wiping this installation and reinstalling.  Dapper doesn't like to install correctly on my Clamshell iBook, and it's a huge headache.

Anyone know of a way to get this thing working?

---

### Post by AbEx on 2006-07-16
In a terminal try: sudo modprobe airport and sudo modprobe ieee80211

if this works add ieee80211 and airport to /etc/modules

---

### Post by jah on 2006-07-18
Does anyone know how to get WPA working on a vanilla Airport card in Dapper?

I'm using an iBook G3 and the card is detected just fine, and i can see my network, however am unable to connect as WPA is not offered as an option in Network Manager - only WEP!

I really hope i can find the answer!

Thankyou

---

### Post by dehmac on 2006-07-31
Hi Jah,

New to ubuntu on the PPC side. But I need help with gettng my Mac PB G4 running OSX 10.4 to work so I can completely move to Dapper. How can I get it to work. I activate it.. but it still does not work.

[email]Cedney@gmail.com[/email]

---

