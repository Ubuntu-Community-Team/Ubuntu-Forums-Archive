---
title: "automatic Wlan help"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by gloscherrybomb on 2007-01-17
Hi,

I have finally managed to get my wlan working (and with network manager) but to get it to work each time I start my computer, I have to go to the terminal and do:

sudo iwconfig wlan0 essid 'myessid'

then I can do: iwlist wlan0 scan and get a result, and connect to my wifi.

is there a way for this to happen automatically so that I dont have to go to the console each time?

---

### Post by lukew on 2007-01-17
> **gloscherrybomb said:**
> Hi,

I have finally managed to get my wlan working (and with network manager) but to get it to work each time I start my computer, I have to go to the terminal and do:

sudo iwconfig wlan0 essid 'myessid'

then I can do: iwlist wlan0 scan and get a result, and connect to my wifi.

is there a way for this to happen automatically so that I dont have to go to the console each time?

You can either add it in as a boot process or as a startup action.

I don't having my wifi connect at startup as it will just hang if it is not on!!

I would write a script and put in in your path so you can call it when you like!!

Luke

---

### Post by aarbear26 on 2007-01-17
it really depends on your hardware. if you let me know what card you use and what you had to do to get the wifi working, i can help you more specifically. 

For me, network manager was a pain in the but and didn't really work, as you seem to be finding out. I use wifiradar. Look for it in the repositories. There are a few other good programs that are in the add/remove programs menu item to make it easier.

Hope that helps a little.

---

### Post by gloscherrybomb on 2007-01-17
My hardware is an IMPROCOMM 2220 802.11g on an acer aspire 1672WLMI.

Surely there must be a way to get wireless to autoconnect on startup? Also I have a button on my laptop which I have to switch on to enable the device, is there a way to get this to turn on at boot like it does on windows?

---

### Post by aarbear26 on 2007-01-18
well I'm not sure about your laptop. Ubuntu senses the intel wireless thats built into my HP. 

If you have to hit the button to turn it on, i'd say you would be best to run the first script of code you had as a startup script (it's in the administer menus somewhere, i can look it up later if you need). That'll start your card without you having to type it every time. 

Then I would go to add/remove programs and add wifiradar. It'll automatically load on startup. It graphically gives you a list of in range wireless signals. You can even save wep and wpa passwords in a profile so you don't need to enter them every time. Give it a try and let us know how it goes.

---

### Post by gloscherrybomb on 2007-01-18
I have network manager and thats great. What do I do with that script thing you said about that stops me having to press my wireless button?

---

