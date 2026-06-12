---
title: "Superier confusion. Please help."
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by bitdefuser on 2006-08-03
I installed Ubuntu, I tried connecting my wireless internet and it wouldn't work. Even the wired Ethernet connection would't work. So, I decided to install windows again. I looked for my HP factory cd which took me an hour. Then I had to format, install windows and my other programs. It was 4 hours in hell. It's hot down here so, that made everything worser. :( 

Oh, by the way, I have a Wifi(?) button which I have to push. It turns blue once it's on but, it doesn't work with Ubuntu.
Laptop Model: HP Compaq nx6110

I need drivers for:

[LIST]
[*]bcm94306mplna known as HP Broadcom 54g MaxPerformance 802.11g

[*]Mobile Intel® 915GM/GMS, 910GML Express Chipset Family (My video driver)

[*]HL-DT-ST DVD-RW GWA-4082N (Long for GWA-4082N [my cd/dvd drive, burner too.])

[*]Intel M Processor 1.73 Ghz (My processor)

[*]Broadcom 440x 10/100 Intregrated Controller (Maybe similar to my 802.11g?)

[*]SoundMAX (My audio driver)

[*]Agere Systems AC'97 Modem (My dail-up which I don't use.)
[/LIST]

Thank you all. :)

---

### Post by cantormath on 2006-08-03
> **bitdefuser said:**
> I installed Ubuntu, I tried connecting my wireless internet and it wouldn't work. Even the wired Ethernet connection would't work. So, I decided to install windows again. I looked for my HP factory cd which took me an hour. Then I had to format, install windows and my other programs. It was 4 hours in hell. It's hot down here so, that made everything worser. :( 

Laptop Model: HP Compaq nx6110

I need drivers for:

[LIST]
[*]bcm94306mplna known as HP Broadcom 54g MaxPerformance 802.11g

[*]Mobile Intel® 915GM/GMS, 910GML Express Chipset Family (My video driver)

[*]HL-DT-ST DVD-RW GWA-4082N (Long for GWA-4082N [my cd/dvd drive, burner too.])

[*]Intel M Processor 1.73 Ghz (My processor)

[*]Broadcom 440x 10/100 Intregrated Controller (Maybe similar to my 802.11g?)

[*]SoundMAX (My audio driver)

[*]Agere Systems AC'97 Modem (My dail-up which I don't use.)
[/LIST]

Thank you all. :)

Its gonna be alot easier to help you with the problem if you have it installed on the laptop.  Sometimes wireless takes alittle tweaking to get going the first time, either that, or you need to know how to do it.

---

### Post by bitdefuser on 2006-08-03
It was installed on the laptop until I removed it and switched it back to Windows.

---

### Post by GuitarHero on 2006-08-03
So what drivers are you looking for?  If you are asking for windows drivers we wont hunt those down for you....  If you still want to get ubuntu to work we can help, but a start would be putting ubuntu on a computer.

---

### Post by bitdefuser on 2006-08-03
I'm lookin for Ubuntu drivers.

I cannot install Ubuntu yet, I need drivers. I have no other computer besides this laptop which I am on right now. (Same one used for Ubuntu installation and useing again.)

---

### Post by GuitarHero on 2006-08-03
Well than that's going to be tough.  You'll have to go to the network card manufacturers website and see if they have linux drivers available.  If not, you could try ndiswrapper.  Ndiswrapper is a program that lets you use windows drivers with linux.  Search the forums for it.

---

### Post by nickpaton on 2006-08-03
Hi Bitdefuser

Sorry to hear of your problems, however the good news is that you do not need to obtain any of the listed drivers for Ubuntu.

This is due to them being automatically detected as the distro loads,

Also, I've used Breezy in the past and now am on Dapper, it loaded V quickly on this HP NX6125 laptop.

Just make sure that you add "vga=791 noapic nolapic" to the boot menuu when you press F2 (I think) when you are asked to make choices.

Also, to stop your laptop from overheating, I went into the bios and permanently enabled the fan when on AC (hopefully yours will have the same).  

As you load the CD make sure you have your LAN cable connected since it should be automatically detected and then subsequently connected to your router / network straight out of the box.

From then on getting your Windows drivers should be straight forward.

In case you don't know your Windows drivers are available on HP's website at:

[http://h18007.www1.hp.com/support/files/hpcpqnk/us/family/model/6133.html?lang=en&cc=ca&prodSeriesId=449877](http://h18007.www1.hp.com/support/files/hpcpqnk/us/family/model/6133.html?lang=en&cc=ca&prodSeriesId=449877)

From there you will need to specify the actual OS and they are all there.

If you are really stuck and live in the UK, PM me and I'll send you them on a CD.

Hope this answers your query and if not please get back to us - we're here to help! :)

---

### Post by bitdefuser on 2006-08-03
I have window drivers. Everything works 100% perfect on windows.
It's just that I want to burn all the drivers on one cd with intructions and everything so I won't have to install windows again and come back to this forun asking again.

---

### Post by vincentvee on 2006-08-03
i have never had a problem with installing linux on an HP computer.....is all that stuff original equipment or did you add it in after you bouoght it?
i had always thought HP was linux friendly in that regard.
the drivers you should need to make everything work should be on the HP website somewhere or you could look at [linux drivers website here]("http://www.linux-drivers.org/notebooks.html")

---

### Post by bitdefuser on 2006-08-03
If I give someone all my system specs, can you create an ISO image for me and upload it so I can simply burn it and install.

That would be super nice. :)

---

### Post by bitdefuser on 2006-08-03
I have all the specs ready.

---

### Post by nickpaton on 2006-08-03
I completely agree with having a set of drivers on CD but why not do it yourself?

Is there any part of the process for doing this you don't understand - let us know & we're happy to assist.

Also you increase your Ubuntu knowledge.

I've never bothered to get any bespoke Linux drivers for my laptop since it all worked out of the box so to speak, so still can't get my head around why you need to burn a CD.:-)

---

### Post by bitdefuser on 2006-08-03
I have no other access to the internet other than my laptop.

When you install Ubuntu, you can't access the internet without the wireless drivers. If I can at least get the wireless drivers for bcm94306mplna known as HP Broadcom 54g MaxPerformance 802.11g, I will be fine.

---

### Post by bitdefuser on 2006-08-03
CLOSE UP:
[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=8805700261&category=31534&ssPageName=STORE:PROMOBOX:NEWLIST#ebayphotohosting](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=8805700261&category=31534&ssPageName=STORE:PROMOBOX:NEWLIST#ebayphotohosting)

Do not bid. It's just my wireless card model. Not my bid.

---

### Post by bitdefuser on 2006-08-03
So, can someone find a driver for me? :( Please?

---

### Post by sguart on 2006-08-03
have you try googling all these informations that you need yourself first?!

just googling "linux driver bcm94306" comes up with lots of the links...
the 1st link looks like it will be a good starting point... it has wireless section using ndiswrapper and winxp drivers...

[http://bnmr.triumf.ca/~zaher/Presario_2197CA/]("http://bnmr.triumf.ca/~zaher/Presario_2197CA/")

you should also check the howto forum, link such as this seems to be related to your problem. (howto setup broadcom wireless without ndiswrapper) [http://www.ubuntuforums.org/showthread.php?t=185174]("http://www.ubuntuforums.org/showthread.php?t=185174")


good luck,

---

### Post by nickpaton on 2006-08-04
Assuming you have wireless working OK on your XP distro, then you should already have the bcm94306 driver.

The files you need are bcm94306.ini and bcm94306.sys files, and this is how to find them on your XP distro:

On **_XP_** to to Start>Search>All files and folders.

In the section on the left hand side - "Search by any or all of the Criteria below.", below the box "All or part of the file name:", type "bcm" (no" "'s), and make sure you are looking in your hard drive not just My Documents.  Continue "Search".

This should bring up many results with variations on "bcm".  My wireless card uses Broadcom driver bcm4318 (I think!), but the .ini and .sys files I use are:

bcmwl5.ini  (that is lowercase L not figure 1 BTW!); file size approx 600k
bcmwl5.sys; file size approx 363k

These files are located in a number of places within XP OS, typically (on my HP laptop) C:\Swsetup\WLAN, C:\WINDOWS\system32\drivers, but will vary from laptop to laptop (as sguart shows with a slightly different location!).

Now make a copy of these files and transfer them into your Home folder within Ubuntu.

Referring to Sguart's excellent post, use the second link " How to: Broadcom Wireless cards", and use that.

Since you already have your correct driver, you should be able to carry on getting your wireless section to work.

Good luck and get back with any problems!:)

---

### Post by drtvasudevan on 2006-08-04
> **bitdefuser said:**
> I have no other access to the internet other than my laptop.

When you install Ubuntu, you can't access the internet without the wireless drivers. If I can at least get the wireless drivers for bcm94306mplna known as HP Broadcom 54g MaxPerformance 802.11g, I will be fine.

excuse me, can i assume you will be dual booting? that is install ubuntu in a separate partition and leaving win xp instact?
in that case you can still see the xp partition and access to leach any driver you want.
thus not having any other access to internet is not a problem.
you can always boot into xp.
i hope this helps.
:cool:

---

### Post by bitdefuser on 2006-08-04
You can Access the windows partation from the linux?

If so, can I always delete either partation and put it back into one?

---

### Post by kurniawands on 2006-08-04
> **bitdefuser said:**
> I installed Ubuntu, I tried connecting my wireless internet and it wouldn't work. Even the wired Ethernet connection would't work. So, I decided to install windows again. I looked for my HP factory cd which took me an hour. Then I had to format, install windows and my other programs. It was 4 hours in hell. It's hot down here so, that made everything worser. :( 

Oh, by the way, I have a Wifi(?) button which I have to push. It turns blue once it's on but, it doesn't work with Ubuntu.
Laptop Model: HP Compaq nx6110

I need drivers for:

[LIST]
[*]bcm94306mplna known as HP Broadcom 54g MaxPerformance 802.11g

[*]Mobile Intel® 915GM/GMS, 910GML Express Chipset Family (My video driver)

[*]HL-DT-ST DVD-RW GWA-4082N (Long for GWA-4082N [my cd/dvd drive, burner too.])

[*]Intel M Processor 1.73 Ghz (My processor)

[*]Broadcom 440x 10/100 Intregrated Controller (Maybe similar to my 802.11g?)

[*]SoundMAX (My audio driver)

[*]Agere Systems AC'97 Modem (My dail-up which I don't use.)
[/LIST]

Thank you all. :)

for your wi-fi problem try using ndiswraper

---

### Post by bitdefuser on 2006-08-04
Ok, thanks. But, can someone aswnser my last question?

---

### Post by bitdefuser on 2006-08-04
[https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6110?highlight=%28nx6110%29](https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6110?highlight=%28nx6110%29)

Also, my dim and undim keys don't work either....

---

### Post by nickpaton on 2006-08-04
> **bitdefuser said:**
> You can Access the windows partation from the linux?

Yes, you'll see the Windows XP partition on the desktop. 


> **bitdefuser said:**
> If so, can I always delete either partation and put it back into one?

Again yes - there's lots of forum posts about this.

---

### Post by nickpaton on 2006-08-04
> **bitdefuser said:**
> [https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6110?highlight=%28nx6110%29](https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6110?highlight=%28nx6110%29)

Also, my dim and undim keys don't work either....

I suggest that you do a search within the Laptop Section of these forums, and if nothing found to then post that question there.

Note that whilst we are happy to help, the answers to most of your queries could have been found in old posts within these forums.

---

