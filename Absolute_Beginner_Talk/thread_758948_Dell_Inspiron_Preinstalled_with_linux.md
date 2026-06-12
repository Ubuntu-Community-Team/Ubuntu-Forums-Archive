---
title: "Dell Inspiron Preinstalled with linux"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Long_Live_Linux on 2008-04-18
Hi all,

I was looking at a Dell Inspiron 1525N Laptop that comes preinstalled with ubuntu 7.10. ( go to: [http://www.dell.com/content/products/productdetails.aspx/inspnnb_1525?c=us&l=en&s=dhs&cs=19&~oid=us~en~29~linux_3~~]("http://www.dell.com/content/products/productdetails.aspx/inspnnb_1525?c=us&l=en&s=dhs&cs=19&~oid=us~en~29~linux_3~~") )

I was wondering if I could add a built in webcam to it and it would work. Has anyone else tried this?? Thanks for the help!

---

### Post by ACMarina on 2008-04-18
I'd think that if Dell will let you add it in, it would about have to work..

---

### Post by Long_Live_Linux on 2008-04-18
Yeah that is what I kind of think, but you never know....

---

### Post by NineKnuckles on 2008-04-20
Hey Long_Live_Linux,

   I have a 1525 (pre-installed) and asked for the built-in webcam.  It does actully work, but I needed to change some settings to vfl2 before it would.  Some programs don't give you the option to use vfl2 but others do.  The only thing I am concerned about is that I seem to only be able to take 1.3MP shots when it's supposed to be 2.0!  But other than that (which I'm hopin to see if it can be fixed, when I get round to it) it works well.
   Hope that helps.

---

### Post by Long_Live_Linux on 2008-04-20
Thanks a bunch! I was wondering what you had to modify?? Could you please tell me how?? Thank you again!!

---

### Post by NineKnuckles on 2008-04-21
Erm just a GUI setting really (should be the same with any program you use with your webcam, in the settings tab usually), no command line was needed. XSane Image Scanner came default on my 1525, it's what I first tried my webcam with.  I found out that it didn't support vfl2 so I ended up downloading Cheese, which is great by the way.  It's in the repos, I just used add/remove.  I think it worked straight away, but other apps might need changing (settings tab).  Also, if you've forced compiz fusion to work with the intergrated graphics card on the 1525, Cheese won't work - you have to disable all effects.

---

