---
title: "how I got my wireless to work"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by joneil1000 on 2007-04-28
I had my wireless working fine under 6.10, but 7.04 knocked things crazy.    I am using an older Toshiba laptop with a Belkin PCIMA wireless card.  I used Ndiswrapper to install the win drivers and all was working fine under 6.10.    

    Anyhow, here is how i got my wireless working.  Your mileage may vary.

1) I am using WEP security.  yeah, i know, but please no lectures on how useless WEP is compared to WPA.  I have 66 - yes, sixty six - wireless networks outside my front door, and 26 of them have no security at all.   So right now, WEP does fine.

2) I installed WIFI Radar.  I had to hook up to the net via cable from my router.

3) Under System-Admin-Network, I brought up ATH0 - which is the Belkin wireless card on my computer - and configured my network for WEP and (hit the "properties" button) and entered my code.  Now here's the thing, if I enter it as ASCII, I cannot connect, but if I set it as Hexidecimal and enter the code, that works.

4) Now here's the weird part.   I go into WIFI Radar, find my network, hit the EDIT button.  I go in, and under WEP, enter the same code that i did in the last step.  But no go.  

So on a lark, I enable or click on the "Enable WPA" even though I am only using WEP, and in the space that says "Driver" I enter my same code as I used above.

Guess what - it work's.  I connect fine now.  But  if I do not enter my code into the WPA driver, even though I am only on WEP, I cannot connect.

Go figure?  Maybe that will help somebody else.

Meanwhile i did a fresh install on a new desktop of 7.04, and i cannot get the Linksys PCI card to be reconized.   Grrrrrr.   Worked fine under Win XP.   I still have my 6,10 CD, so since i haven't setup anything much yet on the desktop, I'll do a fresh install of 6.10 untill the wireless issues under 7.04 get worked out.  Only wireless available where the desktop is, so no wireless card, no net connection.  :(

good luck everyone

---

### Post by Happy_Man on 2007-04-28
Interesting... could be helpful. Me bumping.

---

### Post by lisati on 2007-07-01
Interesting. It reminded me that last night a group I sometimes help with video stuff were asking me if I had a spare usb mermory stick to transfer a presentation from a desktop to a laptop - it hadn't occurred to them that they could've used their wireless network to do the transfer! I must remind them some time and put out a feeler to see if they want some help setting it up and figuring out how to do it.

---

