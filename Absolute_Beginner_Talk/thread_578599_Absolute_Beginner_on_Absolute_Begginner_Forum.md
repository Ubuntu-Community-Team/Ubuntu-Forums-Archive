---
title: "Absolute Beginner on Absolute Begginner Forum"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by castalla on 2007-10-17
I've spent the last 24 hrs trying to discover how to get Broadcom wifi working on Ubuntu 7.10.  Most of that time has been spent trawling though hundreds of posts and so-called easy how-tos.  I am totally at a loss.  I want to simply access my wifi connection.  Instead, I've been sent to pages with scripts to install ndiswrapper, driver files, etc.  Most of these assume much more than the forum title of Absolute Beginner.   Usually, there's the final Catch-22 ... to do this, download from the internet .... err, yes and why am I trying to install my wifi connection?

The irony is that the only way I can see the internet in Ubuntu is by running it under Windows VMware (with the snag that nothing can be changed!). 

Is there anywhere here a foolproof simple way to install broadcom wifi offline?

Somebody somewhere must have the key!

---

### Post by reckless2k2 on 2007-10-17
maybe you should wait until tomorrow or over the weekend to download the latest ubuntu that's going to be released. it has support for broadcom that you would just install broadcom through the restricted drivers menu.

---

### Post by castalla on 2007-10-17
thanks for the tip ... but I'm trying to use Ubuntu 7.10 (release candidate).  Will the release really have the Broadcom support?   It doesn't seem to be there in the Release Candidate.

---

### Post by reckless2k2 on 2007-10-17
i haven't used the betas or the RC. i've only read the reviews explaining how it is supposed to work just like nvidia restricted drivers. i can't comment on the RC or betas. i guess we will find out tomorrow.

---

### Post by drinkpepsi on 2007-10-17
nevermind

---

### Post by castalla on 2007-10-17
This what I get with 7.10 -

Software source for package is not enabled

Can't get any further using the Software manager

---

### Post by aysiu on 2007-10-17
I think you should just give up.

Broadcomm wireless cards are not compatible with Linux, and the use of is *ndiswrapper* is just a clever workaround. The real solutions are:
1. Stick with Windows
2. Get a new wireless card, one that's compatible
3. Tough it out and follow instructions

Are you saying that wireless is the *only* way you have to access the internet? You don't have a stray ethernet cord you can plug into your router?

---

### Post by funrider on 2007-10-17
wireless sucks ball for ubuntu.......

here is a list but it doesnt got updated that often. Last time i picked up the belkin on and it works out of the box fine.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

hope this help

---

### Post by aysiu on 2007-10-17
I'd highly recommend the Intel Pro Wireless 2200

---

### Post by SDL on 2007-10-17
Hi. I had a similar problem with a Broadcomm wireless card when I got Ubuntu a few months ago. The first post in [this thread]("http://ubuntuforums.org/showthread.php?t=405990") worked very well for me.

Assuming you're now using Windows to access the internet. Scroll down to Section 1 and download the offline installer then put it on a USB stick. Restart the PC into Ubuntu, access the file on the USB stick and follow the instructions in DarkN00b's forum post.

I hope this is helpful. Sorry if it's not, I'm a complete beginner myself but this worked well for me!

Stephen.

---

### Post by castalla on 2007-10-17
Well an update ...

I got connected to web via hard wire (success of sorts) and decided to follow the DarkNoob route.
After alot of downloading of new files and updates, I went for the Online installer.  Got loads of error messages.  Mainly that Broadcom not present.  Anyhow I went ahead with the procedure.

When I rebooted I got some real problems - mainly a warning screen at login which said my session had lasted only 10 seconds, and try something about failsafe (whatever that is!).

So effectively the Ubuntu install I had is now screwed!  

This saga is unbelievable - in comparison to Vista, this linux Ubuntu is about as friendly as a scorpion on speed!  

Is there anybody out there who has successfully installed linux on an Acer Aspire 3690 which seemingly has Broadcom BCM94311MCG wifi installed ?  

I don't know why I just don't give up and stick with Vista as somebody suggested!

Thanks for the help so far.

---

### Post by jardo on 2007-10-18
i have that wireless card too and my laptop is acer 5613zwlmi. i have installed gutsy,but after trying for someday to make working good bcm43xx drivers...i didn't know what to do anymore...sometime those work some other no...by the way if u get a bit far away from the router u loose connection. anyway the driver works good in scanning.but doesn't let u connect to the ap.
i wrote some post about this problem but it seems noone interested :(
anyway i wrote it also on bug.lunchpad...hoping in a future this stupid card will work with native linux driver.
infact the card works good with ndiswrapper...but i don't know why i feel a bit stupid using windows drivers on linux :guitar:

---

### Post by castalla on 2007-10-19
What's the easy way to install using ndiswrapper?  Step by step instructions please!

---

### Post by jardo on 2007-10-21
try this : 

[http://ubuntuforums.org/showthread.php?t=297092&highlight=bcm43xx](http://ubuntuforums.org/showthread.php?t=297092&highlight=bcm43xx)

---

