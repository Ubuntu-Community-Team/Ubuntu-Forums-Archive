---
title: "Different Backlighting issue."
date: 2007-08-27
forum: Apple Intel Users
---

### Post by Garrulousbrevity on 2007-08-27
Hey, this problem is probably silly but I've run out of ideas.

First of all I have seen the solution for a backlight issue.  But that seems to assume that you can adjust the brightness of the display at all.  I can't. 

I'm using a relatively new macbook, and I installed Ubuntu Feisty Fawn 7. 04 a few days ago.

When I first installed it, the brightness buttons worked fine, however, since then they've stopped, and the gnome power manager no long shows a brightness slider.

I first noticed the problem after editing the xorg.conf file while trying to make it so a separate monitor will work. Apparently I did something wrong and the xorg.conf file... died.

It was late and I had forgotten to make a backup, so I reset the xorg.conf file.

I don't know if that caused the brightness issue, but that's when I noticed it.

I don't think this is any issue of GNOME. I've removed and re-installed the GNOME power manager and that did nothing. I've also removed and re-installed most of GNOME. So I do believe that it's an issue with the xorg.conf file.

I think the settings for the display are wrong... but then again I don't know what the right ones would be.

If anyone could help that would be most helpful.

Thanks.
__________

---

### Post by Garrulousbrevity on 2007-08-27
So I put the Live CD in, and found a package for Apple Ho, and that made the F1 and F2 keys work.  But the slider in the GNOME Power Manager is still gone and it's still not quite right.

---

### Post by Garrulousbrevity on 2007-09-17
So, With a mixture of insomnia and irritation, I reinstalled Ubuntu on this macbook last night. 

The brightness control worked until I updated the kernel. Has anyone else had this issue?

---

### Post by fyrefly07 on 2007-10-15
I have this issue on my Macbook as well.  I wan't sure when it first started, because I had been adding and removing a bunch of random software.  I have not done any xorg.conf tinkering however so I know that's not the cause.  Perhaps it began after running some updates...  

I looked into an older solution for adjusting Macbook brightness with no luck, incorrect architecture.   I was thinking about a reinstall, however I think I'm going to ride it out until 7.10 is official and then try a fresh install.

---

### Post by Sunspark on 2007-10-15
It's a bug of some sort..

I installed Gutsy from the beta cd on the gf's Sony VAIO. The brightness sliders worked, etc.

Yesterday we did an 'upgrade' to the latest version thinking things would be even better. They weren't. The system was slower running, AND the power manager no longer works, meaning there is no more brightness slider in either battery or AC.

I see there are now multiple kernel entries on the boot screen -14 kernel and -12 kernel. Booting from -12 kernel does not solve the issue, which means they broke something in gnome-power-manager, or X as you posit.

If you want to test, try with a gutsy beta cd, and see if you can figure out the difference.. that was the last 'known' working version on a VAIO for me.

I sure hope they have a version in the works to fix problems, because if they release with broken backlight controls for laptops, and a slower running system than ever, people will just laugh at it and keep on using Windows. I had to boot into Windows to bring up the brightness of the screen.

---

### Post by Sunspark on 2007-10-15
Guys, I have no idea if the VAIO issue is the same as the MacBook one, but if one of you who has the problem doesn't mind downloading the Gutsy Beta cd and seeing if it has working backlight sliders on your macbook, if it does, then please confirm that you are also affected on this bug report I filed yesterday.. there's not a lot of time to get it fixed before it 'releases'.

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/152731](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/152731)

Hmm, looks like they pulled the beta CD url off their site.. here is the Azureus magnet URI to download it over torrent from linuxtracker, has 23 seeds still.
magnet:?xt=urn:btih:ZBWU3KKPMZWCKLHLOOKVPEJ5ILITZM4T

---

