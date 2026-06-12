---
title: "Can't get ubuntu to recognize my wifi card"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by perrybergmann on 2008-03-28
I can't get ubuntu to recognize my wifi card. I have a gateway m-6750 with a marvell card. I have looked at all of the tutorials on here and none seem to work. I can't even get ndiswrapper to install. Guess i'm going back to vista.

---

### Post by LowSky on 2008-03-28
ndiswrapper should work, how are you trying to install the driver?

---

### Post by DBrocks on 2008-03-28
Okay, I'm going to need you to elaborate: What model of card is it exactly?

And why can't you install ndiswrapper? What have you tried doing?

If you have no wifi, you need to hook it up with a hard-connection (NOT WIRELESS) to get ndis-wrapper. (There should be a connection labeled "ethernet") head over to your wireless router (should have ethernet connections on the back), and hook it up.

run:
```
sudo apt-get install ndiswrapper
```
See how that goes, and report back

Good luck!

~Dan

---

### Post by perrybergmann on 2008-03-28
Ndiswrapper is installed, and I don't have the cds to install from.

---

### Post by ibizatunes on 2008-03-28
maybe a long shot, but if you download 8.04 it may have the drivers built in...... but it is a beta

---

### Post by LowSky on 2008-03-28
> **perrybergmann said:**
> Ndiswrapper is installed, and I don't have the cds to install from.

what model is the card?

search the model name on google as in "_________ driver" it should pop up, download it, and install

---

### Post by DBrocks on 2008-03-28
> **ibizatunes said:**
> maybe a long shot, but if you download 8.04 it may have the drivers built in...... but it is a beta

No, Same problem in Hardy. However, Hardy's gonna be great when its released as a stable version!!

---

### Post by perrybergmann on 2008-03-28
every time I try sudo apt-get install ndiswrapper the command tells me its locked. I tried installing from synaptic, but I need the cds to install from that. 

My wireless card is:
Marvell TopDOg PCI Express 802.11n Wireless (EC85)

---

### Post by LowSky on 2008-03-28
Well now I know you have another issue as well. You source list isnt correct. and Synaptic is asking for your Ubuntu disk. Go to System > Administration > Software Sources and make sure you have all the options checked off, and uncheck the option for using Ubuntu CD

---

### Post by DBrocks on 2008-03-28
Okay, low sky knows more about this then I do. I'm just gonna step back for now. But good luck to you guys!

~Dan

---

### Post by perrybergmann on 2008-03-28
Okay, unchecked all options and made sure to uncheck download from cd. 

When I tried the command again  it says.

E:couldn't find package ndiswrapper.

---

### Post by DBrocks on 2008-03-28
As I said earlier, you need to hook it up to a router/modem. I dont think ndiswrapper is on the cd.
You can also download it from here on another computer, and transfer it:
 [http://archive.ubuntu.com/ubuntu/pool/main/n/](http://archive.ubuntu.com/ubuntu/pool/main/n/)

---

### Post by perrybergmann on 2008-03-28
I just got the package from another thread. hooked it up through the flash drive.

Now problem number two!

---

### Post by perrybergmann on 2008-03-28
still trying to figure out how to get my wireless card working. Any help?

---

### Post by deftone32 on 2008-07-15
O.k I have the same laptop and the driver for the marvell wireless is only available for Vista. I have searched for months for a native marvell driver for XP because I hate Vista and I have replaced it with Windows XP. Now I have the driver you need for XP. It's a netgear driver that works just as good if not better. I can give you the driver if you could help me install it on Ubuntu.

---

### Post by Reiger on 2008-07-16
If you have got the ndiswrapper compiled & installed (either through apt-get or through wget & some make code); *all* you need to do is the following:
```

pushd */[driver binary dir]/
sudo ndiswrapper -i net5211.inf
popd

```

That is if I understood the instructions dealing with Ndiswrapper + 'newer' Atheros wifi cards correctly. <_<

---

