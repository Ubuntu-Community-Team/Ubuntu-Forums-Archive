---
title: "DuelBoot Done! Ubuntu and Wireless Card?"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by Viral on 2006-08-22
First off, this morning I sucessfully completed the DuelBoot thanks to some very helpful members of ubuntu. These forums are great for support, I'm glad I ran across the Ubuntu Distributer.

Well, after my duel boot, I got lots of things set up. Right now, I'm typing on Windows, because I can't find a way to connect with my Wireless card with Ubuntu!

I go to "System -> Networks" or whatever, and it lists different connections. I have 2. One is my ethernet port, and the other is my Wireless card.

Now, the ethernet port it activated, but the Wireless card is not. When I highlight it and click "Enable Connection", and for a minute it says "Enabling...." and then it turns off after 5 minutes and it says it's enabled. I exit the Network Settings, come back, and it says that it is still disabled. I don't know what's wrong, but I can't WAIT to use Ubuntu on my computer.

Thanks much!

---

### Post by bob phillips on 2006-08-22
now i've just got xubuntu 6.06 running, and i turned off my ethernet card before turning on the wireless one (which now works beutifully!)

no idea if this really works, but like touching wood, it's not a great problem if it doesn't!

also - have you checked your wireless card is supported? (it's on the main 'how-to' page somewhere)?

---

### Post by Viral on 2006-08-22
How do I find out if my card is supported?

I have no idea what it is, it's inside my comptuer somewhere, came with my Gateway Lappy.

EDIT: When the wireless is working, will I see a list of inrange networks, like Windows XP? That's what I need....

---

### Post by Viral on 2006-08-23
Hmmmm.... I've tried just everything, can someone suggest anything?

---

### Post by crispy_420 on 2006-08-23
What card do you have in there? Chipset?

That is what we need to know, then we can go from there. Or maybe if you could tell us the exact model of Gateway then we could look it up.

---

### Post by Viral on 2006-08-23
[http://support.gateway.com/s/Mobile/Gateway/6000Series/5378nv.shtml](http://support.gateway.com/s/Mobile/Gateway/6000Series/5378nv.shtml)

Product Specs: [http://support.gateway.com/s/Mobile/Gateway/6000Series/5378sp3.shtml](http://support.gateway.com/s/Mobile/Gateway/6000Series/5378sp3.shtml)

What it says under Wireless:
Network 	802.11g integrated wireless (up to 54Mbps)
SecureEasySetup™, 125 High Speed Mode
10/100Mbps integrated Ethernet LAN

---

### Post by Viral on 2006-08-23
Anybody? I really need this done.

---

### Post by Ninjai on 2006-08-23
Ok well I have a Realtek 8180 onboard wireless in my laptop and this is how I get the network to work.(I dont have it near me so sorry if not exact).
Go to System->Network (or wherever it is). Deactivate ethernet, then click "Configure" for the wireless card (Network Name, DHCP or Static, Any wireless security (if not leave blank any select Plain key). Apply and exit, wait until progress bar stops. Make sure Wireless card is activated, make sure WLAN0 is selected in box at the bottom, then close main window.

---

### Post by Viral on 2006-08-24
Is there a way to make it so I can see the networks in my range?

---

### Post by Ninjai on 2006-08-24
Personally I cant. Until I type in my exact name for my network I cant do anything. Do you not know yours?

---

### Post by nickpaton on 2006-08-24
From the hyperlink to your Gateways laptop specs, you appear to have a Broadccom Wireless driver, which will need to be separately installed.

Ubuntu does this by using the bcmwl5.inf and bcmwl5.sys Windows drivers as I detailed in another post here:

[http://www.ubuntuforums.org/showthread.php?t=240279]("http://www.ubuntuforums.org/showthread.php?t=240279")
 
Look at post 7 onwards.

Using the System>Administration>Windows Wireless Drivers program which I installed via Automatix, I found it to be relatively straight forward.

I do emphasise that you need to persevere with getting the wireless settings to be accepted, and the key seems to be rebooting after you have made the settings, as detailed in the post.

---

### Post by Xyus on 2006-08-24
my card isn't supported and out of misery I've gone back to UTP!

I recommend the same. (xyus = quiter)

xyus

---

### Post by Viral on 2006-08-25
Thanks! My wireless connection doesn't have a key, so I'm good there.

Second, I installed Automatix onto LInux (took a LONG time) and I finally got it to tell me that the Network Manager was insatlled. However, it did not appear anywhere in my System>Administation menu.

Any help?

---

### Post by Viral on 2006-08-25
Hello Ubuntu Communtiy!

Thanks for your help so far.

I've got the Windows Drivers installed under System > Administration, and I installed the driver as directed in nickpaten's guide. It works perfectly, flawlessley in Windows XP! However, When I "add" it to Linux, it says:

Hardware Present: No

Which doesn't make any sense because obviously it IS present, and Windows can read it fine.

Can someone give me a suggestion?

---

### Post by nickpaton on 2006-08-26
Have a look at this thread Viral:

[http://www.ubuntuforums.org/showthread.php?t=185174]("http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom")

which is a HOWTO on Broadcom 43xx chipsets.

Especially the first part which helps identify the actual Broadcom chipset you have.

Please could you post the output of 

```
lspci | grep Broadcom\ Corporation 
```

which checks that Ubuntu can see the Broadcom chip and identifies its model, and we can take it from there.

I'm no expert on this, so any further help from anyone else would be appreciated!

---

### Post by Paul133 on 2006-08-26
Actually, I didn't use that tutorial. I found this one ( [http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902) ). It conflicts with the other tutorial, but I got ndiswrapper and the network manager working for me. It's just very important to know your chipset. Like I said, mine is a Broadcom 4306. Yours might be different. You can check with ```
 iwconfig 
``` or go into device manager under adminisntration under system. Then tell us what chipset your card is and we'll find you the right tutorial!

---

### Post by nickpaton on 2006-08-26
Thanks for that Paul - totally agree with your suggestion - ignore mine!

---

### Post by Viral on 2006-08-26
Thanks for your help!

I checked out that tutorial that nickm wrote, and it did not work for my computer.

I followed your directions, Paul, and my chipset is "4318".

Thanks for helping!!!

---

### Post by nickpaton on 2006-08-26
@ Paul: is this the best HOWTO? - looks recent and popular:

[http://http://www.ubuntuforums.org/showthread.php?t=197102]("http://http://www.ubuntuforums.org/showthread.php?t=197102")

@Viral: The one I recommended previously is NOT recommended for your Chipset - apologies for the error.

---

### Post by Viral on 2006-08-26
Thank You nickpaton....

IT FINALLY WORKS!

I'm so glad, you guys are awesome. I can't believe the kind of community you have here at Ubuntu Forums, where people actually want to help other members. Now that I have my internet working, I can FINALLY do some other things, like download skins and applications.

Thanks once again!

ONE more question: For some reason, (for Ethernet and Wireless) I can't access some websites, nor go on my IM client (GAIM.). I don't know what's the matter, but this works PERFECTLY on Windows XP with my card. Yesterday I went to a hotel, and plugged in their ethernet internet, and it worked perfect.

I can't go on:
Google
Ubuntu Forums
eBay
Skype

but other websites I can go on:
dreamhost.com
imageshack.us


I checked my DSL Settings (192.168.0.1) and everything looks fine, it doesn't block any websites, nor disables any services.

Any Suggestions?

---

### Post by nickpaton on 2006-08-27
Hey Viral fantastic news & well done!

May I suggest regardless of the problem that you install Psychocats repositories:

[http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")

This will give you the multiverse and universe repos.

Then do an update and install.

This will ensure you continue to have the latest version of Firefox. 

Secondly try this:

Open Firefox.

Type "about:config" no (" ") in the address box.

Find the entry network.dns.ipv6disable and double click to set it to "true".

(Thanks to Furious Lettuce for this).

If that doesn't work, within the DNS settings try setting your router to get your Internet IP Address dynamically from your ISP (or equivalent wording within your router settings).

---

### Post by Viral on 2006-08-27
Thank you so much! I'm finally posting this from Ubuntu!!

Yay!

:)

Now I can browse flawlessly, but what about GAIM and my Email? They still don't work :(

---

### Post by nickpaton on 2006-08-28
> **Viral said:**
> Thank you so much! I'm finally posting this from Ubuntu!!

Yay!

:)

Now I can browse flawlessly, but what about GAIM and my Email? They still don't work :(

Glad you're up and working!\\:D/ 

What's happening when you try to get your emails?

What browser are you using?

Further details please!!

Don't know or use GAIM - anyone else help??

---

