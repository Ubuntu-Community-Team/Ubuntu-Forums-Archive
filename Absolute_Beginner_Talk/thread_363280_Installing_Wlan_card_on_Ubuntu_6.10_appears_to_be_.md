---
title: "Installing Wlan card on Ubuntu 6.10 appears to be agony!!"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by gwowders on 2007-02-16
Hi,

Ok... first time installing Eubuntu after threatening to for quite some time, and it appears to be a little more painfull than I would have imagined!

I tried 6.06 at first, but it crashed on install (something about X Server not starting... blah blah), a quick hunt of these forums suggested a million and one solutions, none of which seemed entirely clear, so I downloaded 6.10, which seemed to install with no problems.

If it makes any difference at this point I'd like to point out that I have installed Ubuntu on a partition of my existing XP box.

Next problem soon crops up, my wireless card isn't supported out of the box (its not like its a strange make or anything, one of those BT packages using the Voyager2100 and 1040 pci cards, which are based on the Broadcom BCM4306KFB chipset according to the Ndiswrapper list).  So I have to install something called Ndiswrapper, which will allow me to run the driver under some kind of emulation or whatever.  To be honest, I'm sure it is interesting but at this point I'd just like my shiny Ubuntu installation to be able to talk to the outside world, something which Windows makes rather easy (maybe too easy, different discussion for a different time).

Anyway, I follow the (many) instructions dotted about the place, install Ndiswrapper eventually, locate my bcmwl5a.inf file and then Install New Driver...  and this tells me hardware is present, so all good.  I then select Configure Network (also System -> Administration -> Networking I believe?).  I add my Essid and (assume in the correct place) my wep key.  Select Ok.  Tick the box next to Wireless connection (a message tells me Activating network interface).  Then nothing, when according to the instructions I should now be rocking and rolling.  I think I have tried as many different combinations as I possibly can, but still no joy!!!!  I have heard that the /etc/network/interfaces file can be important, I tried a few changes but again nothing so rolled back to the original - this looks like:

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid BTVOYAGER2100-23
wireless-key s:XXXXXX

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth1
```

From the instructions I was under the impression that this driver would be associated with wlan0 as opposed to eth1 but some of the more recent posts suggest that it doesn't matter... again I have no clue!

So.... as with so many on here, all help appreciated.  I have used *nix systems once or twice before but its probably best if any and all instructions were as simple as possible!!!  I'll try to help as much as possible by printing output etc. but please bear in mind that any additional files that are needed will have to be downloaded from the xp partition and then copied across (ubuntu nicely seems to mount my ntfs partition which makes this part a little easier), so again, the simpler the better!!!!

Many thanks in advance!

Ben

---

### Post by gwowders on 2007-02-16
If its of any use, the output from an ifconfig and iwconfig are:

```
ben@Ben-ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 

Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX 

packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7188 (7.0 KiB)  TX bytes:7188 (7.0 

KiB)

ben@Ben-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  

Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  

Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid 

misc:0   Missed beacon:0

sit0      no wireless extensions.

ben@Ben-ubuntu:~$
```

Cheers,

Ben

---

### Post by gwowders on 2007-02-19
I eventually found this [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-1e63934359df5734b0d85f653110de7e4ba224df]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-1e63934359df5734b0d85f653110de7e4ba224df")which proved invaluable!

Ultimately, I had to carry out a fresh install anyway (I think because I had ballsed up the previous installation by trying too many different things), then do everything exactly as described in the HowTo above. The only point I would make to any other complete beginners like myself is that it is very important to make sure that there is a corresponding entry in /etc/iftab and /etc/networking/interfaces for (in my case) wlan0. Because I don't have any other network devices attached to my PC I was able to edit everything else out with a '#'. I also needed to pay extra attention to the Ndiswrapper list which mentions that for my pci card (supplied with the BT Voyager wireless pack and labelled as a 1040) I need to use the bcmwl5a.inf driver, as opposed to most of the other examples which don't.

So, there we have it, last night at 00:15 I managed to get Ubuntu talking to the outside world. if I have to make one comment about this (and I really feel I do), it wasn't easy in the slightes, and I'll bet that for every one person like me that perseveres and eventually gets this working, there are hundreds that don't. If it is the ultimate goal of the Ubuntu crowd to truly push their distro to the masses then this ndiswrapper process needs to be dramatically improved and simplified. I appreciate that there are lots of other driver issues (and that this isn't always the fault of the OS, rather the vendors that just don't create driver software for *nix) but network connectivity is key, because the CD can't contain everything! Once a user has access to the 'net (and the great resource that is these forums) then thats half the battle. IMHO (as far as any opinions are Humble) this needs to be addressed as a matter of priority.

</rant> ;-)

---

### Post by tyres on 2007-03-01
Hi,

Glad you sorted your problem out :-)

Just out of curiosity, what is it you have in /etc/fstab that corresponds with somethng in /etc/network/interfaces?

I've accumulated a fair bit of experience with installing wireless adapters in Ubuntu (mostly BT USB adapters) over the past few months (successfully), but I've never known /etc/fstab to have anything to do with it. Surely that's for mounting filesystems on boot-up, not network adapters?

Colin

---

### Post by gwowders on 2007-03-01
> **tyres said:**
> Hi,

Glad you sorted your problem out :-)

Just out of curiosity, what is it you have in /etc/fstab that corresponds with somethng in /etc/network/interfaces?

I've accumulated a fair bit of experience with installing wireless adapters in Ubuntu (mostly BT USB adapters) over the past few months (successfully), but I've never known /etc/fstab to have anything to do with it. Surely that's for mounting filesystems on boot-up, not network adapters?

Colin

Hi Colin,

Looks like I might have put fstab when I actually meant iftab... ooops!  

Thanks for pointing out my mistake!

The document (that I am now linking to, again another mistake on my part) does reference iftab and not fstab.  I think I had to comment out the eth1 line, but to be honest I had tried so many different combinations by that point that I was just glad that *something* worked!!!

---

### Post by tyres on 2007-03-01
Hi,

Looking back now, it *does* say 'iftab', not 'fstab'. Unless you've been able to magically correct it, I must have misread it originally. I only went to the opticians a few  days ago too! 'iftab' makes more sense, but it's not a file I've ever needed to mess with. Must go and see what's in it ;-)

I think 'trial and error' is how most of us get there in the end! You've just got to be persistent and not get (too) discouraged. It does help if you know others have done it before you, and hopefully they can give a little bit of advice, as in these forums.

Colin

---

### Post by lunchbox_1973 on 2007-03-01
I feel your pain brother, it took me a good two or three weeks to finally get the wireless going on my Dell Inspiron 1300. Like you I read many many different how-to's and tips.

I FINALLY got mine to work by using an outdated driver believe it or not. The up to date Win XP driver didn't do the trick.

I'm very happy with my wireless performance but I've yet to connect to an encrypted signal. I know there are tons of other threads on people like me who are having trouble with WEP and WPA. I'll tackle that next when I need a challenge.

In the meantime please don't hack into my network since I turned the encryption off :) 

Although Ubuntu is great and free so we don't really have the right to bitch, the devs really need to get wireless working out of the box. I'm sure it frustrates a lot of people to the point where they give up and go back to Windows.

---

### Post by gwowders on 2007-03-02
> **tyres said:**
> Hi,

Looking back now, it *does* say 'iftab', not 'fstab'. Unless you've been able to magically correct it, I must have misread it originally. I only went to the opticians a few  days ago too! 'iftab' makes more sense, but it's not a file I've ever needed to mess with. Must go and see what's in it ;-)

I think 'trial and error' is how most of us get there in the end! You've just got to be persistent and not get (too) discouraged. It does help if you know others have done it before you, and hopefully they can give a little bit of advice, as in these forums.

Colin

Hey Colin... No worries, nothing wrong with your eyes, I went back and edited the post after your comment (for which I owe you!) just in case someone tried to use this as a reference...

And yes, I agree with your trial and error approach!  I did get there in the end, my only concern for the Ubuntu community at large is how many people would have fallen by the way side by now...

---

### Post by gwowders on 2007-03-02
> **lunchbox_1973 said:**
> I feel your pain brother, it took me a good two or three weeks to finally get the wireless going on my Dell Inspiron 1300. Like you I read many many different how-to's and tips.

I FINALLY got mine to work by using an outdated driver believe it or not. The up to date Win XP driver didn't do the trick.

I'm very happy with my wireless performance but I've yet to connect to an encrypted signal. I know there are tons of other threads on people like me who are having trouble with WEP and WPA. I'll tackle that next when I need a challenge.

In the meantime please don't hack into my network since I turned the encryption off :) 

Although Ubuntu is great and free so we don't really have the right to bitch, the devs really need to get wireless working out of the box. I'm sure it frustrates a lot of people to the point where they give up and go back to Windows.


Glad you finally got things working!!!!  I must admit, I managed to get WEP up and running at the same time with no extra 'jiggery pokery' necessary, but I understand that it isn't this easy for everyone!

Now....  Off to find that unsecure network...... ;-)

---

### Post by tyres on 2007-03-02
Hey gwowders,

If you want to go for WPA, I've got that going (after a struggle, of course!). I could copy my /etc/network/interfaces script to you. I had got WPA2 going (with hidden SSID), but had to dumb down to WPA1 because XP Home on my dual-boot (with Ubuntu) laptop doesn't seem to support WPA2.

Got to be better than WEP and a visible SSID though.

Colin

---

### Post by gwowders on 2007-03-02
I haven't got as far as that yet buddy!  I've got WEP and a hidden SSID, which will do me for now.  I don't exactly live in a sprawling metropolis, and the signal is pretty weak from my living room up to the office, so I'm not overly worried about my elderly neighbours jacking my broadband.  I may toy with it later though, just as an experiment, so your offer of help could well come in useful later on!!!

---

### Post by jkeyes0 on 2007-03-02
> **gwowders said:**
> if I have to make one comment about this (and I really feel I do), it wasn't easy in the slightes, and I'll bet that for every one person like me that perseveres and eventually gets this working, there are hundreds that don't. If it is the ultimate goal of the Ubuntu crowd to truly push their distro to the masses then **this ndiswrapper process needs to be dramatically improved and simplified.** I appreciate that there are lots of other driver issues (and that this isn't always the fault of the OS, rather the vendors that just don't create driver software for *nix) but network connectivity is key, because the CD can't contain everything! Once a user has access to the 'net (and the great resource that is these forums) then thats half the battle. IMHO (as far as any opinions are Humble) **this needs to be addressed as a matter of priority.**

</rant> ;-)

Honestly, this problem could mostly be solved if the hardware manufacturers would put out Linux drivers, so they could be incorporated into the kernel. As it is, there are some that just plain don't, so we're forced to use Windows drivers to compensate. Ndiswrapper isn't really all that bad once you've done it once, but it's truly an advanced concept, not intended for the entry-level user.

If you really think about it though, how many times have you installed Windows and the wired networking doesn't even work? I'm pleased that every time I've installed Ubuntu, i haven't had to search for Marvell drivers for my Gigabit wired ethernet card.

---

### Post by gwowders on 2007-03-02
> **jkeyes0 said:**
> Honestly, this problem could mostly be solved if the hardware manufacturers would put out Linux drivers, so they could be incorporated into the kernel. As it is, there are some that just plain don't, so we're forced to use Windows drivers to compensate. Ndiswrapper isn't really all that bad once you've done it once, but it's truly an advanced concept, not intended for the entry-level user.

If you really think about it though, how many times have you installed Windows and the wired networking doesn't even work? I'm pleased that every time I've installed Ubuntu, i haven't had to search for Marvell drivers for my Gigabit wired ethernet card.

Hey jkeyes0,

I completely agree, if the drivers were available this wouldn't be a problem of course!  Someday, they'll all start to produce drivers, but it would seem to be a supply and demand problem at the moment and so the whole issue becomes very much like a 'chicken and egg' scenario.  

You've been lucky so far, fingers crossed you never have to worry about this kind of thing!

---

### Post by jkeyes0 on 2007-03-02
> **gwowders said:**
> Hey jkeyes0,

I completely agree, if the drivers were available this wouldn't be a problem of course!  Someday, they'll all start to produce drivers, but it would seem to be a supply and demand problem at the moment and so the whole issue becomes very much like a 'chicken and egg' scenario.  

You've been lucky so far, fingers crossed you never have to worry about this kind of thing!

Actually, I have a Broadcom 4311 wireless card in my laptop, so I've had loads of experience using (and breaking) ndiswrapper. Combine that with both my laptop and desktop having ATi cards, and I've had my hands full. :)

---

### Post by gwowders on 2007-03-02
Ahhhh yeah, I've heard there are a few problems with ATI drivers.  I thought the Nvidia driver installation method was a little more complex than it needed to be!!!

---

