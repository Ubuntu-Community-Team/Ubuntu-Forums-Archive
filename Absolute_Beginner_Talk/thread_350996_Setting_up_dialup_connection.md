---
title: "Setting up dialup connection"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by tyler_roach on 2007-02-01
Hi,  
I've just installed Ubuntu on my friend's laptop, and I'm trying to setup the dialup connection. I've found the driver and installed it, and I think I've configured everything in the Network Settings applet. My question is: How do I connect? I mean, where is the button that I click or the command that I enter to get the modem to dial up the ISP number?

Thanks.

---

### Post by rapattack1 on 2007-02-01
I think I am in the same position. I have Ubuntu 5.04 on my desktop and I used GnomePPP but in the 6.10 distro I have tried everything. Nothing is letting me connect and for some reason I keep changing it from pulse dialing to Tone and it won't stay like that. I have tried wvdial but I need more precise instructions on what to type in. 
Sorry to stick my nose in your post but I am pretty new. My IT friend set this desktop up not me, The laptop was my doing.
Thanks!

---

### Post by Cariboo1938 on 2007-02-01
> **tyler_roach said:**
> Hi,  
I've just installed Ubuntu on my friend's laptop, and I'm trying to setup the dialup connection. I've found the driver and installed it, and I think I've configured everything in the Network Settings applet. My question is: How do I connect? I mean, where is the button that I click or the command that I enter to get the modem to dial up the ISP number?

Thanks.Install "Gnome ppp" with Synaptic Package Manager (-->System -->Administration -->Synaptic Package Manager). 
After that , you'll get a grahical menu! I attached what I did for configuration>

---

### Post by rapattack1 on 2007-02-01
GnomePPP doesn't seem to be available in 6.10.

---

### Post by Cariboo1938 on 2007-02-01
> **rapattack1 said:**
> GnomePPP doesn't seem to be available in 6.10.Sorry for the typo, it is "gnome ppp". You should find it. I use it with Ubuntu 6.10

---

### Post by tyler_roach on 2007-02-01
Thanks,
Can I use synaptic to install Gnome PPP from the CD? We have no internet connection, of course, but if it absolutely came down to it, I could set up my USB DSL modem on his laptop (which would be a bit of a job.)

---

### Post by nixclusive on 2007-02-01
a simpler command line method might be using pppconfig.
in the terminal enter:
```
sudo pppconfig
```

its a menu driven utility. after configuration enter:
```
sudo pon <provider>
```where <provider> is the name you might have assigned in the configuration. To shut down the connection, either turn off the modem or enter:```
sudo poff <provider>
```Here, <provider> is optional.

---

### Post by ieee488 on 2007-02-01
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by nixclusive on 2007-02-01
...erm.. yeah, a USB DSL modem. Is that an ADSL connection?

---

### Post by rapattack1 on 2007-02-02
Still can't find Gnome PPP. It is just not there. 
I have also looked at that how to file but I am also having trouble with the modem. I have tried 2 types of modems. The odd thing is that my internal winmodem is mentioned in device manager so I thought it would work. I heard that winmodems might work now? I also tried the modem(external serial) thta I am using on this machine right now. I tried the same "scan modem" tool that I downloaded for this machine but I am getting no where.

---

### Post by ieee488 on 2007-02-02
If you have an external SERIAL modem, just open up Terminal and type **sudo wvdialconf**. It should find it.

I don't think gnome-ppp comes on the CD which means you won't find it unless you have an internet connection.

Do a search for it, download it to Windows. Copy it to a USB flash drive. Take the USB flash drive to Ubuntu. Install it from there.

You really should read that HOWTO. It explains 3 ways on how to get online.

---

### Post by rapattack1 on 2007-02-02
Yep I tried sudo wvdialconf and it didn't find either modem. I am connected to the net on this machine but I do not have a usb flash drive. I could burn it but I haven't tried to use the burner yet on this machine. Will do that after I get the modem working and I read that how to many times. Sorry it is just way beyond me if the modem works on this machine it should work on the other one. Will try again tomorrow I think. I have been reading too much and it is way too exhausting. Thanks!

---

