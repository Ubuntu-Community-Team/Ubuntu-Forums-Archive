---
title: "How can I use wireless internet on pc?"
date: 2011-06-24
forum: Any Other OS
---

### Post by adventurousman on 2011-06-24
Hey guys, 
 
I've a moderm by motorola and a router by sitecome. I live with 2 housemates and they are already using both of them. I was told I can use sitecome router to connect to the internet. I don't have ethernet cable and would like to connect wirelessly.
 
I don't know how exactly to do it or if I need a card or something?
 
Please help. I'm using internet from a library so don't know the module number of sitecome or motorola.
 
thanks in advance.

---

### Post by adventurousman on 2011-06-24
anyone? please help
 
thanks

---

### Post by chili555 on 2011-06-24
What kind of computer do you have? Is it a desktop computer? They usually do not come with a wireless card, so you'd need to buy one. You could get a PCI or USB device. Here is a Wiki page that will help you decide which one is well supported. Simply try to match what's on sale on line or the store with a card here and that is well supported: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

If you have a laptop, they usually come with a wireless card and we can identify what you have and how to activate the built-in wireless.

So, tell us, what do you have?

---

### Post by adventurousman on 2011-06-24
thanks for the quick reply
 
btw I've a desktop computer
 
so I can either buy a pci or a usb stick one rite? Would the usb one give me the same speed?
 
thanks in advance

---

### Post by adventurousman on 2011-06-24
so which one should I buy?
 
I'm in a hurry because I'm using internet from library and its gonna get close in half an hour and then I've to come tomorrow 
 
thanks in advance.

---

### Post by chili555 on 2011-06-24
> so I can either buy a pci or a usb stick one rite? Would the usb one give me the same speed?It should. It's my opinion that you get what you pay for. I'm pretty sure I could find a US$15 USB wireless device that might work OK for a while; maybe even a year. Spend a few dollars more and get a device that will outlast ten cheap ones.> so which one should I buy?

I'm in a hurry I can't do your homework for you. A few minutes on the Wiki link I gave you and a few searches of the forum will give you the answer. I have dozens of others who need to blame me for something. See you tomorrow.

---

### Post by adventurousman on 2011-06-25
I'm a newbie so I don't know which one would be best, I'd go to the stores today anyway and find something.
 
It would be better if I already knew which ones were atleast good, what exactly to look for, which company or which model
 
thanks

---

### Post by chili555 on 2011-06-25
> **adventurousman said:**
> I'm a newbie so I don't know which one would be best, I'd go to the stores today anyway and find something.
 
It would be better if I already knew which ones were atleast good, what exactly to look for, which company or which model
 
thanksDid you see my post above?> Here is a Wiki page that will help you decide which one is well supported. Simply try to match what's on sale on line or the store with a card here and that is well supported: [https://help.ubuntu.com/community/Wi...CardsSupported](https://help.ubuntu.com/community/Wi...CardsSupported)Write down the brand and model of the six or eight you think are most likely to be in your store and use the list when you go shopping. Does your store have a website? Get the Wiki page in one tab of your browser and the store's wireless devices in the other. Go back and forth until you find a few candidates.

---

### Post by adventurousman on 2011-07-02
I can't find my other thread so I'm posting on this one.

I bought the sitecom XN 300 for the router sitecome 300.

The signal is very low & its very weak. I didn't have internet for the past 3 days and today it shows only 1 mb with signal strength very low.

How do I increase the speed of it or the signal strength? I decided to buy a moderm from another company but where I live I can only get 4 mb, is 4 mb good speed? Or should I keep working on increasing this speed?

Thanks

---

### Post by chili555 on 2011-07-02
We need to know more about the wireless card in your computer. Did you buy a PCI card? If so, please open a terminal and run and post:```
lspci -nn
```Is it a USB wireless device?```
lsusb
```That will help us diagnose and hopefully fix your issue.

---

### Post by adventurousman on 2011-07-02
Thanks for the fast reply, I really appreciate it. I hope this issue is dealt with and I get a good internet speed, btw is 4 mb a good speed for surfing the net and using torrents, downloading movies?

I've wireless network usb micro adapter 300 N from sitecome. Its X3, says xtra range

the router is from sitecome so the shopkeeper said this one is the best for this router.

There are 2 other networks used by my neighbors and both are using channel 11, I tried to change it but I logged it and there was no drop down menu to change the channel + I installed network stumbler, I also heard that maybe a repeater would help.

Before I could do anything, the internet got dc and now its back but a page opens in a minute or so

thanks in advance guys

---

### Post by chili555 on 2011-07-02
> I've wireless network usb micro adapter 300 N What does this terminal command tell us about it?```
lsusb
```With more information, we can probably help.

---

### Post by adventurousman on 2011-07-02
U asked for the network adapter, now I've told u that its usb and I also gave the full name of it. 

Other than that I've a router from sitecome, its sitecom 474bf6. Speed 1 mb, signal strength very low. status connected.

status = weak.

what else can I give u?

The only info I've is from router and the adapter.

My 2 housemates are using the same network. Its on channel 11. 2 other networks are connected on the same channel. The network is open so anyone can use it, so probably other people are using it too which is decreasing its speed. I don't know how much speed it should be getting.

---

### Post by haqking on 2011-07-02
> **adventurousman said:**
> 
what else can I give u?

.

you could give us what has been asked for:

lsusb

as post above asks you for

---

### Post by chili555 on 2011-07-02
> **adventurousman said:**
> U asked for the network adapter, now I've told u that its usb and I also gave the full name of it. 

Other than that I've a router from sitecome, its sitecom 474bf6. Speed 1 mb, signal strength very low. status connected.

status = weak.

what else can I give u?

The only info I've is from router and the adapter.

My 2 housemates are using the same network. Its on channel 11. 2 other networks are connected on the same channel. The network is open so anyone can use it, so probably other people are using it too which is decreasing its speed. I don't know how much speed it should be getting.Please open Applications > Accessories > Terminal. Type in:```
lsusb
```Press Enter. One of the lines that will come out relates to your wireless device. Write down *_every_* detail and post it here, please.

---

### Post by adventurousman on 2011-07-02
I'm sorry, I didn't understand that. What is ISUB and how can I look it up to find out?

---

### Post by chili555 on 2011-07-02
> **adventurousman said:**
> I'm sorry, I didn't understand that. What is ISUB and how can I look it up to find out?Please see my post above.

---

### Post by adventurousman on 2011-07-02
sorry I'm a newbie so couldn't find out the terminal. 

Here I've all programs and there I've accessories, in accessories I couldn't find terminal. 

Should I be looking somewhere else?

thanks

---

### Post by haqking on 2011-07-02
> **adventurousman said:**
> sorry I'm a newbie so couldn't find out the terminal. 

Here I've all programs and there I've accessories, in accessories I couldn't find terminal. 

Should I be looking somewhere else?

thanks


press

ctrl + alt + t

this should bring up a terminal (shell, terminal emulator, console)

then type as requested

lsusb

---

### Post by adventurousman on 2011-07-02
after pressing ctrl+alt+t, it did nothing then I pressed +d and it opened task manager, there is applications but there is no option for accessories or terminal or to type in. I did type in new task but it gave an error saying windows couldn't find it

---

### Post by haqking on 2011-07-02
> **adventurousman said:**
> after pressing ctrl+alt+t, it did nothing then I pressed +d and it opened task manager, there is applications but there is no option for accessories or terminal or to type in. I did type in new task but it gave an error saying windows couldn't find it

You know this is a Ubuntu Linux forum right ?

Do you use Linux ?

This is not a Windows support forum ?

If you are running windows you are in the wrong place.

---

### Post by adventurousman on 2011-07-02
I didn't know that. 

Yes, I'm using windows but its about networking so maybe u guys can still help.

All I saw a network and wireless forum, lol

---

### Post by haqking on 2011-07-02
> **adventurousman said:**
> I didn't know that. 

Yes, I'm using windows but its about networking so maybe u guys can still help.

All I saw a network and wireless forum, lol

yeah i guess the BIG UBUNTU FORUMS logo at top left of the page is hard to see ;-)

i am sure someone might want to help, but i would recommend looking for a Windows forum as they will be more inclined to and also there will be posts there already which fixes your issues.

This is a Linux forum, feel free to leave windows and switch to Linux, remove the chains that tie you down LOL ;-)

peace ;-)

---

### Post by adventurousman on 2011-07-02
I saw the logo of UBUNTU but didn't know its for linux users only, to be honest I don't even know what UBUNTU is :D

I didn't find a windows forum that's why posted here.

if u know any do let me know. I might find it too.

btw is 4 mb a good speed?

I'm stuck between 4mb adsl speed or using this wireless and fixing it somehow if possible

---

### Post by chili555 on 2011-07-02
I don't have or understand Windows. I'm sorry I can't help you.

---

### Post by adventurousman on 2011-07-02
I always typed in for wireless speed problem, lol

anyways thanks.

---

### Post by haqking on 2011-07-02
> **chili555 said:**
> I don't have or understand Windows. I'm sorry I can't help you.


I have it, i taught it, i have over 25 certs in it...do i understand it ? NO ;-)

Can i help you with it, sure....Remove, install Linux ;-)

---

