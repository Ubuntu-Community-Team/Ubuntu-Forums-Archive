---
title: "Imac G3 running 10.04 not able to connect to internet"
date: 2011-01-23
forum: Apple Hardware Users
---

### Post by snafu006 on 2011-01-23
So i Got out my old G3 its a summer 2001 600 mhz 1gig ram 20 gig HHD. And after get the xorg.conf fix and i can post my XORG file if any one needs it. I try to connect to the internet both wired and wireless.

Now it can see my wireless router but can't join it i tryed taking off the wap2 and it still did not work. And wired hooked it up to the modem and no go can anyone help me out on this thanks.

---

### Post by conal on 2011-01-24
Hi Snafu

I just replied to your message but thought I'd have a look at your original post. Just to be clear:

You have tried to connect both wirelessly and wired?

In the message I asked if you have installed the braodcom driver with the broadcom firmware-cutter, however if you can see the wireless router then you obviously have(?). How old is the router? (I take it you mean you have tried both WPA and WPA2). Are you sure you have the password correct? (don't meant to be cheeky but I have failed on that bit many many times).

Regarding Wired connection, did you have the mac connected to the router when you installed? In my experience if the ethernet  going to work then it will detect it correctly on install.

I also asked in the message if you are using LXDE as the window manager, as I have had problems accessing wireless through LXDE on my power-pc macs in the past (due to a bug) Can I confirm if you are using lxde, xfce or gnome (the standard ubuntu install)?

I'm not sure I'm the best person to help as I'm no expert but if you can give me more info I'll try.

Best

Conal

---

### Post by snafu006 on 2011-01-24
i got it to connect to the net i had to open the computer the nick card came loose some how i have not updated it yet i been busy but i will in stall thos brocom drivers you where talking about and i let you know if it work.

---

### Post by snafu006 on 2011-01-24
So the imac is updated will connect to the net when is wired in but still no wireless i installed the broadcom drivers  it can see the the router and i still will not connect. The router is a Linksys wrt54g v4 with DD-wrt on it. I updated the firmware on it and i know its working because be for i put ubuntu 10.04ppc on the iMac it had os10.4 tiger and was able to connect.

I even turn off the security and tryed that but no go what can i do or should i just install mintppc or get a usb wireless card?

iMac g3 600mhz
1GB RAM
20GB HHD
Apple AirPort Card Not Willing to connect

Linksys WRT54G v4 With DD-WRT54 Firmware Working

---

### Post by conal on 2011-01-25
Well I'd always reccomend mintppc or debian lenny anyway, but not for this reason. If you see the available networks including your own one then you should be able to connect. I'm not at home just now but I'll see if I think what might be causing this and get back to you later.

---

### Post by linuxopjemac on 2011-01-25
You are using airport classic (airport/orinico modules). In MintPPC you will get it working by installing firmware-linux-nonfree. This package also exists for Ubuntu. You will have WPA-PSK support for your card then. You might have to do a firmware upgrade for your card though from within Apple OS. It has to be v9.52 to work properly. of course I recommend you to install MintPPC as it is better than Ubuntu.

> So, after banging my head against a wall for a bit, I tried to step back and broaden my troubleshooting scope, and wondered if there was a problem with the airport card itself, or perhaps the firmware was too old, so I reinstalled OS X, and ran all the updates. That was a good thing, since it brought the firmware on the airport card from 8.7 to 9.53, I think it was. But it still wouldn't connect in OS X! So then I decided to look over the AP settings (I have a WRT54G) and I found a setting for basic rate. the help said something about switching to lower speed to be compatible with B cards and it was set to 'all', so I set it back to 'default', and voila, it connected to the AP in OSX now! wow, what a headache; there's so many things that can go wrong that it's easy to focus in the wrong area for the problem. As an aside, I can also get it working with WPA2 w/ TKIP, which is great.

---

### Post by conal on 2011-01-25
Thanks Linuxopjemac, I just noticed the bit about original Airport card not requiring the broadcom firmware-cutter in the PPC FAQ, 

[https://wiki.ubuntu.com/PowerPCFAQ]("https://wiki.ubuntu.com/PowerPCFAQ")

Sorry, my bad. hope this works for you now sanfu006

---

### Post by snafu006 on 2011-01-25
I will try it out when i get home see if there is a setting in the router to lower the rate. and i know the classic airport card firmware is up to date. 

 And if that does not work then i will POST my XORG.CONF file and install mintppc

---

### Post by snafu006 on 2011-01-27
I got it to work i have wireless internet on this old g3 i am making new post with my xorg.conf file and what i did to get this to connect to the net thank you all for your help!!!!

---

### Post by conal on 2011-01-27
Well I don't think I was much use, good to see another happy G3 linux user though!

---

### Post by snafu006 on 2011-01-27
Oh you helped what you told me started to make me think lol so thank you


Upon installing Ubuntu 10.0.4, immediately open the terminal and type:

sudo aptitude install wicd

Follow the instructions. Next, 

sudo aptitude remove network-manager

Follow the instructions.

Next, open up WICD which should be in your applications area, find your network, click properties and enter the password in. Click connect.

---

