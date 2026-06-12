---
title: "Ubuntu. Unable to explore c:\"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by geniustud on 2008-03-27
I am a newbie, so pls excuse my simple questions. 

I am trying to run Ubuntu from the CD drive. Though I have changed the boot option to goto CD ROM drive, it still goes to hard disk and starts windows. 

I started the windows in safemode command prompt, went to E:\ gave start command. It started Ubuntu and splashed the screen which shows I can install firefox, Clamview(?). But how do I go from there to explore the folders? Pls help. The only button I saw was Exit button. 

My PC is virus infected. Seems there is a malware which is stacking by buffers and in no time I get the bluescreen. I tried running different spywares but halfway, I get bluescreen. So I am trying to bypass windows, run ubuntu, and thru that clean my harddisk. If not, copy my data out and then re-install.

---

### Post by iris-n on 2008-03-27
Well, i'm sure you haven't quite changed the boot order, it should boot the live CD or at least give you an error. When you start it from within windows, you can't use it to install the system, only some free software on your windows.

---

### Post by sumguy231 on 2008-03-27
You can't start the LiveCD from Windows, you need to boot from it. How did you burn the CD? Make sure you're using the 'burn image file to disk' function of your CD burning program instead of just burning the .iso file to a data disk which won't make it bootable. If you can't burn a disk from your system, have a friend do it for you.

---

### Post by geniustud on 2008-03-27
Thanks for the reply Iris-n and sumguy321. 

Iris,

You are right. I changed the boot order, but the system cribs the drive is not ready. Press F1 to retry or F2 to reboot. I forgot to mention it. 

Sumguy321,
Let me try the method you mentioned. I got this disk from my friend, so not sure if he burnt the ISO. Is there any quick way of knowing?

Thanks,

---

### Post by iris-n on 2008-03-27
If ubuntu started from within windows, your friend certainly burn the .iso right.
As for the "drive not ready", beats me. I've already installed ubuntu on a dozen PCs and never ran into it. Do you have any other bootable cd to make sure the problem is not with your drive or configuration?

I recommend [DBAN]("http://dban.sourceforge.net/")'s cd to test. It's also a good way to clean a virus-filled hd. Warning: It completely erases data, use it only if you're wiping windows for good.

If you can boot other things, that would leave us with the hypothesis of a damaged or corrupted cd, and in this case you would have to reburn it.

By the way, what are your system specs?

---

### Post by sumguy231 on 2008-03-27
> If ubuntu started from within windows, your friend certainly burn the .iso right.
Wow, you're right. I don't know how I didn't think of that. Still possibly a bad CD.

---

### Post by geniustud on 2008-03-27
So Iris, you are sayng that the CD copied might be ok. Samguy feels that the CD may have some defect. Let me burn the CD again and see what happens. 

few months ago, i had tried to use dban. nope it wont work for me. It could not wipe my hd clean.

my drive works though. If I play music, software etc, the comp identifies it right and plays ok. 

I even disabled the hdd in the boot order kind of forcing it to look at CD alone. nope. it just refuses. not sure what is the problem. pls help.

---

### Post by geniustud on 2008-03-27
samguy,

I have downloaded ubunty and I cut pasted it from c:\ to my Cd drive. is this the right way to burn the image or there is a suggested way? I do not have any specialized burn s/w. I am using xp to burn it. Pls suggest.

thanks in advance to you and iris for all your help and patience.

---

### Post by heartburnkid on 2008-03-27
What kind of CD drive are we talking about here? PATA, SATA, SCSI, USB?

Chances are, either the problem is that the boot order isn't set properly for your setup, or the drive is just having issues booting from the disc (I had a similar issue installing Win XP once).

---

### Post by heartburnkid on 2008-03-27
> **geniustud said:**
> samguy,

I have downloaded ubunty and I cut pasted it from c:\ to my Cd drive. is this the right way to burn the image or there is a suggested way? I do not have any specialized burn s/w. I am using xp to burn it. Pls suggest.

thanks in advance to you and iris for all your help and patience.

Never mind, there's your problem.

You need software to interpret and burn the .iso image; otherwise, all you're doing is sticking the image on your disc as a file.  Your CD burner should have come with someting (Easy CD Creator, Sonic, or Nero Express, most likely).  If not, you can try [CDBurner XP](http://www.cdburnerxp.se/).

Regardless of what software you're using, look for an option called "Burn Image".  That's what you want to use.

---

### Post by geniustud on 2008-03-27
heartburnkid,

I agree with you. This is what I did. I burned a copy, changed boot setting in my laptop to boot from CD and restarted. The laptop ignored the CD and started the XP. So, as samguy was saying I may have been getting copies with ISO images. Let me try with right way you both have suggested and come back. 

Thanks to you and sumguy321.

---

### Post by Jerry N on 2008-03-28
If you can get someone to download and create a boot disk, you might also try Knoppix ([www.knoppix.com](www.knoppix.com)).  Download of the ISO and creation of the bootable live CD works the same with Knoppix as with Ubuntu.  Knoppix has some kind of virus checker - I think it might need internet access to work.  It also has the capability to create a boot floppy in case you can't get your computer to boot from the CD (and, I might add, in case your computer has a floppy drive!).  

Knoppix is intended to run as a live CD and has a lot of diagnostic capability.  You can also do a hard drive install as a debian operating system but I haven't seen any advantage (at least to me) of doing that.

Jerry

---

### Post by geniustud on 2008-03-29
Hi all,

Thank you very much and it worked like charm! However here is my new problem. I copied all my files and I am trying to reinstall windows XP. My explorer shows both the DVD drives as d:\ and E:\. But if I insert the win XP Cd, it refuses to recognise it. One says 'o objects' and other says pls insert a disk. Wonder what is happening. Now my keyboard and mouse have also stopped working. 

my pc is dell dimension 4700, P4, 1gB RAm and 160GB hdd. 

Pls help.

---

### Post by iris-n on 2008-03-29
geniustud,

I'm glad it worked. Remember to thank heartburnkid with the medal icon in the lower part of the post. And please state clearly what solved your problem, so that others could find and use your solution more easily.

Now, here isn't the best place to get help installing windows, but let me try and guess: if you're seeing the drives as letters, you're trying to install it from within your windows. If I remember well, you had to boot the cd to install it, after removing it.

And some piece of advice: if you install windows after ubuntu, it will overwrite the boot registrer, so that in order to ubuntu be able to boot you would have to fix that, possibly with the [SuperGrub]("http://supergrub.forjamari.linex.org/") disk.

My way to do it would:

Wipe everything, with DBAN
Partition nicely
Install windows
Install ubuntu

Please state more clearly the problems with your mouse and keyboard, and in a separate thread.

Iris

---

