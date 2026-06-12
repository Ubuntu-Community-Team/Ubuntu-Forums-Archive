---
title: "bluetooth cannot connect phone 2 macbook"
date: 2008-03-12
forum: Apple Intel Users
---

### Post by niteblind on 2008-03-12
Hi All,

I am now the proud owner of a new macbook and overall I am well impressed. I still prefer ubuntu to the mac OS X so I am trying to install this to my mac.

while fiddling with the Live CD i though being everything is working I would try bluetooth but still I cannot send any files from my phone to my mac. Does anyone know what is up? I paired the devices straight away and allow authentication. I also added the netowkr and serial services in the bluetooth preferences.

Has anyone managed to do what I am attempting?

cheers
niteblind

---

### Post by robzon on 2008-03-12
Hmmm, everything went very smoothly on my side. Are you using Gusty or Hardy?

On Gutsy you may have to install gnome-bluetooth package and run Bluetooth File Sharing application from Accessories. Hardy has everything included.

---

### Post by niteblind on 2008-03-12
okay thanks I can now send files over bluetooth now ontot he next set of problems. 

the wireless card is not being seen at all. I have just installed all of the latest updates and then thought it might be nice to go downstrairs and watch some tele while i work and found that the airport wireless card is not being picked up at all by the gnome network manager. has this been seen at all before or is it just me?

any ideas anyone?

niteblind
PS the macbook rocks !!! :D

---

### Post by robzon on 2008-03-12
Yes, new MacBooks have a broadcom (bcm4328) wireless card for which no Linux driver exists. You'll need to get a Windows driver and use it with ndiswrapper.
There's a change you still have the older 2nd gen (with atheros card). in which case a Linux driver exists, but you need to compile a new version manually.

Here are instructions for 2nd gen MacBooks:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

And here for the newer, Santa Rosa, MacBooks:

[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

I don't know how much has changed in the newest, 4th gen MacBooks, but most probably their still using bcm4328 chipset, so you'd have to follow the wireless instructions for Santa Rosa MacBooks.

Good luck!

---

### Post by niteblind on 2008-03-12
that sounds like the answer, the mac book is the latest model with the new specs so I would assume thisis the 4th gen version you mention.

Would this explain the lack of sound as well??? (in linux only mac os x works fine)

niteblind

---

### Post by robzon on 2008-03-12
Yup, just try the instructions for the 3rd gen MacBooks, I believe there are no specific instructions for 4th gen ones yet.
I have a 3rd gen MacBook and I had the same issues. See if you have the same sound card as I do:

robzon@robzon-mac:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

---

### Post by cyberdork33 on 2008-03-12
there is no differences really from 3rd gen to 4th gen

The only issue with the WiFi is that you have to use the windows driver from your Leopard DVD, you cannot use the Dell driver as instructed in the wikis.

---

### Post by niteblind on 2008-03-12
just got home and checked the sound card and yes we have the same one by the looks of it. 
niteblind@Wolverine:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

will try your how to over the next couple of days when I am not working :D 

Thanks for the assistance :D

niteblind

---

### Post by robzon on 2008-03-13
Cool, let us know how it worked for you.

---

