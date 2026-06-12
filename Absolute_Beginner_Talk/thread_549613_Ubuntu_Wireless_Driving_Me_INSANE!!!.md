---
title: "Ubuntu Wireless Driving Me INSANE!!!"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-09-12
:)  After spending what seems like the better part of my life trouble-shooting the installation of my wireless adapter through ndiswrapper (I'm not complaining or anything. I think it's amazing that 
Ubuntu can even operate a wireless adapter with a windows driver) I can see my 
Wireless network. The problem I'm having now is when I tried to connect to it, it ask for a pass-phrase, I entered it only to watch the little blue swishy thing jog laps around the two green dots where my network icon use  to be (in the upper right-hand corner of the top panel) After becoming bored with watching this. I decided to use my Desktop (witch is also running Ubuntu, and running like a CHAMP!!) to talk to you guys it wouldn't get on either now and it's hardwired. So I restarted my computer and loged into Windows to see if this was just a  Ubuntu issue it wouldn't go on either. I went to networking and clicked repair connection it told me it could not be repaired because the 
ip address could not be refreshed. So after wasting like another 15 minutes trying to figure this out I unplugged my router, plugged it back in, clicked repair connection this time it was able to do to fix.
To make sure this wasn't a fluke I tried connecting wirelessly to the network with my laptop again same thing happened again. So now I know for sure that when I try to connect to my wireless router with Ubuntu network-manager it locks the router up and I have to unplug it to get it to work again. So now I log into windows on my laptop with the same pass-phrase and it worked fine. Then I  
logged back into Ubuntu installed the kde wireless-assistant to see if it would do any better. It does not have a wpa option so I switched the security on my router to 124 bit WEP this would not work so I tried 64 bit WEP and now it works fine. The only problem with this is for one I have to open the wireless-assistant every time I log on, and two if I'm going to use 64 bit WEP I might as well pass out flyer's with my wireless key on them. So if any of you guys can give me some help I would appreciate it. I have come to far and, put to much time into this to give up on this now besides that Ubuntu is way too cool for me to give up on now. I think I'm addicted to it. :)

---

### Post by deadgobby on 2007-09-12
What is your WIFI card? What is your system specs? What version on Ubie are you running? Do you have the 32 but kernel or 64 bit kernel? 
Gobby

---

### Post by swoll1980 on 2007-09-12
Running Feisty 7.04, 2.4mz celeron m processor, i386 32 bit, 768mb ram, wireless card is a Trend-net TEW424UB and uses the rt8187b driver

---

### Post by John.Michael.Kane on 2007-09-12
The below threads explain how to enable wpa, As well as Avoiding password nagging.

Under kubuntu
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu](https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu)
Under regular ubuntu.
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

### Post by Paul133 on 2007-09-12
Pretty sure you can enable WPA on (K)Ubuntu. Not sure how though as I use Gnome and WEP. Check the links SD posted and see if your card is supported. Good luck.

---

### Post by swoll1980 on 2007-09-13
I have Ubuntu installing kde wireless assistant was for trouble shooting only. I couldn't find a gnome equivilant so went with kde out of desperation

---

### Post by Harpoon on 2007-09-13
If you want to get back to gnome, the solution might simply be to drop the network manager altogether, and manage your wifi with either wifi-radar or wicd.  A **lot** of people are reporting problems connecting and the bugs are not getting fixed.

Yes, I know, "but it works for me" are going to flood in.  It worked for me, too, but started to get cranky and then downright violent in the past two weeks (can't help but think an update triggered the problem).  

And, I know prople are going to start telling me what cards they use "out of the box."  The problem, however, is not confined to one single chipset.


Just thought I would offer a relatively painless work-around.

---

### Post by BiGGLouie on 2007-09-13
I have the TEW424UB with the Realtek chipset. Got the WinXP driver from Realtek not Trendnet. Works Great with the ndiswrapper that comes with Ubuntu. I just use wep. I also set mine up with a static ip and all that. Mine never asks me for passwords.

---

### Post by igknighted on 2007-09-13
> **bloor75 said:**
> The only problem with this is for one I have to open the wireless-assistant every time I log on, and two if I'm going to use 64 bit WEP I might as well pass out flyer's with my wireless key on them. So if any of you guys can give me some help I would appreciate it. I have come to far and, put to much time into this to give up on this now besides that Ubuntu is way too cool for me to give up on now. I think I'm addicted to it. :)

Ubuntu always asks for passwords to use a stored key... very annoying IMHO.

Do you really fear a 64bit WEP getting broken?  For someone to get mine, they'd have to like park in front of my house to get the signal, and I doubt I'm that high of a target that it would matter.  For most users I feel that this is the case.  Also, if it is of such concern, why not use MAC filtering and disabling of SSID broadcasting.  You could MAC filter and disable SSID broadcasting and for all intents and purposes be perfectly safe, without any encryption.

---

### Post by stchman on 2007-09-13
> **bloor75 said:**
> :)  After spending what seems like the better part of my life trouble-shooting the installation of my wireless adapter through ndiswrapper (I'm not complaining or anything. I think it's amazing that 
Ubuntu can even operate a wireless adapter with a windows driver) I can see my 
Wireless network. The problem I'm having now is when I tried to connect to it, it ask for a pass-phrase, I entered it only to watch the little blue swishy thing jog laps around the two green dots where my network icon use  to be (in the upper right-hand corner of the top panel) After becoming bored with watching this. I decided to use my Desktop (witch is also running Ubuntu, and running like a CHAMP!!) to talk to you guys it wouldn't get on either now and it's hardwired. So I restarted my computer and loged into Windows to see if this was just a  Ubuntu issue it wouldn't go on either. I went to networking and clicked repair connection it told me it could not be repaired because the 
ip address could not be refreshed. So after wasting like another 15 minutes trying to figure this out I unplugged my router, plugged it back in, clicked repair connection this time it was able to do to fix.
To make sure this wasn't a fluke I tried connecting wirelessly to the network with my laptop again same thing happened again. So now I know for sure that when I try to connect to my wireless router with Ubuntu network-manager it locks the router up and I have to unplug it to get it to work again. So now I log into windows on my laptop with the same pass-phrase and it worked fine. Then I  
logged back into Ubuntu installed the kde wireless-assistant to see if it would do any better. It does not have a wpa option so I switched the security on my router to 124 bit WEP this would not work so I tried 64 bit WEP and now it works fine. The only problem with this is for one I have to open the wireless-assistant every time I log on, and two if I'm going to use 64 bit WEP I might as well pass out flyer's with my wireless key on them. So if any of you guys can give me some help I would appreciate it. I have come to far and, put to much time into this to give up on this now besides that Ubuntu is way too cool for me to give up on now. I think I'm addicted to it. :)

My recommendation is to get a 3945 Intel card.  They are about $20 off ebay new.  The Intel wireless cards are very Linux friendly.

---

### Post by macogw on 2007-09-17
> **stchman said:**
> My recommendation is to get a 3945 Intel card.  They are about $20 off ebay new.  The Intel wireless cards are very Linux friendly.

IPW's are internal Mini-PCI and Mini-PCI-E.  The TEW424UB is a USB wifi dongle.

---

