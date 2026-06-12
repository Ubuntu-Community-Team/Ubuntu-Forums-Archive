---
title: "Wifi Kill Switch on FS Amilo Pro V3505 laptop"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by plopp37 on 2007-12-08
Hello,

Is there any easy way how to make special keys on my FS AmiloProV3505 laptop work on Linux? In Win, the keys are managed by Acer LaunchManager (both the Fn+ keys and special buttons for Wireless, Mail, InternetBrowsing). Some keys are mapped by Ubuntu, but definitely not all of them. The main problem for my needs is Fn+F3, which is screen-switcher, and the problem No1 is the Wireless networking switcher! I have found some info about this problem on the web, but not regarding my type of machine, nor regarding the way, how to solve the problem with my level of experience.

If anybody can help, please do it, otherwise I won't be able to work with Linux.
Thanks alot

---

### Post by pHreaksYcle on 2007-12-08
Did you try:
System->Preferences->Keyboard shortcuts ?
You might be able to find something there you need. Also, if it's just the wireless you want to disable from time to time, go to the wireless icon and right click on it. There are options there to disable your wireless card. Hopefully this helps you some. GL!

---

### Post by comradekingu on 2008-07-05
I got it to work on a fresh ubuntu 8.04 install, then when i updated the kernel it was gone again.
Going back to the old didnt do the trick, nor did a reinstall.
The solution lies in the Bios version, because the killswitch button does not work.
This was confirmed by trying another card known to work.

Solution:
I was able to get it to work with the latest firmware (B0G)
Its available from fujitsu-siemens [http://support.fujitsu-siemens.com/Download/ShowDescription.asp?SoftwareGUID=7F5DC06C-7C41-453C-A791-2D9039BB73FA&OSID=665F4A20-6E31-43C3-82C2-D98CE773007C&Status=True&Component=Flash%20Bios%20for%20AMILO%20Pro%20V3505](http://support.fujitsu-siemens.com/Download/ShowDescription.asp?SoftwareGUID=7F5DC06C-7C41-453C-A791-2D9039BB73FA&OSID=665F4A20-6E31-43C3-82C2-D98CE773007C&Status=True&Component=Flash%20Bios%20for%20AMILO%20Pro%20V3505)
Dont worry about the XP category selection, BIOS is the same regardles of OS.
Burn .ISO to disk and boot. Press F12 to select CD during post.
Write "FLASH" when prompted.

If that does not work you might try this:

[http://odzangba.wordpress.com/2007/05/15/intel-corporation-prowireless-2200bg-amilo-pro-v2000-ubuntu/](http://odzangba.wordpress.com/2007/05/15/intel-corporation-prowireless-2200bg-amilo-pro-v2000-ubuntu/)

---

