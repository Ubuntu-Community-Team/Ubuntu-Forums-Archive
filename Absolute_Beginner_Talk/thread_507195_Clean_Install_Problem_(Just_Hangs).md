---
title: "Clean Install Problem (Just Hangs)"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Sicundercover on 2007-07-22
Ok Im a newb to Linux so there will be some stumbles here. Im an old PC/Mac vet and I cant go any longer without knowing Linux. I figure Ubuntu would be a good place to start.

So I have a AMD X2 5200 w/ 6 Gigs of Corsair XMS RAM, Asus Crosshair Mobo, Nvidia BFG 8800GTX, 

I also have Vista x64 installed on a Raid 0 (2 WDC 75Gig 10,000 Raptors), Xp pro SP2 on another drive , and I wish to put Ubuntu on a 3rd drive. 

I downloaded the AMD x64 version from the home site checked the integrity of the file and burned it at 4x using power iso.

Problem: When I boot from the live CD I get the selection screen I select install Ubuntu it loads the kernel but then sits at a blinking prompt and says the following.

Kernel Alive

Kernel direct mapping tables up to 100000000 @ 8000 - d000

---

### Post by dougfractal on 2007-07-22
Wow what a machine ;-)

Try the gusty development Live CD.It is pre-release, but is also bleeding edge.
Be prepared for regular updates.

Or just play with [knoppix]("http://www.knopper.net/knoppix/index-en.htm") till the the kernel devs have patched your mobo.

---

### Post by Sicundercover on 2007-07-22
Thanks for the advice Im downloading Gutsy Gibbon now, Ill repost in here if I have more problems or if I fix it.


Thanks for the complament on my system, this system is my play around system. It inherates parts from my main system when I upgrade parts.

My main workstation contains, AMD X2 6000, Raid 5 HDD configuration, 8Gig RAM Corsair XMS, 2x Nividia FX5600 SLI (second 5600 is newest edition), Asus Crosshair Mobo.

---

### Post by Sicundercover on 2007-07-22
Well Gutsy through the same fit.

Next try is alternate.

Now I just have to find a good alternate install page.

---

### Post by Sicundercover on 2007-07-23
Well I tried the alternate cd and chose Text Install and same thing happens 

Things arnt looking to good for my Ubuntu review. Im gonna give it a week and see if I can figure it out. However I posted my same post on a 3D community I use and got far more responses.

Also, during Vista RC1 (granted I had alot of problems with RC1) I would get as many as 25 replys in a day.

Not looking so good over here.

---

### Post by asmoore82 on 2007-07-23
try forcing the Linux kernel to only use the first 4 gigs or your RAM....

at the Ubuntu Live CD selection screen hit escape (I think)and add
```
mem=4G
``` to the boot params

---

### Post by pyros on 2007-07-23
I belive this bug has been reported before, but due to a lack of information it was never resolved, If you are willing to help developers resolve this issue, please see this page:
[https://bugs.launchpad.net/ubuntu/+bug/122022](https://bugs.launchpad.net/ubuntu/+bug/122022)

---

### Post by Sicundercover on 2007-07-24
Yea the bug was never resolved. I then posted more info there and got a notice that it was a duplicate bug report and was directed to another thread where the bug had still not been resolved. 

Going to try Fedora to see how that works out.

---

### Post by Sicundercover on 2007-07-25
I love how this whole forum is people asking questions and no one getting answers.

Hmph Ubuntu what a joke.

---

### Post by pyros on 2007-07-26
I really think that this [link](http://ubuntuforums.org/showpost.php?p=1488521&postcount=1) could help you greatly.

---

