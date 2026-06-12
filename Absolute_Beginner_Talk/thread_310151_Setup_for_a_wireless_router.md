---
title: "Setup for a wireless router"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by man-man on 2006-11-30
I know this probably gets asked plenty (I did try a search, but none of the topic titles sounded specifically relevant)

I'm not actually able to install Ubuntu just yet because of lack of hard disc space (going to get a bigger one soon) but I'd kinda like to know how to set the wireless connection up on the live CD, I assume its the same process as if it was installed so when I do install it it'll be good to know what I'm doing.

I'm fairly sure that I'll know all the various bits of information that it needs (setting this thing up on Windows was a bit of a pig so I got to know a lot of the settings) I just need to know where in the administration menus to enter it all in, and what I need to do with activating the connection and.. well, I guess any linux-specific ways of doing things would be good to know, so I don't spend all my time searching for folders with similar names to the Windows equivalents

oh, hardware/version info, almost forgot
Its a linksys WGA354G wireless modem-router, plugs straight into the phone line
Then the computer (a laptop) receives the signal wirelessly through a built in network card
The live CD in question is Ubuntu, either Dapper or Edgy (I have both CDs, not sure of which I want to use/install. If one is easier to set up then that could sway me towards that one ;)

---

### Post by Tilex on 2006-12-01
First of all, you have to know what kind of encryption you're using on your wireless network.  Usually it is WEP (and it's easier to set because with WPA you would need another program).  I am not sure if there is a wireless assistant that comes on the live CD but if not, you should be able to go in your System Settings (in the menu) and check your Network Settings.  Then, by clicking on you're wireless card (which should be named 'eth1') change the settings that apply to your network, i.e. specify the name of the network (SSID), the type of encryption (WEP,if any) and the password (key).  

I am using KDE (Kubuntu) so it might be different with Gnome (Ubuntu) but still, give it a shot.  Hope you'll enjoy this great distro! :)

---

### Post by man-man on 2006-12-01
hmm, less complicated than I was expecting, which is good :mrgreen:
I'll try that and see what happens

---

