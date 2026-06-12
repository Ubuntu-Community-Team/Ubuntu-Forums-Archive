---
title: "Linksys WPC54G V5 setup"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Damoedge on 2007-02-07
Hi People,

This is guide that worked for me, after ages of searching and asking people I finally got my wireless up and running.

**A big thanks to **renzokuken**  who set me off in the right direction.**

I must point out that before doing any of the below I was connected to the internet via a standard ethernet connection, so bare that in mind.

First ndiswrapper needs to be installed and ndisgtk downloaded and saved to home directory. Download ndisgtk from [http://packages.ubuntu.com/edgy/net/ndisgtk](http://packages.ubuntu.com/edgy/net/ndisgtk)

 *Open a terminal session
 *sudo apt-get install ndiswrapper-utils
 *sudo dpkg -i --force-depends ndisgtk_*.deb
 *sudo depmod -a
 *sudo ndiswrapper -m
 *sudo gedit /etc/modules (This will make ndiswrapper load on startup)
 *Add 'ndiswrapper' to the end of the file and save changes.

Now copy the driver files from the windows CD to a named folder of your choice i.e. .inf files.
 
At this point all we have done is install ndiswrapper and force it to load on boot up, now we will install the driver for the wireless card. You can now connect the wireless card into the laptop

 *Goto System>Administration>Windows Wireless Drivers
 *Install new driver
 *Browse to the location of the saved Windows .inf files
 *Select an .inf file, it's likely you'll have more than one
 *Once you choose one, if correct you will see '**Hardware present: Yes**'
 *If no joy on the 1st .inf try another until you see that message.

Now reboot the P.C and the LED lights should start flashing. Once you have Lights Ubuntu has detected the card. You must now configure the settings via network and select the correct SSID ID and WEP keys etc and Bingo you're away.

This is the first time I've every used Linux and very proud I managed to do this. There is no way I'll go back to Windows.

---

### Post by teaker1s on 2007-02-08
there is a bug with ndisgtk, it sometimes shows drivers installed when they are not, to check command in terminal
[COLOR="Red"]sudo ndiswrapper -l[/COLOR]

L not I

---

### Post by alexlindley on 2007-02-09
Hi Damoedge,

I have been having the same problems getting this card working and I couldnt get your instructions to work! :(

I think the problem i have is that i've tried all these before and they were already installed. When I went to the "windows wireless drivers" option it showed the drivers were already installed. It did show the hardware as present though!

What drivers did you use to install the card? I was using the drivers from the linksys site but the power LED is still not lighting up even after a restart!!!!

Any advice you could give would be great, i seems to be in the same situation as you with this the first time i have tried linux.

Thanks,
Alex

PS. i do have the ethernet connection working.

---

### Post by Damoedge on 2007-02-09
Hi

I actually have the CD with the drivers on, I found the link to the V5 drivers on the linksys website but the download timed out.

Im at work now and have no access to my laptop until I get home, If you send me your email address I can email you the driver that works for me. 
However by the sounds of it the driver you have is just fine, are you sure you have enterted the command for ndiswrapper to start at boot up

*sudo gedit /etc/modules (This will make ndiswrapper load on startup)
*Add 'ndiswrapper' to the end of the file and save changes.

---

### Post by alexlindley on 2007-02-09
Is it 'ndiswrapper' with the quotes? i put it in without.

---

### Post by teaker1s on 2007-02-09
without quotes and the link in my signature has a good ndiswrapper tutorial

---

### Post by alexlindley on 2007-02-09
I've done a fresh install of ubuntu and followed the instructions exactly and theres just no power to the card.

I've decided that its probably the laptop with the problem.

I'm just going to have to buy a USB wireless network stick.

Are there any other people who couldnt get their WPC54g v5 working?

---

