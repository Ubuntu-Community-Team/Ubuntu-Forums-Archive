---
title: "ATI Drivers"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by bob74 on 2007-11-11
I cannot get tvtime to run which I believe is due to incorrect ATI driver.
I downloaded the driver from ATI but cannot open the file- I get the message cannot open file it may be binary. Can some kind person explain how I overcome this.
I have looked at other posts regarding TVtime problems and have had no suggestions work for me. I have Radeon X1300. Incidentally this ran without any hassle under feisty.

---

### Post by Daveth on 2007-11-11
they seem to have an automatic installer for linux drivers. Is this what you downloaded? If, so this is relevent

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.42.3-inst.html)

---

### Post by bob74 on 2007-11-11
Thanks for your quick response. I have looked at the link and may have to come back for further help since I am still getting to grips with Linux commands etc.
Thanks once again.
Bob

---

### Post by bob74 on 2007-11-11
sh ./ati-driver-installer-8.42.3.run
Response is "cannot open ATI etc.  Am logged in as superuser. Where am I going wrong?
Hope you are still looking--Bob

---

### Post by Ub1476 on 2007-11-11
You have to use "sudo" in front of the command, however, that driver is extremely buggy. I suggest you use the driver from "Restricted Driver Manager" in System>Administration.

---

### Post by kshane on 2007-11-11
> **bob74 said:**
> sh ./ati-driver-installer-8.42.3.run
Response is "cannot open ATI etc.  Am logged in as superuser. Where am I going wrong?
Hope you are still looking--Bob

I run that driver and it works great for me  Try the code below:

```

sudo bash sh ./<driverfilename>

```

That's how I installed it.

Kevin

---

### Post by bob74 on 2007-11-11
HelloKshane
Sorry to be so thick- can you spell out to an old newbie exactly what the command should include.
Thanks, Bob

---

### Post by kshane on 2007-11-11
> **bob74 said:**
> HelloKshane
Sorry to be so thick- can you spell out to an old newbie exactly what the command should include.
Thanks, Bob

No prob, Bob...

Cut n paste this:

```

sudo bash sh ./ati-driver-installer-8.42.3.run

```

In your terminal, of course...

Better?

Kevin

---

### Post by carlosjuero on 2007-11-11
> **kshane said:**
> No prob, Bob...

Cut n paste this:

```

sudo bash sh ./ati-driver-installer-8.42.3.run

```

In your terminal, of course...

Better?

Kevin
the actual file name for the new drivers should be ati-driver-installer-8.42.3-x86.x86_64.run :) [ATI user here]

---

### Post by kshane on 2007-11-11
> **carlosjuero said:**
> the actual file name for the new drivers should be ati-driver-installer-8.42.3-x86.x86_64.run :) [ATI user here]

Oops!  I stand corrected...

Thanks!

Kevin

---

### Post by mikeserv on 2007-11-11
I have the exact same card and am currently using fglrx.  What is tvtime?  Is it to get your TV-Out to work?  If so, I may be able to offer a simpler solution.  I remember searching and trying for a week just to get that to work.  Get back to me and I can provide you with the correct lines for your xorg.conf and a simple script for automating the process of switching between tv and monitor.

-Mike

---

### Post by bob74 on 2007-11-12
Thanks you guys but I get a message "cannot execute binary file". Where am I going wrong please.
Bob

---

### Post by bob74 on 2007-11-12
Mikeserve
I'm trying to get tvtime to work using wintvgo card which is ok on my dual boot XP. When I click on the application all I get is a flash on the screen and nothing apart from desktop. If I enable restrict driv man it says none are needed for my system. I presumed the trouble is to do with ATI
and d/loaded the driver but cannot open it. As I said earlier  the tvtime app worked ok in feisty.
I'm ok with everything else in Ubuntu so am completely puzzled .
Bob

---

