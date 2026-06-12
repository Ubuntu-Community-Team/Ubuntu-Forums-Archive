---
title: "Compatible wireless network card"
date: 2005-05-23
forum: Apple PPC Users
---

### Post by n!x on 2005-05-23
Hi,

I have just installed Ubuntu to my Powerbook G4 1,5 GHz and I'm now the happy owner of a dual boot Powerbook.

Ubuntu is running like a dream, but the Apple (Broadcom) wireless card is not supported (for now) by Ubuntu (Linux at all). Which one should I buy to have a wireless Ubuntu Powerbook runnin'? My powerbook have a PC Card slot, should I then buy such one or should I buy one of the USB dongles?

Is any of you having any good experiences? If you have some links for the compatible pc card/USB dongles and some urls for some installation guides (I'm quite a n00b) of the pc card/USB dongles.

Thanks in advance!

/n!x

---

### Post by Zelut on 2005-05-23
My emachines notebook uses a broadcom chipset for the wireless & I've managed to get it to work.  I wont promise it'll work with yours but its worth a shot.  Check out this post for instructions:

[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+wireless](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+wireless)

---

### Post by n!x on 2005-05-23
When you're saying "emachines" - you're meaning Apple Macintosh computers, right?

I've heard about a lot of others having their broadcom chipset wifi-card working in Ubuntu - but not those in Apple Macintosh computers....

Well, I could always give it a try :)

---

### Post by Zelut on 2005-05-23
Well, no, I dont mean apple computers.  Like I said, it may be a different chipset that might not work but its worth a try.  Try those steps in the link I set & see if that works.  If not we'll see what else we need to do.

If you need the driver files (generally used for windows machines) let me know & I can send you a copy... its worth a try anyway.

---

### Post by n!x on 2005-05-23
Thanks a lot!

I'm giving it a chance tomorrow - it's getting a bit late here in Denmark (Europe).

---

### Post by ssam on 2005-05-23
any of the ndiswrapper stuff wont work on an apple machine (maybe if you hacked around with qemu, but i think that is beyond most people, and probably not worth the effort.)

i have just got a pcmcia 802.11g netgear WG511, and that works very well and easily, and was only about £15 on ebay. also i have used a pcmcia 802.11b cisco aironet 340, and that works well. both of them requirepretty much no configuration. if they dont automagically connect to the nearest acess point, then you just need to pop into the network prefernces.

some people report sucess with a usb 802.11b d-link dwl-122, but it requires far more work (editing text files) to get going, doesn't show up in the network preffs, and can be unstable (in my experience)

sam

edit
just to clarify, its a netgear WG511 v2.0, FCCID PY3WG511-F, Cananda id 4054A-WG511-F, 32-bit cardbus

---

### Post by flim on 2005-05-24
[QUOTE=ssam]any of the ndiswrapper stuff wont work on an apple machine (maybe if you hacked around with qemu, but i think that is beyond most people, and probably not worth the effort.)

i have just got a pcmcia 802.11g netgear WG511, and that works very well and easily, and was only about £15 on ebay. also i have used a pcmcia 802.11b cisco aironet 340, and that works well. both of them requirepretty much no configuration. if they dont automagically connect to the nearest acess point, then you just need to pop into the network prefernces.

some people report sucess with a usb 802.11b d-link dwl-122, but it requires far more work (editing text files) to get going, doesn't show up in the network preffs, and can be unstable (in my experience)

sam[/QUOTE]
 I've got a netgear MA111 usb stick that's working fine. In general, it's hard to give any advices as cards do change rapidly (in version numbers) and with each change there's a chance of the chipset changing as well. I'd advice to look up some cards on ebay and check if they are supported - or take your powerbook to a shop and test all they have directly:-)

---

### Post by slux on 2005-05-24
Cards based on the Ralink 2500 802.11g chip are a good bet as well. They've GPLed their drivers and there's a project working on improving them. I've got a PCI version running on x86 and it's nice although the driver doesn't come with the default kernel. However, they've got a guide for installing up specifically for ubuntu.

Lots of 802.11b cards will work too, I've also got a prism2 usb stick (from buffalo) connected to an iBook. The 802.11g version of the same white stick should be ralink 2500 based and fits very well to the color of an iBook but since you have the option of using PCMCIA you'll probably want to find something for that. A-Link makes such a card but I don't know whether it's easy to get where you live.

The project's homepage is at [http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/) 

Now if anyone could just confirm that the driver works on PPC, I haven't tried it on a PowerPC machine.

What chip is the Netgear WG511 based on / what driver does it use?

---

### Post by n!x on 2005-05-25
Thanks for all answers - it's great to have a forum that sinply works :)

I have now tries a Wireless PC CARD (Avaya Wireless Silver) and it works, but not on my home network. The wireless card is found in Ubuntu, but it seems that I can't get in contact with my access point (Apple Airport Express). I have tried my Ubuntu and the wireless card at UNI - and it worked - I was online with the wireless card. But at home it just don't work.

My Airport Express access point is set up to be 802.11g and 802.11b compatible and of course I have it password protected to get in contact with it. In "Network Preferences" in Ubuntu i set the wireless card to be joining my access point (the name of it) and write the password. But I think that it's not the right information for it - it would not join the network (no signal). What is ESSID? And what is the password for the access point (I've heard something about that Apple Airport base use one password, not the WEP password).

Any one have an idea?

Thanks again for all the answers!

/n!x

---

### Post by flim on 2005-05-25
[QUOTE=n!x]My Airport Express access point is set up to be 802.11g and 802.11b compatible and of course I have it password protected to get in contact with it. In "Network Preferences" in Ubuntu i set the wireless card to be joining my access point (the name of it) and write the password. But I think that it's not the right information for it - it would not join the network (no signal). What is ESSID? And what is the password for the access point (I've heard something about that Apple Airport base use one password, not the WEP password).
/n!x[/QUOTE]

ESSID is the networks name - the way the accesspoint anounces the network to the public. I don't remember how it is called within the airport setup, but it should be the same as displayed in OSX.
I'm a little confused about your password statements - you do not need the password to access the access point. There's two of them - one to secure administration access (that's the accesspoints password which you don't need) and then the password/key for securing the network. If you didn't enable WEP, you won't need to enter anything as WEP password. I'd suggest doing that first, just to make sure everything else is working: switch of network security in the base station. (Also, give it a name you can easily remember - like 'mybase'). Then try to connect to it again.

flim

---

### Post by n!x on 2005-05-25
I've tried to connect using no WEP password - but no success!

It's more like that my Ubuntu can't or won't see the access point. I'm sure that I've written the exact name for the access point, but nothing helped :s

Which software can you suggest to help me search for wireless networks in my range?

/n!x

---

### Post by kris kincaid on 2005-05-27
I too am interested in software that will detect networks in range. I have a HP laptop and my wife has a new ibook, and they both jump all over any network within range.

---

### Post by oyvindaa on 2006-08-01
> **n!x said:**
> I've tried to connect using no WEP password - but no success!

It's more like that my Ubuntu can't or won't see the access point. I'm sure that I've written the exact name for the access point, but nothing helped :s

Which software can you suggest to help me search for wireless networks in my range?

/n!x

Using wifi-radar 

```

apt-get install wifi-radar

```

I managed to connect my Avaya Silver card to the router (Linksys Wireless G). 

It's important that you pick the right channel and key in the wifi-radar configuration. 

It worked flawlessly here, and maybe it should your end as well.

PS: I know this is an old thread, but maybe someone's got the same problem.

---

