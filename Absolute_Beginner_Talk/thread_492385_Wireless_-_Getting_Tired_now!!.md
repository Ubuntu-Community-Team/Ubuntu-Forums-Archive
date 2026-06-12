---
title: "Wireless - Getting Tired now!!"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by raven3k on 2007-07-04
hi, i am trying to install or trying to get my wireless working.

Every time, i click on the wireless it keeps asking for the passphrase but it doesnt try to connect.
My wireless key is WEP 128.

Some info about my hardware:
Realtek RT73 Usb
Ubuntu 7.04

Also, this is probably first time as i am trying to move away from windoze.

I tried to install the RT73 Alternate driver but i got lost in the commands. Please help me get the wireless working.

---

### Post by lintoon on 2007-07-04
Is it not just a matter of typing in the WEP passphrase which is set on your wireless router.

---

### Post by ubuntu.daemon on 2007-07-04
[http://ubuntuforums.org/showthread.php?t=370108]("http://ubuntuforums.org/showthread.php?t=370108")

other than than there are some other helpful stickies in the wireless forums, and btw i wouldnt use wep anymore bc it isnt really safe considering it can be broken now in like 10-20 min i think?

GL:popcorn:

---

### Post by bradmayne on 2007-07-04
ok so lets see here 

1.  WEP can not be broken in 10-20 minutes even with heavy network traffic!

2.  For the average home user WEP is fine!

3.  What kind of chipset do you have?  Are you using edgy eft, feisty fawn, dapper, etc? 

give me some specifics and I can probably help you.  P.S. do you know what kind of wireless chipset you have hermes, atheros, prism, etc? is the card internal or external?

---

### Post by raven3k on 2007-07-04
> **bradmayne said:**
> ok so lets see here 

1.  WEP can not be broken in 10-20 minutes even with heavy network traffic!

2.  For the average home user WEP is fine!

3.  What kind of chipset do you have?  Are you using edgy eft, feisty fawn, dapper, etc? 

give me some specifics and I can probably help you.  P.S. do you know what kind of wireless chipset you have hermes, atheros, prism, etc? is the card internal or external?

I am using Feisty, the chipset is made by realtek and it is RT73 USB and its internal since its part of the mobo.

---

### Post by ugm6hr on 2007-07-04
> **raven3k said:**
> I am using Feisty, the chipset is made by realtek and it is RT73 USB and its internal since its part of the mobo.
Is it possible for it to be rt73 **usb** and be internal?

---

### Post by ubuntu.daemon on 2007-07-04
Um yes wep can be easily broken now days and wpa is more secure, and pretty easy to use, easier to remember the phrase/passcode you typed in then a hex key

[http://www.hackaday.com/2005/05/15/cracking-wep/]("http://www.hackaday.com/2005/05/15/cracking-wep/")
[http://willy.boerland.com/myblog/extreem_cool_howto_hack_wep_in_10_minutes]("http://willy.boerland.com/myblog/extreem_cool_howto_hack_wep_in_10_minutes")

just type in hack wep into google lol

---

### Post by bradmayne on 2007-07-06
dude- your a tool.  Yes WEP keys can be broken so can WPA.  There are some differences in the methods used to crack  wpa you would need a wordlist etc.  What I was saying is that for the average home user WEP is fine.  I highly doubt someone will sit outside your average users home to try and gather enough weak IVs! On a home network that would take quite a bit of time.  Even by sending out deauth messages to the target to force reassociation would still take more time and effort.  What I'm saying is most people trying to get free internet access or script kiddies are just gonna go for the lowest hanging fruit.

---

