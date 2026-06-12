---
title: "[SOLVED] Suspected corrupted bios."
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by percy_vere_uk on 2008-01-19
Hi

Having encountered a problem loading gutsy on a dual boot system with windows xp I was forced to re install xp. On 

hindsight I probably should have allowed xp to use the whole of the hard drive and then re installed gutsy from the 

live disk. Anyhow xp ran fine that is until I turned off the computer. Next day neither the
cd/dvd drive or the floppy drive are recognised when the computer is turned on. Nothing can be run from either just 

an initial short activity from cd/dvd drive, the computer does not boot. I can only guess that perhaps the bios has 

either been corrupted or destroyed. If there are no other suggested possible causes then is there anyway that I can 

obtain and re install a new bios. 



percy

---

### Post by dstew on 2008-01-19
It depends on your motherboard. Sometimes it is possible to restore a BIOS. You have to look at the manufacturer's site and the motherboard manual. I recall looking at this once, and there was a special plug that you put onto one of the motherboard ports. Then a new BIOS could be loaded from a floppy drive.

---

### Post by fatality_uk on 2008-01-19
> **percy_vere_uk said:**
> Hi
Having encountered a problem loading gutsy on a dual boot system with windows xp I was forced to re install xp. On hindsight I probably should have allowed xp to use the whole of the hard drive and then re installed gutsy from the live disk. Anyhow xp ran fine that is until I turned off the computer. Next day neither the cd/dvd drive or the floppy drive are recognised when the computer is turned on. Nothing can be run from either just an initial short activity from cd/dvd drive, the computer does not boot. I can only guess that perhaps the bios has either been corrupted or destroyed. If there are no other suggested possible causes then is there anyway that I can obtain and re install a new bios. 
percy

Be VERY careful before you try and reset your BIOS. It's unlikely that installing Ubuntu would have directly effected your BIOS. I suspect it's more likely that:

a) You are trying to boot from the CD/DVD drive without a bootable disk in there (Sorry if it seems silly but I have to ask.)
b) Your hard drive has failed or a connector has come lose.

Flashing the BIOS should be a LAST resort.

Can you try and run the Ubuntu live CD and se if you get anything from that

---

### Post by bwhite82 on 2008-01-19
This BIOS is pretty difficult to screw up (other than when you are attempting to flash it and something goes wrong there). Installing and uninstalling things from the Hard disk will not affect BIOS. What error messages (assuming there is any) show up on screen when you boot? Can you enter the BIOS when you first start your computer?

---

### Post by percy_vere_uk on 2008-01-20
Thanks for your replies on this folks. On turning on the computer the hard disk runs but there is no sound from the heads  trying to access data. Neither the floppy drive  or the cd/dvd will boot to anything. I have various boot disks none of these will do anything. I have tried the gutsy live cd, same thing. I have tried various F keys at the point were the computer should be booting, nothing and nothing on the screen. 

This is a fairly new computer (just out of warranty of course) These factors do I know point to a hardware failure but I am certain that this was down to xp not liking finding gutsy on there.

I think it must be a question of accessing and correcting this by connecting another computer to it. Because of this problem and to get back online I had to by a laptop last week so I could do this but of course with no risk to the laptop!!!

I have managed to find some information on the bios 'bios 0202 american megatrends Inc' . I will try to find a website for this. In the meantime any more suggestions please.

Percy

---

### Post by Malta paul on 2008-01-20
Hi, It is very unlikely you BIOS is bad, but it is possible that your BIOS setting might have changed.
As Soldierboy said when you switch on your computer will it start to boot up? If so you should be able to enter the BIOS setup pages. Depends on your system it usually requires you to press Delet or F1 at the start of the boot sequence. 
Best think is then to post your findings on this forum.
Good luck

---

### Post by bumanie on 2008-01-20
1. It is highly unlikely that installing software would stop the hard drive heads accessing data
2. Xp is not smart enough to know anything other than 'an unknown file system' is on the hard drive, ie it won't stuff things up for that reason
3. _If_ you've had a hard drive failure, updating the bios won't resurrect the hard drive
4. I would be reticent to go head-long into updating the bios at this stage due to the above.
Firstly check all your connections in case one/some have come loose somehow.
If everything was working fine until reboot that shows that the hardware was (to that point working) as was xp.  Also if you can't boot how do you propose to do a bios upgrade?
It is possible you have had a hardware failure, but it is not necessarily the bios or hard drives. May be your power supply unit is shorting or something.
Try and download and burn super grub disc, if the computer can be booted, this tool will do it. It can boot both windows and gnu/linux. If this doesn't work you will have to eliminate hardware problems one by one. Very painful, but often a good learning experience.

---

### Post by percy_vere_uk on 2008-01-22
Hi

I have now got the system to boot. It was almost certainly a corruption of the bios, because as I have said I could not get the dvd/cd or floppy to do anything at all, the screen was also dead.  Having gone to the 'asus' site I could not get any info on this motherboard. So what I did eventually was to remove the battery from the board. You need to leave this out for quite some time. 10 minutes was not enough so I left it for 24 hours. Probably because these types of memory use very small amounts of power and I guess that having only turned the computer off for a short while there was enough current kicking around inside the computer to support the bios. 

Anyhow after this it booted and I was able to reset the bios to the original value. I know that most folk have said otherwise but I am convinced that this was caused by having to re-install xp. The security to avoid piracy on MS products goes to the extreme not only did I have to enter the MS key when re-installing. Once it was up and running and before you can log in they force you to go on line (not possible until you can get in and configure your connection) so at the moment I am still locked out. 

Don't care too much though because gutsy is up and working!

Thanks for all your input on this folks.

percy

---

