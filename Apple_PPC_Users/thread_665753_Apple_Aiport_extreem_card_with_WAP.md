---
title: "Apple Aiport extreem card with WAP"
date: 2008-01-12
forum: Apple PPC Users
---

### Post by computer geek on 2008-01-12
Hi all,
        I am kind of stuck in this one. I can't get wireless to work. I know that i have done this before but none of the things that I did back then work. can I please have help?

Geek

---

### Post by computer geek on 2008-01-13
I would like some help. :KS

---

### Post by havoc_joe on 2008-01-14
Does the AP use any type of encryption? What tools are you using to scan/connect/etc?

---

### Post by computer geek on 2008-01-14
I am sorry, i don't know what you are talking about.
:(

---

### Post by havoc_joe on 2008-01-14
Basically do you need to enter any type of password to connect to the access point? If you are having trouble seeing the access point, you might want to search the forums for help with drivers and utilities. I believe that you will need broadcom drivers for the airport extreme chipset, but there is pretty good support for that card now.

Also, I have found WICD to be a really nice way to get things setup:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

It would help to know what type of router you use and what settings you have on it, though the biggest thing is whether or not you have encryption setup (WPA, WEP, etc).

---

### Post by computer geek on 2008-01-15
Hi, Yes I do need a password. The pass is set-up 4 WPA Personal. I've got an Airport Extreme Base Station. (802.11n,b,g,a) It is broadcasting at "b,g".

I have installed bcm43xx-fwcutter and bcm43xx_compwiz.

I have tried Wicd cause that was what i used before i had 2 re-do everything on on my sda.

It just keeps going 55% 0% 55% 0% and different numbers and i never stops! I have tried many different ways but they all don't work!

Hope this helps!

Geek

---

### Post by havoc_joe on 2008-01-15
That's a really interesting problem that you describe. I've only had something like that happen to me once before and it was due to a defective router.

My suggestion to you is to try and reinstall the broadcom drivers on your computer and see if that changes anything. Another thing that you may want to try is connecting with another machine or with a separate OS (if you dual boot, etc). If the problem occurs outside of ubuntu as well, there may be an underlying hardware problem with either the card or the router.

One more thought that occurs to me is that you may be out of range or connecting on a wrong channel/frequeny or on one that is very busy. In other words, there may be interference with the particular frequency that is being used. Try using a different frequency and channel on the router if you can. Unfortunately I don't have an Airport base station to play with atm.

---

### Post by computer geek on 2008-01-15
Yes I see, I am posting from OSX and I know It is not my card or router. And I have conected to my router before and surfed the net. And in Wicd, i get conected but I get the 0% 55% 0% 65% and so on. I can surf the net useing wired but I get that thruogh my laptop that shares it's conection with ubuntu via ethernet. But I like wireless. I will try to up date the firmware on the bcm43xx-fwcutter.

I will post again if that works or not.

Geek:)

---

### Post by computer geek on 2008-02-05
OK, can someone please HELP! I am kind of in a hump.:(

---

### Post by AlphaMack on 2008-02-06
You're not being specific at all about the question or what your situation is, so I'll give you a checklist of connecting to a WPA-encrypted network (at least the way it works for me).

1.  Install bcm43xx-fwcutter and have it extract the firmware.
2.  Drop into a shell and type wpa_passphrase SSID where SSID = your network's name.
3.  You will be prompted for the network password.  Enter that in.  Hit enter.
4.  You should receive a very long alphanumeric key.  That is your hex key.  Copy it.
5.  Select your AP from the list in NetworkManager.  You should get an authentication box.
6.  Select WPA or WPA2 Personal, depending on what you set up.  For the password, paste in the hex key you generated.
7.  You should then be able to connect.

I also suggest using pam-keyring so you don't have to continuously enter in your keychain password every time you log in.  Search the forum for relevant threads.

---

### Post by computer geek on 2008-02-06
Yes I will try. I saw someone else do the same but they did not click on their server. I will do yours

---

### Post by computer geek on 2008-02-19
Didn't work, I tried and network manager goes back to the "No internet connection"  sign and the system malfunctions  and I have to force shut off and restart.

---

### Post by computer geek on 2008-02-21
I tried to use ndiswrapper with Network-manager but now I can't even Dectect My Base station! This really stinks. Can I please have some help?:(:(:(:(:(

---

### Post by AlphaMack on 2008-02-23
You cannot use ndiswrapper with a PowerPC Mac.

---

### Post by computer geek on 2008-02-24
That stinks, can you give me any other suggestions?:?:

---

