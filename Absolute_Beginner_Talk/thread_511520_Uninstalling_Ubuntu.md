---
title: "Uninstalling Ubuntu"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by 4Real on 2007-07-27
Ubuntu is great I installed it on several computers but on 1 of my computers it is slow because i barely matches expectations... how do i uninstall ubuntu????

---

### Post by Songwind on 2007-07-27
The only thing to do to uninstall Ubuntu is to delete its partitons.

You can probably do that with the installer disk for whatever OS you are going to install next.  Or, you can use GParted on the Ubuntu live CD.

---

### Post by 4Real on 2007-07-27
You kind of lost me there :confused::confused::confused:

Sorry I just started using Ubuntu for 3 days :(

---

### Post by p_quarles on 2007-07-27
Sorry, Songwind, but that's incorrect. That will delete Ubuntu, but will also delete GRUB, thereby preventing you from booting into Windows. 

Here's a step-by-step:
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by HermanAB on 2007-07-27
You can wipe the whole drive, then install Windoze. Something like this:
sudo dd if=/dev/zero of=/dev/hda bs=1M

That will take a while.

Cheers,

Herman

---

### Post by st33med on 2007-07-27
Boot up the LiveCD. Install Ubuntu, but manually handle the partition. Remove the ext3 and linux-swap partitions and go foward.

Now the Ubuntu OS is uninstalled. If you want something like Ubuntu on your computer, but with lower system requirements, try Xubuntu.

---

### Post by Songwind on 2007-07-27
My point is that there is nothing to install Ubuntu from.  If you wanted to uninstall OpenOffice you would go into Ubuntu, where OO.org is installed, and remove the package, right?

There is no lower level than Ubuntu on you system.  There is no software you can start that controls Ubuntu and is responsible for removing it.

So, to remove Ubuntu you just need to delete the partitions that it is installed on.  When you install some other OS, you can probably just instruct it to delete your Ubuntu partitions and use the space.

---

### Post by p_quarles on 2007-07-27
Again, no. And you didn't read the link I gave. Deleting the Ubuntu partitions will also destroy the GRUB bootloader, and completely disable the MBR. Your system will hang. The best way to prevent this is to restore the Windows MBR *prior* to deleting the Ubuntu partitions. 

If you don't believe me, try it yourself.

---

### Post by st33med on 2007-07-27
I've removed the partitions before and had Windows still work. But I realized why. I made Ubuntu's root install on it's own partition, not the MBR. So, essentially, It deleted GRUB and enabled windows to boot.

So, I would suggest following p_quarles link. DO NOT DELETE THE PARTITION!!!!!!!!!!!

---

### Post by 4Real on 2007-07-27
> **HermanAB said:**
> You can wipe the whole drive, then install Windoze. Something like this:
sudo dd if=/dev/zero of=/dev/hda bs=1M

That will take a while.

Cheers,

Herman

Wipe the drive??? I've heard that thats a risky way.

---

### Post by 4Real on 2007-07-27
> **st33med said:**
> Boot up the LiveCD. Install Ubuntu, **but manually handle the partition**. Remove the e**xt3 and linux-swap partitions and go foward**.

Now the Ubuntu OS is uninstalled. If you want something like Ubuntu on your computer, but with lower system requirements, try Xubuntu. 

Augh I dont get it.. I'm newb... i wish i installed Kubuntu in the beginning :(

---

### Post by HermanAB on 2007-07-27
There is a very simple solution for the slow PC - get Puppy Linux and run that off a CDROM till you know a little more about Linux: 
[http://puppyos.org/](http://puppyos.org/)

The nice thing about Linux is that there are so many flavours to choose from and deep down they are all the same, so the better you get to know any one, the better you get to know them all.

---

### Post by 4Real on 2007-07-27
so you sure that wiping the drive will do the trick? i have windows 98.. I have to boot CD....

---

### Post by p_quarles on 2007-07-27
> **4Real said:**
> so you sure that wiping the drive will do the trick? i have windows 98.. I have to boot CD....
No, you don't need to do that. Follow the link in my earlier post, and you'll get clear, step-by-step instructions for removing Ubuntu safely, without reinstalling Windows.

---

### Post by speeddemon8803 on 2007-07-27
BACK UP EVERYTHING ON PC BEFORE DOING THIS!

Ok to solve this drama indulged session, save all the information that is pertinent in the windows partition to an external medium, grab you a floppy disk, insert it to your floppy drive.  make you a startup disk by going to my computer, right clicking flopppy drive (either your A: or B: drive. and clicking Format, then use the Create startup disk option. Oh, one more itty bitty feature I forgot to mention, has to be a windows 98 start up disk.

Once you have created your start-up disk you must restart your pc.

When it goes to the option of with cd or without cd, look for the option at the botom that gives you the keystrokes for command prompt, do that!

When you get to command prompt. type in FDISK, follow the options, create your Primary master...and if you want it partitioned any more than that do the primary slave and so on.

once you have your hard drive set up with the partitions you wish press escape until you get to the main command prompt.

Here, type in "format C:/s" DO NOT FORGET THE /s or your drive will not be bootable!

once you get done with all that, restart your computer, pop in the windows cd, restart yet again, go to your command prompt like I showed you earlier.

next type in cd X: (where X: denotes your CD-rom drive, its definately going to be different!)

When your in your cd drive, type in Dir

Look for something that says setup.

after you see that type in....you guessed it..SETUP!

If all goes well your little computer will be purring like a kitten installing Windows!

If not, come back!

---

### Post by 4Real on 2007-07-28
ok thanks after i remove ubuntu im thinking of installing Damn Small Linux... I tried installing Puppy Linux but it just wont work :confused:

---

### Post by anewguy on 2007-07-28
> **speeddemon8803 said:**
> BACK UP EVERYTHING ON PC BEFORE DOING THIS!

Ok to solve this drama indulged session, save all the information that is pertinent in the windows partition to an external medium, grab you a floppy disk, insert it to your floppy drive.  make you a startup disk by going to my computer, right clicking flopppy drive (either your A: or B: drive. and clicking Format, then use the Create startup disk option. Oh, one more itty bitty feature I forgot to mention, has to be a windows 98 start up disk.

Once you have created your start-up disk you must restart your pc.

When it goes to the option of with cd or without cd, look for the option at the botom that gives you the keystrokes for command prompt, do that!

When you get to command prompt. type in FDISK, follow the options, create your Primary master...and if you want it partitioned any more than that do the primary slave and so on.

once you have your hard drive set up with the partitions you wish press escape until you get to the main command prompt.

Here, type in "format C:/s" DO NOT FORGET THE /s or your drive will not be bootable!

once you get done with all that, restart your computer, pop in the windows cd, restart yet again, go to your command prompt like I showed you earlier.

next type in cd X: (where X: denotes your CD-rom drive, its definately going to be different!)

When your in your cd drive, type in Dir

Look for something that says setup.

after you see that type in....you guessed it..SETUP!

If all goes well your little computer will be purring like a kitten installing Windows!

If not, come back!

There's an important distinction to be made here for all the other new people who are reading this thread, trying to figure out how to go back to Windows.  If you have a dual-boot system,  you DO NOT need to reinstall Windows.  You DO NOT need to format your drive.  DO NOT delete your Linux partitions.  This is speaking from MANY tries at this myself - that's why I wrote the guide that's pointed to earlier in this thread.  Don't make things complicated for new people - let them follow my guide, which wil have them remove Linux and leave their system booting into Windows.  Other distros, etc., can be suggested AFTER they have gotten back to a clean starting point!:)  If we keep things simple, and distinctly to the point, we make their experience more enjoyable.  The more people who have an enjoyable experience, the good word of mouth there will be for Ubuntu. You can follow the advise I quoted here if you want to completely start over, but if you just want to remove Ubuntu from a dual-boot system, PLEASE see my how-to as pointed to earlier - you will be GLAD YOU DID!!!:)

---

### Post by speeddemon8803 on 2008-02-22
I wasnt aware of your stuff, i gave it in depth because thats what i was taught...sorry new guys!

---

