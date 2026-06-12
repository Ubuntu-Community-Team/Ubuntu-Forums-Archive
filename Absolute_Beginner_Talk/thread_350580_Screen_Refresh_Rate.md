---
title: "Screen Refresh Rate"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2007-01-31
Why when I use "sudo dpkg-reconfigure xserver-xorg" to configure my monitor it gives me the right resolutions, but the wrong refresh rates.  It produces all refresh rates at 60hz.  My monitor is capable of up to 85hz so why does it not show the correct refresh rate.  I always end up using the modeline generator to get the correct refresh rates.

---

### Post by tchoklat on 2007-01-31
If you have an LCD it won't matter I understand. Mine does the same. I have a 19 inch Syncmaster and it runs at 1280 X 1024 with the only options of 56 or 50 Hz refresh rate. I cannot see a difference with either.

I am open to be corrected on this though

Tony

---

### Post by alienexplorers on 2007-01-31
My monitor is an old 14" CRT.  It is as picky as hell about setting refresh rates.  Some it likes and others it burps on.

---

### Post by alienexplorers on 2007-01-31
Any body have an idea how to fix this problem.

---

### Post by Scarlett on 2007-01-31
I had an old CRT and the blinking and resizing at first was horrible.  I tried for two days to fix it and I'm sorry I can't give you easy step by step instructions because I honestly don't know what all I did to make it work.  But here a link to some of the threads that helped me finally get it sorted out.

[http://www.ubuntuforums.org/showthread.php?t=250070](http://www.ubuntuforums.org/showthread.php?t=250070)

---

### Post by tchoklat on 2007-01-31
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by ed-j on 2007-01-31
Novice Alert!

When you use the command, click until you reach the part that asks you if you would like to set up the resolution and refresh rate as "easy, medium or advanced", choose "medium". This should give you a list of resolutions and refresh rates to choose from.

Only choose that which you know your monitor can support.

---

### Post by alienexplorers on 2007-02-01
Ed-J,
have tried using the medium setting and it gives me a list of screen resolutions and refresh rates that my monitor will not work with, so how does this help me.  I have tried this before and it did not work then either.

---

### Post by tchoklat on 2007-02-01
,,, click on the resolutions and refresh rates you want, they will be written to a file on your PC. You can then go into <system><preferences><screen resolution> to change them to the one you want. This is written to file also.


Tony

---

### Post by alienexplorers on 2007-02-01
Thanks for all of your help.  I have decided instead of messing around more with this ati card and old crt that I would finally put out a few bucks and get a new pair.  Going with Nvidia this time and LCD screen.

---

### Post by ed-j on 2007-02-02
Just lost my e-mail. Back in 5 minutes!

---

### Post by ed-j on 2007-02-02
Back again( Novice Alert)

If you want to be able to change the res', do not buy an LCD or TFT.

You can buy a 19" or 21" CRT used for £50 or less (Liyama, Sony most expensive, but worth it for 0.25dp) or a "no name" as below for probably less than £30.

My monitor (Bless Her):

19" Tatung CRT, build date Nov 2nd 2000!
Runs Ubuntu 5.1 @ 1280x1024@ 85Hz
          Ubuntu 6.1 @ 1600x1200@75Hz

I would recommend the move to Nvidia, there is new and legacy support in Add/Remove. With your system spec you might be able to run 6.06 or 6.1 with a used Nvidia card that suits your machine, if not, try 5.1. I still run this on my old system with an ATI Xpert Pro 2000 (the year, not the speed) @ 1024x768@85Hz. You would have to check out the graphics card, but the used monitor I would recommend.

In the meantime, try setting your graphics card choice to "Vesa" and see if this gives you any options.

Best of luck!

---

