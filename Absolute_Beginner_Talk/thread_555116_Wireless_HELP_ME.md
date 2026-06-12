---
title: "Wireless HELP ME"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by madmatrixz3000 on 2007-09-19
Ok i am a nub so I have a Netgear WG511 v2 Wireless card and cannot seem to even get the power light to come on when I put it in.

Please give me some step by step

---

### Post by madmatrixz3000 on 2007-09-19
Please someone help me set up my wireless card[-o<

---

### Post by madmatrixz3000 on 2007-09-19
please help I have no idea where to even start to get this to work.  Right now I have to wait for the hard line to be open to get downloads and such and the modem is in a very bad area of my house

---

### Post by sstusick on 2007-09-19
You could try searching the forums for similiar issues/questions that have already been asked and resolved. Google is a good source, too.

---

### Post by Maestro23 on 2007-09-19
You running Feisty? Good place to start: [https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless)

---

### Post by madmatrixz3000 on 2007-09-19
Netgear 
 WG511 
 Prism 
 ? 
 Yes 
 Yes 
 Yes 
 v1 Taiwan works out of the box with Hoary, Breezy. and Edgy. Also works with Feisty 
 2007-05-09 
 PCM
 
On fiesty

---

### Post by madmatrixz3000 on 2007-09-19
I just went into my network settings and cannot find any way of getting wireless working, I can't even get power to the card

---

### Post by sstusick on 2007-09-19
Try the instructions contained [here]("http://ubuntuforums.org/showthread.php?t=76804&highlight=Netgear+WG511+v2"). 

If that doesn't work, try [this]("http://ubuntuforums.org/showthread.php?t=51993&highlight=Netgear+WG511+v2").

And here's [another one]("http://ubuntuforums.org/showthread.php?t=414207&highlight=Netgear+WG511+v2") for good measure.

---

### Post by madmatrixz3000 on 2007-09-19
i've gone through the [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check) guide and I could not find my card at all

---

### Post by Maestro23 on 2007-09-19
> **madmatrixz3000 said:**
> i've gone through the [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check) guide and I could not find my card at all

Use one of the links provided above.  Contains all the steps.  Good luck.

---

### Post by madmatrixz3000 on 2007-09-19
I'll have to try it later both my computer and I are getting tired

---

### Post by sstusick on 2007-09-19
You try this? >     *

      Some devices are not recognized by the OS upon insertion. [Needs expansion.]
         1.

            If card doesn't show up immediately try these steps:

    *

      Run the following command. Hopefully you'll get some output about the device.

        sudo pccardctl ident
        



---

### Post by madmatrixz3000 on 2007-09-19
socket 0 and 1 : "no product available"

---

### Post by sstusick on 2007-09-19
Try rebooting the PC with the card inserted.

---

### Post by madmatrixz3000 on 2007-09-19
I did

---

### Post by Maestro23 on 2007-09-19
> **madmatrixz3000 said:**
> I did

Best bet.  Get you some sleep and tackle it later using one of the guides posted above.  You're tired and that is going to lead to mistakes and frustration.:guitar:

---

### Post by madmatrixz3000 on 2007-09-19
best left till friday

---

### Post by lisati on 2007-09-19
Yet another link: [http://kbserver.netgear.com/products/wg511.asp](http://kbserver.netgear.com/products/wg511.asp)

---

### Post by madmatrixz3000 on 2007-09-28
OK i found the firmware and such on the page [http://kbserver.netgear.com/products/WG511v2.asp](http://kbserver.netgear.com/products/WG511v2.asp) now what?

---

### Post by madmatrixz3000 on 2007-09-28
Can anyone help on my wireless

---

### Post by masingerz on 2007-09-28
for wireless, get windows driver and use ubuntu ndiswrapper, use this link:

[http://ubuntuforums.org/showthread.php?t=25683&highlight=HOW+TO%3A+Configure+wireless+cards+with+Broadcom+chipsets](http://ubuntuforums.org/showthread.php?t=25683&highlight=HOW+TO%3A+Configure+wireless+cards+with+Broadcom+chipsets)

---

### Post by madmatrixz3000 on 2007-09-28
I am completely lost

Someone send me a link to the direct download for the thing to make it so all I have to do is find the windows driver

---

### Post by Skidpad on 2007-09-28
> **madmatrixz3000 said:**
> I am completely lost

Someone send me a link to the direct download for the thing to make it so all I have to do is find the windows driver
I'm not trying to ruin the party here, but your other alternative is to just purchase a wireless card that offers better support, or perhaps, out-of-the-box support without having to use ndiswrapper.  I originally had a Broadcom 4309 card that I decided wasn't worth my time.  $30 later, I had a card that did work. (A Ralink RT2500-chipset based card).  

Check out this list: [Here]("http://linux-wless.passys.nl/query_alles.php?")

---

### Post by madmatrixz3000 on 2007-09-28
where can I find a ndiswrapper .deb file.  I'm begging for a link

---

### Post by Skidpad on 2007-09-29
> **madmatrixz3000 said:**
> where can I find a ndiswrapper .deb file.  I'm begging for a link

[Here...]("http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/")

While you're at it, please read this:[Here]("http://ubuntuforums.org/showthread.php?t=142716").

---

