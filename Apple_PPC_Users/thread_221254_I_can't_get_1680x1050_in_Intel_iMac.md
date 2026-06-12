---
title: "I can't get 1680x1050 in Intel iMac"
date: 2006-07-22
forum: Apple PPC Users
---

### Post by 2cute4u on 2006-07-22
Hi, I've got a 20" Imac Intel and I'm using Dapper in a Parallels Desktop Virtual Machine.  The maximum resolution i seem to be able to get is 1024x768 ](*,) 

What do I need to do to get 1680X1050?

---

### Post by hajk on 2006-07-24
The screen resolutions that you'll be able to use in a Parallels VM depend on how the VM is set up. Open the Parallels Configuraton Editor (and check out page 85 of the Parallels_Desktop_for_Mac_User_Guide.pdf that came with your copy of Parallels). Does it show 1680x1050 as being available?

---

### Post by Christiaan on 2006-07-24
Haven't looked at the user guide but I added 1280x800 and 1650x1050 custom resolutions to the Screen Resolution settings in the Configuration Editor. However, when I started Ubuntu up they didn't appear under System > Preferences > Screen Resolution, which is apparently what they're meant to do if your Guest OS supports the screen resolutions.

P.S. In addition to this I've previously installed 915resolution.

---

### Post by hajk on 2006-07-24
> **Christiaan said:**
> Haven't looked at the user guide but I added 1280x800 and 1650x1050 custom resolutions to the Screen Resolution settings in the Configuration Editor. However, when I started Ubuntu up they didn't appear under System > Preferences > Screen Resolution, which is apparently what they're meant to do if your Guest OS supports the screen resolutions.

P.S. In addition to this I've previously installed 915resolution.

The custom resolutions must also be checked off in Parallels Configuration Editor to signify that they are available.

You must purge the 915resolution package, because that is meant to speak directly to the hardware. Instead, do "sudo dpkg-reconfigure xserver-xorg", then choose i810 driver and the best available resolution.

---

### Post by Christiaan on 2006-07-24
Damn, it asked me a bunch of other questions and I must have answered one of them incorrectly because it won't start up the window environment now. 

Think I'll pass on Ubuntu for the moment. Maybe with the next release I won't have to fiddle around with all this stuff. Thanks for all your help.

---

### Post by hajk on 2006-07-24
Don't give up this soon, I'm sure there is a simple solution somewhere. For the moment I have to let it pass, but my new MacBook will be delivered tomorrow and I plan to install Parallels, and Ubuntu, later in the week. So, I'll get back to you then (or you can remind me).

Good luck!

---

### Post by Christiaan on 2006-07-24
Okay, thanks hajk, I'll keep an eye out.

---

### Post by 2cute4u on 2006-08-03
> **hajk said:**
> Instead, do "sudo dpkg-reconfigure xserver-xorg", then choose i810 driver and the best available resolution.

Ok i tried this and it didn't work.  X failed to load.  :(

---

### Post by Christiaan on 2006-08-04
> **hajk said:**
> Don't give up this soon, I'm sure there is a simple solution somewhere. For the moment I have to let it pass, but my new MacBook will be delivered tomorrow and I plan to install Parallels, and Ubuntu, later in the week. So, I'll get back to you then (or you can remind me).

Any luck hajk?

---

### Post by Christiaan on 2006-08-05
Couldn't get 1680x1050 working but got 1280x800 to work. This is what I did:

First I edited the video screen resolutions option in the Parallels VM Configuration Editor, adding 1280x800.

Then I started up Ubuntu and edited xorg.conf in the Terminal, using the following command:

sudo gedit /etc/X11/xorg.conf

and added the following text to the modes line for 24 colour depth (probably worth adding to each depth): "1280x800"

then I saved the file then restarted Ubuntu. It then started up using 1280x800 by default.

---

