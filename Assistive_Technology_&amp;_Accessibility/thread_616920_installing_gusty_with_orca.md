---
title: "installing gusty with orca"
date: 2007-11-18
forum: Assistive Technology &amp; Accessibility
---

### Post by CactusWren on 2007-11-18
Hello,
While I am fairly new to ubuntu, I have been using fedora and redhat enterprise linux for a while now. I want to install ubuntu gutsy onto my system, but can find no documentation on how to do this with orca running. 

I am totally blind, and would like to do this without sighted assistance if possible.

Any assistance in this area gratefully accepted.

---

### Post by fscodelaro on 2007-11-22
This might help you, it's a verbatim copy from [https://help.ubuntu.com/community/Accessibility](https://help.ubuntu.com/community/Accessibility) :

> Once you've downloaded and burned the live CD image, insert it into your CD/DVD drive and reboot your computer. You should find that your drive spins for a short while and then stops. The point at which it stops coincides with the appearance of the boot options screen. At this point, you have about 30 seconds to perform the next step. If you do not perform the next step quickly, Ubuntu will automatically continue booting.

In order to enable accessibility options, press F5. This will cause a list of accessibility options to appear: None (has focus), High Contrast, Magnifier     *Screen Reader, Keyboard Modifiers, On Screen Keyboard

If you want to try Orca, you should press 3 to give focus to Screen Reader, followed by Enter to indicate your selection. You will be returned to the boot options screen then press Enter again to indicate you would like to boot.

Within a few minutes, Ubuntu will be loaded with Orca running and you will hear a greeting such as "Welcome to Orca. Orca Preferences. Tab list. General page."

The CD drive should also stop spinning at this point. If the CD drive stopped spinning and you did not hear a greeting from Orca, you might need to try to reboot from the CD and repeat the steps for selecting the Screen Reader.

Now, the graphical desktop is up and running, Orca is active, and the Orca Preferences dialog has focus. The Orca Preferences dialog is a multi-page dialog with several pages that allows you to configure your settings.


You will find more Accesibility information on [https://help.ubuntu.com/community/Accessibility](https://help.ubuntu.com/community/Accessibility)

---

