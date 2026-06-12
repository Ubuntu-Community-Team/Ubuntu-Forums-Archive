---
title: "About to give in (WEP problems)"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by apotts on 2008-02-08
Armed with a 7.10 CD, I am an experienced Windows user who wants to get Ubuntu on to a laptop but am about to give in.

First attempt:

A brand new Samsung Q45 (with 4695AGN). After working out why the installation wouldn't start (acpi not supported), I just couldn't get the wireless network to work with WEP. I read loads of threads and vaguely related wiki articles, had to learn all sort of CLI stuff and summarily failed. Back to Vista on this one (which works perfectly). Also the graphics were a mess, with the resolution all messed up.

Second attempt:

A Rock Quaddro Pro (about 3 years old, P4 3.2 "Ralink 802.11g WLAN Pen Drive") - exactly the same, no WEP capability. Having discovered that when you want to setup the Network it is in fact wrong to go to System - Network (!), I click on the little network icon at the top right, it sees my ESSID and so I double click and it produces a hopeful box that asks for my WEP passphrase. I change it to HEX key, enter the key and it waits for a few minutes and comes back up with the box. I can try hex, ascii whatever and it just doesn't work.

I then went risky and tried ver 8 alpha4, but the graphics failed and I couldn't even boot. But no complaints, it is an alpha.

The wireless router is fine (it's a Vigor / Draytek which is working with Vista, XP, PSP and Squeezebox). I realise that millions of others have struggled with wireless and that the solution will involve wrappers or custom driver building, but I don't have the time and have found it easier to just revert to Windows.

Will Ubuntu ever be built in such a fashion that Windows users can come over and get something to work without having to get oily hands on the first day? Or have I missed something and the answer to getting a basic working laptop is just a few clicks away?

---

### Post by Dr Small on 2008-02-08
If WEP is a problem, why not disable it ?

---

### Post by Whiffle on 2008-02-08
Depends on the wireless card really.  Which wireless card do these two have in them?

---

### Post by apotts on 2008-02-08
If I disable WEP, which wireless security scheme can I use that is compatible with **all **the other devices on the network (listed above) and is reasonably secure?

Whiffle, the cards are listed just after the laptop descriptions in the first post.

---

### Post by Dr Small on 2008-02-08
I never had any sucess with WEP keys on Ubuntu, so I just disabled it altogether, but then again, I live out in the middle of nowhere.

That may not be your case, and that may not be an option.

---

### Post by apotts on 2008-02-08
No, indeed it's not an option here. The thought of opening my network to the world or having to control it by MAC address is just too complicated compared to Windows. I possibly got the impression that Ubuntu was more mature than it is. Surely secure wireless networking is one of the basic essentials of a modern OS?

---

### Post by Dr Small on 2008-02-08
> **apotts said:**
> No, indeed it's not an option here. The thought of opening my network to the world or having to control it by MAC address is just too complicated compared to Windows. I possibly got the impression that Ubuntu was more mature than it is. Surely secure wireless networking is one of the basic essentials of a modern OS?
It is, and I know it is possible because I have heard of people doing it, but I myself have had no luck with it...

---

### Post by hyper_ch on 2008-02-08
for securing wifi don't use WEP.... WEP can be cracked within seconds. In that case save yourself the trouble and use nothing.

If you want to be secure, use WPA2.

If you have an outside box you can connect to, you could also setup a vpn tunnel to it. In that case no security on the wifi is also needed.

---

### Post by stchman on 2008-02-08
Trash using WEP.  From everything I have read WEP is worthless.  Use WPA or WPA2 and don't hide your SSID.

---

### Post by sneeks on 2008-02-08
as above,use wpa psk at least...

---

### Post by Deived on 2008-02-09
I didn't have a problem with WEP before, but I just keep it open and use a Mac Filter.

---

### Post by mike555 on 2008-02-09
If you use your laptop plugged in all the time or if you use a desktop you could get a gaming adapter , once they are set up they work with anything with an ethernet port (because the driver is in the box) ..........

---

### Post by euler_fan on 2008-02-09
[Comparison of WEP/WPA/WPA2]("http://compudent.blogspot.com/2006/09/wireless-wep-vs-wpa-vs-wpa2.html")

---

