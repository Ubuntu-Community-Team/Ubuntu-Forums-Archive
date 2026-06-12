---
title: "Video Card failure dissaster."
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by andyJH on 2006-07-29
Hello.  I am a complete newbie but am very impressed with the Linux world in general and Ubuntu in particular.

I have 2.4 ghz P4 with a gig of ram and two 80 gig drives with WinXP installed on the master drive.  I ***had*** a Ti4200 video card.  

I formatted my slave drive and installed Ubuntu 6.06.  It was easy and performed flawlessly right out of the "box".  It was an eye opener for this windows user.

Then dissaster struck.  My video card died a slow death that had me working for an entire weekend to diagnose the problem.  My computer would not post.  I finally discovered it was the vid-card and replaced it with an ATI card: msi rx9250.

After I got my computer to post and continue to boot, my Ubuntu installation hung at the "loading esential drivers" screen.  I thought that the problem was caused by not being able to remove my previous vid-card before installing the new one.

I tried booting from the Ubuntu disk with the same results.  I then deleted the slave drive partition, created a new one and formatted it.  I figured the original install went well, so I will go back to square one and do it all over.  

So I am now sitting with the same computer with a new video card.  WinXP on the master drive and an empty, freshly formatted slave drive.  I put the Ubuntu CD into the drive and reboot.  It hangs at the "loading esential drivers" screen.

Any ideas?

Thanks in advance,
Andy.

---

### Post by ovimunt on 2006-07-29
When you boot from the live CD you should have an option to start in safe mode. That should help you avoid the graphics problems. Try starting with that option and see what happens.

---

### Post by andyJH on 2006-07-29
> **ovimunt said:**
> When you boot from the live CD you should have an option to start in safe mode. That should help you avoid the graphics problems. Try starting with that option and see what happens.

Same result.  It hangs at the "loading essential drivers" page.

Could there be some remaining trace of my first install somewhere on either of my drives?  Is my new MSI RX9250 TD128 video card supported?

Thanks again,
Andy.

---

### Post by andyJH on 2006-07-30
Does anyone have any idea why Ubuntu will not load (hangs on the "loading essential drivers") even in safe graphics mode?

Thank you,
Andy.

---

### Post by Drakkor on 2006-07-30
I do know that ATI cards,as I have seen on this forum, seem to have alot of problems with linux. I have a nvidia G4 Ti4200 video card,and it works flawlessy. Sorry,that's all I know.
Edit: Install problem, I know it's probably a long shot,but are you sure the install disk is still ok ?  Maybe check the disk for defects ?

---

### Post by andyJH on 2006-07-30
Ok.  I will only be out 30 bucks for the card, I may as well get a different one.  I am just worried that a geforce card will make no difference.  Thank you.

---

### Post by Drakkor on 2006-07-30
As I said make sure your install disk is still OK !!
I think that's the 2nd option,when you put your Ubuntu disk in:
2.Check CD for defects
I had a problem installing Ubuntu because of 1 checksum error,even though the md5sum was good !  Good luck !

---

### Post by andyJH on 2006-07-30
Ok, even if I choose check disk for error I still end up going right to the loading essential drivers screen hang up.  Is there any way that there could be a remanent of my old install in the MBR or something.  Is there anything left on my master (xp) drive from my former slave ubuntu install?

Thanks again.
Andy.

---

### Post by Drakkor on 2006-07-30
Assuming you were dual booting,you should probably still have grub on your mbr.To fix this,just boot from your XP disk,wait till you get an option to hit "R" for repair and at the prompt type in fixmbr   That will write a new master boot record and allow you to only boot to Windows,then, try re-installing Ubuntu.
Good Luck !!  ;)

---

