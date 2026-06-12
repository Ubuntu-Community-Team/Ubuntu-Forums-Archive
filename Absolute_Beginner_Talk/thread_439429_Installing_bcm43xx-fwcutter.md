---
title: "Installing bcm43xx-fwcutter"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Aloir on 2007-05-10
Hi There

I am currently trying to patiently configure my delighful Broadcom 4318 wireless card to work in Feisty. 

I tried the ndiswrapper approach, which promptly made the card vanish. So I gave up and re-installed Ubuntu.

So now I am finding out that it is better to stick with the native driver - bcm43xx.

The wireless card is recognised in iwconfig as eth1.

I think that the main problem is with bcm43xx-fwcutter. I have downloaded the package 

bcm43xx-fwcutter-006.tar.bz2 

extracted it, but am for some reason unable to install it. That includes using Synaptic Package Manager.

I have also downloaded the bcm43xx-softmac-sa as the latest driver. 

Can anyone offer any more advice on the steps to take, or perhaps the fwcutter is the wrong version? I am a total newbie to Ubuntu but am keen to figure this thing out.

I am using a Compaq Presario V4000 with a dual boot alongside windows. The card works fine in windows.

Many thanks.

Aloir

---

### Post by Bachstelze on 2007-05-10
Can you get a wired connection temporarily ? If so, you can just do

```
sudo apt-get install bcm43xx-fwcutter
```

---

### Post by Aloir on 2007-05-10
Thanks for the quick response!

Okay, so I now have fwcutter installed, but as you mention it wants to get a connection to the internet to find the firmware. I cannot get a wired connection through Ubuntu yet, so I only have another computers connection and a USB drive to transfer any files.

Is there any way round this catch-22?

Do you know a link where i can get to the latest bcm43xx driver?

Thanks again, it seems like i'm nearly there.

---

### Post by Bachstelze on 2007-05-10
Nope, sorry, I don't remember where bcm43xx-fwcutter gets the file. Doesn't it give you the address of the file before failing to download it ?

(w00t, 10 messages to go until the 3000 !!)

---

### Post by Aloir on 2007-05-10
Well the good news now is that i have the light shining brightly from my wireless card (!) and the Network Manager shows all the usual networks available.

However, the network i normally connect to in windows is not working for me in Ubuntu.

Please forgive my ignorance, but what is the best thing to check now?

Thanks for your help.

---

### Post by Bachstelze on 2007-05-10
"It is not working" doesn't help much... What are you tring to do and what does it do instead of working ?

---

### Post by Aloir on 2007-05-10
Sorry.

When I click on the network to try and connect, it attempts to join the wireless network, but after a minute or so it says unable to connect.

This is all from the desktop by the way.

---

### Post by Bachstelze on 2007-05-10
Pretty much why I never use the GUI, it makes troubleshooting much harder... What kind of encryption does your wireless network use ?

---

