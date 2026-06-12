---
title: "Ubuntu 6.06 LTS fails to load from CD"
date: 2007-04-06
forum: Apple PPC Users
---

### Post by Lefkows on 2007-04-06
I have an Imac G5 with 250MB RAM, 1.6 GHZ processor. When I attempt to load the OS from a Ubuntu CD  (Live CD) the progress bar gets to the end but then fails. I have no external devices connected. I have never been able to load the OS from the CD even though I have tried several times. I know my hardware is all OK. Any ideas why the load fails at the very end? :(

---

### Post by x64Jimbo on 2007-04-06
Have you tried Edgy or the Alternate Install disc?

---

### Post by Lefkows on 2007-04-06
Thanks for your quick response X64Jimbo. I am really new to Ubuntu so I am not familiar with Edgy or the Alternate Install Disk. Right now I did not want to install Ubuntu but just use Ubuntu CD as a LiveCD ,i.e., run off the CD. If you could provide me with some info about Edgy or the Alternate Install CD that would be great.

Thanks Stan

---

### Post by Auria on 2007-04-06
> **Lefkows said:**
> Thanks for your quick response X64Jimbo. I am really new to Ubuntu so I am not familiar with Edgy or the Alternate Install Disk. Right now I did not want to install Ubuntu but just use Ubuntu CD as a LiveCD ,i.e., run off the CD. If you could provide me with some info about Edgy or the Alternate Install CD that would be great.

Thanks Stan

Edgy is simply a more recent version than what you're using. (it's the weird name for Ubuntu 6.10)

Alternate version cannot boot as a live CD so if you're not interested in installing then it's not the right solution

---

### Post by Lefkows on 2007-04-07
Thank you for your response Auria. I will try downloading Ubuntu 6.10 and see what happens. If I were to install Ubuntu on an external HD how would I boot up the system from it. If Tiger recognizes Ubuntu as a system I can boot from and then I could use the Startup Disk function in the System Preferences. If not then could I use the startup key combination to tell the system to ignore the internal HD?

---

### Post by Lefkows on 2007-04-07
I downloaded Ubuntu 6.10 LTS and was able to load the OS. One thing I noticed is that the fans speeded up. They seem to be working much harder than with Tiger. When I shut the system down the disk got ejected and a note was displayed on the screen telling me to hit ENTER. When I hit ENTER nothing happened and I had to manually shut the computer down. Anyone els e experience these anomalies?

---

### Post by Auria on 2007-04-07
> **Lefkows said:**
> I downloaded Ubuntu 6.10 LTS and was able to load the OS. One thing I noticed is that the fans speeded up. They seem to be working much harder than with Tiger. When I shut the system down the disk got ejected and a note was displayed on the screen telling me to hit ENTER. When I hit ENTER nothing happened and I had to manually shut the computer down. Anyone els e experience these anomalies?

When you're running from the liveCD, i'm pretty sure it's normal the fans are noisy because the CD has to be constantly spinning

as for the shutdown error, it's a known bug but harmless because when you get to this point the computer is ready to be shut down anyway

---

### Post by ZoiaGuyver on 2007-04-07
Auria is almost correct about the fans, its actually a bug with the 6.06 and 6.10. I believe its been fixed with 7.04 (Fiesty) thats what i have read.

Its something to do with the Thermal controller for the fan not running correctly (if what ive read is correct), this causes the fans to be at full all the time rather than just when needed.

I would suggest either getting it installed and trying a dist-upgrade to the Feisty beta (pretty stable as far as ive seen) or wait for the Fiesty release on the 19th (i think thats when its due).

If your willing to give the beta a try the command you would need is 

sudo "update-manager -c -d" (think thats right not 100% as im not on my Ubuntu box to test it)

Hope this helps

---

### Post by Lefkows on 2007-04-08
Thank you for your response Z. If I install Ubuntu on an external HD how do you boot from it.

---

### Post by ZoiaGuyver on 2007-04-09
I dont think exteranl HD's are supported as a boot option by OF (tbh im not 100% as ive always installed on internal drives).

Sorry i cant help more on this one but ive never tried it :D maybe someone who has can tell you more.

---

