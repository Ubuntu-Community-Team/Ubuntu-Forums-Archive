---
title: "Internet doesn't work under Gutsy"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by dismal_denizen on 2007-11-15
Like most of you, I was excited by the release of Gutsy Gibbon. However, the internet doesn't work at all from the Live CD ore after installation. Feisty Fawn used to work with no such problems, straight from the CD.
I am connected to my ADSL broadband  modem router via Ethernet. Help would be much appreciated, I really want to use Gutsy!

---

### Post by laidback on 2007-11-15
With Feisty my system connected to the internet with DHCP without any assistance from me even though my connection is meant to use Static IP. When I ran Gutsy I found that I was back to static IP, no real issue as you just need to configure the connection System>Admin>Network. Or click the screen icons in the system tray, left click choose manual configuration.

---

### Post by kleo skywalker on 2007-11-15
I connect to the internet the same way, and I couldn't get internet to work on the Gutsy LiveCd either (I never tried it with the Feisty LiveCD). I manually configured it after installation, set to Static IP and all the other numbers like DNS entered correctly. I also need to run > sudo pppoeconf and then reboot to get my internet to work.

---

### Post by philinux on 2007-11-15
I'm on an old wired 2wire router and it worked just the same under gutsy. did not have to touch a thing. This is a weird symptom for some. I wonder if its specific to a brand of hardware?

---

### Post by dismal_denizen on 2007-11-15
How did you do this manual configuration?

---

### Post by laidback on 2007-11-16
System>Admin>Network (password is your own)

Then choose Wired Network>Properties. 
Select Static IP from Configuration
Set your IP address, something like 192.168.1.2
Network sub_mask will probably be 255.255.255.0
Gateway: I use the address of my router/modem, 192.168.1.1

back at the front screen choose tab DNS
use the ADD and Delete buttons to set your DNS addresses as required.

back at front screen make sure you have the Wired connection box ticked.

That's it, or should be. Try it out.

If it still doesn't work check you settings again, make sure you have the addresses right, e.g. DNS and properties. Try again. I have had to check a couple of times before I get success, make sure lights on router/modem are alight to signify connected. You may also get a message from system tray to say connected to internet.

---

### Post by Milind on 2007-11-16
> **dismal_denizen said:**
> Like most of you, I was excited by the release of Gutsy Gibbon. However, the internet doesn't work at all from the Live CD ore after installation. Feisty Fawn used to work with no such problems, straight from the CD.
I am connected to my ADSL broadband  modem router via Ethernet. Help would be much appreciated, I really want to use Gutsy!

I had the same problem which I posted today and got a solution within hours . Check this thread - [http://ubuntuforums.org/showthread.php?t=614608]("http://ubuntuforums.org/showthread.php?t=614608")
Hope it works for you.

---

