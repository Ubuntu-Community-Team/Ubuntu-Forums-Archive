---
title: "Audio loss over HDMI"
date: 2012-07-04
forum: Any Other OS
---

### Post by kopchoir on 2012-07-04
Hi 
I wondered if some of you nice people could help me i have always used windows and im seriously thinking of going back to it.
Im new to ubuntu and currently running Mint maya i have picked up a machine for primiarily xbmc.
I have scoured the net and im currently lost,im new to terminal and all the codes,im slowly getting the hang of it.
Quick break down 
I cant get any audio via HDMI on my TV worked fine yesterday when i had windows installed.
I have an inbuilt Nvidia MCP78 card tried unmuting in alsamixer but no joy.
Can anyone help me im been really impressed with the quickness of Mint and i want to keep it.
Seems there are many people with the same problem but i need a noob friendly guide for someone new to ubuntu and terminal.
 
Cheers
 
Kop

---

### Post by jmfal on 2012-07-04
Welcome to Ubuntu

Open the alsamixer and  unmute and increase the  s/pdif controls.

Open up the sound settings and click on the "digital" card. 

You may need to restart your TV after making changes.

---

### Post by kopchoir on 2012-07-04
> **jmfal said:**
> Welcome to Ubuntu
 
Open the alsamixer and unmute and increase the s/pdif controls.
 
Open up the sound settings and click on the "digital" card. 
 
You may need to restart your TV after making changes.
 Hi there thanks for the welcome.
I have opened alsamixer v1.0.25 and unmuted everything there is no option to increase nor decrease S/pdif controls there is no meter.
All Master PCM MIC  mic boos and beep are up full.
When i go into alsamixer sound card via the f6 key it gives me 2 options
-(default)
0 HDA Nvidia
enter device name 
 
I thought it might be the fact that it says 0 HDA Nvidia instead of 1 HDA nvidia??

---

### Post by jmfal on 2012-07-04
Try pressing F5 and use the right arrow, sometimes there are more controls that can't be seen till you navigate farther to the right.

---

### Post by kopchoir on 2012-07-04
> **jmfal said:**
> Try pressing F5 and use the right arrow, sometimes there are more controls that can't be seen till you navigate farther to the right.
 Hi no all controls are unmuted and everything is turned up full.

---

### Post by jmfal on 2012-07-04
You can try changing sound cards, maybe the s/pdif will show up.

I don't use hdmi  so this is as far as I can help you.

Try looking at the stickies in the multimedia section of the forum ..

---

### Post by kopchoir on 2012-07-04
> **jmfal said:**
> You can try changing sound cards, maybe the s/pdif will show up.
 
I don't use hdmi so this is as far as I can help you.
 
Try looking at the stickies in the multimedia section of the forum ..
 Cards fine as it works flawlessy with windows and xbmc.
Have searched so many threads and seen lots of ways to do different things,seems its a regular problem with Nvidia and Linux.
But i just cant get it sorted and i really dont want to go back to windows

---

### Post by Perfect Storm on 2012-07-04
Moved to Other OS/Distro Talk.

---

### Post by mitanc on 2012-07-06
> **kopchoir said:**
> Cards fine as it works flawlessy with windows and xbmc.
Have searched so many threads and seen lots of ways to do different things,seems its a regular problem with Nvidia and Linux.
But i just cant get it sorted and i really dont want to go back to windows

I have an ion2 card with my lenovo q150.  The newest version of ubuntu picked up everything alright.  To get my digital sound for DTS and Dolby I had to add a custom device.  Do a search for Lenovo q150 hdmi sound in google, tons of info there.

Good luck!

---

### Post by MadmanRB on 2012-07-07
Maybe you should use analog connections, HDMI can be a bit troublesome in linux depending.
I know analog is considered "outdated" but if it works use it and dont be a HD snob.

---

### Post by gordintoronto on 2012-07-08
Run System Settings, Sound. The Hardware or Output tab should show you an HDMI device. Maybe.

I think the MCP78 actually describes your motherboard, right? If you open Terminal and enter this command:
lspci

it should show all your "pci" devices, including any audio devices. Could you copy/paste that output?

I use Maya and have experience with HDMI devices. Other people who have responded to you want to be helpful, but....

---

