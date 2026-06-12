---
title: "Can i connect to hidden SSID?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by wcgoh on 2007-10-25
Hi,

Using Ubuntu 7.10, Wireless card is D-Link DWL-G520+. Can i connect to a hidden SSID network?
Thank you for the help.

---

### Post by gsiliceo on 2007-10-25
Yes, you need to know the SSID, there is software to "spot" for SSID nearby. I forgot the name thou sorry

---

### Post by jon zendatta on 2007-10-25
yeah unsure quite what you mean! but try out 'netstumbler' :KS

---

### Post by The Tronyx on 2007-10-25
I believe you might be looking for a program called Kismet.  It does quite a bit more than SSIDs but it should bring them up.

---

### Post by wcgoh on 2007-10-26
I found the SSID, try to connect to it but it failed. Is it due to the driver fault? It worked well under Winxp though (same system - dual boot)

---

### Post by Joeb454 on 2007-10-26
Why would you need to have the SSID hidden anyway?

---

### Post by BrendanM on 2007-10-26
You should check out WICD: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

It's a really nice network manager application for Ubuntu, and it has options for hidden SSIDs.

---

### Post by Trebaruna on 2007-10-26
As an aside: hiding your SSID does not actually make things more secure. As you can see, there are plenty of programs available to retrieve an SSID even if it's not being broadcast. For security, make sure you are using WPA.

I seem to recall that I also had an Ubuntu system trying to connect to a hidden SSID. It din't like it very much. Just enabled SSID broadcast and all was well.

---

### Post by mandrill on 2007-10-26
As Trebaruna mentioned, the only really important part of wireless security anymore is wpa, the rest is just false security.....literally. that and maybe a strong password on your NAT/router.with an innocuous network name

---

### Post by jtekUSA on 2007-10-26
> **Trebaruna said:**
> As an aside: hiding your SSID does not actually make things more secure. As you can see, there are plenty of programs available to retrieve an SSID even if it's not being broadcast. For security, make sure you are using WPA.

I seem to recall that I also had an Ubuntu system trying to connect to a hidden SSID. It din't like it very much. Just enabled SSID broadcast and all was well.

I also purposely disabled the SSID broadcast in my routers wireless settings as I was believed it prevented others from finding my internet connection.  After reading your and others post on this matter, I have re-enabled it as I, too, have found my wireless connection works great in Ubuntu as long as it is broadcasting.

I am currently using WPA-PSK security with a 63 letter passphrase.  I found a web site that helps create passphrases based on the diceware theory.  Here is the site for those interested:  [http://world.std.com/~reinhold/diceware.html]("http://world.std.com/~reinhold/diceware.html").  It takes some time (reading)  but is worth the effort.

Thanks again for the enlightenment as this was my main source of frustration with Ubuntu since upgrading to Gusty Gibbon.  Ever since then, I can't use my docking port screen (worked fine under Feisty Dawn).  Stupid me, I did not save a backup of my xorg.conf file so I could see how the second monitor was setup.  Still working on this and off topic for this post.

---

### Post by wcgoh on 2007-10-28
:) Haa, I didn't choose to hide the SSID. It is the working of my office's system admin.
They have a hidden SSID but no encryption wireless running inside the office premises, so i had been trying to connect to it.
I am giving up on the Dlink G520+, cause i tried to use Ndiswrapper, using the winxp driver that came along in the CD, but it told me that the hardware is not correct :confused:

Going to try a USB wireless, hope it is of less trouble than the Dlink.

---

### Post by speedwell68 on 2007-10-28
If I connect to my Netgear router using only WEP encryption, a hidden SSID works a fine.  But it will only connect to the router when WPA is used if the SSID is broadcasted.  It is the same if I use nm-applet or Wicd.  Does anyone know why this is?

---

### Post by Animal Mother on 2008-01-15
> **BrendanM said:**
> You should check out WICD: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

It's a really nice network manager application for Ubuntu, and it has options for hidden SSIDs.

Just what the doctor ordered! thanks fella!

---

