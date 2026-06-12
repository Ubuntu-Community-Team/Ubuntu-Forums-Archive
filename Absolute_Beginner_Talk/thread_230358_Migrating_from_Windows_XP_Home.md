---
title: "Migrating from Windows XP Home"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by Brain1337 on 2006-08-05
Hi,

I have begining to see the light... Help me come away from the evil that is Microsoft Windows and none open-code software.

My Computer:

**Dell Dimension 8400**

Intel Pentium 4 3,6 GHz with HyperTreading (Dual Core)

**RAM:** 2048MB PC-4200 DUAL CHANNEL DDR2 533MHZ

**Harddrive:** 320GB SATA RAID 0 STRIPE (1ST (2X) 160GB 
(2ND 160GB (7200RPM) SATA HARD DRIVE RAID)

**Sound: **	SOUNDBLASTER AUDIGY 2 ZS 7.1 SOUNDCARD

**3D Card:** ATI 256MB RADEON X850 XT Platinum Edition

**Monitor:** Dell 2405FPW [http://support.dell.com/support/edocs/monitors/2405fpw/en/about.htm#Specifioications]("http://support.dell.com/support/edocs/monitors/2405fpw/en/about.htm#Specifioications")

_My Problem_

Something is wrong with my video card or maybe my Monitor because Iam just running at *1600x1200 @ 60Hz* my optimal resolution is *1920x1200 @ 60Hz*...

And I also belive that my video card don't have any ATI drivers to use, and are useing the standard OS drivers... 

A harddrive sector I put at /storage is were Iam going to store my stuff I can't access and the alert is: You are not the owner, so you don't have any   permissions.

---

### Post by tkiesel on 2006-08-05
Hi Brain1337,

To earn that name of yours (implying that you are both intelligent and elite) it's time to start learning!

So get your resolutions going, try this in a terminal window....

```
sudo dpkg-reconfigure xserver-xorg
```

Say yes to the defaults all the way through, but when you're presented with setting up your monitor, go "Advanced"  and you'll get the opportunity to choose resolutions you want to run.  The arrow keys and space bar to select the resolutions you want.  Accept defaults for the rest.

After you get resolutions sorted out, then turn to getting the drivers for your ATI card. To get your ATI card going with full 3D acceleration compatibility, check out  the [HOWTO here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"). For maximum simplicity, use the method there for getting xorg-driver-fglrx from Ubuntu instead of going for the drivers off of the ati.com website.

You're well on your way!

Take care,
-T

---

### Post by Brain1337 on 2006-08-06
Hafter I have done the things you said my X-Window System completely crashes. And tells me that fglrx don't exist and it is something wrong whit the screen in 'xorg.conf'..

Any comments?

---

### Post by tkiesel on 2006-08-07
Did you do the resolution part first and verify that it worked by rebooting/restarting X, before you went on to try installing the ATI drivers?

You want to take things like messing with X one step at a time, to ensure that if(when) you encounter a problem, you know which of your tweaks did it.

Edit:  More info.....

I'd recommend going in and doing the sudo dpkg-reconfigure xserver-xorg and choosing the default chosen driver.  Make sure that you've got your resolution issue sorted out. Once you have the res. issue set up, then you'll be golden even after switching drivers later.

Then do a few ATI related searches here on the forum.  Or there might be an ATI user who can help point you in the direction of the driver method you'll need.  I'm familiar with installing the drivers for my Nvidia card. The ATI setup I'm not familiar with.

Good luck!
-T

---

### Post by Brain1337 on 2006-08-09
Thanls, I will replay when things start working..

But for now I will just use the standard 2D drivers... I did get the resolution to work and I choose the standard resolutions my monitor could handle and now it is working atleast the high resolution is not that bad but it is a bit laggy...

I will continue to test what drivers is best to use. I will start a new thread consierning my grafic card drivers..

Hope that any one else could help me sort out what is wrong whit the partition I set under /storage

Thanks for all your help!

---

### Post by darrenm on 2006-08-09
Hi :)

Congratulations on choosing the enlightened path. Stick with it through any teething troubles and you will never look back.

The ATi binary drivers from their website are definitely the best to use. 

Whats wrong with your /storage partition?

---

### Post by Bloch on 2006-08-09
You probably created the /storage directory as root.
To mess around with files as folders with root (aka superuser aka administrator) permissions enter
sudo nautilus

and give your password.
Then you can create and delete files at will (this is dangerous of course)

But people usually store their files etc in their home directory
/home/_whateveryoucalledit_
You always have permissions to read and write in your home directory.

---

### Post by Brain1337 on 2006-08-09
I got my storage patition to work =)

To install the binary drivers for ATI 3D card is it best to follow this guide? [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

If so where do I start following the guide?

---

### Post by darrenm on 2006-08-09
yes that guide is the best one, start from the part where it says about using drivers from ati.com

---

