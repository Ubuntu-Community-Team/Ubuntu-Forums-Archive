---
title: "Understanding 3G Internet"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by r3bol on 2008-03-29
I'm having problems understanding this 3G internet thing. There are adverts here in Finland offering 3G internet with USB modems. The info on the companies web sites is a little confusing for me and sometimes references mobile phones. Does this mean that I need a 3G enabled mobile phone with the modem on a computer or does the modem replace the need for the phone (for internet access)?
If so, then how is 3G support for Ubuntu? Are there Ubuntu forum members using this technology?

Thanks.

---

### Post by bwhite82 on 2008-03-29
I use 3g technology for my primary internet. Basically, I use my cellphone carrier (AT&T) to connect to the internet via their cellphone towers. You have two options, either "tether" your phone to your computer and use your phone as the modem. Or, like I do, purchase a USB 3g modem (which includes its own sim card) there are also PC-Card type devices as well as the newer PC-card express type cards. Ubuntu support is dependent totally on the device which you purchase. I would recommend googling before buying. Try searches such as: "tether yourPhoneModel phoneManufacturer" or "USBdeviceName ubuntu".

For reference, I use the Sierra Wireless 881U for which they provide Linux drivers complete with a howto.

-Cheers

---

### Post by mcduck on 2008-03-29
> **r3bol said:**
> I'm having problems understanding this 3G internet thing. There are adverts here in Finland offering 3G internet with USB modems. The info on the companies web sites is a little confusing for me and sometimes references mobile phones. Does this mean that I need a 3G enabled mobile phone with the modem on a computer or does the modem replace the need for the phone (for internet access)?
If so, then how is 3G support for Ubuntu? Are there Ubuntu forum members using this technology?

Thanks.

3G uses the same 3G cell phone network that the phones use, but you don't need a phone to use it, as the USB modem itself connects to the network. The modem actually contains a SIM card just like your cellphone does, so it's practically just a dumbed-down cell phone that is only usable as modem, not as stand-alone cell phone.

If you happen to have a 3G cell phone it will most likely also be able to work as modem so you could use that instead of getting a separate modem, but most operators seem to give the usb modem free anyway..

(so, the simple answer is that you do not need a cell phone, the modem connects directly to the 3G network)

The biggest problem you might have is if the USB-modem is actually supported in Linux. It's kind of hard to find out, as the operators are selling the modems with their own marketing names, with no technical data available. You'd better ask them about Linux compatibility beforehand.

---

### Post by r3bol on 2008-03-29
Thanks for great explanation. I now understand!
I don't have a 3G phone so I would need the modem. I might look into buying my own if its possible because they are quite expensive to rent. 
Maybe even the Sierra Wireless 881U :)

[B][COLOR="Red"]Edit:
How do you connect? Does it work like DHCP or is there some procedure you need to go though every time?[/COLOR][/B]

---

### Post by bwhite82 on 2008-03-29
There's a script on Sierra's website that you startup each time you connect. I wish there was some kind of graphical manager but I've yet to find one for this card in Linux. Basically the command in a terminal is:

> pppd call gsm

Then when you want to cancel your connection you just hit CTRL+C

---

