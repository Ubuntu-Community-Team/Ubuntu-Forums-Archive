---
title: "Can I format?"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by bt224 on 2006-05-02
Last night I tried the Live CD. Everything installed ok, or so it seemed, then the screen went blank. After reading several posts and anything else I could find, I wanted to try some stuff. Now I can't even get the Live to boot, and since it's Windows 2000 Professional (NT), I can't get to the BIOS settings to ensure ot will boot from the CD. This is on an old Toshiba Satellite, and it's a good place to learn (read screw up) Linux. Since I can't get it to even boot, what if I just formatted the HD and then put in the install disk? What are the real dangers? There is no data on this thing and I certainly don't like the current OS.

---

### Post by nanotube on 2006-05-02
well, if there is no valuable data on the disk, then sure, go ahead and format... i don't see why not. :)

---

### Post by Qrk on 2006-05-02
Are you positive you can't get it to boot from a CD? BIOS doesn't have anything to do with 2000 or XP, in fact, my laptop origionally ran NT 4.0 and boots from a cd just fine. 

If you really can't boot from your cd through BIOS, the easiest way to install Ubuntu is booting to a floppy disk, and then from the floppy disk boot from the cd. 

[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

---

### Post by NeghVar on 2006-05-02
Im sortry I'm not seeing how you can't get into the Bios. When you first turn it on try hitting F8, F11, Delete 3 seperate times to enter your Bios. Im not sure which one your notebook uses.

The formatting option won't work unless you can boot from the CD, I would get into your Bios using one of those keys most likely and make sure it boots the cd first. Once you can do that if you don't care about the data on the Hard Drive then go for it. The biggest danger is that some piece of Hardware is incompatable and it won't work. 

I'd advise keeping your 2k disk around until you know that it installed fine, you probably won't need it but in my experience you can't be to safe.

---

### Post by bt224 on 2006-05-02
Well, as positive as I can get. Worked last night but not today. It could be my luck that something else has gone wrong, like the CD-ROM has died, except I just played a CD to check it.

---

### Post by bt224 on 2006-05-02
F8 is the only one that work's, and just gives me several Safe Modes to choose from, nothing about settings. I've tried every option on this window and none take me to BIOS. While no expert, I have had to go into the BIOS on other machines for various reasons, just never this one. I really hate W2K Pro.

---

### Post by bt224 on 2006-05-02
Ok, now I'm ready to toss this laptop. It won't even let me format the c drive. Any ideas? Did I mention that I hate W2K?

---

### Post by joshrobinson on 2006-05-02
[QUOTE=bt224]Ok, now I'm ready to toss this laptop. It won't even let me format the c drive. Any ideas? Did I mention that I hate W2K?[/QUOTE]

as soon as it turns on there is a screen that ususally says your make of laptop, dell, hp, compaq whatever.. there will be a button that you have to hit that says BOOT MENU or system setup.. so as soon as you turn it on look for that prompt

f8 is the windows safe mode window, that means you are hitting it too late, you have to hit it on the bios menu like i said above, that says your make of laptop

ususally one of the f keys, or maybe delete or escape
it should then put you into a menu where you can selet to boot from a device, or a boot priority list, you need to move your cdrom to the top, or below your floppy

---

### Post by bt224 on 2006-05-02
You are correct, I found it was the escape key during boot. Boot sequence was correct. Right now I am installing Windows ME over W2K Pro. I have no idea if that will make this easier, but Pro is a b***h to work with, or maybe just not in my comfort zone. Again, CD-ROM may be flaking out too. At least this way I'll be on familiar ground. Thanks again! I'll update here in a minute after the new ME install is complete.

---

### Post by joshrobinson on 2006-05-02
[QUOTE=bt224]You are correct, I found it was the escape key during boot. Boot sequence was correct. Right now I am installing Windows ME over W2K Pro. I have no idea if that will make this easier, but Pro is a b***h to work with, or maybe just not in my comfort zone. Again, CD-ROM may be flaking out too. At least this way I'll be on familiar ground. Thanks again! I'll update here in a minute after the new ME install is complete.[/QUOTE]

so you are going to switch back to ubuntu? id boot with a floppy like someone posted above:-D

---

### Post by bt224 on 2006-05-02
I'm farked. Formatted the hard drive but won't install ME. Will boot from DOS floppy and that's it, won't recognize the cd-rom

---

### Post by joshrobinson on 2006-05-02
[QUOTE=bt224]I'm farked. Formatted the hard drive but won't install ME. Will boot from DOS floppy and that's it, won't recognize the cd-rom[/QUOTE]

well id make a boot floppy like the link someone posted, then once it boots the floppy it will start the installer from the cd.. hopefully that will work

your cdrom drive sounds like it has some issues

the cdrom drive is set to boot before the hard-drive right?
make sure you save the bios settings on exit

---

### Post by bt224 on 2006-05-02
Tried the Smart Boot Manager [http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm), no luck. Boot sequence is CD>FDD>HDD. CD spins right up, just doesn't do anything. It's pretty heavy, might end up being a really good boat anchor.

Edit: when cd spins up, error message says Invalid System Disk

---

### Post by nanotube on 2006-05-02
[QUOTE=bt224]Tried the Smart Boot Manager [http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm), no luck. Boot sequence is CD>FDD>HDD. CD spins right up, just doesn't do anything. It's pretty heavy, might end up being a really good boat anchor.

Edit: when cd spins up, error message says Invalid System Disk[/QUOTE]
hm, maybe you have a bad disk? try burning another one, and at a slower speed. (and of course, verify the md5 on your iso download to make sure the download is not corrupted)

---

### Post by bt224 on 2006-05-02
Funny you mention that, I am downloading again and trying to figure out what checksum and md5 are. I downloaded MD5Check. It asks for 2 different files to check, so I'm trying to figure out how to check the download against the server. Or am I dense and it's to check the burn against the desktop file? I haven't even got this onto a computer and I'm already learning stuff. And not the fun way either.

---

### Post by bt224 on 2006-05-02
It just booted up the live cd. wtf? Too bad it wasn't the install. Nothing changed and I was about to turn off the laptop, then boom! I will try this again with the install. Good thing I haven't spent money on this.

---

