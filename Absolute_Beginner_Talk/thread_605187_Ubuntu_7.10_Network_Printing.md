---
title: "Ubuntu 7.10 Network Printing"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by paulbeattie87 on 2007-11-06
Just starting off with Ubuntu tonight but hit a bit of a snag.

Setting up the computer to be moved elsewhere and what to get everything tested before I install it for good. Managed to get through all of the harder bits e.g. Real player...

One thing has stumped me and its network printing. I simply cannot do it when I choose the samba option the network doesn't display the computers but the network my home router sets up and thats the only one. Only problem is the printer I need is not in the workgroup setup by the router.

I have a Windows 2000 machine with a shared printer with a workgroup name of "Workgroup" How imaginative! The Printer is a Epson DX5000. Their is a second computer I also need to install the printer on its running on the same network but a different workgroup called "home" the printer I want to use is a Epson Stylus D92. I have looked for driver support both are supported which is a good start.

The problem occurs as I said before when I'm trying to add them. I have looked about the net and most tutorials are for the older versions of ubuntu which installing a network printer on seems fairly easy unlike 7.10! 

All help is gratefully received I have posted on other forums but nobody seems to reply :( .

---

### Post by g2g591 on 2007-11-06
network printing is a difficult topic, therefore fewer people are knowledgeable enough to solve problems (post replies) (even me with my 150 something posts need help [one printer w/o a linux driver on a win 2000 share]

---

### Post by fustanella on 2007-11-06
Can you reach the printer by its computer's local-network IP address? That's what ended up working for me. To wit: Device Url = smb:///192.168.xxx.xxx/printername

---

### Post by paulbeattie87 on 2007-11-06
> **fustanella said:**
> Can you reach the printer by its computer's local-network IP address? That's what ended up working for me. To wit: Device Url = smb:///192.168.xxx.xxx/printername

I tried that but no luck wasn't sure if it was a driver error or if it just never connected. Will be trying it with the Epson DX5000 on Thursday so will be able to report back if that works or not. The two printers I have at home (Epson D92 & Canon Smartbase MP370) are unsupported with any distro. The Epson from reading about on the net looks like it works ok with the drivers supplied with Ubuntu which would be a bonus. 

The other confusing thing was when I read the prompt it asks for a port number, I don't have a clue what the port number would be. I typed into the box "Home/192.168.1.2/EPSONSty". When I turn the other PC on tomorrow morning (later today now) I will try just typing in the IP with printer name and see.

I can see that the networking isn't popular but its the way of life these days, was quite shocked at the lack of support and outdated help their is. It's good to see driver support has taken leaps and bounds in recent years though. Thanks for the quick replies too! :guitar:

---

### Post by paulbeattie87 on 2007-11-07
> **fustanella said:**
> Can you reach the printer by its computer's local-network IP address? That's what ended up working for me. To wit: Device Url = smb:///192.168.xxx.xxx/printername

Thanks that worked a treat, used the D62 drivers and it worked without a hitch, only setting I had to change was on the XP box disabling Bidirection Support otherwise it would just print nothing well several hundred pages of nothing. 

Now to find support for the DX5000 on 2000 and see how it goes tomorrow.

---

