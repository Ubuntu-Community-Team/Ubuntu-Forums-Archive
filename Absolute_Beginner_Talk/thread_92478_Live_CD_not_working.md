---
title: "Live CD not working"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by Klipi on 2005-11-19
I just downloaded the live CD and burned it. Then I booted my computer with the CD in my CD drive and only Windows XP started. I searched a few minutes and in a few threads there were some options that allowed me to change, in what order my computer boots from. I tried searching through my BIOS settings but found nothing. If someone could tell me where to change the boot order or give me some other help I'd appreciate it. :) 

Also, as this is my first post here, I'd like to say hello to everyone here on these forums.

---

### Post by stuporglue on 2005-11-19
A little investigation...

How old is your computer and what kind? Older computers may not be able to boot from CD. 

When you insert the CD into the computer, how many files show up on it? 

What is the name of the file you burned to CD?

Those'll help us figgure out what went wrong.  


Welcome!

---

### Post by Klipi on 2005-11-19
Thanks for the reply!

My computer is about two years old. AMD 2600+, ATI Radeon 9800 and 1 Gb of RAM. I'm using a DVD drive that reads R/RW in addition to DVD's and the CD is a CD-RW.

There's seven files and twelve folders and none of the folders is empty.

The file is ubuntu-5.10-live-i386.iso

Burned with Nero using burn from image or something like that.

I hope this helps!

---

### Post by stuporglue on 2005-11-19
> My computer is about two years old. AMD 2600+, ATI Radeon 9800 and 1 Gb of RAM. I'm using a DVD drive that reads R/RW in addition to DVD's and the CD is a CD-RW.

Sounds like it's new enough to boot from CD.

> There's seven files and twelve folders and none of the folders is empty.
So, it seems you've burned it correctly

> The file is ubuntu-5.10-live-i386.iso
And you're using the right image. 

That covers the most common mistakes. :-) 

I'm guessing you just missed the CD boot option in your bios. I'd go back to the BIOS and poke arround there untill you find it. It's probably labed "boot order" or "startup order" or something similar. It probably has items like "Floppy" "Onboard NIC" "HD", and hopefully "CDROM" in a list. You want to make sure that CDROM is before HD on that list. 

Good luck

---

### Post by Klipi on 2005-11-20
After looking around in the BIOS a bit moreI managed to stumble upon the boot order. It was right there, in the middle of Advanced Options, but I just looked past it. Well thanks for your time.

I'm posting this from Ubuntu. Looks great so far! :)

---

