---
title: "Newbie networking questions"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by Bionic_Beefpile on 2006-02-08
Hi, I'm new to the forums and to Ubuntu.  So far I really like it, but I'm having networking issues that I hope someone can lend me a hand with.

First of all, and I'm sure this is an easy one to fix, is that when I boot my laptop without the ethernet cable plugged in, the boot takes a very long time, hanging at network initialization.  Is there a way to avoid this?

Secondly, I'm having wireless configuration issues.  I've got a PCMCIA Linksys card with a RealTek chipset.  I've used ndiswrapper to run the Windows driver, and the wlan0 shows up in the network configuration.  I selected the SSID of my network and entered the WEP key (in hexadecimal form).

I still don't get a connection through the wireless.  The "on" LED is lit, but not the "link" LED.  Also, if I go to "Network Tools", I don't see an IP address.  The wireless card works fine in Windows, since I'm using it atm to post this thread.  I've done some forum searches, but haven't stumbled upon the proper keywords yet to find the answer to my problems.  Any assistance will be appreciated.

Thanks

---

### Post by Bionic_Beefpile on 2006-02-08
Ugh I hate being new, I feel so dumb when I find out how little I know

Answer to q#1: Hit Ctrl-C, n00b
Answer to q#2: It has to be something with the WEP key.  I logged into the router (in windows) and disabled WEP, and now the card is working just fine in Ubuntu.  I'm still not sure why, but oh well :-k

---

### Post by paulmilliken on 2006-02-08
[QUOTE=Bionic_Beefpile]First of all, and I'm sure this is an easy one to fix, is that when I boot my laptop without the ethernet cable plugged in, the boot takes a very long time, hanging at network initialization.  Is there a way to avoid this?
Thanks[/QUOTE]
 You could remove all the networking-related applications from the /etc/rc.* directories.  The names that start with S start an application and the names that start with K kill an application.  If you do this, you will still be able to start the relevant applications manually after the computer has booted.

---

### Post by Bionic_Beefpile on 2006-02-08
Thanks Paul, Ctrl-C is working fine for me.

I'm still confused by the WEP key problems.  I've tried using both upper and lowercase letters in the hex key, as well as prefixing the key with "s:", and still haven't had any luck.  Lately, the "link" LED is lighting up on the wireless card, but I don't get an IP address assigned from the router, and don't have internet access.
The fact that the card works with the WEP turned off seems to me to indicate some sort of bug in the way Ubuntu is implementing the WEP... off to do more forum searches.  If anyone stumbles across this thread and has some guidance, I'd appreciate a hint!

::EDIT::
Well, I rebooted after putting the s: in front of the WEP key, and now I've got a connection.  Time to find more newbie issues :)

---

