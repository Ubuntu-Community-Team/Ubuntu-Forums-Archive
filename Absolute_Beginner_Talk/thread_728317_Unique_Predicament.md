---
title: "Unique Predicament"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by McMagic on 2008-03-18
Running Gutsy 64 bit .10 as primary on dual boot w/ vista 32 bit on turion 64 single core.

Vista was installed first on master, and gutsy was added to slave. everything worked fine for about a week. now vista boots fine out of grub menu, but ubuntu, which has been slow to load from the start, now suspends for 2-3 minutes, and then the machine powers off prior to boot.

I'm planning on booting from liveCD when i get back home and seeing if there isnt something that needs repairing. seeing as im new to linux, ill need to know what to do once ive got liveCD up in order to repair my install.

also, before this started happening, I was having issues with a 500Gig LaCie External which was giving an error in ubuntu that it was still active with the windows system...but this isnt possible..any suggestions?

---

### Post by McMagic on 2008-03-18
Ok, so I am now back on my computer, i tried booting to the recovery version of ubuntu and that didn't work either, Now here I am on LiveCD with no idea of how to fix my corrupted(?) installation. Please help!

---

### Post by McMagic on 2008-03-18
OK so this is really frustrating. After all the trouble I had gone through to set up ubuntu the way i wanted it, i reformatted the drive and reinstalled from scratch, rebooted after an update, and we're back to the same ****.

PLEASE SOMEONE HELP!

it is an hp pavillion dv8000
grub loads
vista runs
if i try to boot ubuntu, it stays on a black screen for 2-3 minutes, and the computer promptly turns off.
whats going on here?:confused::confused:

---

### Post by theRightNee on 2008-03-18
did you check the md5sum? perhaps you have a corrupted CD? 
sorry for the delay in responses...but please realize that this is a forum

missed the second post
to check whether or not it is corrupted you need to check the "md5sum" instructions are on Ubuntu's main page (i believe) and you can just google it if neccessary
if it is, you'll need to redownload the .iso file (that where the corruption is), preferably through torrent because fewer bytes are lost in the transaction (i know they're pretty much dead, but thats the best method)
    missing _+_ 10-25 bytes shouldn't be an issue tho

if not corrupted ( which it most likely isn't if you can run the LiveCD) and the fact that you had installed it previously....i'm sorry mate but i am at a loss for what could be wrong, maybe some of the higher ups have a solutoin

---

### Post by McMagic on 2008-03-18
I ran the "Verify Disk" application on the livecd boot menu, and it said everything was fine. I updated my BIOS and Linux booted successfully, but extremely slowly.

weird.

---

