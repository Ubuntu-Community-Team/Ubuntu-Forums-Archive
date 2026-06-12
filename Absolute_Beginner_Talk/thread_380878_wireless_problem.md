---
title: "wireless problem"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Griffiss on 2007-03-10
hey everybody

I'm totally new to linux and having some real problems getting my wireless connection going.

My card is an ASUS WL-138G. It needs ndiswrapper and I think i've installed that ok.

I thought my problems were over because typing code: 'ndiswrapper -l' gave

Installed ndis drivers:
mrv8k51 driver present, hardware present

But when I go to System > Administration > Networking, there is no wireless connection, just a wired connection (from a different ethernet card), and a modem connection (from the built in modem I think.

Any ideas with this? Please help I'm going crazy!!

---

### Post by Griffiss on 2007-03-10
can anybody help with this please? I'm getting nowhere on my own

---

### Post by Kobalt on 2007-03-10
Alrighty then :) Can you please post us the result of the following command line ```
iwconfig
```
Is there still any wireless connection after you type the command ```
sudo modprobe ndiswrapper
``` ?

---

### Post by Griffiss on 2007-03-10
thank you kind stranger!  :)
```
iwconfig
```

gives
```

lo        no wireless extensions.

eth0    no wireless extensions.

sit0     no wireless extensions.
```

and when i type ```
sudo modprobe ndiswrapper
```
it gives ```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
```

to my untrained eye, this doesn't look too good?

---

### Post by Kobalt on 2007-03-10
Well then you aren't trained too badly : it's not that good :( 
It seems ndiswrapper isn't installed correctly. How did you install it : through Synaptic or did you compile it yourself ?

---

### Post by Griffiss on 2007-03-10
well I've bashing away at this problem since yesterday and have followed numerous walkthroughs.

I installed ndiswrapper through synaptic first of all, and installed all the ndiswrapper packges that were on the ubuntu cd: ndiswrapper-common (1.18-1ubuntu2), ndiswrapper-utils-1.8 (1.18-1ubuntu2), ndiswrapper-utils (1.1-5), and ndiswrapper-utils-1.1-5. But then i believe I uninstalled these when the method didn't work.

then i tried this: ```
sudo modprobe -r ndiswrapper
sudo apt-get install ndiswrapper-utils
```

and the result is what i have now i think.

ps when i type ```
sudo lshw -C network
```
the entry for my wi-fi card starts like this ```
*-network:1 UNCLAIMED
```
and there is no 'configuration:' line.

---

### Post by Griffiss on 2007-03-10
i just had a look in synaptic and all the ndiswrapper packages mentioned above are installed, apart from ndiswrapper-utils-1.8, which is not installed.

---

### Post by Kobalt on 2007-03-10
Did you install your kernel headers before installing ndiswrapper ? 
```
sudo aptitude install linux-headers-$(uname -r)
```
If not, run the above command line and then reinstall ndiswrapper...

---

### Post by Griffiss on 2007-03-10
ok, thanks, i'll try that now

---

### Post by Griffiss on 2007-03-10
Omigod! it's now recognizing the wireless connection in System > Administration > Networking!

But I don't know if it's connecting.

---

### Post by Griffiss on 2007-03-10
thanks a lot for your help Kobalt, I really appreciate it.

I put in the network name and passkey, but still no connection. It's a WPA

---

### Post by Kobalt on 2007-03-10
I would recommend you to install network-manager (it's in the repos) to manage your wireless connection, as it support WPA.

---

### Post by Griffiss on 2007-03-10
I tried that, it says network manager can't download on my type of machine (i386)

---

### Post by Kobalt on 2007-03-10
> **Griffiss said:**
> I tried that, it says network manager can't download on my type of machine (i386)
bump :-| 
Network-manager is definitely compatible with i386 architectures : how did you try to install it, Synaptic or the Terminal way (aptitude or apt-get) ?

---

### Post by Griffiss on 2007-03-10
I tried it through the Add/Remove... option under applications. Can't find it through synaptic

---

### Post by Kobalt on 2007-03-10
you should find it in synaptic under *network-manager*... what version of Ubuntu are you using ?

---

### Post by Griffiss on 2007-03-10
hello again Kobalt, thank you for your continued assisstance.

I have version 6.10, installed from the i386-desktop cd.

I can't find network-manager in synaptic. i don't have a connectio ntop the internet from the computer i've installed ubuntu onto.

---

### Post by honns on 2007-03-10
hey again, just go and download wifi radar in the add/remove, i was told by the staff that it works with WPA

---

### Post by Griffiss on 2007-03-10
hey honns

it says I need a working internet connection to continue installing wifi radar, and I don't have one on the computer I've installed ubuntu onto (posting from a separate windows laptop at the moment)

---

### Post by honns on 2007-03-10
oo yea i forgot about that, well this is where i found out that network manager wont work on my computer...maybe it will help you

[http://www.ubuntuforums.org/showthread.php?t=341357&highlight=how+to+network+manager](http://www.ubuntuforums.org/showthread.php?t=341357&highlight=how+to+network+manager)

---

### Post by Griffiss on 2007-03-10
Thanks honns, I had a look at that but my card wasn't in the list of those supported by Network Manager anyway - I can feel the pangs of despair creeping on now....

---

### Post by honns on 2007-03-10
yea same here, but i am going to be in the same boat tonight when I go home to my router with WPA AES encryption ive downloaded 2 applications that will hopefully allow  me to connect, ill let you know what works and what doesnt

---

