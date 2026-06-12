---
title: "Can't get my wireless card to work in Xubuntu"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by mrgreg on 2008-01-28
I am trying to get my net gear wireless card to work in Xubuntu 6.06.1... I am running this on an old IBM thinkpad 600e that I brought back from the grave. I have read some of the posts regarding 600e's and have added this at the install (acpi=off pci=noacpi pnpbios=off vga=0x317) I have no other way to get on the internet with this computer as it does not have an ethernet port. Any help with this would be great. I should also mention that I am a recant windows cross over.

---

### Post by jan quark on 2008-01-28
some input would be nice
please post the results of the following terminal commands

iwconfig
ifconifg
lspci
sudo iwlist scan, here you have to type in your login password

there are helpful to shed light on your network status

---

### Post by agim on 2008-01-28
Hi mrgreg, welcome to Ubuntu.

You may need a program called ndiswrapper to load your wireless driver. You will have to find out what kind of wireless card you have and then find the driver for it online.

Although, I would consider using Xubuntu 7.10 if I were you, with an older pc like that the wireless card may be included. Wireless card support is much improved in 7.10.

To find your wireless card. Open a terminal and type:

lspci

A few lines of info will stream down, you are looking for something that has the words Network and probably wlan in it.

As an example, here's mine.

01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

---

### Post by mrgreg on 2008-01-28
iwconfig = go wireless extensions 
ifconfig = Lik encap:Locl Loopack
                inet addr: 127.0.01 Mask 255.0.0.0
                up loopiback running MTU:16436 Metric:1
                RX packets:3 errors:0 Dropped :0 overruns:0 frame:0
               TX  packets:3 errors:0 dopped;0 overrns:0 carrer:0 
               RX bye: 172 (72.0b)  TX btes:172 172.0 b)
lspci = big long list of things which line do you need? 
sudo islist scan = command not found

---

### Post by agim on 2008-01-28
With lspci we just need the line that says Network or wlan or both.

---

### Post by mrgreg on 2008-01-28
[QUOTE=agim;4221770]Hi mrgreg, welcome to Ubuntu.

You may need a program called ndiswrapper to load your wireless driver. You will have to find out what kind of wireless card you have and then find the driver for it online.

Although, I would consider using Xubuntu 7.10 if I were you, with an older pc like that the wireless card may be included. Wireless card support is much improved in 7.10 

Can I upgrade, or do i need to do a complete reinstall to get 7.10? 

Where do I get ndiswrapper? 

Is this the line I need? 0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wirelesss (rev 03)?

---

### Post by agim on 2008-01-28
No, thats not the line you need. Feel free to post the entire output.

Ndiswrapper can be found here: [http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/) . Though again, if possible I would suggest getting 7.10.

---

### Post by mrgreg on 2008-01-28
There is no line that says line that says Network or wlan or both??

---

### Post by agim on 2008-01-28
Its alright, as I said, just post the entire output of lspci.

Edit: Oh my god I need to pay more attention. Yes that last line is your wireless card.

I will see if I can help you find the drivers.

Your wireless card is 88w8335 [Libertas] 802.11b/g Wirelesss (rev 03). We will need to download the drivers (you can look on google, I will also) and then use ndiswrapper to make it work with your system.
We are on the right path.

---

### Post by Zars on 2008-01-28
Have you checked your restricted driver menu? Just worth checking.

This site suggests that ndiswrapper will help your case

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_0-9/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_0-9/")

Although I would recommend getting Gutsy for the Xubuntu distro. It have far greater driver support.

If you need to use 6.10,you can download ndiswrapper here at [http://sourceforge.net/project/showfiles.php?group_id=93482]("http://sourceforge.net/project/showfiles.php?group_id=93482") and it is well documented over the internet.

Let us know how it goes.
Zars.

Edit: Just found this, might come in handy: [http://www.encore-usa.com/download/driver/ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip]("http://www.encore-usa.com/download/driver/ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip")

---

### Post by mrgreg on 2008-01-28
Just one more question? how do I check my restricted driver menu?

---

### Post by agim on 2008-01-28
Good find zars. I think thats it. 

So mrgreg, download the link that zars provided and ndiswrapper and get them onto your linux machine.

You can find the restricted drivers menu in the main menu bar (top left of the screen) then you will look for something like System, from there you should be able to see it. I use Ubuntu, so I can't tell you exactly how in Xubuntu. In mine its System-Administration-Restricted Drivers Manager

Out of curiousity, is there a reason you don't want to try xubuntu 7.10?

---

### Post by mrgreg on 2008-01-28
I am downloading now... I read in a post that 6.06.1 worked well in the IBM thinkpad 600e. I am going to install the newer version in the morning and hopefully I won't have to mess around with ndiswrapper. Thanks for all you help I will give it a go in the morning.

---

### Post by Zars on 2008-01-28
Let us know how it goes :D and welcome to the Xubuntu/Ubuntu world :P

---

