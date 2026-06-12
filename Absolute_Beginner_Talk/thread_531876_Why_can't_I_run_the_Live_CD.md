---
title: "Why can't I run the Live CD?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by scrubzhero on 2007-08-22
I'm trying to install Ubuntu on my Inspiron 5160. I've booted the cd and run an integrity check of the disc and it's says everything's good. When I select the Start or Install Ubuntu option it begins to go through the process, but then I get an error.

First I'm taken to a screen which says, "Failed to start the X Server (your graphical interface). It is likely that it is not setup correctly. Would you like to view the x server output to diagnose the problem?"

In the time that it takes me to read this message a new error appears over the previous one which says, "bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed"

Honestly, I don't know anything about Linux and I have no idea where to go from here. What do I need to do to get the installation to work? You might have to spell some things out very plainly because I don't understand how all of the command lines work and all of that good stuff.

---

### Post by HW_Hack on 2007-08-22
The LiveCDs are a great tool to test your hardware prior to trying an actual install. 

Not sure how old your notebook is - but a BIOS update can fix many things - or if your BIOS is up to date you might try resetting it to "Default Setting" just incase something is out od whack in your settings 


you can also choose one of the CD menu options (or a function key)  to get a  boot:    prompt to appear on the screen   type in   acpi=off         and hit return   that may help 


As to the BCM43xx  error  - congrats ... you've got the wireless chipset from hell :)   -- I have the same thing on my Dell and I can point you to a forum post to install an NDIS Wrapper to make your wireless 

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

If at all possible install Ubuntu 7.04 as its the latest

---

### Post by AceofSpades19 on 2007-08-22
whats your video card?

---

