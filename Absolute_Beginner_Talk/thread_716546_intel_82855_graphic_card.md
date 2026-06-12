---
title: "intel 82855 graphic card"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by alishoojaa on 2008-03-06
hi every one 

please i need help 
my laptop graphic adapter is intel 82855 
when i install ubuntu the xserver dose not apper
it steel black screen
when i remove the hard disc and put it on the desktop computer (the graphic card is nVIDIA fx 440)
it is working and i can see the desktop
help please

thanks for all

---

### Post by mikeyphi on 2008-03-06
Try this:
Reboot into the recovery mode
when at the Command prompt, enter the following:
dpkg-reconfigure -phigh xserver-xorg

There will be a lot of text with a question at the end of each section - accept the default answer unless you know better!
When finished reboot into normal mode - you should have a default screen
If required - Open System/Administration/ Restricted Drivers Manager and install the driver.
After that Open System/Administration/Screens and Graphics - to select the correct screen and resolution.

Please post results or error message!

---

