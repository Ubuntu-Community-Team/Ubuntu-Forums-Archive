---
title: "Can Ubuntu 7.04 use a cellular phone as a modem?"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-05-24
Cellular phone is the only high-speed connection I have access to in the rural and forested area I live. Cable modem, DSL, and satellite are not available. But Cellular Phones have come out with good high-speed modem connections in the past 6 months. In the U.S., Verizon and AT&T have excellent download speeds of 500-700 Kb/sec. But they say their software is only for Windows and Mac. What about Ubuntu???? If I can't get on-line using a cellular phone, I'm going to have to buy a Windows machine instead of using Ubuntu. --Which I do not want to do.

---

### Post by blazercist on 2007-05-24
Yes, In fact I have setup my laptop with my Verizon XV6700-PPC.  It depends entirely on the phone, usually only PDA phones have that ability, phones with Windows Mobile 5 and alike are the easiest to configure.  There are many many guides on google for doing this.  search for USB dongle and stuff like that.

---

### Post by swarup on 2007-05-24
> **blazercist said:**
> Yes, In fact I have setup my laptop with my Verizon XV6700-PPC.  It depends entirely on the phone, usually only PDA phones have that ability, phones with Windows Mobile 5 and alike are the easiest to configure.  There are many many guides on google for doing this.  search for USB dongle and stuff like that.

That's great news. Does it need any special software? Because I checked with Verizon myself, and the phones they quoted to me as being capable of being used as a modem (the Motorola Razor and LG8300), according to him were only set up for use with Windows and Mac.

---

### Post by blazercist on 2007-05-24
Well my phone the 6700 comes with WM5, and it has a special app called winmodem, I'm not sure about the Razr and the LG as they aren't Window Mobile phones... 

By the way I dont think you can get the unlimited data plan on those phones anyway so It would get very expensive and I don't think they are EVDO rev A so they wouldnt be too fast either.  

thats one guide i dunno if it works...

[http://www.shawnhogan.com/2004/12/motorola-razr-v3-bluetooth-powerbook.html](http://www.shawnhogan.com/2004/12/motorola-razr-v3-bluetooth-powerbook.html)

you could also PM Jason_25 

>  Re: EVDO Cell Phone as Modem 

--------------------------------------------------------------------------------

I use my Motorola Razr with EVDO almost constantly. It works perfect using wvdial.

---

### Post by adam.skinner on 2007-05-24
[http://www.summet.com/blog/2007/01/27/using-bluetooth-pan-dun-on-samsung-blackjack-with-linux/](http://www.summet.com/blog/2007/01/27/using-bluetooth-pan-dun-on-samsung-blackjack-with-linux/)

[http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=TGu&q=linux+PAN+bluetooth&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=TGu&q=linux+PAN+bluetooth&btnG=Search)

---

### Post by swarup on 2007-05-24
> **blazercist said:**
> Well my phone the 6700 comes with WM5, and it has a special app called winmodem, I'm not sure about the Razr and the LG as they aren't Window Mobile phones... 

By the way I dont think you can get the unlimited data plan on those phones anyway so It would get very expensive and I don't think they are EVDO rev A so they wouldnt be too fast either.  

thats one guide i dunno if it works...

[http://www.shawnhogan.com/2004/12/motorola-razr-v3-bluetooth-powerbook.html](http://www.shawnhogan.com/2004/12/motorola-razr-v3-bluetooth-powerbook.html)

you could also PM Jason_25

Actually, those phones (the Razor and the LG8300) do come with the unlimited data plan, and they do work with Revision A. The only question in my mind is whether they would work with Ubuntu since they don't have the WM5 as you say. I don't know what phones come with the winmodem app. But it's very good news that the whole thing is possible. I'll just have to check further which phone will work with Ubuntu. Because I don't want to spend the money on a PDA. The Razor and LG8300 are only $50 after rebate. But will they work with Ubuntu??? That's the question.

---

### Post by blazercist on 2007-05-24
adam.skinner the first like you gave invariably freezes my browser.

And yes it will work as a modem just cant find a guide right now cuz im at work.

---

### Post by blazercist on 2007-05-24
Ok I found one specifically for the RazrV3

[http://ubuntuforums.org/showthread.php?t=343989&highlight=evdo+motorola](http://ubuntuforums.org/showthread.php?t=343989&highlight=evdo+motorola)

Enjoy.

---

### Post by swarup on 2007-05-24
Another question is whether an "aircard" will work. These are the PCMCIA cards that are like a cellular phone without the phone part. They are just the cellular modem. And monthly rates are cheaper than phone + modem. You can have unlimited data use for $80/month. Does anyone know if aircards can be used with Ubuntu?

---

### Post by swarup on 2007-05-24
That's great news about the RazrV3. Thanks for the tip. At least I know I can go with that one...which is really good news. 

Do you have any experience or have you heard of using Ubuntu with aircards?

---

### Post by blazercist on 2007-05-24
they are just pcmcia cards that are cellular, all the big cell companies have them, I would assume they also work but I have no idea how as i have never used one in either windows or linux and never read about them being used. Whats the dif anyway, everyone needs a cell phone lol, unless you are planning on talking on your cell and surfing the web on your comp at the same time then i think the cellphone/modem route is best, at least for me.

---

### Post by swarup on 2007-05-24
> **blazercist said:**
> they are just pcmcia cards that are cellular, all the big cell companies have them, I would assume they also work but I have no idea how as i have never used one in either windows or linux and never read about them being used. Whats the dif anyway, everyone needs a cell phone lol, unless you are planning on talking on your cell and surfing the web on your comp at the same time then i think the cellphone/modem route is best, at least for me.

Using the aircard, I can make all my phone calls virtually free on the web using Skype. It costs $2.50 per month for unlimited domestic calls. At $80/mo, the aircard with free Skype calls is a better deal than the cellular phone/modem at $100/month.

---

### Post by kevdog on 2007-05-24
Not that I do it regularly but Ive periodically used my Nokia 6600 phone -- has IR port, as a regular dialup modem for years.  If you have a laptop with an IRDA port - you can set this up as a serial device and then use any phone with an IR port as a modem.  I dont see why it wouldnt work with more modern phones.

---

### Post by blazercist on 2007-05-24
> **swarup said:**
> Using the aircard, I can make all my phone calls virtually free on the web using Skype. It costs $2.50 per month for unlimited domestic calls. At $80/mo, the aircard with free Skype calls is a better deal than the cellular phone/modem at $100/month.

Yea but you cant fit your laptop in your pocket can you?

---

### Post by Mach1US on 2007-06-14
If you are interested in in connecting phone as a modem i have to say it is relatively easy with motorola v3 , all you need is mini-to-regular-USB cable like one for your digital camera and use this guide which serves for USB connection capable phones as well for PCMCI cards: 
[http://ubuntuforums.org/showthread.php?t=343989&highlight=motorola+evdo](http://ubuntuforums.org/showthread.php?t=343989&highlight=motorola+evdo)
If you have us continental calling included in your plan you can sign up for totally free internet acces via dialup on this website.
I have an account just for emergencies set up  with my motorola v3 , othervise i use EVDO PCMCI card.
[www.metconnect.com](www.metconnect.com)
And as far as making local calls with skype i remember few times when i left my cell phone at home and this is what i used to save my bacon , beats searching for quarters or public phone especially if you are in the middle of nowhere.;)

---

