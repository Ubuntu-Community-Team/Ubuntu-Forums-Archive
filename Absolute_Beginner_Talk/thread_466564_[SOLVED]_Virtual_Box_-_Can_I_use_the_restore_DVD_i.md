---
title: "[SOLVED] Virtual Box - Can I use the restore DVD in lieu of the original WinXP?"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-06-06
Hello,

I want to know if I can safely use my restore DVDs to install on the hard disk file with Virtual Box, or must I buy the original version of XP?

Thank you for the help!

---

### Post by starcraft.man on 2007-06-06
That depends. If these DVDs came with the computer and I assume their made by a company (dell or HP or such) then they usually rely on a small or hidden partition on your computer to verify its your computer and to prevent you from using the restore disks on any other machine. If this is the case, no. It won't work on virtual box.

I won't tell you to buy a new copy of XP either. I am annoyed and upset by these new practices. I remember the days when 95 and 98 disks came with the computer so you could reinstall at will.

If you ask me, its fair use to get a copy of the XP installer through less than legitimate means. My recommendation, go to [isohunt...]("http://isohunt.com/") search for a copy of XP thats the same version as your using (XP home, pro or MCE) and then download it, make sure its the OEM version. Then burn it and pop it into your computer. When you get to the license key stage, put your computers one (usually written on the side of the computer). This worked for me when I unfortunately formatted my hidden partition and my company told me it wasn't their fault. It should work for you. 

Just one note on the above method, don't do it if your dual booting XP as well. MS will obviously realize you activated two copies with same key.... in that case, find another key/copy to use thats strictly pirated.

I'm not trying to endorse piracy, but I am tired of these system disks, their just a way for companies to get out of giving you a disk and loading their crap into your computer with every restore.

---

### Post by Bohlio on 2007-06-06
While we are on the topic of restore disks, Will they effect the partitions at all? I originally had just XP, then i shrunk the NTFS partition by about 20 gigs and added ubuntu. If i use the restore CD, Will it reclaim that 20gigs for the NTFS partition? Im thinking about using the Restore CD to get rid of all the crap thats bogging down my XP system but i dont wanna have it effect Ubuntu or Grub at all.

---

### Post by starcraft.man on 2007-06-06
> **Bohlio said:**
> While we are on the topic of restore disks, Will they effect the partitions at all? I originally had just XP, then i shrunk the NTFS partition by about 20 gigs and added ubuntu. If i use the restore CD, Will it reclaim that 20gigs for the NTFS partition? Im thinking about using the Restore CD to get rid of all the crap thats bogging down my XP system but i dont wanna have it effect Ubuntu or Grub at all.

Sadly the answer is yes. Most restore disks have a predetermined partition formatting (its set at time of creation, whether OEM or when you burned them from the utility) that they will recreate overwriting everything else on the drive when they are used. It's just the cheapest easiest way for them to be made. The only exception would be if the disks asked you to target what partition to reinstall XP/restore the state to. If it doesn't ask for that, it's likely going to wipe your drive clean and reformat it all.

If you wanna preserve your partitions... my suggestion stands. Take back your right to your OS and get a copy of the installer that matches your OEM version. I am tired of this progression of companies trampling the rights of end users.

---

### Post by Bohlio on 2007-06-06
that really sucks! Im starting to see your whole point of view here. Thats kinda BS! If I bought the computer, I should have the right to reinstall the xp onto the partition withought getting rid of everything else! As long as its on the same computer, Its perfectly legal. Im a little angry :-( Time to go complain to dell and see what happens :-)

---

### Post by lazyart on 2007-06-06
The thing is, when you buy your dell you have an option to get the full install CD for a few bucks more.  I always tell anyone buying from dell (or hp or any vendor for that matter) to insist on the original media.

---

### Post by Bohlio on 2007-06-06
I think I may have got that... there was a CD that was I believe $10 more. Lemme check. :-)

I dont quite know if this is the restore disk or not... It says 
> Operating System
Already installed on your computer
Reinstallation DVD
MS Windows XP Media Center Version 2005 w/ Update Rollup 2
It says "Reinstallation" so that doesnt quite seem like the restore disk...

---

### Post by the8thstar on 2007-06-07
Although I understand frustration, I do not condone piracy. Alright, so let me sort this out; if I use my restore disks instead of a new copy of XP, then my Ubuntu partition will be wiped out during the reinstall or some stupid sub program will just inactivate my current copy of Windows altogether?

Well, with these options, I have no other choice but to keep on dual booting Ubuntu/XP to use Office 2007. Thanks for being so good with us Microsoft. NOT.

---

### Post by sailor2001 on 2007-06-07
except for some games, there is no reason to using windows anyhow..........open office is much faster and better than windows office, if that is your concern...take control of your computer, you're the boss, design in the way you like it in ubuntu....

---

### Post by the8thstar on 2007-06-07
** sailor2001**  	> except for some games, there is no reason to using windows anyhow..........open office is much faster and better than windows office, if that is your concern...take control of your computer, you're the boss, design in the way you like it in ubuntu....

You're right, but I bought Office 2003 with my computer (that was before I switched to Ubuntu) and got a free upgrade to Office 2007. I would just like to be able to use it since I spent my hard-earned cash on it.

Apart from that, the only other reason why I'm still using MS Windows is because my webcam is a Microsoft. I don't know of any decent programs in Ubuntu I could use for webcam broadcasting.

---

### Post by ccfjeff on 2007-06-08
> **starcraft.man said:**
> That depends. If these DVDs came with the computer and I assume their made by a company (dell or HP or such) then they usually rely on a small or hidden partition on your computer to verify its your computer and to prevent you from using the restore disks on any other machine. If this is the case, no. It won't work on virtual box.

I won't tell you to buy a new copy of XP either. I am annoyed and upset by these new practices. I remember the days when 95 and 98 disks came with the computer so you could reinstall at will....

Thanks for the info.  I'm in a similar, actually worse, boat.  I bought a factory refurbished HP through PCMall online.  It came with no disks whatsoever.  All of the software was pre-installed.  Dumb me didn't make a recovery disk and about a year or so later my hard drive crashed.  They couldn't recover anything.

A computer guru, who's company went out of business, put in a hard drive and reinstalled Win XP for me, but it apparently didn't have all of the correct documentation etc.  Now a couple of years later Microsoft downloaded their "Genuine Advantage" software which pops up warnings all the time that I need to purchase (another) copy of Windows and hijacks my computer to display their Genuine Advantage web pages.

It reminds me of the way Microsoft went after charities that were collecting old computers donated by businesses that were upgrading, and then were distributing to poorer school districts that couldn't afford them.  Microsoft was demanding proof of purchase for each of the OSes.  Most of the businesses couldn't or wouldn't provide them and obviously weren't too worried about the record keeping for computers that would have ended up in the trash if not for these charities.

Microsoft demanded that they pay full price for the OSes even though most of the computers were so old that they would only run Win 3.11 or Win 95 on them.  At least one charity decided that they would just install Linux on them, but Microsoft threatened to sue as they had contracts from the manufacturers that each of the computers were required to have Microsoft OSes on them.  They were basically admitting that they had already been paid for the OSes when the computers were manufactured and now they were twisting the arms of these charities to make them pay for them again.

I remember reading one guy's account who said he just dropped the project as it was too expensive to try and fight them and too expensive to pay prices for Win 3.11 etc. at rates more than the computers were worth.

I hate Microsoft.

---

### Post by ccfjeff on 2007-06-08
> **the8thstar said:**
> ** sailor2001**      

You're right, but I bought Office 2003 with my computer (that was before I switched to Ubuntu) and got a free upgrade to Office 2007. I would just like to be able to use it since I spent my hard-earned cash on it.

Apart from that, the only other reason why I'm still using MS Windows is because my webcam is a Microsoft. I don't know of any decent programs in Ubuntu I could use for webcam broadcasting.

I don't know if all of the virtual machines would have the same problem as Virtual Box in this situation, but here is a comparison with some others courtesy of Wikipedia:

[http://en.wikipedia.org/wiki/Comparison_of_virtual_machines](http://en.wikipedia.org/wiki/Comparison_of_virtual_machines)

---

### Post by the8thstar on 2007-06-08
This doesn't help me specifically, but brings light on the different solutions available. Thanks for the link, **ccfjeff**.

---

