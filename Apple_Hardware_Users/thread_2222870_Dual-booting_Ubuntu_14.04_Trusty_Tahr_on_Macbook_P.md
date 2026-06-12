---
title: "Dual-booting Ubuntu 14.04 Trusty Tahr on Macbook Pro 5.4 (Mid 2009)"
date: 2014-05-08
forum: Apple Hardware Users
---

### Post by Simon_Woolf on 2014-05-08
Hi,

I'd like to contribute a page to the community documentation that details installation of Ubuntu 14.04 (Trusty Tahr) on a MacBook Pro 5.4

I've tried logging in and then creating the new page (which would have the theoretical url [https://help.ubuntu.com/community/MacBookPro5-4/Trusty](https://help.ubuntu.com/community/MacBookPro5-4/Trusty) ) however I just get the following message

[COLOR=#333333][FONT=Ubuntu]**[COLOR=#AEA79F][FONT=inherit][FONT=inherit][MacBookPro5-4]("https://help.ubuntu.com/community/MacBookPro5-4")[/FONT][FONT=inherit]/[/FONT][Trusty]("https://help.ubuntu.com/community/MacBookPro5-4/Trusty?action=fullsearch&value=linkto%3A%22MacBookPro5-4%2FTrusty%22&context=180")[/FONT][/COLOR]**
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][FONT=inherit][FONT=inherit]You are not allowed to edit this page.

So I'll detail my experiences here instead. If some kind soul wants to explain how I can create a more formal documentation page at the above location, I'll be glad to do so.

____________________

Hardware: [B]MacBook Pro 5.4 (June 2009) amd64/15" screen/4GB RAM/250GB HDD

[/B][/FONT]**Mac OSX 10.8.5 (Mountain Lion)**

____________________

I started by following the instructions here:  [/FONT][/FONT][/FONT][/COLOR][https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) however this is out of date and often didn't help.
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][FONT=inherit]
1. I installed rEFind ([/FONT][/FONT][/FONT][/COLOR]http://www.rodsbooks.com/refind/) as rEFit is no longer maintained. However, it turned out that rEFind was not necessary at all, and just complicated things.

2. I ran "disk utility" from spotlight, and shrunk the OSX partition, leaving 15GB free disk space. I *did not* create a new partition in the free space, as I knew the ubuntu installer would be able to do that.

3. I then created a bootable USB drive with Ubuntu 14.04 Desktop 64-Bit edition, using the instructions here: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx) - however these instructions contain some unnecessary steps (4 and 9 make no sense to me). Furthermore, the alt-option key combination did not work for me. I had to hold down just "alt" immediately after hearing the Mac chime, to get into the boot options. rEFind did not allow me to see the usb drive or boot from it.

4. I booted from USB and ran Ubuntu from the USB drive to test. Everything worked, apart from wireless. Going to System settings > software & updates > additional drivers and selecting the broadcom driver fixed this.

5. I then rebooted (again holding down alt to get to the boot options) but this time chose "install ubuntu"

6. I installed Ubuntu with all default options - "install alongside OSX". The install process completed, but the computer then froze whilst shutting donw.

7. Rebooting gave me a grub menu from which I could boot into Ubuntu. There were obvious graphics card issues in the loading screen (noise in the upper half of the screen). The Grub menu options for booting into Mac OSX did not work.

8. Going into System settings > software & updates > additional drivers now did not show me any additional drivers, so no easy way to get wireless working

9. Solution to get wireless working: browse the bootable USB drive, find /pool/main/d/dkmc/ and double-click the .deb package to install (opens in software centre - click "install").
    Then do the same for [COLOR=#000000]/pool/restricted/b/bcmwl - once both are installed, wireless should work and show available networks

10. Now run the software update and install all updates

11. Go to [/COLOR]System settings > software & updates > additional drivers and additional graphics drivers should now be shown. Select the first nVidia graphics driver and apply change.
[COLOR=#000000]
12. The wireless networking will stop working after reboot. To fix this, open a terminal (ctrl+alt+T) and type
[/COLOR]
[FONT=courier new]sudo nano /etc/modprobe.d/blacklist.conf[/FONT]  - locate the entry bcw43xx and comment it out (#) (we do not want to blacklist the correct wireless driver!)

13. To be able to boot back into Mac OSX from Grub, I selectively followed the instructions here: [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy) - ie:

 [FONT=courier new]sudo efibootmgr[/FONT]   - to check that indeed I had grub in first position (0000) and Mac OSX in second (0080)

Then to allow fallback to MacOS (which is what happens when we exit grub):

[FONT=courier new]sudo nano /etc/grub.d/40_custom  [/FONT]
[COLOR=#333333][FONT=Ubuntu]
add to the end of file:
[/FONT][/COLOR]
[FONT=courier new]menuentry "MacOS" {
  exit
}[/FONT]

So we now have a "MacOS" entry in the grub menu, which simply exits Grub and boots OSX normally.

Note: I then logged back into OSX and removed rEFind, since it wasn't needed. This was done simply by running the following in a terminal:

[FONT=courier new]sudo rm -rf /EFI/refind[/FONT]

That's about it. I now have a fully working system. Just need to create a shared partition so that OSX and Ubuntu can share files, and we're done. I'll save that for another day, I intend to follow these instructions: [http://www.tuxation.com/creating-home-partition-mac-linux.html](http://www.tuxation.com/creating-home-partition-mac-linux.html)

Simon

---

### Post by Simon_Woolf on 2014-05-12
No-one able to advise why I can't create the proper community documentation page?

---

### Post by mattsony on 2014-05-12
I don't know why you cannot add to the community page but thank you for posting this. I was worried about the drivers with my 5,4. Specifically the nvdia drivers. Did you try dual monitors? This and suspend are my main concerns with upgrading.

---

### Post by Simon_Woolf on 2014-05-12
Suspend worked a treat - no problems waking up, wifi included. I didn't try with dual monitors I'm afraid.

---

