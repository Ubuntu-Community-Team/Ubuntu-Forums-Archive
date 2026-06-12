---
title: "Sound via Alsa"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by ckamc on 2007-10-23
Well I am almost done but there is one thing bothering me.  I am unable to get any sound out of my Asus 939 A8N32-SLI Deluxe on board audio (I also have a PCI based creative sound card but upon search was told to forget it)  So I download the ALC850 Drivers and look thru the readme, refers to Alsa.  I find and use the how to config wiki page but when I get the config portion I am unsure what to do and have set it to dummy  ```
sudo dpkg-reconfigure alsa-sourc
```  am I making this way too difficult and missed something? or just continue following the wiki page and some how figure out how to compile.(Still dont understand how to conduct a successful compile with out GUI interface)  Thank you for your time.

---

### Post by ckamc on 2007-10-23
I just don't understand why whatever says should work right out of the box (onboard sound) is the one thing that doesnt work.

---

### Post by orange2k on 2007-10-23
Make sure your BIOS settings are right - if your onboard audio card is disabled, there is no chance to make it work in Ubuntu or anywhere else for that matter...
But if you have a Creative sound card, it should work, too (except X-FI series which works now only on 64-bit Linux)...

After setting up your desired audio card, check your hardware settings (system settings - hardware information) to see whether your audio card is detected properly...

---

### Post by ckamc on 2007-10-23
Yeah I am unlucky to have a XFI card.  I am 100% sure I enabled the audio in bios.   Also when I check my hardware manager it shows the CK804 and even the SB XFI. I also know that that all 6 connections work becuase my speakers do make that loud connection noise.

---

### Post by ckamc on 2007-10-23
No longer any error codes

---

### Post by ckamc on 2007-10-23
Well checked a few other threads to make sure but should I have this many listings for one on board sound processor? Normally its only two correct?

[IMG]http://img249.imageshack.us/img249/1701/screenshotdevicemanagerqh8.png[/IMG]

---

### Post by orange2k on 2007-10-23
I have a new machine with onboard audio only, so I will check when I get home and I will get back to you...

But I think its normal to have such a long listing...

BTW if you are able to run 64-bit Ubuntu, you will be able to make your X-FI work, because Creative released 64-bit Linux drivers for X-FI not long ago...

edit: I checked it, I have a similair listing...   You still can`t get any sound with this card?

---

### Post by ckamc on 2007-10-23
> **orange2k said:**
> I have a new machine with onboard audio only, so I will check when I get home and I will get back to you...

But I think its normal to have such a long listing...

BTW if you are able to run 64-bit Ubuntu, you will be able to make your X-FI work, because Creative released 64-bit Linux drivers for X-FI not long ago...

edit: I checked it, I have a similair listing...   You still can`t get any sound with this card?

Nothing out of it.

Going to try another fresh install and pull the Xfi to see if it work then.

Or I may just take a break from the OS for a while until I am able to update from 939 to am2 since I am still on a single core 939.

---

