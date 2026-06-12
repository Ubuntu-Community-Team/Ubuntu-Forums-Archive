---
title: "PCI dialup modem"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by dr_dirk on 2007-05-22
I have a US Robotics 0637 modem that I took from an old computer and tried to install.  After doing some research it seems that there aren't any linux drivers available for it.  If somebody knows differently, please let me know.

However, because they are inexpensive I don't see why I shouldn't just buy a new modem that is known to work with linux.  What modem do you recommend I look into?  That is, is there (I know there is) a decent modem that will work under Ubuntu and XP?  Thanks for your input.

Derek

---

### Post by dstew on 2007-05-22
Have you looked at this [HowTo]("https://help.ubuntu.com/community/DialupModemHowto")? Modems are not trivial to set up in Ubuntu, but that page can help you a lot. If you follow the directions carefully, you should be able to get that modem to work in Linux. I do know that modems with Conexant and PCTel chips will work with Linux. I think I have a Conexant modem in my computer at home, I can let you know once I get there.

EDIT: It looks like 3Com softmodems such as yours might be a problem. But, check with Scanmodem anyway.

---

### Post by dr_dirk on 2007-05-22
I did check with scanModem and it was not helpful.   Here is the contents of ModemData.txt from scanModem.

--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 7.04 
Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007
 scanModem update of:  2007_May_11


ALSAversion 1.0.13
USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 05:02.0	12b9:1006	12b9:005d	Communication controller: 3Com Corp, Modem Division WinModem

 Modem interrupt assignment and sharing: 

 --- Bootup diagnositcs for card in PCI slot 05:02.0 ----

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:284b	1043:81ec	Audio device: Intel Corporation 82801H 

 Modem interrupt assignment and sharing: 
 21:       2219          0   IO-APIC-fasteoi   HDA Intel

 --- Bootup diagnositcs for card in PCI slot 00:1b.0 ----
[   14.983984] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   14.983998] PCI: Setting latency timer of device 0000:00:1b.0 to 64

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 and a NEW HDA softmodem controller.


My understanding is that scanModem should give information about where to download drivers.  This was the experience of a friend of mine who has done this before.  Does this help?  Thanks.


(Let me know if you need to see scanout.00:1b.0  or scanout.05:02.0 instead of ModemData.txt)

---

### Post by phidia on 2007-05-22
You can also look at [www.linmodems.org](www.linmodems.org)
IMO external modems are the easiest to set up. Try looking on ebay since more people are going with broadband you should find one cheap there. US Robotics or Multitech are excellant brands.

---

### Post by Terl on 2007-05-22
> **phidia said:**
> You can also look at [www.linmodems.org](www.linmodems.org)
IMO external modems are the easiest to set up. Try looking on ebay since more people are going with broadband you should find one cheap there. US Robotics or Multitech are excellant brands.

And that's the truth!  I have a perfectly fine serial external modem in the box in a cabinet after my switch to broadband.  I had an old winmodem when I first tried Linux so I bought the serial modem.  If all else fails and you are in US pm me and I will mail to you gratis.  I have no need of it and hate to see it sit.

---

### Post by dr_dirk on 2007-05-22
I appreciate that, Terl.  Unfortunately right now I'm in a remote enough area that the only broadband available is via satellite.  I'm accustomed to cable and this 5k downloading is driving me buggy.

I'll see what I can get done with this modem, but I may take you up on your offer.

---

### Post by Terl on 2007-05-22
Sorry, maybe I misunderstood.  I thought you needed a dial-up style modem.  That is what I have.... a 56K v90 serial modem.  It works with Linux or win 95/98 no xp.  I got Roadrunner soon after I bought it so I just put it back in its box.

I hope you get it sorted out.  I hated the slow speeds too.  My wife **really** hated them :)

---

### Post by dr_dirk on 2007-05-22
You are correct, I do need a dial-up modem that works with Linux.  With the research I have done, the 3com modem that I'm trying to use appears to be incompatible with Linux, but I don't know that for absolute sure.  If I find that I cannot, in fact, get this modem to work, another would be wonderful.  Thanks :)

---

### Post by dstew on 2007-05-23
Just to complete the loop, it looks like you are out of luck with that modem. If the Scanmodem people had a solution, it would have appeared in the ModemData.txt file. I think you are out of options. You can try strange things if you want, like using ndiswrapper and a Windows driver. From the [ndiswrapper site]("http://ndiswrapper.sourceforge.net/joomla/"): "Although ndiswrapper is intended for wireless network cards, other devices are known to work: e.g., ethernet cards, USB to serial port device, home phone network device etc." It would just be a crazy experiment for fun, but if you got it to work you would be famous.

---

### Post by _duncan_ on 2007-05-23
> However, because they are inexpensive I don't see why I shouldn't just buy a new modem that is known to work with linux. What modem do you recommend I look into? That is, is there (I know there is) a decent modem that will work under Ubuntu and XP? Thanks for your input.


If you are the type that's comfortable with compiling modem drivers to get dial-up connection, getting a linux-supported winmodem is the cheapest alternative. You can get one for 5-10 US$. There are plenty to choose from. I have a lot of success working with modems with smartlink chipsets.

Conexant based PCI modems used to work well with Ubuntu up to Dapper 6.06, but they seem problematic with recent Ubuntu releases (Edgy 6.10 and Feisty 7.04). From what I heard, no one is maintaining the open-source driver, so users will have to pay 20 US$ annually to linuxant for its proprietary driver.

External hardware modems are easier to use with linux, especially those that plug into the serial port of the computer. Most will work even without a driver. So all you have to do is to configure a dialer program to connect to the internet. The usual range is around 40-80 US$ brand new.

---

