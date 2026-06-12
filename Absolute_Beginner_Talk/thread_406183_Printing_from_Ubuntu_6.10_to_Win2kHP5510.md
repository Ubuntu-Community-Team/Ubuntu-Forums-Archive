---
title: "Printing from Ubuntu 6.10 to Win2k:HP5510"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by drmbogo on 2007-04-10
Hi Folks!
Here's my situation:
I have my office network set up as follows;
Win2k box 1 [FRED] acting as file/print server
Win2k box 2 [ETHEL] as a client
WinXP lappy for quickbooks and other business stuff
Ubuntu 6.10 box mostly as a test bed, to cut my teeth on Linux

All the win boxes 'talk' to each other fine; i.e. can share files, print, etc, and have been fine for years (as 'fine' as winblows can be :) )
Set up a Dell desktop w/ Ubuntu 6.10, install went fine, configuring Samba went fine (thanks Stormbringer!) I can share files to/from win/ubuntu no problem.
Here's where it gets ugly:
I can add the network printer (shared on FRED) to the Ubuntu box, either thru System>Administration>Printing or via CUPS. 
Everything seems fine at this point, but...
When I attempt to print to said printer, the printer starts making noise as if it wants to print (I can hear the printhead shuttling back and forth a few times, 'print' light flashes...) but then it hangs. The print queue on the Win2k box shows "remote downlevel document | Printing" but nothing happens.
If I attempt to delete the job in windows, it reports Deleting-Printing, but won't delete the doc until I reboot. The Ubuntu printer queue seems to show that the job completed successfully.

I've seen a few other posts with similar details, but none with any resolution.

Anyone have any ideas?
TIA
Dave

---

### Post by Dekunuts on 2007-04-10
I have the exact same problem and although i've been using linux for over a year i can't fix it, so my guess is that windows creates the problem. Maybe you have to install or enable some unix compatibility somewhere on the windows machine. I know this is not a lot of help, but I hope it can maybe help you on your way.

---

### Post by drmbogo on 2007-04-10
Hey Dekunuts, Thanks for the reply
Funny you mention Unix; I saw a post somewhere about installing Unix Print **** on the windows box. I'll have to see if I can find that post again!
It does seem like an HP issue tho', as other people have the same problem, and the common thread is HP.
Have you read this?
[http://ubuntuforums.org/showthread.php?t=361978](http://ubuntuforums.org/showthread.php?t=361978)
Cheers
dB

---

