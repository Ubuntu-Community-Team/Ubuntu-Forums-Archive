---
title: "dual boot os8 and xubuntu on powermac G3"
date: 2006-12-28
forum: Apple PPC Users
---

### Post by deezay on 2006-12-28
i've recently bought an 'older' school powermac G3 233mhz with 192mb of ram.

this is my first mac and i got it cheap (<20$ on ebay). and i have 0 experience with mac, but i'm really loving linux. i've got a copy of ubuntu 6.10 on my duron 1800, and xubuntu on my pentium 2 300.

what i'd like to know is...

A) how challenging is it going to be to do a dual boot with os8 already installed.. if this is even possible, as i have absolutely no other macs and no way to resize the hard drive partitions.

B) can xubuntu run on this old of a mac? it's a G3, but pre-imac era... beige desktop box.. very boxy looking. right now xubuntu w/ fluxbox is running fine on my p2 300mhz with 64mb of ram, so i don't see a problem.. unless there are issues with the ppc build.

does anyone have any OLD school macs running linux with success? i've read about bootx and assume i will need that to boot from the linux cd, since i'm running an old world mac. i got this just to see if there are any benefits from running the risc style processor compared to the cisc... since i have a direct comparison with a p2.

i've been browsing the ppc posts and have seen that some users are experiencing problems with their cpu's running maxed out for periods of time.. is this a ppc problem or an imac problem?

basically anyone with some insight as to whether or not running xubuntu on this machine would be a smart move, please post. thanks!

---

### Post by 3rdalbum on 2006-12-29
If you've not got an appropriate Mac OS install CD, you're really going to be limited in what you can do. The Xubuntu installer cannot resize Mac OS partitions. Best bet would be to look on Ebay and find an OS 8, 8.5 or 9 CD that is not locked to a particular computer. (with Apple, the operating system CDs that come with the computers only work on the computers they actually came with, sorta like those "System Restore" discs that come with PCs except more so).

---

### Post by deezay on 2006-12-29
ok, i'll give that a try. is it even worth dual booting? is os 8 worth keeping? even os 9?

---

### Post by 3rdalbum on 2006-12-30
The "old-world" Macs (i.e. the beige ones) need to dual-boot. Their OpenFirmware does not support directly booting Linux, so you must always boot OS 8 or OS 9 first and run the BootX program ([http://penguinppc.org](http://penguinppc.org)) to load Linux.

It's a bit of work to get it all running, but it is possible. I myself got a Live CD running on an Oldworld back before I'd used Linux.

It's your call. Personally, I think keeping Mac OS 8 is also a good move.

---

### Post by Brian Smith on 2006-12-30
I'm dual booting OS9 and Xubuntu on a Beige oldworld G3 (though slightly faster than your 233, mine is over 300MHz with 384Mb.)  The easiest way for you to achieve this will probably be the same way that I did - adding a second hard drive for the Xubuntu partitions.  Booting from the Xubuntu CD is not well documented for an oldworld mac.  I'm enough of a geek to spend the time making such an installation work simply to keep the machine usable as a backup, spare, or loaner, but I don't think I would have specifically bought one as a Linux project.  You seem to enjoy the project, though, and I encourage you to give it a shot, since you've already done installations previously and are not stranger to hardware in general, I suspect you'll achieve what you want with it.

---

### Post by deezay on 2006-12-31
thanks brian and everyone else. dual booting here i come..

thanks!

---

### Post by handylinux on 2006-12-31
> **3rdalbum said:**
> ... (with Apple, the operating system CDs that come with the computers only work on the computers they actually came with....
Often, but not always the case. For instance, I have a Mac OS 8.6 Install CD that came with a 'Lombard' PowerBook G3 that's worked fine with any other Mac I've tried it with that can run that OS version (mostly other PowerBook models), and a 9.1 Install CD from a PowerBook G4 that's also worked with other Macs. Of course it's best to get a retail version OS CD if possible, but others might work -- though I don't know for sure how to find out other than trying them. For a 233MHz "beige" (actually platinum) PPC, Mac OS 9.1 would be best, especially if you want to use the Mac OS also. 9.0 or 9.0.x would also be fine, as you can download the free 9.1 updater from Apple.

The best resource for older Macs is **[Low End Mac]("http://lowendmac.com/")**; click the "Mac Specs" button to learn more about the Mac you have, and do a search for "Linux" for discussions about using Linux on Macs.

---

