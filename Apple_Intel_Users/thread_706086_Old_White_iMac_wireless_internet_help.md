---
title: "Old White iMac wireless internet help"
date: 2008-02-24
forum: Apple Intel Users
---

### Post by hikaru56 on 2008-02-24
I just got done installing Ubuntu on my 2.0 gig dual core iMac and I found out my wireless card won't work. (I am new to Ubuntu) I tried to follow the guide here [https://wiki.ubuntu.com/iMacIntel?highlight=%28mac%29](https://wiki.ubuntu.com/iMacIntel?highlight=%28mac%29) but it didn't seem to work. 

Can anyone help me???

---

### Post by cyberdork33 on 2008-02-24
> **hikaru56 said:**
> I just got done installing Ubuntu on my 2.0 gig dual core iMac and I found out my wireless card won't work. (I am new to Ubuntu) I tried to follow the guide here [https://wiki.ubuntu.com/iMacIntel?highlight=%28mac%29](https://wiki.ubuntu.com/iMacIntel?highlight=%28mac%29) but it didn't seem to work. 

Can anyone help me???
You need to go into further details about "it didn't seem to work" How do you know it didn't work?

Can you check the output of ifconfig?
Did you reboot after installing the ndiswrapper driver?
Did the driver load properly? (output of 'ndiswrapper -l' that's a lowercase L)

---

### Post by hikaru56 on 2008-02-24
Ok so I ran the ifconfig and this is what came up: 

eth0 Link encap:Ethernet HWaddr 00:16:CB:8C:8A:04
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:16

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:64 errors:0 dropped:0 overruns:0 frame:0
TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:5008 (4.8 KB) TX bytes:5008 (4.8 KB)

I did reboot after installing and when I did the -l command for ndiswrapper it came up with three drivers all of them invalid.  I tried to remove the driver so I could reinstall them but I don't fair too well with the terminal just yet. 

(Thank you for the help)

---

### Post by cyberdork33 on 2008-02-24
> **hikaru56 said:**
> I did reboot after installing and when I did the -l command for ndiswrapper it came up with three drivers all of them invalid.  I tried to remove the driver so I could reinstall them but I don't fair too well with the terminal just yet. Well, if you have 3 drivers installed, I would guess that is an issue. You need to remove all but one. (The right one ;) )

to remove the driver, use the -l command to list all the drivers installed, then use the remove command to remove the driver you want, as named in the output of the -l command. For instance, If the driver is named bcmwl5, then to remove that I would type:
```
sudo ndiswrapper -r bcmwl5
```
Do this until the list is clear, then install the one and only appropriate driver as instructed in the [Macbook-SantaRosa wiki page]("https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b") (It has the same card as our iMacs do).

---

### Post by hikaru56 on 2008-02-24
Ok so I cleared the list and installed the driver just like how the instructions said. But when I try to connect to my router it won't let me and keeps on asking for the password (which I keep on putting in). Is there some special way to connect to a router using ubuntu? 

(Thanks again for all your help so far)

---

### Post by uberlube on 2008-02-24
you have to specify what kind of password it is. wep1/2 or wep or whatever yours is.

---

### Post by hikaru56 on 2008-02-24
I did specify the kind of passcode. It will try to connect then ask for it again.

---

### Post by uberlube on 2008-02-24
Ya I've been in that same situation without much luck. The only thing that I can suggest it to switch over to Kubuntu or any distrobution that uses KDE (K Desktop Environment) it has way better support for wireless drivers, plus I just prefer it overall. 

Here is what mine looks like:

---

### Post by hikaru56 on 2008-02-24
Okay I will try switching over to Kubuntu. Hopefully it works. Is Kubntu that different from Ubuntu?

---

### Post by uberlube on 2008-02-24
Yes in alot of ways. But it is also very similar. I find it much nicer looking and easier to work with.

---

### Post by hikaru56 on 2008-02-24
I tried Kubuntu and it had the same problem Ubuntu had. It kept on asking for a key and I kept on selecting my encryption choice and entering the right password. When it said it did connect I would get zero signal. Any idea of what is wrong?

---

### Post by uberlube on 2008-02-24
Exacctly what methode are you using to get this working? Past the steps in a post and tell me what you did.

---

### Post by hikaru56 on 2008-02-24
[https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b)  <--- I used the method that is found here

---

### Post by uberlube on 2008-02-24
Ok so you have a Broadcom. Go to my HowTo and try my method and let me know how it works.
[http://ubuntuforums.org/showthread.php?t=706034](http://ubuntuforums.org/showthread.php?t=706034)

---

### Post by uberlube on 2008-02-24
I know it is similar but try it out anyway. I got another guys Broadcom to work yesterday using this method and it works like magic for my LinuxMint KDE daryna laptop.

---

### Post by cyberdork33 on 2008-02-24
your driver seems to be working fine if you can even see a WiFi network. Try testing with the encryption turned off to see if it can connect that way. If that works then you know it is related to the encryption you are using.

---

### Post by hikaru56 on 2008-02-24
> **cyberdork33 said:**
> your driver seems to be working fine if you can even see a WiFi network. Try testing with the encryption turned off to see if it can connect that way. If that works then you know it is related to the encryption you are using.

That is the thing. I can't see a wifi network. I go to connect to other network.

---

### Post by cyberdork33 on 2008-02-25
> **hikaru56 said:**
> That is the thing. I can't see a wifi network. I go to connect to other network.
You never gave output for ifconfig after installing the driver over. Does it list your card now?

If the card now shows up, for network-manager to use your card correctly, you need to make sure it is in roaming mode. You can check this in System > Administration > Network in Ubuntu. I don't know the equivalent location in Kubuntu.

---

