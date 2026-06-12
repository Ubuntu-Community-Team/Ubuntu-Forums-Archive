---
title: "Wrecked my Dapper Drake 6.06"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2006-10-22
I have had Ubuntu 5.10 thru Dapper up and running for about 60 days. In trying to get my graphics up to speed to use 3D I managed to kill my xserver.
I have tried EVERY how-to that is listed, even the one on the Ubuntu Guide and the ones on the wiki. 
Now I fear that I have the system so corrupted that I may have to reinstall and loose all my info which of course was not backed up.

I have spent hours trying to get this back and have run out of ideas. Perhaps someone can help?

---

### Post by bulldog on 2006-10-22
Well I don't know what you have tried,shall not give further advice.

But can't you use the live cd and copy your data to another safe place?

---

### Post by kindafunnylookin on 2006-10-22
The live cd will not boot. even with cd selected as 1st boot in the bios grub comes up 1st with no option for the cd.

---

### Post by bulldog on 2006-10-22
> **kindafunnylookin said:**
> The live cd will not boot. even with cd selected as 1st boot in the bios grub comes up 1st with no option for the cd.


Yeah that's correct,but you have to look in your BIOS to set the cd as first boot.

If GRUB comes insight you're too late.

If your BIOS isn't working correct,try to set the computer off and wait a minute and put it on again.

Look again in the BIOS and set boot cd first.

---

### Post by kindafunnylookin on 2006-10-22
> Look again in the BIOS and set boot cd first.

OK, I just checked and I have the BIOS set to boot the CD first, it still goes right to Grub.

---

### Post by bulldog on 2006-10-22
I only can say you're cd player is malfunctioning or you have a bad disk.

Can't do anything about it from here.

Did you use this cd already?

---

### Post by kindafunnylookin on 2006-10-22
> Did you use this cd already?

Yes, I have used the live cd before. I also tried the Ubuntu 5.10 installation CD and the boot went right to grub even with the CD chosen as 1st boot priority.

---

### Post by mysticrider92 on 2006-10-22
There should be a button to press to choose what you boot from. Watch the memory check screen when you turn on the computer and it should give you an key to press for "boot selection popup menu" or something similar (it depends on the motherboard). As mentioned earlier, your cd or drive could easily be messed up, so you might want to try a new cd or try it in another computer.

One other thing, the Ubuntu live cd's don't give you access to any hard drive data. If you wan't to get files off of the hard drive you can try a Knoppix cd ([www.knoppix.net](www.knoppix.net)), which can give you full read/write access to files, and maybe help fix the problem.

---

### Post by frostie on 2006-10-22
What happens if you select 'recovery mode' from grub? Does it boot to a command prompt ok? If so cd to /etc/X11 and have a look. There's a good chance that a backup copy of your original xorg.conf was made automatically and will be listed as, for example, xorg.conf~ (note the squiggly line on the end).

If so try:
# cp xorg.conf xorgcopy

(in case you need to keep a copy of the one installed now)

and then:

#cp xorg.conf~ xorg.conf

and reboot.

Or try any other backups you see.

Plus, if you can still browse the filesystem from here than you should still be able to backup your data ok from the prompt.

hth

---

### Post by kindafunnylookin on 2006-10-22
> What happens if you select 'recovery mode' from grub? Does it boot to a command prompt ok? If so cd to /etc/X11 and have a look. There's a good chance that a backup copy of your original xorg.conf was made automatically and will be listed as, for example, xorg.conf~ (note the squiggly line on the end).

OK, I'm going back to try that.

---

### Post by kindafunnylookin on 2006-10-22
Well I got into Xorg.conf and there are a lot of entries but nothing with an ampersand(~). I experimented a little but all ended with 0screens found.

---

### Post by frostie on 2006-10-23
Ok.
How about...boot into recovery mode and then:
# dpkg-reconfigure xserver-xorg

and follow your nose. Maybe you can build a working xserver from there. (tip...keep a note of your monitors hsync and vsync values handy).

---

### Post by kindafunnylookin on 2006-10-23
I have tried that but have just gone baco for another go. It does not work, this time I tried using the manuf. specs to no avail, then did some experimenting and no screens still.

Another things is that when I boot to the live cd I get the same problem. No xserver.

---

### Post by kindafunnylookin on 2006-10-23
OK. Problem is solved and the answer was there in front of my eyes the whole time the message at the begining of my xorcg.conf is:
> #If you have edited this file but would like it to be automatically updated again run the following command.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and that did it.
Thanks to all of you who have been helpfull

---

