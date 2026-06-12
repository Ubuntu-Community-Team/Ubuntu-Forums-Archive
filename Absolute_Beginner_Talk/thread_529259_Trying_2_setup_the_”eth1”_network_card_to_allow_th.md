---
title: "Trying 2 setup the ”eth1” network card to allow the internet to pass onto other PCs"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by bhowerton on 2007-08-19
Hello,
Can someone please help me as this is what I am trying to do:

I have a  computer (Compaq 5300US / Intel Celeron Processor 1.1GHz / 320MB SyncDRAM / 40GB HDD / “2” Ethernet network cards / 6MB download & 1MB upload Fiber Internet connection / CD-RW / Running Ubuntu Christian Edition vers. 7.04) that I am dedicating to be a Linux Server.  

I am trying to setup this machine so that I can take my my internet connection from the wall and send it into the “eth0” Ethernet card (to supply the internet to the network).  Then I want to send the internet out through the “eth1” Ethernet card (to supply the internet to all other PCs on the network).

So far I have got the “eth0” Ethernet card to accept the incoming internet signal (I am using that connection right now).

But, how do I setup the”eth1” Ethernet network card to allow the internet to pass onto all the other PCs on the network.

Please be as specific as possible as I am a new Linux user.  I desperately want to get away from Microsoft and help support the Ubuntu Linux movement.

Thank you, in advance, for your help!

Bobby

---

### Post by Sujith.James on 2007-08-19
Check in BIOS to enable Ethernet CARD;

---

### Post by bhowerton on 2007-08-19
Ok, I just rebooted and went into BIOS.  I checked the status of both Ethernet cards.  It shows them as being active.  I also clicked on the Ubuntu Start Menu button / System / Administration / Network.  This also shows both "eth0" & "eth1" as being both a wired Connection and Active with a check mark.  The address for both is "DHCP".

Right now I have the internet going from the wall into "eth0"...it is working...I am on the internet typing this post.

I also have a cable going from "eth1" (out of the Linux box) into the WAN port on my Netgear WGR614v5 Wireless router.  From the router I have my other desktop PC connected by cable and I have a wireless laptop.  Neither of the 2 PCs currently have any internet going to them.

It is like the internet is going into "eth0" but not leaving through "eth1".

Any help would be and is greatly appreciated!!

Bobby

---

### Post by bhowerton on 2007-08-19
So does anyone have any ideas of how to get my eth1 to hand out / send out the internet signal???

Any help would be greatly appreciated!

Thanks,

Bobby

---

### Post by garciadc on 2007-08-19
Hello,

I saw this and haven't tried it yet:
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)
 I'm kind of in a similar situation only my internet source is from a wireless transmission.  I will try this as soon as I get my touchpad to work.  Good luck

---

### Post by JustinMorris on 2007-08-19
I think I am looking for the same answer.

---

