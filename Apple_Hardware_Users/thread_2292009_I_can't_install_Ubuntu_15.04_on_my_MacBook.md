---
title: "I can't install Ubuntu 15.04 on my MacBook"
date: 2015-08-24
forum: Apple Hardware Users
---

### Post by m6rshmallow on 2015-08-24
**Hello!**
Today I download **Ubuntu 64bit ISO** and burn into a **DVD** with ubuntu's guide. After restart MacBook and press option key, added two option (with disc icon) show on the screen, Windows and EFI Boot!!

When I click on Windows or EFI Boot icon, after Ubuntu loading screen, I see **mouse cursor with black screen** that repeat many times without restart or any errors!!

With Bootable flash drive and other bootable DVD that I made with Rufus(@PC) and Disk Utility(@Mac), I have same issue. Just with 2nd bootable DVD I start using setup to install ubuntu that after type username and passwords receive an error about problem on DVD reading....

How to install Ubuntu inside OS X on my MacBook? :confused:
My **MacBook model, mid-2010 white 13-inch, ModelID: 7,1** with OS X Mavericks installed.
I have **55GB free disk space** on my MacBook that made by Disk Utility for new OS. :rolleyes:

I'm so sorry for bad english writing. :(
Thanks

---

### Post by asmodeus3 on 2015-08-25
[B][Regarding the cursor and black screen issue]
[/B]Hello.
This might be a problem of a bad display configuration. I had the same problem with a powermac that uses nvidia.
I guess pressing* Ctrl+Alt+F1* brings a prompt up.
You can create a configuration file for the Xserver manually with : [I]sudo **X**org -configure 
[/I]Then move the generated *xorg.conf.new* with : [I]sudo xorg.conf.new /etc/**X**11/xorg.conf
[/I]Then you can view/edit it with nano : [I]sudo nano /etc/**X**11/xorg.conf
[/I]Some users might be able to help you if you post your conf setup here.

You can also check your Xserver log for any errors.
You can do so by pressing *Ctrl+Alt+F1* and then from the console search in ***/var/log*** for *Xorg.0.log* or something like that.

To get through the installation at least, you might want to use an alternative install and  Im not sure whether 15.04 is a good choice.
[This]("https://help.ubuntu.com/community/MacBookPro7-1/Trusty") wiki post explains the steps needed to install 14.04 on a macbook pro 7.1

Hope this helps a bit.

---

### Post by crystalocean on 2015-09-01
Hi m6rshmallow,

Please look into installing rEFInd and using that to boot from the bootable flash drive you've created. (Personally, I prefer installing rEFInd to its own partition on the mac hard drive. 100 MB should be more than enough space if you choose to go that route.)

After installing rEFInd, once you reboot your computer with the flash drive plugged in, the rEFInd boot menu should appear and a menu option should appear for booting from the flash drive. If you install rEFInd to its own partition and the menu doesn't appear after booting, you can either check the startup disk section in system preferences or simply hold the option key once your hear the apple chime during boot-up, and then you will be able to select the rEFInd partition.

Hope some of this is useful to you (or others)!

---

