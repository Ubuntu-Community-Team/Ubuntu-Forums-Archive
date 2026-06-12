---
title: "Need help going back"
date: 2011-06-17
forum: Any Other OS
---

### Post by sirgerbil on 2011-06-17
Hi there! I'm new to the forums. I gave Ubuntu a shot for a couple of months and, while it was fun, I don't think that it was for me. I am now trying to go back to windows.

Here's my predicament. 

I'm trying to reinstall Vista on the computer (yes, Vista, I didn't have any problems with it) using my MSDN account, which grants me free copies of popular software through microsoft (legally, of course). Couple of issues here.

1. I'm not really sure which file to install. They're all pretty similarly named. The list of available software is found here: [http://msdn.microsoft.com/en-us/subscriptions/downloads/default.aspx](http://msdn.microsoft.com/en-us/subscriptions/downloads/default.aspx)
which one of those is the right download?

2. I've tried a couple of them and they all have something_downloader.exe as a title. Obviously they don't run, since they are windows executable files. How do I run these or get the necessary files on a USB for the reboot?

Please keep in mind I am, as the forum suggests, an Absolute Beginner, so you're going to have to take it slow and explain pretty much everything. Any help is greatly appreciated! 

Thanks in advance :)

---

### Post by mastablasta on 2011-06-17
the highest that your subscription allows you to. porbably visa DVD with SP2 one of those. i dont' know which one you had before.
 
you probably need to somehow put it on DVD or make a bootable DVD. i am not sure how this is done. perhaps the whole procedure requires you to have windows installed on your maschine.
 
you could also maybe request a DVD from local microsoft office with your code.

---

### Post by xavi787 on 2011-06-17
I think you should choose

 > Windows Vista with Service Pack 2 (x86) - DVD (English)

---

### Post by An Sanct on 2011-06-17
> **mastablasta said:**
> the highest that your subscription allows you to. porbably visa DVD with SP2 one of those. i dont' know which one you had before.
 
you probably need to somehow put it on DVD or make a bootable DVD. i am not sure how this is done. perhaps the whole procedure requires you to have windows installed on your maschine.
 
you could also maybe request a DVD from local microsoft office with your code.

When I checked the link you gave us, it prompted me to sign in, after I chose "Vista".

I've downloaded from that page from out company account tho, so I can surely say, that there is an "ISO" option, choose that one and then burn that to a CD/DVD (make sure to use the "write an image" option, to make it bootable).

---

### Post by Supergoo on 2011-06-17
You have to download the complete Image of the Vista and then burn it to a DVD, then you can pop it into you drive, and make sure you drive is first in boot order , yourBios can tell you if it is, or the easiest is just see if it boots from the DVD follow the instructions and you will have Vista installed , remember you will have to delete both the swap and the main partitions.


Good luck with the reinstall
:popcorn:

---

### Post by An Sanct on 2011-06-17
> **Supergoo said:**
> You have to download the complete Image of the Vista and then burn it to a DVD, then you can pop it into you drive, and make sure you drive is first in boot order , yourBios can tell you if it is, or the easiest is just see if it boots from the DVD follow the instructions and you will have Vista installed , remember you will have to delete both the swap and the main partitions.


Good luck with the reinstall
:popcorn:

Remmeber, he has problems downloading ... Microsoft is serving him an "EXE" (for obvious reasons...).

The alternative (altho a not so good one ...) would be to install WINE and let that exe run :)

---

### Post by sirgerbil on 2011-06-17
> **An Sanct said:**
> Remmeber, he has problems downloading ... Microsoft is serving him an "EXE" (for obvious reasons...).

The alternative (altho a not so good one ...) would be to install WINE and let that exe run :)
Proooobably should have mentioned that I downloaded/have no idea how to use Wine....

---

### Post by crispy_420 on 2011-06-17
Assign the program to run as a wine executable from context menu by right clicking and "open with". Then select "Add". Custom command. Type in wine and click add. Select wine and double click. Assuming it does not require other Windows components this should work.

---

### Post by MRoeDesigns on 2011-06-17
How would one go about doing this without a DVD drive? I know you can make bootable USB's, but I also know ubuntu doesn't like to make them for windows.

---

### Post by An Sanct on 2011-06-17
> **MRoeDesigns said:**
> How would one go about doing this without a DVD drive? I know you can make bootable USB's, but I also know ubuntu doesn't like to make them for windows.

No, its not, that Ubuntu (or Linux or any other OS, including Windows) doesn't like to do USB boot images for Windows, they are just really hard to produce. Besides, *Microsoft "doesn't want"* you to do windows bootable USBs, that way they couldn't charge you for using their OS...

The good news is, it can be done ... google for Bart PE and its USB derivates. (This still leaves you with a non-install "cca Live" USB)

---

### Post by mips on 2011-06-17
sirgerbil,

Does your account give you access to Windows 7?

If it does I suggest you rather go for Windows 7.

What is the highest version Win7 on MSDN available to you?
What version would you prefer?
Would you prefer the 32-bit or 64-bit version?
What language would you prefer?

If you provide me with the above information I will give you a direct link to the **ISO image** for the version you want. Fully **legitimate** and directly from a **[B]official**[/B] MS digital distribution site.

MS has a official ISO to USB creation tool for transferring ISO images to USB. You might be able to use it in WINE.
There is also WinToFlash by Novicorp.

---

### Post by Supergoo on 2011-06-17
AH I understand now. How about a original install disk ? Did you get one with the machine or did you make them ? using a wizard they might be called system restore disks ? Ido not know of a way to make a Windows USb- I am sure it possible but I do not think it would be supported by Micorosoft. If none of these work for you, do youhave a friend that could lend you a vista disk ?
:(

---

### Post by Supergoo on 2011-06-17
I took another look at the msdn and I see Iso. files which is what you need, I have a Technet account and it let me download them without the installer if I am not runninga Microsoft OS, then you can use Furius ISo Mount <---Its in repos  to moound and Burn the Iso file. that should work for you 
:)

---

### Post by sirgerbil on 2011-06-17
> **mips said:**
> sirgerbil,

Does your account give you access to Windows 7?

If it does I suggest you rather go for Windows 7.

What is the highest version Win7 on MSDN available to you?
What version would you prefer?
Would you prefer the 32-bit or 64-bit version?
What language would you prefer?

If you provide me with the above information I will give you a direct link to the **ISO image** for the version you want. Fully **legitimate** and directly from a **[B]official**[/B] MS digital distribution site.

MS has a official ISO to USB creation tool for transferring ISO images to USB. You might be able to use it in WINE.
There is also WinToFlash by Novicorp.
I do have Windows 7 Available, and I would gladly install it on my machine.
Any version is fine at all.
I'd like the 32- bit English version.

If you could give me the link, in a PM or on here, that would be great :)

---

### Post by mips on 2011-06-17
> **sirgerbil said:**
> 
If you could give me the link, in a PM or on here, that would be great :)

You have PM ;)

---

### Post by MRoeDesigns on 2011-06-17
> **An Sanct said:**
> The good news is, it can be done ... google for Bart PE and its USB derivates. (This still leaves you with a non-install "cca Live" USB)

I downloaded it but it can't seem to find the flash drive. I tried it in WINE and in Virtualbox running my copy of XP. I even made sure the drive was shared between ubuntu and virtualbox, and tried mapping it to a drive in virtualbox through windows. I can't think of what could be causing the issue, Ubuntu recognises the drive immediately.

---

### Post by wolfen69 on 2011-06-17
[IMG]http://fastcache.gawkerassets.com/assets/images/4/2007/01/bad-vista.JPG[/IMG]
Just kidding btw. ;) Whatever floats your boat.

---

