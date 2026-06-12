---
title: "Installation problem"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by kalbear on 2007-10-23
Hi all...I've finally decided to install linux for the first time. I downloaded the 32-bit versiion of Ubuntu 7-10. 
Unfortunately, I can't even start the installation problem. Right after I chose install Ubuntu and did its loading thing, the installation stops and displays "Windows shutting down" screen with three Ubuntu logo on top. I couldnt even get to the desktop. Sorry if this problem has been addressed somewhere else..I tried looking around  but couldnt find anything. 

Little bit about my computer:
AMD Athlon 64 Processor
1 gb RAM
Chaintech Volari V3 XGI video card (this might  be the problem)
ECS nForce3-A motherboard
WD 200 gb hard drive. 
I did cd check and the live cd was fine.

I really appreciate all the help I can get. Thank you.

---

### Post by toddward on 2007-10-23
kalbear,

Put the CD in the cdrom drive when you're rebooting.  This will bring you to the liveCD.  You need to make sure that your BIOS tries to boot the cd-rom first. 

Once in there (it may take a while to boot the liveCD), you should see an icon to install Ubuntu 7.10.

---

### Post by kalbear on 2007-10-24
I booted using the live-CD. The problem happened when I chose the "Start or install Ubuntu". It went through the loading kernel part, showed the progress bar of the Live-CD starting up and it stopped there showing the screen that I mentioned before. Thanks.

---

### Post by rsambuca on 2007-10-24
Did you check the md5sum prior to burning the cd?
Did you burn it at a slow rate to help avoid single bit errors?
Did you try running the cd integrity check?

---

### Post by kalbear on 2007-10-24
Did you check the md5sum prior to burning the cd?
Did you burn it at a slow rate to help avoid single bit errors?
Did you try running the cd integrity check?

I just did md5sum on the image and i was the same
I ran cd integrity check and the cd was fine. 

Any more suggestions? Thanks

---

### Post by rsambuca on 2007-10-24
You may have better success with the alternate CD then.

---

### Post by multifaceted on 2007-10-24
The answer is easy, you are using a 64 bit processor and you downloaded the 32 bit version.

Download and burn the 64 bit version and you should have no problems.

---

### Post by rsambuca on 2007-10-24
> **multifaceted said:**
> The answer is easy, you are using a 64 bit processor and you downloaded the 32 bit version.

Download and burn the 64 bit version and you should have no problems.

I like the 64bit version as well, but the 32bit version is not the reason for these specific problems.

---

### Post by multifaceted on 2007-10-24
> **rsambuca said:**
> I like the 64bit version as well, but the 32bit version is not the reason for these specific problems.

Just curious... what the significance?

Faster graphics rendering?... refresh time?

---

### Post by Sef on 2007-10-24
> The answer is easy, you are using a 64 bit processor and you downloaded the 32 bit version.

NOT true.  The 32-bit version will run just fine on 64-bit hardware.

> I like the 64bit version as well, but the 32bit version is not the reason for these specific problems.

Correct.

> The problem happened when I chose the "Start or install Ubuntu".

Is there another machine that you could use to see if the install starts?  You can cancel after it starts.  Nothing is installed until you format the hard drive.

---

### Post by kalbear on 2007-10-24
good suggestion...I tried it on my friend's computer and the CD works just fine. 
It's probably something wrong with my hardware then...could it be my video card?

---

### Post by kalbear on 2007-10-24
would it be a problem if my hardware is not recognized by live-cd?

---

