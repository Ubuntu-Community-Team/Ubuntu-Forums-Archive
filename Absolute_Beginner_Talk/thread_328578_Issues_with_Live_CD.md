---
title: "Issues with Live CD"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by Charles_Bell on 2006-12-31
I downloaded (for the 3rd time today) Ubuntu from a North America server, for desktop. 

I'm running Windows XP SP2, with IE 7 and an ATI Radeon video card and integrated Sound. My issue is that when I run the Live CD I've tried running it on both Safe VGA mode and regular mode, I get an error starting X.

Once, I found an error saying No Screens Found. This was once, and I've not seen it since, but I just continue to get an error starting the Live CD due to X. 

I've read the forums and found posts stating to slow down the burning of the ISO. So I burned it at the slowest setting Infra Recorder would allow me to burn. I'm not sure what more I can do to start this.

I am extremely new to Linux in general so I don't know most of the command line instructions. Any assistance you can give me would be spectacular.

---

### Post by taurus on 2006-12-31
Try the alternate CD then...

---

### Post by Charles_Bell on 2006-12-31
Where is the Alternate CD?

Out of curiosity, what options do the Alternate CD offer me? I'm sure it's a great suggestion and I do intend on trying it, I just like to know more about what I'm shoving into my PC, before I throw it in there.

Thank you for your quick response.

---

### Post by taurus on 2006-12-31
The alternate CD is the same as the LiveCD (desktop CD) except it allows you to install Ubuntu right away in text mode instead of booting from it first...

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/ubuntu-6.10-alternate-i386.iso](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/ubuntu-6.10-alternate-i386.iso)

---

### Post by Sef on 2006-12-31
The alternative version has been located below the desktop version.

Read about installing the alternate version from the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/").  If you are not going to dual boot, then ignore the part about making a FAT32 partition.

---

### Post by Charles_Bell on 2006-12-31
Thank you very much for your assistance. I'm downloading the file.

I will post once I have burned the file and attempted to install.

---

### Post by Charles_Bell on 2006-12-31
Ok, so here is how I fixed the issue with the No Screens found.

I downloaded the Alternate CD however, I decided to try one last thing before moving to it.

I ran the Live CD yet again, and this time I did the following:

When it came to a black screen with a flashing cursor _, I pressed Alt+F2
Then I got a prompt, where I typed sudo dpkg-reconfigure xserver-xorg
Followed the prompts, except after discovering my video, I switched it from ATI to Vesa.

I followed the remaining prompts, taking the default settings. Once all was done, I got back to the prompt for ubunto and I typed startx and tada it started :)

As of right now, I'm trying to figure out how to repartition my hard drive, so that I can dual boot. Any information about the partition manager would be great as I have absolutely no idea, but I so don't feel like spending all day sunday reinstalling everything on my pc. That would totally blow.

I do have the link previously posted about the dual booting, but it seems a bit far over my head, and I just would like the newbie post if you have one on how to do it without deleting everything on your hard drive, or using all remaining space.

---

### Post by taurus on 2006-12-31
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by Charles_Bell on 2006-12-31
Crossing fingers now

I'm installing the OS at this time. Here's hoping

---

### Post by riven0 on 2006-12-31
> **Charles_Bell said:**
> Ok, so here is how I fixed the issue with the No Screens found.

I downloaded the Alternate CD however, I decided to try one last thing before moving to it.

I ran the Live CD yet again, and this time I did the following:

When it came to a black screen with a flashing cursor _, I pressed Alt+F2
Then I got a prompt, where I typed sudo dpkg-reconfigure xserver-xorg
Followed the prompts, except after discovering my video, I switched it from ATI to Vesa.

I followed the remaining prompts, taking the default settings. Once all was done, I got back to the prompt for ubunto and I typed startx and tada it started :)



Kudo's to you for researching before posting questions. You're already on your way to becoming a Linux expert. :D

---

### Post by Charles_Bell on 2006-12-31
Thank you for the compliment. I always try to look for myself before pestering other people. I finally got my system installed. Though it barked at me for not using a swap file. I know from all the time in windows that swap files are good, but I wasn't sure how to configure it. I figured that I can find a way to add one later if I decide to use Ubuntu more frequently, but for now I resized a partition to 30gb for me to give it a go.

---

