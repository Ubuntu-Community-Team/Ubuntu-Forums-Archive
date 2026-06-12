---
title: "[SOLVED] Wireless WEP woes"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by steenledet on 2007-12-17
Hi all,
just about to migrate from Vista to Ubuntu Gutsy (dual-booting so far). First-time linux user.

I'm on a Dell 6400 with Dell Broadcom 1390 wireless card, and it seems to work fine once the restricted drivers are installed - the wifi light is on, and I can locate my wireless network.

However, when trying to log on, I type in my key and nothing happens - the lower of the two buttons go green, but after a while it asks for my key again - and I know it's the right key. My wireless connection is WEP and I can't turn this off, since my provider put it there. I have no problems in Vista.

I have looked around for solutions here and elsewhere. I have tried Wicd (didn't work), and Wifi radar (didn't work). Any thoughts about what to do?

Help me ubuntu community, you're my only hope.

---

### Post by Lord_Dicranius on 2007-12-17
Broadcom wireless cards are a little wacky in Linux.  I think the only way to get those to work is to actually used the closed source driver provided to Windows, just loaded on Linux.  Do you have the 'ndiswrapper' packaged installed? (it can be found in the repositories).

---

### Post by steenledet on 2007-12-17
No, I haven't. Should I have this installed instead of the broadcom driver or in addition to?

---

### Post by Lord_Dicranius on 2007-12-17
How did u install the broadcom driver initially?  Through the restricted drivers manager?

---

### Post by Technoviking on 2007-12-17
> **Lord_Dicranius said:**
> How did u install the broadcom driver initially?  Through the restricted drivers manager?

Some broadcom drivers will install though the restricted driver manager, others need ndiswrapper  install by hand.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Lord_Dicranius on 2007-12-17
Ah, there we go.  Thanks for posting that link, Mike :)

---

### Post by steenledet on 2007-12-17
Yes, I installed the broadcom driver through the restricted drivers managers, and it seems to work fine, except for the WEP issue. But, I'll try the ndiswrapper solution, thanks.

---

### Post by steenledet on 2007-12-19
Well, my wifi reception is certainly a lot better with the ndiswrapper and Windows Driver: I can see networks before that I can't now. That's great, and I can even connect without any problems to public networks.

However, no luck getting past my WEP encryption - I punch in the key, get a high percentage connection in Network Manager, but still won't connect to the Internet, and after a short period, it asks for the key again.

Any thoughts?

---

### Post by Lord_Dicranius on 2007-12-19
What do your /etc/network/interfaces file look like?  In reading other forum posts, it sounds like the only device you want in that file NOT commented out (doesn't have an "#" ahead of it) is the "lo" device.  Network-manager should take care of the rest.

---

### Post by gilf on 2007-12-19
Make sure you are entering the right kind of key (ie 128 bit vs 64 bit) Just resolved a problem where a user was entering a 128 bit key, but had 64 bit set up on their router. There is a place in the password dialog that allows you to specify the number of bits in WEP.

Also make sure the router doesn't want a WPA password.

In other words, **check the router setup first.**

In network manager auto you should be entering your key with this procedure:

Click on the network icon on the top right of your screen.

A list of available networks with bargraphs should appear.

Click on the bar graph network line that you want to connect to.

You should then be given a dialog asking for the wep or wpa or whatever password.

This is where you enter it.

You will be asked if you want to save it in the keyring, I say yes here.

You should be connected.

This all assumes auto, roaming mode.

Many, many problems are caused by trying to set these parameters manually through some other method than the above procedure. Particularly when the settings are saved for startup. Many people then lose the ability to connect via auto without rewriting the network/interfaces file.

Hope this helps.

ps. The only way you can enter a WPA key in network manager, to my knowledge is with the above procedure. Many people are stumped when they try to find a profile manually to set a WPA key. There doesn't seem to be one for Network Manager.

It is designed to work automatically. It requires that you select a network and try to connect to it by the above procedure BEFORE it asks for a WPA password. There are no profiles to enter it in advance.

Nevertheless, through the keyring, you can store the WPA password AS IF network manager had a profile.

I've devoted a thread to some basic and common misunderstandings of network manager here:

[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

A large number of people are altering their systems unecessarily (and to little or negative effect) because of some simple misunderstandings.

While you may legitimately need special drivers for broadcomm chips, many people do not for others -- this can be easily determined by booting from a LiveCD and trying to connect by the above method, as outlined in the thread I wrote.

---

### Post by steenledet on 2007-12-19
> **gilf said:**
> Make sure you are entering the right kind of key (ie 128 bit vs 64 bit) Just resolved a problem where a user was entering a 128 bit key, but had 64 bit set up on their router. There is a place in the password dialog that allows you to specify the number of bits in WEP.

:oops:

This forum needs a Homer smiley - it wasn't a 64/128-bit problem, but I should have set if for 128 Hex rather than 128 passphrase.

D'oh!!

Thanks a lot for all of your help, the problem is now solved.

---

### Post by gilf on 2007-12-19
We're all homers under a thin candy shell.

Happy Ubuntuing! :)

---

### Post by jwvans on 2008-01-01
i had a similar or maybe the same problem. Just until i installed Wicd with the mandatory wpa_supplicant. Make sure that you choose 'wext' as the wpa supplicant driver in the Wicd    Manager preferences. Works for me...

---

