---
title: "Linux on macbook 2,1"
date: 2008-12-07
forum: Apple Hardware Users
---

### Post by Death_To_The_World on 2008-12-07
Hey,

 I do not have money to spend on Leopard so I am trying to get linux working on my Macbook 2,1.  I tried Suse 11 but the touchpad doesnt work nor the keyboard.  I tried Ubuntu but airport didnt work.  I tried to plug in my ethernet cord but it still didnt detect.  Maybe it will work if I install ubuntu with the cord plugged in? If not does anyone know of a distro that works well on macbook 2,1?

---

### Post by cyberdork33 on 2008-12-07
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by Death_To_The_World on 2008-12-07
Yeah but internet wouldnt work when I plugged in the ethernet cord. So I couldnt download wicd.  Do you think if I reinstall ubuntu with Ethernet plugged in during installation it will detect it?

---

### Post by Sigudian on 2008-12-07
How did you get the Macbook Air and do not have Leopard??
(keep in mind, i dont have a mac, yet)

---

### Post by Death_To_The_World on 2008-12-07
Huh? I don't have a macbook air.  I have a macbook 2,1 airport is for wifi.  I have OSX 10.4.11 but I don't have Leopard.

---

### Post by Sigudian on 2008-12-07
> **Death_To_The_World said:**
> Huh? I don't have a macbook air.  I have a macbook 2,1 airport is for wifi.  I have OSX 10.4.11 but I don't have Leopard.

Okay, hehe, i misread :P sorry

Why would you need to by Leopard if you have Tiger?
And by the way, I'm getting Ubuntu anyway, even though the mac im soon buying comes with Leo..

---

### Post by Death_To_The_World on 2008-12-07
Well if I had the money I would like to check out Leopard. I would assume it is more secure sense it is newer.  But I would really like to get Ubuntu to run on it but I cant seem to be able to.  I dont wanna reformat again just to see if reinstalling with ethernet plunged in will help.

---

### Post by Sigudian on 2008-12-07
> **Death_To_The_World said:**
> Well if I had the money I would like to check out Leopard. I would assume it is more secure sense it is newer.  But I would really like to get Ubuntu to run on it but I cant seem to be able to.  I dont wanna reformat again just to see if reinstalling with ethernet plunged in will help.

I bet a buck there is more viruses for leo than for tiger, Ubuntu is really nice,  but you could get the ethernet plug to work after the install, just follow cyberdork33's guide, find what Mac you have, and then find out how to install your RJ45... erm ethernet plugg. Copy all the files you need to fix it to a USB pendrive (with the pc your using now) and copy em over to your ubuntu on your mac

---

### Post by Death_To_The_World on 2008-12-07
Oooh, thanks sigudian.  I have a macbook 2,1.  Where would I find instructions on how to instal my RJ45 plug in ubuntu?  I don't see it in his guide, maybe I am looking in the wrong spot? Bear with me Im pretty noobish, but I really do appreciate the help.

---

### Post by Sigudian on 2008-12-07
1. Update the firmware to the latest version. If you prefer, you may use the standard "Software Update" (accessible from your OS X partition, if you have one)

Did you do this one?

And, atleast for the wireless, go to Cybergeeks link and check out the wireless....  Use either ath9k, Madwifi or Ndiswrapper, not all of them, just choose one (if that does not work take the another one)

And may your Rj45 plugg be ruined?? I heard of someone who ruined there USB port, but they reset something called SMC and it started to work again. Actually Cybergeek told me what SMC was, hehe, i have not bought a MAC yet, but im getting the air :P

---

### Post by Death_To_The_World on 2008-12-07
By update the firmware you mean just run a software update in osx? That I have done. OSX is fully updated and patched.  Hmm I will download one of these on my desktop and put it on a flash drive and install it on my laptop. I hope it works. my desktop is x64

---

### Post by Death_To_The_World on 2008-12-07
Also I dont think it is the port because when i plug it in on osx it works fine. on my desktop it wouldnt detect internet when i plugged it in either. Then I reinstalled suse with it plugged in now it detects it.

---

### Post by Death_To_The_World on 2008-12-07
Actually you might be right. It isnt detecting the rj45 in osx. how would i reset it?

---

### Post by pxwpxw on 2008-12-07
Death_To_The_World

There was a firmware upddate wwhich fixed dead keyboard at startup.
macbook firmware
[http://support.apple.com/downloads/#macbook%20firmware](http://support.apple.com/downloads/#macbook%20firmware)

ubuntu intrepid 810 install includes the ath9k wireless driver which works for my MacBook2,1, but you might need to do some setting up.

Wired network setup is part of the install if it is connected.

You should post your MacBook hardware info from Apple-aboutthismac-more if you need more help. (see the Macbook link).

---

### Post by Death_To_The_World on 2008-12-08
Hmm then I suppose I would need to do some setting up of the driver (no idea how). 

also it says that keyboard firmware update is for osx 10.5...

what from moreaboutthismac would you like to see?

---

### Post by pxwpxw on 2008-12-08
> **Death_To_The_World said:**
> Hmm then I suppose I would need to do some setting up of the driver (no idea how). 

also it says that keyboard firmware update is for osx 10.5...

what from moreaboutthismac would you like to see?

Get your wired network going first, then post for help with setting up the wireless

Leave the firmware update for now unless you are having keyboard problems that stop you installing or restarting. You can check that later.

Just post the lot. All this stuff -
```

Hardware Overview:

  Machine Name:	Mac
  Machine Model:	MacBook2,1
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	2 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache (per processor):	4 MB
  Memory:	1 GB
  Bus Speed:	667 MHz
  Boot ROM Version:	MB21.00A5.B07
  SMC Version:	1.13f3
  Serial Number:	W8717FYXWGL
  Sudden Motion Sensor:
  State:	Enabled

```

---

### Post by Death_To_The_World on 2008-12-08
Hardware Overview:

  Model Name:	MacBook
  Model Identifier:	MacBook2,1
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	2 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache (per processor):	4 MB
  Memory:	1 GB
  Bus Speed:	667 MHz
  Boot ROM Version:	MB21.00A5.B07
  SMC Version:	1.13f3
  Serial Number:	4H706AYVWGL
  Sudden Motion Sensor:
  State:	Enabled

---

### Post by pxwpxw on 2008-12-08
> **Death_To_The_World said:**
> Hardware Overview:

  Model Name:	MacBook
  Model Identifier:	MacBook2,1
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	2 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache (per processor):	4 MB
  Memory:	1 GB
  Bus Speed:	667 MHz
  Boot ROM Version:	MB21.00A5.B07
  SMC Version:	1.13f3
  Serial Number:	4H706AYVWGL
  Sudden Motion Sensor:
  State:	Enabled

You have the  MacBook EFI Firmware Update 1.1 same as me.
  Boot ROM Version:	MB21.00A5.B07
[http://support.apple.com/downloads/MacBook_EFI_Firmware_Update_1_1](http://support.apple.com/downloads/MacBook_EFI_Firmware_Update_1_1)

---

### Post by Death_To_The_World on 2008-12-08
It says I do not need the update. :confused:

---

### Post by Sigudian on 2008-12-08
can you force update it???
i dont know if it would help but i dont have a mac untill next month..

anyways, i think resetting te SMC would help:

   1.  If the computer is on, turn it off.
   2. Disconnect the AC Adapter and remove the computer's battery.
   3. Press and hold down the power button for 5 seconds and then release the button.
   4. Reconnect the battery and AC Adapter.
   5. Press the Power button to restart the computer.

---

### Post by pxwpxw on 2008-12-08
> **Death_To_The_World said:**
> It says I do not need the update. :confused:

Yes that is correct, that is what I meant you to see for yourself.

---

### Post by cyberdork33 on 2008-12-08
your ethernet is likely not working because it was not connected during install. You should be able to get it going with reinstalling though. There are also quite a number of packages available to install on the Ubuntu LiveCD.

---

### Post by Death_To_The_World on 2008-12-09
Cybergeek you were right! I just reinstalled with the ethernet plugged in and it now detects.  Now I just have to figure out how to get right clicking to work. In the guide it says     *

      On Ubuntu: Go to System &#9656; Preferences &#9656; Keyboard &#9656; Accessibility in the Main menu. Check Enable keyboard accessibility features. Click the Mouse Keys tab and check Enable Mouse Keys also. 

It isnt labeled "Enable keyboard accessibility" features or "enable mouse keys" but I clicked what read similar enough.  
 Then either edit the system files or use a local configuration file and xmodmap:

    *

      Editing system files (choose one of the following options):
          o

            option 1: lower Enter key = Right Mouse Button, Shift + lower Enter key = Middle Mouse Button

            sudo sed -i~ 's/KP_Enter/Pointer_Button3, Pointer_Button2/' /etc/X11/xkb/symbols/keypad

I dont know where to put that though...Im a noob...I tried to run it in the terminal but nothing happened hah...
what should I be doing?

Also how do I install flash? Adobe doesnt have one for this architecture.

---

### Post by Rog-Mahal on 2008-12-09
Those instructions for right clicking are outdated. Intrepid uses a new system, and some great instructions can be found [here.]("http://http://ubuntuforums.org/showthread.php?t=981474")

Flash installation instructions can be found [here]("http://ubuntuforums.org/showthread.php?t=772490") if you are looking for 64 bit help.

---

### Post by cyberdork33 on 2008-12-11
> **Rog-Mahal said:**
> Those instructions for right clicking are outdated. Intrepid uses a new system, and some great instructions can be found [here.]("http://http://ubuntuforums.org/showthread.php?t=981474")

Flash installation instructions can be found [here]("http://ubuntuforums.org/showthread.php?t=772490") if you are looking for 64 bit help.
your link was broken... reposting:
[http://ubuntuforums.org/showthread.php?t=981474](http://ubuntuforums.org/showthread.php?t=981474)

---

### Post by Rog-Mahal on 2008-12-12
My apologies.

---

