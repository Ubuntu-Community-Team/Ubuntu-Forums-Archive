---
title: "Boot EMERGENCY"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by saxofoner on 2006-11-17
I have a dual boot machine, windows and ubuntu on the same drive, seperate partitions.  It's worked perfectly for about 3 months.  Then yesterday, I got this.
"DISK BOOT ERROR.  PLEASE INSERT SYSTEM DISK."  
Oh sh**.  
So I messed around, and got GRUB Errors 16, and 18...
Then I did a memtest from the Ubuntu Live disk (which wouldn't boot) and then rebooted, and everything worked in Ubuntu.  Then I booted Windows, and it didn't work.  Reboot.  Reboot.  It worked!  Then I got home today and booted and Ubuntu froze at "loading boot files" or whatever the second orange thing says, after the kernal loads on boot.  Then I rebooted, and Ubuntu booted.

YAY!  Then, oh sh**, again.  

"The greeter could not load.  Trying alternative greeter"  Then I logged in.

" 'Nautilus' has unexpectedly quit"  "'Notification Area' has quit"  etc.

So I booted Windows (thank God it worked) and posted this desperate plea for help.  HELLLLLPPPP!!!

---

### Post by Swab on 2006-11-17
> **saxofoner said:**
> I have a dual boot machine, windows and ubuntu on the same drive, seperate partitions.  It's worked perfectly for about 3 months.  Then yesterday, I got this.
"DISK BOOT ERROR.  PLEASE INSERT SYSTEM DISK."  
Oh sh**.  
So I messed around, and got GRUB Errors 16, and 18...
Then I did a memtest from the Ubuntu Live disk (which wouldn't boot) and then rebooted, and everything worked in Ubuntu.  Then I booted Windows, and it didn't work.  Reboot.  Reboot.  It worked!  Then I got home today and booted and Ubuntu froze at "loading boot files" or whatever the second orange thing says, after the kernal loads on boot.  Then I rebooted, and Ubuntu booted.

YAY!  Then, oh sh**, again.  

"The greeter could not load.  Trying alternative greeter"  Then I logged in.

" 'Nautilus' has unexpectedly quit"  "'Notification Area' has quit"  etc.

So I booted Windows (thank God it worked) and posted this desperate plea for help.  HELLLLLPPPP!!!

Backup everything straight away, definitely sounds like something is dying, hard disk perhaps?

---

### Post by saxofoner on 2006-11-17
Will do.  But I doubt it.  It's less than a year old.  The whole computer.  And I've had little boot problems all along.  This just seems most serious.  So I'll back up stuff.

By the way, I can still access the terminal in Linux.  I mean the Ctrl Alt F3 or whatever terminal.  I hope I can save my computer...

---

### Post by Swab on 2006-11-17
> **saxofoner said:**
> Will do.  But I doubt it.  It's less than a year old.  The whole computer.  And I've had little boot problems all along.  This just seems most serious.  So I'll back up stuff.

By the way, I can still access the terminal in Linux.  I mean the Ctrl Alt F3 or whatever terminal.  I hope I can save my computer...

In my limited experience, hardware goes when it goes, sometimes very quickly, sometimes it will last forever.  I've had plenty of components DOA, so I wouldn't rule out hardware.

I was having intermittent boot problems on a machine I build recently.  Turned out the power connector for the HD has a loose wire.  Damned power supply arrived that way.

---

### Post by saxofoner on 2006-11-17
I backed everything up, and rebooted into Ubuntu.  IT WORKS!  

See, every 30 Linux boots, it runs some kind of check on partition 6, I'm going to see what partition that is.  I think it got confused w/ Windows booting, and then trying to do that check.

---

### Post by saxofoner on 2006-11-19
Damn, I was wrong.  My PC is still screwed up.  It worked fine for about 2 days.  Just now it froze up, and I restarted, and I got some weird errors. 

One was "Memory exceeds maximum supported by BIOS"  and the other was GRUB Error 16.  

I've read about this.  I was, thankfully, able to boot from a live CD, and now I'm desperately calling for help.  Again.  ](*,) ](*,) ](*,) :evil: 

Can someone help me?

---

### Post by saxofoner on 2006-11-19
[http://www.freewebs.com/saxofoner91/Screenshot.png](http://www.freewebs.com/saxofoner91/Screenshot.png)

That's the screenshot of the partition table opened up from the liveCD.  It doesn't seem right.  I don't remember doing it like that.  The sda6 one is what causes all my problems.  Ubuntu doesn't seem to know what to do with a windows partition...  What should I do?   And about the maximum memory/BIOS thing.

---

