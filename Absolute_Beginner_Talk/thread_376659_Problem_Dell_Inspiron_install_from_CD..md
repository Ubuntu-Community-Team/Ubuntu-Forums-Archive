---
title: "Problem: Dell Inspiron install from CD."
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by mountielad on 2007-03-05
Hey,
I'd appreciate input with this problem. 

I am trying to install Ubuntu 6.10 from the CD in my laptop (Dell Inspiron 1505) CD Drive. To the best of my ability I set the computer's BIOS to boot from CD (i.e. re-order CD-ROM to the top of the list). Unfortunately the following shows up on the screen when I turn it on:

Media Test Failure, check cable
Exiting Broad com PXE ROM
Operating System Not Found
_

When I revert back to boot from Hard Drive it's fine.
I had the Ubuntu 6.10 installation CD in the CD ROM. It has been checked with the MDSum programme.

Does anyone know the route to take to get BIOS to boot from CD on a Dell Inspiron laptop?

Thank you.

---

### Post by wataboutbob on 2007-03-05
You don't necessarily have to change the boot order under BIOS. Press F12 when your computer starts up and Dell should throw all available boot options, i.e., HDD or CD/DVD or USB if enabled.

---

### Post by mountielad on 2007-03-05
Ok, thanks.
Do I press F12 when the Dell logo appears?

---

### Post by bigken on 2007-03-05
yes 


how did you burn the iso (ubuntu cd)

---

### Post by mountielad on 2007-03-05
I downloaded it from the website onto my desktop.
The I burned it onto a CD.

---

### Post by wataboutbob on 2007-03-05
> **mountielad said:**
> Hey,

Media Test Failure, check cable
Exiting Broad com PXE ROM
Operating System Not Found

Thank you.

Besides, I think you may have chosen Boot from Network by accident. Dell's built-in ethernet controllers are Broadcom based.

Try it again. Its an awesome experience using Ubuntu and Beryl.

---

### Post by bigken on 2007-03-05
how did you burn it what software did you use ?

---

### Post by mountielad on 2007-03-05
Well I think it was either Roxio or remotely Nero. I'm not quite sure as I don't have it with me now.

---

### Post by bigken on 2007-03-05
take a look [here]("https://help.ubuntu.com/community/BurningIsoHowto") on how to burn the iso :)


then like wataboutbob says select F12 at dell boot screen [URL="http://ubuntuforums.org/member.php?u=245237"]
[/URL]

---

### Post by mountielad on 2007-03-05
OK, I looked at that part before but missed out on the Infra Recorder part, so originally I burned straight from the dowloaded file to the CD without the image specifications perhaps.

---

### Post by bigken on 2007-03-05
just follow the guide and you should be up and running in no time good luck and enjoy ubuntu :)


also make sure you backup any important data 1st and you must run defrag in windows before you install ubuntu also look up automatix and easyubuntu
to install codecs and extra software

---

### Post by mountielad on 2007-03-05
**New Problem**(Dell 1501 Windows XP)

I have placed the Ubuntu disk in checked for defects (none).

Went to install and got to Step 5 of 7, which only gave me one option: Manually edit partition table.
I went forward and at the 'Prepare Partitions' it said **No Devices detected**. 
I clicked forward again and got to Step 6 of 7: Prepare mount points. 
It allows me to scroll mount points but I cannot allocate the partition (when I click on the box nothing comes into it) or reformat and I cannot go further at this stage of the instalation.

I have just defragmented my Local C Drive. Should I do anything else? Thank you.

---

### Post by bigken on 2007-03-05
you could try using gparted liveCD its in my signature see if you create your partitions that way :)

---

### Post by mountielad on 2007-03-05
Afraid I've been looking around for what that is and still not understanding.
Do I have to download it and run it to allow partitioning when I boot and want to install Ubuntu or is it in the Ubuntu CD?

Sorry, I'm quite new to this.

---

### Post by mountielad on 2007-03-05
I've tried using the Gparted function:

From the Ubuntu live CD: System>Admin.>Gnome partition editor> 'No devices detected'.

Has anyone had a similar problem where it claims there are no partition devices detected?

---

### Post by bigken on 2007-03-06
i think the problem is its a sata hdd try searching for sata problems in the forum sorry I cant be of anymoren help also try google

---

