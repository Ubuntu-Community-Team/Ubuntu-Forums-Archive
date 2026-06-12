---
title: "monitor &amp; modem issues"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by DonDodge on 2007-12-20
Hello, I installed the x86 version of Gutsy Gibbon on my compute.

First thing I notice is any display resolution higher than 1024x768 gives me pinstripes of rapidly moving vertical dashed lines about an inch apart. I like my monitor to display 1152x864. It's no problem in windoze xp. Any suggestions?

On to the dialup internet connection. I can connect/disconnect to my ISP  with pon/poff but that's as far as I go. I can't connect the browser to any website. Just reach an error page no matter where I go.  The connection is set up as closely to windoze as possible. My ISP wants DNS and IP to be issued automatically. What's up with this?

Finally, although pon/poff in a terminal does work to dial , I'd like to have a better way. The dialup HowTo says put the Modem Lights panel-application in the top panel. I don't have Modem Lights available. The button I have is  called Modem Monitor. I'm assuming it the same thing but it doesn't work. I have the properties set as accurately as possible but it's a dead button. Does absolutely nothing. Any help here?

---

### Post by jken146 on 2007-12-20
For your resolution problem, what graphics card do you have?  Have you considered enabling the restricted drivers for it?  Also it may just be a case of you choosing the wrong refresh rate for this resolution -- read your monitor's documentation.

---

### Post by scottym on 2007-12-20
It sounds as if your user name and password are not being transmitted. I have had better luck using wvdial than ppp. With both of these you have to configure the files for them by using the command pppconfig in terminal. You must sudo the command to run the utility and you will need your isp's ip address which you can by searching on Google or perhaps from your windoze settings. After that configure wvdial and then go on line using wvdial and you should have access to your isp and the internet. If you still have trouble go to system>accessories>network and make sure that you have the right configuration for your system. To disconnect wvdial you do Control C. While you are connected get Gnome ppp which is a better dial tool than the one that is in the default menu. 

You can also try downloading the Gnome ppp dialer with your windoze system and then installing it in your Ubuntu OS. It will allow you to configure your password, user name and telephone number to connect. 

Using a modem seems to be of the more frustrating things about Ubuntu perhaps because most users are fortunate enough to have wireless high speed. Too pricey for me so I deal with the frustration but believe me it is worth it to have Ubuntu.

---

### Post by DonDodge on 2007-12-20
Thanks.

The graphics card is on motherboard Intel 82815. I don't think refresh rate is an issue as it seems to be non-negotiable in ubundu. Sorry but I don't know anything about enabling restricted drivers in unbuntu. I'll have look and see if I can figure that one out.

I've downloaded gnome ppp and vwdial. I have a feeling, from looking at the gnome dialer page, it has some additional parameters that will help me out.

I'll go back to ubuntu and see how this works.

---

### Post by DonDodge on 2007-12-20
So, when I started ubuntu this time, my computer started connecting to the internet before I even logged on to ubuntu :confused:. Now I'm able to access websites but it's slow as christmas. Will install the gnome dialer and see what's up.

Edit: Funny thing, neither poff or ctrl c disconnects me now so I wonder what connected me? Surely couldn't have been pon. Seems like I remember reading about an automatic internet connection occurring upon system logon.

Regarding the display: The restricted drivers manager says my hardware doesn't need any. The refresh rate of resolution 1152x864 is non-negotiable at 75 mhz.

---

### Post by DonDodge on 2007-12-20
Okay, I'm stuck.

How do I make ubuntu stop automatically connecting through dialup before I even get logged on to ubuntu? And when that happens, how can I disconnect it poff doesn't work?

How do I clean up the dialup connection so it at least approaches the speed of windoze? With windoze, I download at over 5 Kbps. With ubuntu, I'm only getting a max of 3.3 Kbps.

Why is it when I connect with Gnome PPP I'm always left at a little window that says it's still authenticating even though it's connected. This discrepancy leaves me with two steps to complete before I can disconnect.

Any idea why the panel-app "Modem Monitor" is nothing but a dead button? The only life within it is a message that says "Could not get connection time" when I lay ther mouse cursor on it.

How do I make ubuntu run my monitor at resolutions that work just fine in windoze? Refresh rate isn't adjustable for the higher resolutions and the system tells me my hardware doesn't need any restricted drivers.

Thanks,
Don

---

### Post by scottym on 2007-12-22
> **DonDodge said:**
> Okay, I'm stuck.

How do I make ubuntu stop automatically connecting through dialup before I even get logged on to ubuntu? And when that happens, how can I disconnect it poff doesn't work?

How do I clean up the dialup connection so it at least approaches the speed of windoze? With windoze, I download at over 5 Kbps. With ubuntu, I'm only getting a max of 3.3 Kbps.

Why is it when I connect with Gnome PPP I'm always left at a little window that says it's still authenticating even though it's connected. This discrepancy leaves me with two steps to complete before I can disconnect.

Any idea why the panel-app "Modem Monitor" is nothing but a dead button? The only life within it is a message that says "Could not get connection time" when I lay ther mouse cursor on it.

How do I make ubuntu run my monitor at resolutions that work just fine in windoze? Refresh rate isn't adjustable for the higher resolutions and the system tells me my hardware doesn't need any restricted drivers.

Thanks,
Don

n.t been fixed.

I had the same problem with auto connects and it turned out that I had the auto update time option enabled.Right click on your date /time and select 'adjust time' to check yours. The ppp dialer is the culprit here so you will have to use the terminal command sudo poff to disconnect. After that you can use the Gnome ppp or Wvdial  program. I have never gotten the modem monitor to work with any of the Ubuntu versions I have used. It apparently has known bugs but has never been fixed.

Can't help with the graphics issue.

Are you using Firefox to connect. If so there are adjustment you make in FF. Do a search on Google or here and you should get plenty of hits. My laptop w/ Ubuntu is noticeable faster on the internet than the desktop w/ Windoze despite the fact that the desktop claims to connect at a faster speed.

---

### Post by DonDodge on 2007-12-23
Thanks Scotty. The time update function wasn't the problem causing the autoconnect thing but it fixed itself while doing all the ubuntu updates. The display issue resolved after I crashed the x server and reconfigured xorg.

I'll search around for the Firefox fix you mention but I've checked out the settings and everything seems to be good. Nice to know Modem Monitor is a useless program and it's not just me.

Did you have a hard time getting your laptop modem to function?

---

### Post by scottym on 2007-12-23
I never got the laptop modem to work because it has a winmodem which it turns out is not supported by Ubuntu. I worked for weeks stubbornly trying to get it to work and finally broke down and bought a 56k modem card and voila after going through what you have just gone through got connected. My laptop is an IBM thinkpad and and works quite well with Ubuntu. 
Scotty

---

