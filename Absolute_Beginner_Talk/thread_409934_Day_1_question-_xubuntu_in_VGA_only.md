---
title: "Day 1 question- xubuntu in VGA only"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by richardbuk on 2007-04-15
I have installed xubuntu 6.06 on an old passed down pc after reading lots in the forums and buying a couple of books, but I can only seem to configure my display as VGA. The display settings dialog only offers "default" as a resolution option. 

I am not sure how to find out what card I have, but I know my graphics card and flat screen display can support 1024x768x16 because that's what they were doing under windows me (I told you it was on old machine - hence using xubuntu)

Typing lspci into terminal showed that I have "0000:01:00.0 VGA compatible controller: S3 Inc. Trio 64 3D (rev 01)"

Do I need to install another driver - if so how? Or is it a case of configuring what I already have? If there is somewhere I should go to read up on how to do this, happy just to get a helpful link - not expecting a tailored step by step guide. But as it is day 1 of my linux life, please take things gently ;-)

Best wishes from a sunny London, richardbuk.

---

### Post by reality_hunter on 2007-04-15
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by Tundro Walker on 2007-04-15
While you're at it, do the following...

1) install a GUI file searcher and other useful utils.  Open a terminal and type the following then hit enter...

```
sudo apt-get install gnome-utils
```
2) Fix "fonts getting smaller" issue....

```
sudo mousepad ~/.config/xfce4/Xft.xrdb
```...add "Xft.dpi: 96" on last line and add blank line on end. Save.  This forces the window manager to keep 96 dpi, preventing the fonts from shrinking ever smaller.  (I think the XFCE developers fixed this bug in newer XFCE's, but  the XFCE's packaged with older Ubuntu distro's are, naturally, older, and may have this bug.  I know a 6.10 Edgy Eft Xubuntu install I was using had that problem.  More current Xubuntu 6.10 Edgy Eft ISO's may have been updated with the current XFCE.  Caveat Emptor...)

Hope this helps...

---

### Post by freebird54 on 2007-04-15
The **vesa** driver is likely to give you the resolution you want.  The guide you were pointed to should tell you enough beyond that.  If not, just say so and someone will walk you through it - or point you to another guide that works well!  IT definitely should be possible.

---

### Post by richardbuk on 2007-04-15
Thanks for the help, I checked the card and monitor by logging back into Windows ME and noting the settings there, then worked through the config process. The autodetect of the S3 graphics card failed, but I chose vesa for the card and the autodetect worked firne for the monitor, so all sorted now with 1024x768 - thanks again to all.

richardbuk :D

---

