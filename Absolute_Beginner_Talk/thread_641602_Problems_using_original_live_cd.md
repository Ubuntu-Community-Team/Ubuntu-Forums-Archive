---
title: "Problems using original live cd"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by eimor on 2007-12-15
i got a new laptop and gave my older one to my gf, but using the same live cd the ive used to install ubuntu gutsy in my laptop i cant get to boot with the live cd:( and i get this warning
```
120.680364 kernel panic - not syncing: VFS - unable to mount root fs on unknown-block (104,1)
```
:confused:

if i try to boot in graphic mode or even in safe mode the loading bar goes back and forward a few times and then it just stops. 
Im fed up with this new laptop, i think the old one was better, despite the new one has nvidia geforce go 6100 onboard. Hope someone can help me with this cause this is the first post im making on the horrible windows.

---

### Post by Ub1476 on 2007-12-15
Have you checked the CD for defects? Might have been slightly scratched over time.

---

### Post by jimbob on 2007-12-15
Download and burn the alternate (text mode) CD.  It seems to work a lot better with laptops.

---

### Post by eimor on 2007-12-16
i did the cd check and it was fine, but i did some research and i think this laptop might have an scsi hard drive, could this have something to do with my problem?

---

### Post by logos34 on 2007-12-16
it almost certianly does not have a scsi drive...sata maybe (ubuntu uses the libata storage driver which sees all drives as 'sd_' instead of 'hd_').  

jimbob is right--get the alternate cd.

---

