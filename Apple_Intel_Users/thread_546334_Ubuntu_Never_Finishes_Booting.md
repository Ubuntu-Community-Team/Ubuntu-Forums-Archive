---
title: "Ubuntu Never Finishes Booting"
date: 2007-09-08
forum: Apple Intel Users
---

### Post by xluryan on 2007-09-08
While trying to install 7.04 on my friends MacBook Pro, I'm running into some issues. I put in the live cd, start it up, choose the first option for start ubuntu or install, but then 10 seconds or so in the boot process it just stops, then the screen goes blank, and nothing.

I've tried both quiet and non-quiet modes. Same result, just different amounts of output. Any suggestions?

I *have* checked the cd for md5sum, it checks out ok.

---

### Post by benanzo on 2007-09-08
Did you check the CD after burning it or did you just check the ISO after downloading?  This is quite indicative of a faulty download/burn.

Normally when the boot process dies (as yours does) it will spill out some error.  If the screen just goes blank it usually means there's trouble getting instructions as if from a faulty CD.

---

### Post by alephsmith on 2007-09-08
If it is a Santa Rosa Macbook Pro you need to change the boot options.

Select safe graphics mode
Press F6 to edit boot options
Remove quiet and splash
Insert all_generic_ide

If you search the Santa Rosa thread there should be a better explanation.

---

### Post by xluryan on 2007-09-09
Reply to post #2: I did check all that, same result.

Reply to all above: I added "vga=791" to the boot options and that got me much further, but then I got the screen attached.

I haven't tried the option from post #3 yet, but definitely will. Do you think that will solve this screen?

---

### Post by Sef on 2007-09-09
> haven't tried the option from post #3 yet, but definitely will. Do you think that will solve this screen? 

No one can say for sure.   But it is worth a shot.


> I *have* checked the cd for md5sum, it check out ok.

Did you burn the iso at 4x or less?  More can cause corruption.

---

### Post by russo.mic on 2007-09-09
You need to install xorg-driver-fglrx package, I believe it's called. 

Then run aticonfig to configure it.  There are plenty of help tutorials on that among the forums.  You have to get to a command line then follow the steps required.  You will then have to do it a second time once the system is installed.

Good luck!

Russo

---

### Post by cyberdork33 on 2007-09-09
> **russo.mic said:**
> You need to install xorg-driver-fglrx package, I believe it's called. 

Then run aticonfig to configure it.  There are plenty of help tutorials on that among the forums.  You have to get to a command line then follow the steps required.  You will then have to do it a second time once the system is installed.

Good luck!

Russo

This is correct unless you are on a Santa Rosa machine with nVidia graphics.

---

