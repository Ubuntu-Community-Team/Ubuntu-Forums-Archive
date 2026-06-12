---
title: "Cannot install Ubuntu 12.10, freezing before installation screen"
date: 2012-10-26
forum: Apple Hardware Users
---

### Post by dumples5 on 2012-10-26
I'm having massive issues with the installation of Ubuntu 12.10 on my Macbook Pro 5,1.  During boot of the install disk, I see a screen with a keyboard at the bottom and a guy in a circle.  After that, a blinking cursor in the top right, then a random character of yellow text highlighted in red.  This is where it freezes.

I've tried the regular .iso, the mac version .iso, and booting from a USB stick, all with the same error.  I have also had installations of both Debian Wheezy and Arch Linux installed on this system before, along with Windows 7 and Windows 8.

I've spent hours searching and have turned up no similar issues.  Any suggestions?

---

### Post by aChipmunk on 2012-10-26
this is kind of an odd sugestion, but maybe you could install 12.04 and upgrade, direction for that here [http://askubuntu.com/questions/206113/i-cannot-upgrade-to-12-10](http://askubuntu.com/questions/206113/i-cannot-upgrade-to-12-10)
if you have the same problem during the install, use the alternate installer for 12.04 since they abandoned it for 12.10.  it is basicly a text besed installer, like arch.

if that doesent work, and you have a second computer laying around, boot the mac into target disk mode and plug it into the second computer.  run the 12.10 installer from that computer.  MAKE SURE TO INSTALL ONTO THE MAC HD NOT THE SECOND COMPUTER HD.  INSTALL GRUB ONTO THE MAC HD NOT THE SECOND COMPUTER HD!!! if you do not do that last step,  you may have trouble booting both computers!!!!!!

---

### Post by dumples5 on 2012-10-26
I was really hoping to go straight for 12.10, but the alternate install for 12.04 sounds like what I need to do.  I've had issues with graphics installers in the past with this laptop, so that's a good idea.  Thanks!!

---

