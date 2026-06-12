---
title: "Hardware Question"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by SamMessing on 2006-02-20
So I have been having trouble running the ubuntu live disc on my computer... whenever I try and run it, when the 'detecting hardware to find CD-ROM drives' window shows up, it gets stuck at 92% _regardless of what module it is loading._ I have checked the MD5sums of the disc image I d/led and it's fine, plus I have tried burning the disc a few times, to see if the first time was just a bad time, but everytime the same thing happens.


I am using a Dell Latitude D810 Laptop, is there any reason why this ubuntu live cd would be incompatable with my hardware? 

If not, what do I try next?

---

### Post by nickle on 2006-02-20
I had a similar issue with the hoary release. Some how it had trouble with my cdrom. I am afraid i didn't find a solution, but waited for Breezy.
Incidently, I also had a cdrom read problem with Fedora FC3; the problem disappeared with FC4....

Sorry, I can't offer naymore than that...

---

### Post by paxmaster on 2006-02-20
what is your video card is ?

---

### Post by Mr_Grieves on 2006-04-03
There is some problems getting the screen running.

I had to boot with these parameters to get it going:

```

linux vga=771

```

That was the case for me when I tried to install Ubuntu on my D810.

---

