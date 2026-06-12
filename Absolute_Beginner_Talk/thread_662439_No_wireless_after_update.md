---
title: "No wireless after update??"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by sbussy89 on 2008-01-08
I updated my system and the wireless stopped working.  When trying to connect to the wireless network, the first green dot  in the graphic went on but the second one never did.  I connected fine through windows (which I'm starting to question ever leaving behind).  I tried rebooting, etc. but nothing worked.  When I first began with ubuntu I had to install the drivers for the Broadcom wireless card, so I tried to re-install them.  It said they were already installed and then hung, and after I quit the installer my wireless totally stopped working - now it's not even an option in the manual network configuration window.  Help - and add system restore as a feature to ubuntu.

---

### Post by Hospadar on 2008-01-09
well, what I'd bet is that there was a kernel update, and probably the broadcom drivers build themselves on installation for the specific kernel you are using, so you'd need to re-install, which would apparently require some uninstallation first.  I don't know about the broadcom drivers specifically, but if they offer some uninstallation, do that first, if not, you might try to track down which files specifically that they install and delete them

---

### Post by sbussy89 on 2008-01-09
My broadcom drivers were found automatically through the restricted drivers manager.  When I turn off the broadcom firmware and then turn it back on the wireless works, but I have to do this every time i restart my pc.  The problem with it is that when I re-enable the firmware it goes back online to re-download them, so I need a wired connection to access my wireless connection which entirely defeats the purpose of the wireless connection

---

### Post by sbussy89 on 2008-01-09
I found a temporary fix by saving the file to my desktop, so I no longer have to use the wired internet to get the firmware restarted, but its still a pain having to disable and re-enable it every time i turn on the pc... any fix yet?

---

### Post by Cinnamon on 2008-03-24
I'm having a similar problem. I downloaded the update over the weekend, now wireless isn't working.   There appears to be no wireless networks available to connect to, and if I try to connect to my wireless network manually, it doesn't work.

My wireless works on Windows, and use to work on Ubuntu. I don't remember what I had to do to get it to work before:( but I know I downloaded ndiswrapper. Is there a tutorial somewhere that I can follow?

Cinnamon

ETA: I got it working. I used this <https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy> it was really simple

---

