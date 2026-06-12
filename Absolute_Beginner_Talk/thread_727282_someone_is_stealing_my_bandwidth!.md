---
title: "someone is stealing my bandwidth!"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by princeofchildren on 2008-03-17
hello, I have a dlink di-524 wireless router and I am picking up the signal with a linksys wireless-g wusb54g v.4 usb network adaptor. we have discover that someone is picking up our signal, we tried to put a password on the network using WEP(hex) with a 6 number pass, this did not work.
I tried WPA1 and WPA2(psk), non of this worked, I could not log in from this computer. I called dlink, they were worthless. if someone could tell me what I'm doing wrong that would be awesome, thanks.

-D

---

### Post by Nythain on 2008-03-17
dude, screw encryption... MAC filter that badboy... less work (no encrypting and decrypting) and everyone and thier mother snoops for encrypted passwords, not to many think of getting your MAC addy and spoofing it...

Basically there should be a section in Wireless or Security to enable MAC Filtering, wich will keep out any wireless device that doesnt have a mac address in the list... just get your mac address, add it to the list... turn off encryption, and unless the person is smart, your good to go

---

### Post by upbeat.linux on 2008-03-17
Make sure you read the configuration manual before putting your router into production.

Also, the first thing that you should do before configuring your wireless device is to change the default password and disabled access to the web interface from wireless devices.

So, check out the manual on the DLink web site and read it thoroughly.  

Reset your router to factory defaults, log into the web interface, go to Admin | Tools and change the password for the administrator and the user.  Make sure they are different passwords. Apply/Save changes.

Next select Wireless. Change the SSID to something creative. Select Disabled for SSID Broadcast. For Security select WPA2/PSK and enter a passphrase. Apply/Save changes

In DHCP change the starting address to 10 and the ending address to 13 (say, if you have 4 different boxes connecting).  

That's the gist of it, but please read the manual.

Also, keep in mind that support for your product has been discontinued through DLink.

---

### Post by Nythain on 2008-03-17
yeah, you should totally ignore my post and follow those directions... you will end up with a much more secure router... (thats not sarcasm either... that was a well written  example/guide to securing stuff... kudo's mate)

---

### Post by LifeSign on 2008-03-17
Hah, I came here to help, but ended up getting some tips myself!

---

### Post by upbeat.linux on 2008-03-17
> **Nythain said:**
> yeah, you should totally ignore my post and follow those directions... you will end up with a much more secure router... (thats not sarcasm either... that was a well written  example/guide to securing stuff... kudo's mate)

sorry mate. i had a reply tab open for about 20 minutes before i even got around to writing a response. didn't check to see if any followups were posted, 

your mac filtering is something this user should definitely consider

---

### Post by Pijits_1 on 2008-03-17
Try not to use PSK encryption, i know of a Linux distro that can actually crack it. When doing a password use numbers and letters. Its harder to crack.

---

### Post by Mithrilhall on 2008-03-18
If your device supports passphrases use that instead of a password.

---

### Post by bukwirm on 2008-03-18
Or you could do [this]("http://www.ex-parrot.com/~pete/upside-down-ternet.html"). (Upside-Down-Ternet)

---

### Post by redcrayon on 2008-03-18
HAHA i came here to help too and also got some tips :) cheers!

---

