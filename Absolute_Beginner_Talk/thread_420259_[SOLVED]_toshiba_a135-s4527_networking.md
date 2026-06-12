---
title: "[SOLVED] toshiba a135-s4527 networking"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by jludeman on 2007-04-23
I recently purcased this laptop. I have Ubuntu live cd version 6.10.
The first thing I noticed is no modem access. This could probably be fixed if I had some additional files.

My question is how to network this thing to an ethernet wired hub and share files with my desktop computer.
That computer has internet access. I currently dual-boot debian and windows 2000 on that machine. 

The windows partition has a static address peer to peer network using cables and a hub. That part works fine but have never attemted a linux network.

I would eventually like to go wireless but the Atheros card does not work right now.
Can I set up a wired network that will work with the wireless when I get that working?

lspci shows the following:
Ethernet controller Realtek unknown device 8136  - wired lan?
Ethernet controller Atheros unkown device 001c  - wireless lan?
 modem not listed - probably a software modem

Windows lists the modem as a toshiba software modem using Agere drivers.

Thanks

---

### Post by jludeman on 2007-04-23
I guess from the lack of replies that I'm in the wrong spot in the forums.

Could somebody with experience with these forums point me in the right direction.

I'm in a bind for the following reasons.

1. Ubuntu does not support my laptop  modem.
2. My only access to the internet is by phone line.
3. I cannot download drivers to make my modem work because my modem does not work.
4. My wifi (Atheros) is not recognized by Ubuntu.
5.  I cannot use wifi to connect with a working computer with internet access.
6. No files - no fix -no fix no files
:confused:

---

### Post by mostholy on 2007-04-24
I have the same laptop and am posting this from there using 7.04 feisty fawn via wifi to my home network.  I'm only running under the cd boot as I have yet to fully install (and rid myself of Vista).  It took a bit of trying to get the wireless working (mostly due to lack of experience with Gnome, but some searching of the forums enlightened me).  I agree that the modem is listed as software modem and not really sure what exactly that means.  

Not sure if this really helps your situation much.  I haven't found much support for this laptop as it is still fairly new and less user base for support.  

On a side note, have you managed to get the sound working?

Cheers!

---

### Post by stchman on 2007-04-25
> **jludeman said:**
> I recently purcased this laptop. I have Ubuntu live cd version 6.10.
The first thing I noticed is no modem access. This could probably be fixed if I had some additional files.

My question is how to network this thing to an ethernet wired hub and share files with my desktop computer.
That computer has internet access. I currently dual-boot debian and windows 2000 on that machine. 

The windows partition has a static address peer to peer network using cables and a hub. That part works fine but have never attemted a linux network.

I would eventually like to go wireless but the Atheros card does not work right now.
Can I set up a wired network that will work with the wireless when I get that working?

lspci shows the following:
Ethernet controller Realtek unknown device 8136  - wired lan?
Ethernet controller Atheros unkown device 001c  - wireless lan?
 modem not listed - probably a software modem

Windows lists the modem as a toshiba software modem using Agere drivers.

Thanks

I have a Toshiba laptop as well and Ubuntu 6.10 does not support that particular Winmodem.  Frankly I have not use dialup in years so I don't ever think about it.

If you want to get your Atheros card up and running then follow my procedure:

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

It installs madwifi on Ubuntu.

Hope this helps.

---

### Post by jludeman on 2007-04-25
As to the sound yes it worked right away under 6.10. I decided to try 7.04 and it's on the way from Frozen Tech.

On the other hand you got me worried with the question about sound. If you had sound problems with 7.04 then maybe I'm going the wrong direction here.

If I get wi-fi working I can go to the beach and drink a little coffee and download what I need to get Ubuntu working on this laptop.

I really really hate Vista with a passion.8-)

---

### Post by mostholy on 2007-04-25
FWIW I am seeing alot of posts about sound working in 6.10 and then failing to function after upgrading to 7.04.  

And please minimize the beach comments, I live in a desert :>)

---

### Post by jludeman on 2007-04-27
Just to let you know that I've recieved 7.04 and the sound does not work with the live cd. The wifi card is recognized and I'll try to follow the link in a previous post to get it working. 

I'll post the results of that and any sound or modem fixes I find.

Also there's not much difference between the desert and the beach except all that water on one side.
Gotta go - surfs up!:wink: :grin:

---

### Post by mostholy on 2007-04-28
thanks for the sand perspective, made me smile.  Glad to hear at least the wifi is functional.

---

### Post by jludeman on 2007-11-07
Got this working under 7.04. Fixed a lot of problems on my home lan as well.
To see a detailed description follow the link below.
[http://ubuntuforums.org/showthread.php?t=587560](http://ubuntuforums.org/showthread.php?t=587560)

---

