---
title: "Wifi card?"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by Tixer on 2006-05-11
I have a spare computer, and since I use Windows most of the time, I decided I want Linux on the spare, since it would be fun to learn Linux.

I originally wanted to put server2003 on it, but that failed, along with XP, so after getting fed up, I called my friend and asked for a copy of ubuntu.

I need to know how to set up my WiFi card on ubuntu, as well as all the other hardware. How do I connect to a network in ubuntu, and also, how do I set up VNC, since I'll need that. 

How good is Ubuntu for file sharing? I need this thing to be able to share my files with WIndows computers, so how do I set that up.

The wifi card fyi is an RT2500 chipset, fairly common. Its an old machine, so I dont think anything else will have problems.

---

### Post by mjm115 on 2006-05-11
A response is posted in the [same exact thread]("http://www.ubuntuforums.org/showthread.php?t=174220") that you started.

---

### Post by louis_nichols on 2006-05-11
you might wanna try [here ]("https://wiki.ubuntu.com/WiFiHowto?highlight=%28wifi%29")first

the wiki has very useful info on a very large variety of aspects.

---

### Post by macdo on 2006-05-11
For your Wifi card: [http://wiki.ubuntu.com/Rt2500WirelessCardsHowTo](http://wiki.ubuntu.com/Rt2500WirelessCardsHowTo)

To connect to a network, just plug it in - it should do it itself. Ideally, have it on the network when you install Ubuntu.
If you need to see whether your network card is recognised, or if your network is up, use the command ifconfig -a in a terminal. If your card has an IP address, it's working. If it's listed but with no IP address, then it's not. Ask for help, in that case :-)

To share with Windows, use Samba. I don't know if that's installed by default with Ubuntu, but it's definitely in the repositories. Search the forums if you need help, as it's been covered many times :-)

---

