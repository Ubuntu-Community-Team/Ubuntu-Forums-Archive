---
title: "Problem installing :S"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by matt7 on 2008-04-13
Okay so I got my 7.10 disc in the post on friday and i've tryed a few times to instal it but everytime before the live os loads up, it freezes. It's when the little loading bar its scrolling accross.

My laptop is fairly new (got it 3 months ago new) Its a gateway ml3108b with a semperom 3200 and 512mb of ram so it's equiped to run it but for some reason it wont load up:S

Is there a simple solution to this or am i stuck with windblows?

PS. I've tryed 2 offical copys of the 7.10 and a few iso's i've burnt and the same thing has happened :(

---

### Post by spiderbatdad on 2008-04-13
Here's a cryptic tutorial on boot prompts: [http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

You might try noapic nolapic

Press f6 at the boot options screen...delete 'ro quiet splash' add 'noapic nolapic vga=792'

---

### Post by Hendrixski on 2008-04-13
That might be something that is getting fixed with the latest release: 8.04.  Try the beta.  and while I don't recommend that you run on the beta.... I'm just saying you try booting the liveCD with it.   If so... just wait 2 weeks for it to come out.  :-p

---

### Post by alzie on 2008-04-13
Have you tried installing with safe graphics mode?  That works for some.

Others recommend using an alt distribution for installation on laptops (its the same distro but without the live option)

I hope this helps :)

---

### Post by stuart brogan on 2008-04-13
1. try 8.04
2. can you get the live cd going?
if you can get the live cd going maybe try looking for clues with dmesg etc.
$ dmesg
If your new to Linux this looks confusing at first but basically it is a great way to troubleshoot because then you can Google the specific error.

I don't know the model of laptop you are using but I doubt if you are stuck using windows. There is always a solution. 

I have a new fujitsu that gave me some problems with 7.10 and I went to experimental (actually it is fairly stable) and my woes were fixed.

When you open up windows and look in my computer do you have both C: and a small D: drive?

I dont know why, but if you reinstall the winblows software and make one partition it could also solve your problems. 

Are you doing a clean Linux install with no windows partition? I will tell you from experience that leaving a 5 or 6 GB windows partition is helpful for a number of reasons on some laptops.

(provisioning evdo cards for instance)

A friend wasn't able to get his wireless card working until he put a small windows partition then used something like bcm-fwcutter to fetch info. (something like that)

I noticed that your post was unanswered so I hope that I could help even a little, sorry I can't give you the automagic fix. A lot of times in Linux being patient is your best bet, the answer is out there. You can do some amazing things in Linux that windows can't do and never will be able to do.

---

