---
title: "[SOLVED] 2GB Fat32 USB drive &amp;quot;Invalid Parameters while copying...&amp;quot;"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by SloYerRoll on 2007-10-08
Sorry I went to subscribe and accidentally solved the thread...:(

Hey,
I have already searched for about an hour to try and find an answer for this.

I have a 2GB thumb drive that I can't access via Ubuntu..
I get the error message in the title bar. I try to retry many times and I continue to get the same message. I skip and I loose files, I cancel.. well duh I can click on the skip button about a dozen times and it will "complete" the process and copy some files over to the usb. When I look at the folders (original vs. thumbdrive) the thumbdrive is missing tons of files (probably about a dozen..)

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

### Post by SloYerRoll on 2007-10-08
Sweet mother McRee!
I'm figuring this stuff out myself!

Thanks NEway to all the ppl in here helping NOOBs like me!

Cheers,
-Jon

---

### Post by shad0w_walker on 2007-10-08
If you are using Fiesty (7.04) or above you should be able to install these two programs from the package manager:

```
ntfs-3g
ntfs-config

```

When you have installed those, press Alt + F2 to open the run dialog and run this command:

```
gksu ntfs-config
```

That will give you a nice GUI to setup read/write access to your windows drive.

---

