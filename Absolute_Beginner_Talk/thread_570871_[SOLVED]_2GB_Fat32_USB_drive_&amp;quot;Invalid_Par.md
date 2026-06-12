---
title: "[SOLVED] 2GB Fat32 USB drive &amp;quot;Invalid Parameters while copying...&amp;quot;"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by SloYerRoll on 2007-10-08
Hey,
I have already searched for about an hour to try and find an answer for this.

I have a 2GB thumb drive that I can't access via Ubuntu..
I get the error message in the title bar. I try to retry many times and I continue to get the same message. I skip and I loose files, I cancel.. well duh  :-?  I can click on the skip button about a dozen times and it will "complete" the process and copy some files over to the usb. When I look at the folders (original vs. thumbdrive) the thumbdrive is missing tons of files (probably about a dozen..)

I have gone over a few threads that say to use VMware. I can't find this in Synaptic Package Manager though and don't know anything past file browsing in terminal. 

This is what I need to be able to do:

Retrieve files from an application used in Ubuntu. Save them to my Home folder. Toss my USB in and load the files onto that. Reboot and load windoze so I can use the files off the USB in Dreamweaver. 

I have read some threads also on how to make windows files visible from linux and vice versa. The things I've read are over my head though or they have big disclaimers that it might not work and "do at your own risk". 
My machine is my lifeblood and I can't afford to loose it. 

details:
REALLY fast machine
Vista/Ubuntu dual boot (most current version of Ubuntu I guess. I just d/l it 2 days agao and installed)
Fat 32 formatted USB 2GB thumbdrive
Brain that feels like it's gonna pop!

---

### Post by ryanVickers on 2007-10-11
Are you using the terminal or GUI to copy them?  Incorrect parameters can't really happen in the GUI as far as I know :p

Try doing it as root - type "gksudo nautilus" in the terminal to get the root file browser and view both places with that - then try to copy them.  Windows doesn't comprehend permissions (much less Unix ones ;)), so this should n't be a problem! :)

---

