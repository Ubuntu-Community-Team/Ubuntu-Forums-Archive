---
title: "Wireless again"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by psmul on 2006-09-24
Looo evryone

I'm also quit a n00b @ linux, but for school and fun I really want to learn it.
I installed the new version of it on my Toshiba Laptop and (besides from the installation blackscreen wich i ignored) it works great.

I do have some trouble getting my Linksys wireless PCMCIA (WPC54G) to work. I read almost every HOWTO's and stuf there is.
After some time i figured it was the WPA encryption, but even switching to WEP didn't help. I think i got the right driver installed though (i think it came with the installation because i didnt install one). It doest list in the Network toolbox thingy next to my normal Ethernet connection (wich does seem to work)

Can anyone tell me? (please do not refer me to another post, cos i visited them all)

Thnx alot

---

### Post by happy-and-lost on 2006-09-24
Umm...

give ```
sudo apt-get install wifi-radar
``` a go

---

### Post by emale07 on 2006-09-24
I can tell you that the card does work.  I have one and up until about 2 wks ago it worked like a charm.  Haven't had time to check out the problems yet, but hoping wifi-radar will help.

The frustrating thing is that it used to show up in the network manager, but now it doesn't.  I was beginning to think I had a hardware problem.  maybe not.

---

### Post by psmul on 2006-09-24
i tried 

sudo apt-get install wifi-radar


but it sayd that it couldnt locate wifi-radar packet. Is that a bad thing ?@! :-s

---

### Post by happy-and-lost on 2006-09-24
Have you enabled all your repos and pressed the "reload" button in Synaptic?

---

### Post by psmul on 2006-09-24
repos? Synaptic ?

sorry m8 but doesnt ring a bell

---

### Post by happy-and-lost on 2006-09-24
Right then. System-->Administration-->Synaptic package Manager

It'll probably tell you to reload. Do as it says!

Quit synaptic and try sudo apt-get install wifi-radar again

---

### Post by psmul on 2006-09-24
still returns the same error, couldnt find wifi-radar.

I tried looking in the list for it, but i could only find wireless-tools (installed)

---

### Post by happy-and-lost on 2006-09-24
You'll need to enable repositories.

In Synaptic Settings-->Repositories-->Make sure *all* of the ones Labeled "Ubuntu 6.06 LTS", "Ubuntu 6.06 LTS Security Updates" and "Ubuntu 6.06 LTS Updates" are selected.

Now reload and try again.

---

### Post by psmul on 2006-09-24
wow, i have no idea what i just did, but the command u gave me 

```
sudo apt-get install wifi-radar
```

worked and installed something i think.

Still, when i tried to connect my wireless, he took a long time to activate, and afterwards i still can't use the internet, so whats next :) 

btw. thank you very much for your time

---

### Post by psmul on 2006-09-24
when i try wifi-radar i get error's in the command line that 'interface does not support scanning: no such device' 

could there be somethin wrong with the standard driver Ubuntu installed ?

---

### Post by happy-and-lost on 2006-09-24
```
sudo apt-get install ndiswrapper
```

ndiswrapper is a sort of generic Linux wifi driver which should sort you out.

EDIT: Sorry, can you post what the terminal says when you type the command "iwconfig".

---

### Post by psmul on 2006-09-24
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```


makes me more and more think that there isnt a decent driver installed :-s


edit: eth1 = my cable internet, im sure of that

---

### Post by happy-and-lost on 2006-09-24
```
sudo apt-get install ndiswrapper
```

ndiswrapper supports your card, it should do the trick

---

### Post by psmul on 2006-09-24
:confused: 
i feel so stupid 

```
sudo apt-get install ndiswrapper
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ndiswrapper

```

sorry for the trouble, but i feel were getting close [-o<

---

### Post by happy-and-lost on 2006-09-24
I'm heading into the unknown now (My wifi worked out of the box)... but try... (taken from ndiswrapper wiki)

Before you load the module, DO NOT FORGET to type "depmod -a". If there is no error, continue.
To load the module type "modprobe ndiswrapper". If you get no error, the driver should now be loaded. You can verify this by checking the system log produced by dmesg. If the driver is loaded successfully, you should see a message in the system log

"ndiswrapper version <version> loaded"

---

### Post by psmul on 2006-09-24
depmod -a worked fine i guess,

but modprobe ndiswrapper gave me back this

```
ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-27-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

```

---

### Post by happy-and-lost on 2006-09-24
Seeing as I've not really got a clue what to do with ndiswrapper (I've only been using Linux for 3 weeks), this thread may prove useful:

[http://ubuntuforums.org/showthread.php?t=5645](http://ubuntuforums.org/showthread.php?t=5645)

EDIT: Did you try using the card whilst in the LiveCD? It might just not have installed properly.

---

### Post by psmul on 2006-09-24
it took a long time to complete the Howto you posted, but it worked :D 

thnx alot m8

---

