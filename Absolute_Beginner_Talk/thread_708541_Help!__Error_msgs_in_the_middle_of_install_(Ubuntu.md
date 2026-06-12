---
title: "Help!  Error msgs in the middle of install (Ubuntu 7.10 alt cd)"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by SeaQiyas on 2008-02-26
After problems install from the Ubuntu 7.10 Live CD, I took others' advice to try the alternate CD.
([http://ubuntuforums.org/showthread.php?t=707134](http://ubuntuforums.org/showthread.php?t=707134)  I originally posted this on that thread, but makes more sense for a new thread)

Computer:  Acer Aspire laptop 3003Lci, 40GB HD, 256 DDR, AMD Sempron processor (1.8Ghz) with a DVD/CD-RW drive

Downloaded the alternate CD, checked the md5sum, all okay, burned to cd.

Now I'm installing on the Acer laptop, and these are the error msgs:

Debootstrap warning
File://cdrom/pool/main/x/xkeyboard.config/xkb-data_0.9-4ubuntu3-all.deb was corrupt

pressed enter to continue, then
Debootstrap warning
file:///cdrom/pool/main/z/zlib/zlib1g-1.2.3.3.dfsg.5ubuntu2_i386.deb was corrupt
pressed enter to continue, then after about 30 seconds of what looked like more installation,

Debootstrap warning
Failure while configuring base packages. This will be attempted 5 times.
Had to press enter 5 times (didn't give other options), then continued to configure APT sources, then said storing.

Last error message, still up on screen:
"No installable kernel was found in the defined APT sources
You may try to continue without a kernel and manually install your own kernel later. This is only recommended for experts, otherwise you will likely end up with a machines that doesn't boot."

**HELP, ANYONE??**

Should I quit & reinstall (will that make any difference?) should I go back & do anything differently?

Is there any way to just get a program to install? I really don't want to continue with Microsoft, but this is time consuming, just to INSTALL....

Thanks!

---

### Post by taurus on 2008-02-26
How fast did you burn the CD?  If you burnt it as a default speed, try burning it again but at much slower speed like 4x if you could.

Also, don't forget to run the Scan Disc for Defects at the first menu to check the CD to be sure everything on the CD is good to go.

---

### Post by julian67 on 2008-02-26
> **SeaQiyas said:**
> After problems install from the Ubuntu 7.10 Live CD, I took others' advice to try the alternate CD.
([http://ubuntuforums.org/showthread.php?t=707134](http://ubuntuforums.org/showthread.php?t=707134)  I originally posted this on that thread, but makes more sense for a new thread)

Computer:  Acer Aspire laptop 3003Lci, 40GB HD, 256 DDR, AMD Sempron processor (1.8Ghz I think) with a DVD/CD-RW drive

Downloaded the alternate CD, checked the md5sum, all okay, burned to cd.



ok the downloaded file passed the check but how about the burned CD? Reboot and choose the option to check the CD.  It's important that the CD is a good quality blank and that it's burned without error. Sounds to me like you're probably using cheap low quality CDs.

---

### Post by SeaQiyas on 2008-02-26
I had burned 2 copies of the alt CD, and I just did a CD check for both (twice each - same results)

Both CD tests showed "Integrity test failed".  But the corrupted files were different on each cd ???

Does this mean I should re-download the file, or try re-burning the file from the downloaded iso?

I'd rather not download again because it took about 12 hours last time - plus I had to restart the process 3 or 4 times before that.

---

### Post by taurus on 2008-02-26
Here are some steps you need to do to be successful.

1.  Run the checksum of the ISO image right after you've downloaded it to check the integrity of the ISO image.

2.  Burn it as a slow speed like 4x.

3.  Check the disc for defects at the first boot screen.

So, how fast did you burn those two CDs?

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29)

---

### Post by SeaQiyas on 2008-02-26
ok, will try burning again at a slow speed... thanks!

{ I just left the burning at the default rate which is the fastest, I think 10x]

---

### Post by julian67 on 2008-02-26
If your burner is decent brand and not ancient then the speed of the burn isn't the issue, it's the quality of the blanks you're using. If you have an old or no-name burner then try at 4x or even 1x. If you're using a bad/old burner *and* cheap CDs then go out and buy some good quality CDs.

edit I see you just posted that your burner has max burn speed of 10x.....it's very old.....go get some quality CDs!

---

### Post by SeaQiyas on 2008-02-26
I read recently that it's better to use CD-Rs, but I was using CD-RW (just ran out of CD-Rs yesterday). Max to burn CD-RW on my burner is 10x, for CD-R is 16x.  
We just had this DVD player installed a couple months ago. It's a Sony Dvd+rw dw-p50a.

I burned again at 4x speed and same problem - same corrupt file as one of the other CDs. 

My Nero software doesn't give the option to burn at 1x (not that I noticed anyway).  Is that because the CD-RWs are 4x-12x? I'm clueless about DVD/CD burners/ software.  Should I update drivers or anything like that?

Is it possible there is a problem with the downloaded file, or just with the burning?

I'll see about getting some good quality CD-Rs. Thanks!!

---

### Post by SeaQiyas on 2008-02-29
Update:

I bought some Sony CD-Rs, burned the Alt CD again at 4x & the CD passed the integrity test.  So I'm installing now. yay! :)   (Though I'm sure I'll have more questions)

I also did a new Memtest, this time after the laptop was off for hours.  It went thru the whole cycle, passed, then on the 2nd round it shut off again, about 20 minutes into the testing. So I wonder if that is an overheating issue?  We may go ahead & replace the RAM, increase it to 512k.

In the meantime, I loaded up Puppy Linux 3.01, wanting to see if *anything* could load on that laptop. And it worked great - I can't believe how FAST internet surfing is now!  I'll leave Puppy Linux on until I can get Ubuntu up & running. 

Your advice worked out perfectly - thanks so much!

* * * * * * * *

YES - Installed without a hitch!  THANKS!

---

### Post by miesnerd on 2008-02-29
For the future, if you're on Windows, the best burner is infraexpress imo.
In Linux, most things (obviously) can perfectly handle .iso's, but my clear fav is k3b, even in the gnome environment. Its just good.

---

### Post by SeaQiyas on 2008-02-29
Thanks, I'll check into that software.

The computer I added Ubuntu on had no operating system (I wiped it first), and will remain " Windows free".  But the laptop I was using to burn has Windows XP .  I used Nero.

Now onto getting Skype loaded, updates etc...

---

