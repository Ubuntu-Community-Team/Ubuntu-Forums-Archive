---
title: "Wireless Problems"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by Love&lt;3Duckie on 2006-05-27
Hey,

Before I made this thread I checked out one which went through somethings that Ubuntu just doesn't cover. This also mentioned problems with Wireless.

Recently, I took ownership of my sisters old computer. It had always been a curiosity to know what using Linux was like so, if you haven't guessed already what i'm about to say - I formatted her computer over to Ubuntu. It was fun fiddling about but then I wanted to go online.

I tried hooking it up with my main PC which is on Windows through an ethernet connection but my main PC gets to the net via a Wireless PCI card which goes to my router downstairs. I tried configuring it but it just wouldn't work.

So I gave up and thought "What the heck" and went out and bought an extra wireless PCI card for my sisters PC instead of it relying on my main.

I put it in and then looked at device manager to find Ubuntu knew it was there it just didn't know what it was.

So obviously Network Admin couldn't use the device.

So my question is, how do I get it working?

Luc.

---

### Post by tartarian on 2006-05-27
There are a few roads to go down:

Get ndiswrapper (run a search in synaptic) and install your driver if its not already installed. 

Look at this tutorial. It is very good:

> [https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29](https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29)

Hope it helps

---

### Post by Koech on 2006-05-27
What make is the wireless device? What is the output of running lshw or lspci in terminal?

---

### Post by Love&lt;3Duckie on 2006-05-27
[QUOTE=Koech]What make is the wireless device? What is the output of running lshw or lspci in terminal?[/QUOTE]

It's a Belkin Pre-N adapter.

The components on the board are Ricoh.
Other than that, I don't know anything.

---

### Post by nalmeth on 2006-05-27
For a fairly comprehensive troubleshooting guide, see the Wireless Help link in my signature.

Good luck

---

