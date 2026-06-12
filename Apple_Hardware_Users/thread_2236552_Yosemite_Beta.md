---
title: "Yosemite Beta"
date: 2014-07-27
forum: Apple Hardware Users
---

### Post by alex231 on 2014-07-27
I recently installed the Yosemite beta and I lost refit that I'd been using to boot into Ubuntu. I don't have any important files on my Ubuntu partition, so I'm okay in that regard, but I'm a little baffled that now I just boot straight into Yosemite without first heading to refit. I tried reinstalling refit and refind but so far neither has worked. Any thoughts on how I can get dual boot back up and running with Yosemite?

---

### Post by este.el.paz on 2014-07-27
> **alex231 said:**
> I recently installed the Yosemite beta and I lost refit that I'd been using to boot into Ubuntu. I don't have any important files on my Ubuntu partition, so I'm okay in that regard, but I'm a little baffled that now I just boot straight into Yosemite without first heading to refit. I tried reinstalling refit and refind but so far neither has worked. Any thoughts on how I can get dual boot back up and running with Yosemite?

@Alex:

OSX has never "played well with others" . . . once you install OSX it wipes other settings . . . .  And, rEFIt doesn't work with systems after . . . perhaps 10.6.8, but definitely Mtn Lion . . . .

So, if you have installed rEFInd since you upgraded to Yosemite, you might try using the option key on boot to get to the rEFInd window.  I posted a question about getting rEFInd back after doing the recent Mav upgrade on the rEFInd Sourceforge forum; you might check it out for some hints--same screen name.  

Also, OSX probably reset the GRUB settings . . . you might find something online about how to run a command to get GRUB working or use the SuperGRUB2 CD to boot to GRUB and use the "Boot repair" option to get GRUB set up . . . or, you might have to re-install GRUB . . . something like that.  I went through this recently when I upgraded to Mav . . . I can't remember all the details, but I think I used the SuperGrub2 app to boot into the Linux partition or GRUB, and then used the options there . . . as I mentioned.

e.e.p.

---

### Post by alex231 on 2014-07-27
Here's where I'm at:


I installed refind via the EFI System Partition installation option described here: [http://www.rodsbooks.com/refind/installing.html](http://www.rodsbooks.com/refind/installing.html). Got me to boot into refind. Only EFI detected was Ubuntu. Boot into the OS X recovery option from refind because I want to make sure I can get back into OS X before going on to Ubuntu. Gets me back into Yosemite. Only now, all the directories I created and the modifications to the ESP don't exist. So I guess I can follow the installation instructions again to get back to refind/Ubuntu. Any ideas on why it would clobber all the directories I had just created? I suppose I could make a shell script that would mount the ESP every time but it'd be nice if there was something more permanent.

---

### Post by este.el.paz on 2014-07-28
> **alex231 said:**
> Here's where I'm at:


I installed refind via the EFI System Partition installation option described here: [http://www.rodsbooks.com/refind/installing.html](http://www.rodsbooks.com/refind/installing.html). Got me to boot into refind. Only EFI detected was Ubuntu. Boot into the OS X recovery option from refind because I want to make sure I can get back into OS X before going on to Ubuntu. Gets me back into Yosemite. Only now, all the directories I created and the modifications to the ESP don't exist. So I guess I can follow the installation instructions again to get back to refind/Ubuntu. Any ideas on why it would clobber all the directories I had just created? I suppose I could make a shell script that would mount the ESP every time but it'd be nice if there was something more permanent.

Hopefully you'll read through my prior post about putting OSX in first and in the first partition, and then add linux . . . have you tried that yet?  After the linux install apparently it's best to shut down the computer and do a cold reboot.  I put rEFInd in the OSX partition, the easy way . . . .

e.e.p.

---

### Post by mode7 on 2014-07-29
It's quite a bit easier than it used to be, in my experience. I too would install it under OSX if possible. For me, it's always detected every OS. And if an OSX update kills rEFInd, all I have to do is run the install.sh script again to reset it as the boot target.

If you're comfortable with it, the new EFI kernel boot stubs circumvent the need for Grub, so you can boot straight into Ubuntu from rEFInd. 'ubiquity --no-bootloader' in the live session will run the installer sans grub-install. rEFInd has always found the kernels, for me.

The only thing I run under Linux concerning rEFInd is the included shell script (Can't remember it's name) that creates kernel boot entries, and that is just to help me get the boot splash back (For whatever reason, it really likes verbose boot when booting in EFI mode)

---

### Post by shrawder on 2014-10-21
Bit late here, but I have your answer. 

While on Mac, run this in the terminal:

cd /efi/refit
./enable.sh

Restart your computer and Refit should show up now.

Worked perfectly for me, anyway. Credit goes to "uji" from this Mac Forums post: [http://www.mac-forums.com/forums/running-windows-anything-else-your-mac/313648-yosemite-beta-having-trouble-dual-boot-linux.html](http://www.mac-forums.com/forums/running-windows-anything-else-your-mac/313648-yosemite-beta-having-trouble-dual-boot-linux.html)

---

