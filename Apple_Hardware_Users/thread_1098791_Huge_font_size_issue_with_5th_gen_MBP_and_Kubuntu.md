---
title: "Huge font size issue with 5th gen MBP and Kubuntu"
date: 2009-03-17
forum: Apple Hardware Users
---

### Post by Eothred on 2009-03-17
Just succeeded in fixing a major issue with Kubuntu and the new MBP. Upon installing (or running the live cd), the fonts were just gigantic. In fact it was impossible to hit any buttons because of it, and so fixing became an issue (not possible to use system settings etc). The same issue were present both with 8.10 32/64 bit and 9.04 beta 6 64 bit. I only tried to install 8.10 64 bit, the other two were the live cd's. Didn't try Ubuntu, and considering the solution one could expect that this might have worked better. I am posting here so that other can find the solution.

Solution: Install from the alternate cd (follow instructions from [https://help.ubuntu.com/community/MacBookPro5-1/Intrepid](https://help.ubuntu.com/community/MacBookPro5-1/Intrepid) ). Once installed, open a new tty (ctrl+alt+1), login, go to ~/.kde/share/config/, open a file (nano/vim or whatever) called kcmfonts (don't think it is there before you have altered something in systemsettings). Finally, add the following three lines:
[General]
dontChangeAASettings=true
forceFontDPI=96

I do not believe the second line is necessary, but doesn't hurt. I also added an option in /etc/X11/xorg.conf as follows:

Section "Device"
        Identifier      "Configured Video Device"
        Option          "NoDDC"
EndSection

I do not believe the NoDDC-option solved anything though, but telling just in case. Further, I think the xorg.conf is empty by default after a fresh install, so you can generate it with:
sudo dpkg-reconfigure -phigh xserver-xorg

After a full restart and login (login screen still looked terrible but you can type even though you don't see where you are typing), I finally got normal fonts. As I am not entirely sure what solved the problem I added all this information here, but I am quite confident it is the forceFontDPI=96 which is crucial.

To developers: If there is any information you need from me in order to permanently fix the issue, please do not hesitate to ask!

---

### Post by cyberdork33 on 2009-03-17
I think the forcefontdpi stuff was removed because the xorg server is supposed to detect the best dpi to use based on your monitor. It sounds like it isn't working properly though.

---

### Post by Canezila on 2011-01-27
Spot on!   I have had this problem with nvidia and a huge lcd monitor.   Thanks for restoring my sanity.   I did your solution with 10.04 but have had the font problem with other versions as well.

---

### Post by teh603 on 2011-01-28
> **Eothred said:**
> Just succeeded in fixing a major issue with Kubuntu and the new MBP. Upon installing (or running the live cd), the fonts were just gigantic. In fact it was impossible to hit any buttons because of it, and so fixing became an issue (not possible to use system settings etc). The same issue were present both with 8.10 32/64 bit and 9.04 beta 6 64 bit. I only tried to install 8.10 64 bit, the other two were the live cd's. Didn't try Ubuntu, and considering the solution one could expect that this might have worked better. I am posting here so that other can find the solution.
There's another option as well, going thru System Settings. You don't have to edit your config files to fix this. Go to System Settings -> Application Appearance -> Fonts. Then use the dropdown menu I indicated in the attached picture to set your font DPI.

If we're going to solve Bug #1, we're going to have to start posting solutions that use the frontend instead of just saying "edit this file to say blah."

---

