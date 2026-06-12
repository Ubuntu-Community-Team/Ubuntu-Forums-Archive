---
title: "Question about Dual-Boot System"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by navymom on 2006-07-22
If you are wanting to have both XP and Ubuntu on your computer, which is easier, installing Ubuntu and then XP or does it really even matter?

---

### Post by blanc11 on 2006-07-22
> **navymom said:**
> If you are wanting to have both XP and Ubuntu on your computer, which is easier, installing Ubuntu and then XP or does it really even matter?


XP then Ubuntu, otherwise XP will override your Ubuntu installation.

---

### Post by confused57 on 2006-07-22
> **navymom said:**
> If you are wanting to have both XP and Ubuntu on your computer, which is easier, installing Ubuntu and then XP or does it really even matter?

Yes, as suggested, you must install Windows first...then when installing Ubuntu from the alternate CD(not the LiveCD), you can opt to install grub to floppy:
[http://www.ubuntuforums.org/showthread.php?t=188819&highlight=floppy](http://www.ubuntuforums.org/showthread.php?t=188819&highlight=floppy)

Without the floppy inserted, your system would automatically boot to Windows...with the floppy inserted, you can choose to boot Ubuntu.
This method doesn't install grub to the Windows mbr, but you can do so later as described in the link.

Herman is the forum expert on dualbooting:
[http://www.ubuntuforums.org/showthread.php?t=220792](http://www.ubuntuforums.org/showthread.php?t=220792)
Anything he posts about dualbooting can be very informative.

---

### Post by navymom on 2006-07-22
umm does grub *have* to be installed to a floppy cos the floppy drive sometimes work, most times doesn't....it's a witch. lol  Another thing, what exactly is "grub" and at the risk of sounding like a total moron here, what is Windows mbr?  lol  btw confused57, thank you so very much for the cds...i haven't attempted to install it yet as i'm in the process of d/ling the sys rescue iso...it's almost finished (man is sucks being on dial up lol) and as soon as i've burned it to a cd, i'm going to try....the kids have played on the livecd most of the day and they absolutely love it!  i just hope i can get it to working as beautifully installed as on the cd. lol

---

### Post by aysiu on 2006-07-22
I've had nothing but good experiences installing Grub to the MBR. One time I tried to use Windows' boot loader and add Linux to the boot.ini file--it was a pain in the ***.

If you use the Desktop CD, Grub will automatically be installed to the MBR, and most of the time, this is a good thing, as Windows will automatically be added to the Grub menu. If it isn't, you can manually add it later.

If you want to install it to a floppy instead, you'll need the Alternate CD.

---

### Post by navymom on 2006-07-22
i have both the live and alternate cds.  i think i read some where that it installs quicker with the alternate....i am assuming that the alternate gives you the option to install on floppy or not.  am i correct?

---

### Post by aysiu on 2006-07-22
Yes, the Alternate gives you plenty of options, is faster, and is more reliable. It's just not as pretty.

---

### Post by confused57 on 2006-07-22
> **navymom said:**
> i have both the live and alternate cds.  i think i read some where that it installs quicker with the alternate....i am assuming that the alternate gives you the option to install on floppy or not.  am i correct?
Glad to help out, I was only giving you the grub floppy install as another option...as aysiu said, there shouldn't be a problem installing to the Windows mbr.
Check out aysiu's website, lots of good information:
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

### Post by navymom on 2006-07-22
alright, i can do without pretty...but will it give me instructions i understand?  by this i mean i've browsed around the forums reading over things that may cause me a problem.  i already know that i will probably have a problem configuring my modem...it's a lucent winmodem.  i was concerned about sound but the livecd took care of that as soon as it booted...i heard the music loud and clear.  i'm not certain about the modem though because when i went to configure it i was asked for a pw and didn't have any idea what that would be so i just closed it...i'm thinking now that it may be slower but i'm going to opt for the livecd install.  gosh i'm so excited. lol  the sad thing is i know as soon as i get it installed and everything working, i'm going to have to give up the computer so the kids and hubby can play. lol  good thing for me i have another computer i can install it on and play with. lol

---

### Post by aysiu on 2006-07-22
This will give you a preview of what the Alternate CD installer looks like:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by Tarvok on 2006-07-22
You know, given the fact that you're on dial-up, and given the fact that a large portion of the Ubuntu Experience involves downloading files (security updates, loads of free software in the repositories, etc.), you might want to reconsider this. I don't want to rain on your parade, but Ubuntu does involve a lot of downloading. You will be tying up your phone line for extended periods of time (not to mention the winmodem thing). You will want too; there is just too much good stuff out there! :D

Thad said, if you think all this is okay, go for it! I believe Ubuntu is vastly better than Windows.

---

### Post by navymom on 2006-07-22
You're not the first person to tell me that...but...people on dial up all over the world that use windows have to go through the same thing...if we want to dl a game, a song, etc, it ties up our phoneline...and as for updates, windows updates aren't that great over a dial-up connection either....service pack 2 wasn't a picnic...so no matter what OS i use i'm still going to have that problem.  as long as the the programs that are included on the livecd are what's installed when i install, i have no problems waiting a while if i chose to add anything else...as for tying up my phoneline, it's an internet dedicated phoneline...i don't believe i've ever had to use it to make a call and we never disconnect from it until we shut down our computer at night.  no biggie....oh and at least i'm not having to fork out 200 bucks every year or so for a newer version.

---

