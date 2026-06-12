---
title: "Installing Windows fonts"
date: 2006-12-06
forum: Art &amp; Design
---

### Post by Thumper322 on 2006-12-06
Maybe I should've kept this as part of my [other thread]("http://ubuntuforums.org/showthread.php?t=313769"), but this isn't of as much importance.

I'm wondering, how exactly do I install fonts from Windows? (Specifically, Garamond and Tahoma.) I have a copy of XP (well, the CD anyhow, I'm running Ubuntu now :D), and I was wondering:
[LIST]
[*]Do I have to install Windows somewhere and grab the fonts from the FONTS folder, or is there some way to extract them from the install CD?
[*]Once I have the fonts, how do I install them?
[/LIST]

Thanks for any help...

---

### Post by djf_jeff on 2006-12-06
Just do

sudo apt-get install msttcorefonts


And the Windows fonts will be installed!

---

### Post by Thumper322 on 2006-12-06
> **djf_jeff said:**
> Just do

sudo apt-get install msttcorefonts


And the Windows fonts will be installed!

Thanks, but I already did that.

I need Garamond and Tahoma specifically, neither of which are in the msttcorefonts package.

---

### Post by Madpilot on 2006-12-06
[https://help.ubuntu.com/community/FontInstallHowto](https://help.ubuntu.com/community/FontInstallHowto) has most of the information you need.

Short version: drop everything in ~/.fonts.

To get the two fonts you need out of XP, I suspect you will have to install it; someone might know a method of extracting stuff from the compressed XP install CD, though. Or you could just grab the font files from a friend's XP install - you do have a license, after all.

---

### Post by Thumper322 on 2006-12-07
> **Madpilot said:**
> [https://help.ubuntu.com/community/FontInstallHowto](https://help.ubuntu.com/community/FontInstallHowto) has most of the information you need.

Short version: drop everything in ~/.fonts.

To get the two fonts you need out of XP, I suspect you will have to install it; someone might know a method of extracting stuff from the compressed XP install CD, though. Or you could just grab the font files from a friend's XP install - you do have a license, after all.

Thanks!

Is there a wiki page about installing PostScript fonts, by chance? (See link in my original post.)

---

