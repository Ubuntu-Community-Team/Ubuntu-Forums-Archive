---
title: "Tiscali Internet Connection Broadband"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by Benontheroad2006 on 2006-11-30
Hello, I have installed ubuntu 6.06 dual booting with xp sp2 and I need to connect to the internet

I have a Thomson speedtouch 330 Modem and my broadband ISP is Tiscali

I have downloaded the linux drivers for the modem and they appear as .eni files - 

A. I logged into ubuntu and double clicked the .eni files on my external HDD and they would not open - some sort of error message -  how do I open and install them?

B. I followed the following instructions to try and setup the internet connection :

1. System>Administration>Synaptic Packet Manager
2. Scroll down left hand menu. Click on Networking.
3. In right hand box, mark 'eagle-usb-data' and 'eagle-usb-utils' for installation.
4. Stick the Ubuntu installation CD in the drive.
5. Click Apply
6. The system should then install these two packages from the CD.
6.5 Plug in your modem.
7. Go to Applications>System Tools>Root Terminal. (Don't do what I did the first four times I tried this and go to Applications>System Tools>Terminal. You need to be in root to make it work.)
8. At the prompt type in 'eagleconfig'. This will give you a list of options for different ISPs. You'll see Tiscali at the bottom as 'UK01'
9. Type in 'UK01'
10. At the prompt, type in your ISP username
11. At the prompt, type in your ISP password
12. At the prompt about encryption, say 'no'
13. At the prompt about startup on boot, say 'no'
14. You should then get a message saying that configuration was successful.
15. Type 'startadsl'
16. Go to System>Administration>Networking
17. Double click on 'Ethernet connection eth01'
18. Tick the 'This device is configured' box'
19. Change the Connection Settings Configuration drop down from 'Static IP Address' to 'DHCP'
20. Click 'OK'
21. This takes you back to the first dialogue box.
22. Make sure that 'Ethernet connection eth01' is highlighted and then click on 'Activate' 

BUT - I got an error at point 14 - Loading DSP & options... [ Error ]

Can anyone help? All help is appreciated! I have read through the posts and seen that buying an adsl router would help but I want to stick with the free USB Modem I have been given :)

Sorry for the long post but I do want to get onto the internet

Thanks

---

### Post by vikingprincess on 2006-11-30
Can't help you with the connection problem unfortunately. No doubt somebody else can though. 

I just want to suggest that you THINK TWICE before committing to Tiscali as an ISP. They are really unpopular here in the UK, and I do not think that many techies would be with them volountarily.  They throttle/choke bittorrent downloads, have appalling customer service and don't deliver the speeds that you pay them for. Also more than average outages etc. All according to ADSL guide. 

(I found this out after Tiscali bought the ISP that I am with. Luckily the purchase has not affected my own ISP yet, but if it does, I'll go elsewhere immediately. See ADSLguide for other alternatives assuming you are in the UK too)

---

### Post by gn2 on 2006-11-30
This may help: [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch?highlight=%28adsl%29](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch?highlight=%28adsl%29)

I can't stress strongly enough that you should ditch it and get a router.

Better performance more reliable, and better security if you get one with a hardware firewall.

My own recommendation would be a Netgear DG834, or DG834G if you want wireless.

---

### Post by Benontheroad2006 on 2006-11-30
Thanks for the advice 1) just signed up with Tiscali so hope they are not as bad as you reckon, 2) checked out the link (thanks) I will have a go at following the instructions tomorrow

---

### Post by gn2 on 2006-11-30
If it's at all possible I would agree with other posters (here and elsewhere) and suggest you don't complete with Tiscali, they're simply awful.

---

