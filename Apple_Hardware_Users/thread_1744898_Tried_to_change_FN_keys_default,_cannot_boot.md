---
title: "Tried to change FN keys default, cannot boot"
date: 2011-04-30
forum: Apple Hardware Users
---

### Post by micseydel on 2011-04-30
I followed the instructions at [https://help.ubuntu.com/community/AppleKeyboard#Corrections](https://help.ubuntu.com/community/AppleKeyboard#Corrections) doing the recommended change, but after I rebooted everything hangs at either a purple screen or purple with "Ubuntu" and the orange dots.

If I boot in recovery mode and do a "resume boot", it works fine as a terminal session but I need X. I also tried reversing what I did while in recovery mode but that didn't fix the problem. I'd have backed up my kernel if I knew that command was going to overwrite it. I also tried installing the kernel over again with apt-get but my new Natty install only has one kernel so I didn't have anything to fall back on if I deleted the current one.

I'm running Ubuntu Natty on a Macbook Pro 5,5.

---

### Post by Hatsune Miku on 2011-05-01
> **micseydel said:**
> I followed the instructions at [https://help.ubuntu.com/community/AppleKeyboard#Corrections](https://help.ubuntu.com/community/AppleKeyboard#Corrections) doing the recommended change, but after I rebooted everything hangs at either a purple screen or purple with "Ubuntu" and the orange dots.

If I boot in recovery mode and do a "resume boot", it works fine as a terminal session but I need X. I also tried reversing what I did while in recovery mode but that didn't fix the problem. I'd have backed up my kernel if I knew that command was going to overwrite it. I also tried installing the kernel over again with apt-get but my new Natty install only has one kernel so I didn't have anything to fall back on if I deleted the current one.

I'm running Ubuntu Natty on a Macbook Pro 5,5.

If you boot into a terminal; try typing this

```
startx
```

This will start a X enviorment if it gives an error... **_WRITE IT DOWN AND POST HERE!!! <3 <3_**

also try this command as well

```
service gdm start
```

---

### Post by micseydel on 2011-05-01
Thank you for the attempt to help, but I ended up reformatting.

---

