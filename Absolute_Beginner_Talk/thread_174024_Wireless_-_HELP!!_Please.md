---
title: "Wireless - HELP!! Please"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by cowley on 2006-05-11
Hi,

I have wanadoo wireless and have recently updated my system from xp pro to ubuntu (!) which i think so far is great.

i have managed to get quite a few things sorted and so far am learning a fair bit about this system, but i cannot get my wireless working.  ubuntu recognises my wireless dongle and has assigned it as eth2, i have tried configuring it for the livebox, using network manager and today i tried another wireless util, gkwit (or similar!), but it doesnt pick up any access points anywhere.  i know the livebox is ok as i still have xp on another computer and that picks it up ok.  

Is this a known problem with wanadoo wirless?  would i be better off buying another wireless adapter and if so which one would be the best/easiest?



i have a dell inspiron 5150, the wieless dongle is a usb one.

thanks

simon

---

### Post by Papa-san on 2006-05-11
I have no idea about your particular setup, but the links in my signature may offer you some help. I recommend the 'wireless help' one...
Linux is kinda quirky with some wireless setups, so search these forums and google for help. there is an amazing amount of help out there.

Good luck!

---

### Post by tribaal on 2006-05-11
Since you connect with Wanadoo I suppose you speak French, so you might want to give [this]("http://lea-linux.org/cached/index/Configurer_le_wifi_avec_une_livebox,_freebox_etc....html") a try.

Bon courage!

- trib'

---

### Post by cowley on 2006-05-11
i wish i did speak french... the amount of googles returned in french!!

simon

---

### Post by macdo on 2006-05-11
The Livebox has a MAc address filtering function (you have to press a button to connect for the first time), doesn't it?

---

### Post by cowley on 2006-05-11
hi

i have never had to press any buttons b4 to connect to the box so i dont know.  does it matter it the dongle is assigned as eth2 not wlan0??  the dongle all seems to be working itself - but when i scan eth2 returns as no scan results even though the livebox is about 5 ft away and i normally get a belkin54g in the area too

thanks

simon

---

### Post by macdo on 2006-05-11
In a terminal, run ```
iwconfig
```, to check that your dongle is up and running.
Then try ```
iwlist eth2 scan
```

Post results.

---

### Post by Ray Hamilton on 2006-05-16
Simon

I'm not sure if this will help because I have just noticed that you are using Dapper.  However, I presumbaly have the same Wanadoo wireless kit - the USB adaptor being labelled Inventel.
Roughly this is what you do.
Install ndiswrapper from the Ubuntu CD.
Copy your windows files to a directory that you can access from Ubunutu:
   prisma02.inf  probably found in /windows/system32
   prisma02.sys probably found in /windows/drivers
now open a terminal (Applications->Accessories->Terminal)
and type (you will need to enter your root/main login password when prompted):
*sudo ndiswrapper -i /pathtoyourfiles/prisma02.inf*
*sudo ndiswrapper -l* (that's a small L)  hopefully you see no message about hardware not being present!Click
*sudo ndiswrapper -m*
*sudo modprobe ndiswrapper*

From here you can use a GUI to do the rest of the job, so close the terminal window
Now System->Administration->Networking
Click on Wireless connection/wlan0 then click properties
for Network name (ESSID) use WANADOO-E696
for key type use Hexadecimal
for WEP enter the key that is printed on the sleeve of the Wanadoo Wireless CD cover - NOTE do not use spaces
for configuration use DHCP
click OK
click activate

You should see a light on the USB adaptor - say "Hallelujah! I have seen the light" "Yea, brother"
You should now be able to click on the firefox icon, enter an URL and surf away.
BTW the "Hallelujah" is optional

Of course, there is more info in the wiki, etc.

---

### Post by FraserHughes on 2006-06-06
Cheers Ray, have been trying to sort wanadoo out on my laptop for ages, so hallelujah will definately be in order when it is work.

Have started following though your instructions, unfortunately when I type "sudo ndiswrapper -l" to list the drivers, although the driver is shown it is listed as invalid.

Any more advise would be greatly received.

Thanks again.

---

### Post by Ray Hamilton on 2006-06-07
Hi Fraser

Firstly let me say that my instructions were for using a desktop PC, but there is no reason that I know that they won't work on a laptop (even an Acer Travelmate 202T! - sorry just joking) using the USB adaptor from Wandoo (or Orange as they are now). My laptop is an IBM/Lenovo ThinkPad R50e and being wi-fi enabled already connected very easily.  Please make sure that you have both files from the locations specified NOT from your CD. I thought I could save time by doing that but it does not work, presumably because some configuration is done to them when they are installed.  Did I mention that both files need to placed in the same directory before using ndiswrapper.  You will be pleased to note that you have not broken anything - the first few times I tried, with different files etc. I got the same "message" from ndiswrapper.  I even tried ignoring the message and continuing, but this does not work!

I hope this helps you sort it.

Ray

---

### Post by FraserHughes on 2006-06-19
Hi Ray,

Thanks for your help.

You have email.

Cheers again Fraser

---

### Post by superD on 2006-08-30
Hello, I'm also trying to use this adapter, but have a problem. I can see PRISMA02.sys in /windows/drivers, but cannot see the .inf. Any help?

---

### Post by Ray Hamilton on 2006-08-31
Hi superD

Can you give a bit more info e.g. what "other" OS are you using (XP, NT etc.) As far as I remember, the .inf should be in  /windows/system32.  If you still have problems I could send you my files.  (Although having upgraded to Dapper my Ubuntu is stuffed or at least the wi-fi part!)

---

### Post by kuberprok on 2006-10-26
> **Ray Hamilton said:**
> Simon

I'm not sure if this will help because I have just noticed that you are using Dapper.  However, I presumbaly have the same Wanadoo wireless kit - the USB adaptor being labelled Inventel.
Roughly this is what you do.
Install ndiswrapper from the Ubuntu CD.
Copy your windows files to a directory that you can access from Ubunutu:
   prisma02.inf  probably found in /windows/system32
   prisma02.sys probably found in /windows/drivers
now open a terminal (Applications->Accessories->Terminal)
and type (you will need to enter your root/main login password when prompted):
*sudo ndiswrapper -i /pathtoyourfiles/prisma02.inf*
*sudo ndiswrapper -l* (that's a small L)  hopefully you see no message about hardware not being present!Click
*sudo ndiswrapper -m*
*sudo modprobe ndiswrapper*

From here you can use a GUI to do the rest of the job, so close the terminal window
Now System->Administration->Networking
Click on Wireless connection/wlan0 then click properties
for Network name (ESSID) use WANADOO-E696
for key type use Hexadecimal
for WEP enter the key that is printed on the sleeve of the Wanadoo Wireless CD cover - NOTE do not use spaces
for configuration use DHCP
click OK
click activate

You should see a light on the USB adaptor - say "Hallelujah! I have seen the light" "Yea, brother"
You should now be able to click on the firefox icon, enter an URL and surf away.
BTW the "Hallelujah" is optional

Of course, there is more info in the wiki, etc.

Ray

I have the same problem with the same card. Where did you get the prisma02 files from?

On my Cd and on my XP, I can find it.

Where can I get them?

---

### Post by Henry Rayker on 2006-10-26
Have you tried enabling the viewing of hidden files? The .inf may be hidden.

---

