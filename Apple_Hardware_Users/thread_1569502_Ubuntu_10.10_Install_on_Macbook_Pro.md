---
title: "Ubuntu 10.10 Install on Macbook Pro"
date: 2010-09-06
forum: Apple Hardware Users
---

### Post by bash321 on 2010-09-06
I have got some problems installing Ubuntu 10.10 Beta on my Macbook Pro

I have the daily  release from Monday 6th September:

My Current Issues are that i can boot with modeset in my grub entry once i have installed it on my macbook pro 5.1. The problem i have is that my network manager doesnt start when I boot using startx or using the modeset option. I cannot not get a connection to the internet even with an ethernet connection on my macbook.

How do i start the network manager?? so that i can get a connection to the internet?

bash321

---

### Post by hipstersandwich on 2010-09-06
Riddle me this:  Does Ubuntu recognize your network card at all?

---

### Post by hipstersandwich on 2010-09-06
Also, see [http://ubuntuforums.org/showpost.php?p=9812329&postcount=6](http://ubuntuforums.org/showpost.php?p=9812329&postcount=6)

---

### Post by bash321 on 2010-09-06
on all other versions of ubuntu that i have had on my computer including 10.04 it recognised the wired network card but it never recognised the wireless one. It now cannot recognise the wired network. Meaning network manager isn't running. Or is running as a processor. i tried to restart the network manager process but it told me it was there! I  then tried to kill the process no and it said it didnt exist!

---

### Post by bash321 on 2010-09-06
it seems that it doesnt when i boot up, it did in all the other versions of ubuntu except for 10.10

Here is the error code displayed at boot.

 (6.172244) b-43-ph 0 Error Found unsupported (Analog 8,type 4,Revision 4)

b43 is my broadcom driver for wireless im not sure about wired though, but then it must be!

---

### Post by bash321 on 2010-09-06
then i have the nouveau driver error underneath it then it hangs, cause i dont have the nvidia graphics installed, is there any way to change the driver using the live cd to the vesa driver instead of nouveau?

the only solution is nomodeset to boot into graphical interface.

---

### Post by bash321 on 2010-09-07
but i still dont have an ethernet connection when i am logged in the system.

---

### Post by hipstersandwich on 2010-09-07
Use the driver from the live CD.

---

### Post by bash321 on 2010-09-07
where is the driver found on the live cd so that i can transfer it to my hard drive?

---

### Post by hipstersandwich on 2010-09-07
Look up broadcom.

---

### Post by larrinski on 2010-10-25
Don't mean to bump an old thread, but has anyone been able to find a solution to this problem? I have a perfectly good 10.10 install on my Macbook Pro 5,5, but have no network connectivity...It's useless until I do...

---

### Post by bash321 on 2010-10-25
the solution should of been found in the stable version of 10.10, the best way to boot the live cd is to have the option selected no modesetup 
i think that is the option for macbook pro,
it then should detect your ethernet hardware.

you need to have your ethernet hardware on first then install your wireless drivers via the hardware drivers in system administration additional drivers

---

### Post by vsh3r on 2010-11-01
Hi,

I have a Macbook Pro 6,2 and had a similar issue with a fresh install of the Ubuntu 10.10 CD ROM (Live CD).  Ubuntu doesn't detect the drivers correctly for the newer Macbook Pro's yet and some other non-mac systems from what I've read about on the forums.  The newer Macbook Pro's (like the i5 models) require that you update the wireless drivers with:

SOLUTION: (update drivers with Broadcom Proprietary)
system->administration->additional drivers

Ubuntu has an issue with BCM43XXX drivers.  

V$H.

---

### Post by larrinski on 2010-11-07
My problem is that I can't update via system->administration->additional drivers as when it loads the drivers I am missing and I select Activate, it tries to connect to the internet, which of course I can't...Catch 22. If I just had ethernet access, I would be done, but I don't. Ugh.

---

### Post by linuxopjemac on 2010-11-07
larrinsky: connect your Mac to the internet with a cable. Then:
```
sudo apt-get update
sudo apt-get upgrade
```

Then System -> Hardware Drivers. Select the Broadcom proprietary driver. Enjoy.

---

### Post by larrinski on 2010-11-07
> **linuxopjemac said:**
> larrinsky: connect your Mac to the internet with a cable. Then:
```
sudo apt-get update
sudo apt-get upgrade
```

Then System -> Hardware Drivers. Select the Broadcom proprietary driver. Enjoy.

I wish it was that simple. When I plug in the ethernet cable, it times out trying to connect. I see the auto eth0, but can't get any wired connection.

---

### Post by itismike on 2010-11-08
@larrinski: Sounds like either your network is misconfigured, or your network settings in Ubuntu have been fiddled with. Can you test that physical network port with another machine to be sure the connection is available?

---

### Post by larrinski on 2010-11-09
> **itismike said:**
> @larrinski: Sounds like either your network is misconfigured, or your network settings in Ubuntu have been fiddled with. Can you test that physical network port with another machine to be sure the connection is available?

I plugged in the ethernet cable while still in OSX, and after a bit of rebooting the cable modem, the ethernet connection came up! So, I rebooted and it ran great! Did all the updates and rebooted again. I was able to connect to my wireless network successfully(or so it said), but I can't get an IP address for some reason...I tried to disconnect/reconnect etc. but can't get one. Any idea what now? Is there a terminal command to force an IP address?

Thanks for all the help!

**Edit - I am using an Apple Airport Extreme basestation**
**Edit - Well nevermind! For some reason, my most recent reboot seems to be working, and I am posting now from my wireless connection...Woot.

---

### Post by itismike on 2010-11-10
Woot, indeed! 
:guitar:

---

### Post by poundplay on 2010-12-27
dude i had the b43 driver that worked in 9.10 and 10.4 but after i install it i have to plug in the hardwire then pull it and thern the wireless works help!!!!!!!! mbp 7.1

---

### Post by itismike on 2010-12-27
Hey buddy, you're gonna have to be a little more descriptive if you're looking for help. Are you saying you have to do this with each boot/sleep?

---

### Post by poundplay on 2010-12-28
yes every time i turn it on. its a mac book pro 7.1 i got it summer 2010. 13 inch. it happens every time i leave ubuntu. its basically saying it has lost the driver. it says its installed but it doesnt even look for wireless. but when i remove then reinstall it says it cant find the driver

---

### Post by phatqao on 2011-01-02
> **linuxopjemac said:**
> larrinsky: connect your Mac to the internet with a cable. Then:
```
sudo apt-get update
sudo apt-get upgrade
```Then System -> Hardware Drivers. Select the Broadcom proprietary driver. Enjoy.

Thank you! This worked for me with no issues. Very helpful.

---

### Post by poundplay on 2011-01-02
dude again i cant do that. there is no internet.

---

### Post by poundplay on 2011-01-03
i dont always have a hardwire around to do that every time i log on. does anyone know a way i can install it manually.

---

### Post by itismike on 2011-01-03
@poundplay: Here are a couple pages on manually installing wireless drivers, but as the first link indicates, this should not be necessary on your 7,1. Is your wireless stable when booted to your Mac OS?

[https://help.ubuntu.com/community/MacBookPro7-1/Maverick](https://help.ubuntu.com/community/MacBookPro7-1/Maverick)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by poundplay on 2011-01-03
oh yes. in fact on windows and osx its completely stable.

---

### Post by itismike on 2011-01-03
That seems quite odd. Did you make modifications after installing? 

Other than the links above I'm not sure what else to suggest. Even if you put in a live 10.10 CD and enable restricted drivers, I think it'd have to reboot to activate it, obviously loosing the updates.

---

### Post by poundplay on 2011-01-03
yeah i think that is what is causing the problems. cause when i had the b43 cutter it worked for a sec. i had the sta which is the right one. it only worked till i turned it off. and after the right driver i would have to shut down then turn on again to get the hardwire to even read. yeah. no thanks. 10/10 not for me.

---

