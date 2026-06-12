---
title: "Setting up a secure wireless network"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by kcparker on 2007-08-22
I have just plugged in my belkin router and have an unsecured wireless network now which other machines can access fine. I do not know how to set up the security on the wired PC which is running feisty fawn.

Can anyone help - my knowledge is very very basic. Thanks

---

### Post by coxy on 2007-08-22
Ok then; first of all you need to connect to your router using it's IP address. This may be in the manual or printed on the router label somewhere. It may be [http://192.168.2.1](http://192.168.2.1) but that is just from a quick Google search.

Once you connect, enter the default admin username and password which should also be in the manual. Once logged in you need to change the default password to something different that you won't forget. Make it something that is not easily guessed. You then need to find your wireless security settings and enable some encryption.

The encryption you use should be WPA. WEP encryption is floored and can be cracked within minutes. You also need to check that the wireless cards on your machines are able to use WPA (they should do). If you go to a site like [http://www.speedguide.net/wlan_key.php](http://www.speedguide.net/wlan_key.php) and generate a HEX key you can use this for your encryption key. Make sure you keep a copy of it in a text file; if you have a USB key it is ideal because it will allow you to connect your wireless machines with the new encryption key without having to type it out (use copy and paste).

That should give you a secured wireless connection.

---

### Post by kcparker on 2007-08-22
Thank you so much - that has done the job perfectly.

Thank you for taking the time to reply!

---

### Post by dca on 2007-08-22
Not to mention, most newer routers have MAC address filters that can be applied for extra security...

---

### Post by stchman on 2007-08-22
> **kcparker said:**
> I have just plugged in my belkin router and have an unsecured wireless network now which other machines can access fine. I do not know how to set up the security on the wired PC which is running feisty fawn.

Can anyone help - my knowledge is very very basic. Thanks

Setting up wireless security is not a Feisty thing.  Your router is responsible for security.  I would select WPA minimum and WPA2 if your card supports it.

WHen you are done with the router select your SSID and it should ask you to input the passphrase.

---

### Post by ruggrat on 2007-09-18
Hi, I'm pretty new, so bear with me- 

I have a Belkin wireless router at home (Belkin is crap btw, don't buy it), which was working okay with their default WPA settings.  Once I installed Feisty on my laptop (main computer for the house), the wired worked for a little while, but no wireless.  I used ndiswrapper for my bmc4306 built-in wireless card, and *everything* stopped working.  No wired, no wireless, no connection on my slow as molasses powerbook.

I reset the router (with the button in the back), and it works pretty well now, except that when I try to change the SSID or security key, the router poops out until I give it a hard reset.  So basically I have no security and no way of getting it.  

The configuration disk that came with the router has no linux support of course, and won't even work on the powerbook (even though it claims to be "PC/Mac" software).

I guess my question is, Is there anything I can do from the software end to configure the router so I can put a password on it, or should I just toss it in favor of linksys?

I understand that this is mostly a hardware issue, but it was never a problem til Feisty, so I'm suspicious.

Thanks a lot!

---

