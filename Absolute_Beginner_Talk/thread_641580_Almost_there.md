---
title: "Almost there"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by CasPol on 2007-12-15
Hi there;

Thanks to a lot of help form you guys I have now managed to successfully install the driver for my broadcom wireless card in ubuntu 7.10.

Sadly I still cannot connect to the wireless network. The network:confused::confused::confused: settings have all the correct information for the Essid, dhcp, and Wap key. Where is it going wrong ?

---

### Post by mmichalik on 2007-12-15
I had this problem too, yesterday, until I realized that even though the restricted drivers panel said I had a Broadcom BCM43xx card, I actually had a Broadcom BCM94311MCG card and it required a different work around to get it going

The thing that tripped me up was that my wireless light was on, like it was working correctly under the wrong driver.  But, once I had the right driver installed, it worked like a dream.

I'm sure everyone had to check out what card you had but, what was the output to the lspci command?

---

### Post by CasPol on 2007-12-15
It comes back with :

Broadcom Cooperation BCM 4318 (Airforce One 54g) 802.11g wireless lan controller (rev02)

---

### Post by mmichalik on 2007-12-15
Have you seen this HowTo yet?

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

It appears that it works for Gusty as well.

---

### Post by CasPol on 2007-12-15
Tried it step by step ...no change at all. Does not work

---

### Post by CasPol on 2007-12-15
Success  !!

This did the trick for me ..

[http://ubuntuforums.org/showthread.php?t=210538](http://ubuntuforums.org/showthread.php?t=210538)

Thanks to all who replied to my post !!

---

### Post by CasPol on 2007-12-15
Or so I thought ....

After restarting the computer it is now NOT working ....

what have I forgotten ?

---

### Post by mmichalik on 2007-12-16
If I could suggest one more thing.

follow this howto:

[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

but use the new broadcom driver that you downloaded in the other post.

This how to downloads the latest ndiswrapper and that may help out.

It's just a stab in the dark but, it may help out

P.S. I should add that I used that howto to setup my Broadcom BCM94311MCG card in my Compaq Presario C700 on Friday.

---

### Post by CasPol on 2007-12-16
Thank you for the advice. I did indeed install Wicp and bingo !!! It immediatly detected all wireless networks around me ...... but not my own !!!!!!!!!!!!!

I have a Netgear Rangemax dg834pn modem/router. WPA-psk access control st to off, and wirelesting on. Wcip does NOT detect it.

I hav already reset, rebooted, and all of that with the rooter .... no difference.

I must say, I am now really at a loss with this. I would soooo much like to use Linux, but there is no point if it will not let me have wireless.....


I really could do with some last advise here...... would rather not go back to windoze ....

---

### Post by mmichalik on 2007-12-16
well, if it's seeing things around you then, the wireless is working.  So 90% of the problem is solved.

Did you check to see if the ssid on your router is being broadcast?  I know that ours has the ability to turn it off so other wireless users can't see it and try to use our internet connection.

If that's broadcasting, I would change it to something unique, so you know which one is yours as opposed to someone else using a default name identical to what yours was.

also, I would install the KWifiManager from the repository.  It's a very useful tool.

Let me know how it goes.  I wouldn't want you to go back to windoze either.

---

### Post by CasPol on 2007-12-18
It DID detect everything around but not any more.....

I also noticed that NDISWRAPPER and NTFSG as well as network admin and network manager, are no longer available to me ..... ???

Does Wicd depend on any of these, and if so which ones should I get , and from where ?

Many thanks.

---

