---
title: "Big problem,  please please help."
date: 2009-02-06
forum: Apple Hardware Users
---

### Post by Matthew2009 on 2009-02-06
I've successfully put ubuntu on my iMac Intel Core Duo, runs just fine on it's own partition.  Problem is I can't access OSX anymore.  cannot start from bootdisk pressing C.  option key does nothing.  tried a option-V and control-option-P-R.  no response.  For the life of me I can't figure this out.  I just want my iMac back.  I feel as though ubuntu has taken it hostage.

Please help.


Regards

---

### Post by Noah0504 on 2009-02-06
You're going to have to format the hard drive for the Mac OS X system disc to boot and recognize your drive.  Take a look at this link: [http://ask.metafilter.com/58998/Reinstall-Mac-OS-on-G3-iMac-after-installing-Linux](http://ask.metafilter.com/58998/Reinstall-Mac-OS-on-G3-iMac-after-installing-Linux)

---

### Post by flaggh on 2009-02-06
Don't scare him like that.  He probably just installed grub on the wrong partition.  Did you install rEFIt?

---

### Post by cyberdork33 on 2009-02-06
> **flaggh said:**
> don't scare him like that.
+1

---

### Post by Matthew2009 on 2009-02-06
> **flaggh said:**
> Don't scare him like that.  He probably just installed grub on the wrong partition.  Did you install rEFIt?
I did not install REFit.  Really wish I did, but I didn't know anything about it until it was to late.   I thought this was going to be as easy as installing windows on my macbook, wish I would have researched it more.  I would assume Grub is on the same partition as Ubuntu, not sure I'll check it now.  Which partition should it be on?   If I could reformat that would be wonderful.  I was at least smart enough to back it up on an external drive.

---

### Post by cyberdork33 on 2009-02-06
GRUB installs to the MBR by default.

I don't know why holding alt/option during startup wouldn't do anything. Maybe your timing is not correct. You should hit it just after turning on the machine and hold it until you see the boot selector.

You can also download the rEFIt iso file and burn a CD and start from there.

---

### Post by Matthew2009 on 2009-02-06
> **Noah0504 said:**
> You're going to have to format the hard drive for the Mac OS X system disc to boot and recognize your drive.  Take a look at this link: [http://ask.metafilter.com/58998/Reinstall-Mac-OS-on-G3-iMac-after-installing-Linux](http://ask.metafilter.com/58998/Reinstall-Mac-OS-on-G3-iMac-after-installing-Linux)
Well, I've followed Major's instructions on the link about opening a terminal.  He's correct, I did wipe the drive, well most of it.  I had to do a hard restart.  On boot up I put in my OSX disk and held C after the chime.  Still I get a screen that says 

Grub Loading stage1.5.

GRUB loading, please wait...
Error 17

I tried command-option-p-r , no change. And now I can't remove my disk.

This is starting to scare me.

---

### Post by flaggh on 2009-02-07
Those instructions weren't really relevant to your original question.  They are for reinstalling OSX over a hard drive that only has Linux installed on it.  Not for a dual boot.

Assuming that you did not overwrite your OSX partition, all you need to do is repair the MBR and boot back into OSX.  When you installed Ubuntu without specifying where you wanted to install GRUB, it installed it to your MBR by default which is incorrect.  You're really making this more difficult for yourself by reformatting and restoring, but if that's the path you wish to choose, go ahead.

Hold down the 'Alt/Option' key from the moment you turn on your computer until the menu pops up.  It takes a little persistence sometimes.  The 'Eject' key also needs to be held for a long time if that's what you're trying to do.

---

### Post by Matthew2009 on 2009-02-07
I think I've figured out why I couldn't boot from OSX disk.  After giving up and looking at this as a new opportunity to upgrade my internal hard drive and use the existing one as an external after I wipe it,  I found the same issue of not being able to boot from disk after a hard drive swap.  Then I realized that When I bought the metallic keyboard over a year ago, an update happened and a new icon appeared in the OSX utilities folder (not sure what it is, never opened it, assuming it's a driver.)  Anyway, I plugged in a different keyboard, held the C button and booted from disk 1st try.  I'm not for sure, but I think that Ubuntu wasn't recognizing the keyboard and I probably was ok from the get go.  Just needed a different keyboard.  I'm interested to here everyones take on this.  Thank you all again for your support.  Hopefully this will help someone else in the future.


Regards:p

---

### Post by cyberdork33 on 2009-02-07
> **Matthew2009 said:**
> I think I've figured out why I couldn't boot from OSX disk.  After giving up and looking at this as a new opportunity to upgrade my internal hard drive and use the existing one as an external after I wipe it,  I found the same issue of not being able to boot from disk after a hard drive swap.  Then I realized that When I bought the metallic keyboard over a year ago, an update happened and a new icon appeared in the OSX utilities folder (not sure what it is, never opened it, assuming it's a driver.)  Anyway, I plugged in a different keyboard, held the C button and booted from disk 1st try.  I'm not for sure, but I think that Ubuntu wasn't recognizing the keyboard and I probably was ok from the get go.  Just needed a different keyboard.  I'm interested to here everyones take on this.  Thank you all again for your support.  Hopefully this will help someone else in the future.


Regards:p
I believe this may be a bug in the apple firmware as several iMac owners have been complaining about their aluminum keyboard not working properly during the bootup phase. The good news is that once it gets into Ubuntu, the keyboard will work again.

Glad you got it figured out though.

---

