---
title: "How to uninstall ubuntu?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Mightyspider on 2007-04-24
Hi there i would like to know how to uninstall ubuntu without uninstalling windows on my laptop can anybody help me with it please


Thanks in advance

---

### Post by will_in_wi on 2007-04-24
I assume what you mean is that you want the computer to boot right into windows and to have the space that you put into ubuntu avalabile on your windows hd.

I also am assuming you have windows xp. This might work in vista too but I am unsure having not used it myself.

I am also assuming you have only one disk.

FIRST******
Make sure you don't have any data on ubuntu that you want saved. This will destroy the ubuntu stuff on your computer but will leave windows intact. It is best that you have the entire drive backed up, just in case you mess up the entire system by accident.

To get the computer booting right into windows with out the menu, find your windows install disk and boot from it. While it is booting it will say something like hit somefkey for recovery console. Go to the recovery console using that. Once there you type help and hit enter. In the output it will come up with a list of commands. The command you want is fixmbr (I think. It is mbr something). Type fixmbr, hit enter and then type exit and hit enter. Now reboot. It should now boot right into windows.

If this is the case then you can move to the next step.

To remove the ubuntu partitions and allow windows to access the space, you need the ubuntu desktop install cd. Boot into the cd. Now open System -> Administration -> Gnome Partition Editor. Inside you will see a listing of the partitions on your disk. You need to delete and partitions that say swap, reiserfs, ext2, ext3, or jfs.

DO NOT remove any partitions that say ntfs. If you do by accident, close the application and click quit instead of cancel. Then reopen it and start over with removing partitions.

After you are sure that you have the partitions removed, click Apply. This could take a while. When it is done, ubuntu will be off of your computer. Close and reopen gnome partition editor. Now find the ntfs partition and resize it so that it takes up the whole drive. Click apply, wait until it finishes, close gnome partition editor, reboot and you should boot right into windows and be able to access the new space.

---

### Post by mspolar on 2007-04-24
why on earth would you do a thing like that??

---

### Post by will_in_wi on 2007-04-24
I know that I would (I am not the original poster) remove ubuntu if I had a major project in windows and I had no space. Or if I was a new user and I could not figure out ubuntu and needed to get on with life.

---

### Post by solar george on 2007-04-24
> why on earth would you do a thing like that??

The point of the ubuntu forums is to help people get the best from their computing experience, if they feel that they do not wish to continue using Ubuntu we should help them to return to a system that they are familiar with, not to force them to continue with a system that they don't like, by refusing to answer their questions. Apart from anything else it sets us apart from people like Micro$oft and Apfel who will will do anything they can to lock you to using their systems.


solar.george

---

### Post by allforcarrie on 2007-04-24
> **mspolar said:**
> why on earth would you do a thing like that??

constant crashing of firefox...

---

### Post by aktiwers on 2007-04-24
> **allforcarrie said:**
> constant crashing of firefox...
Happend on my second PC too. Removing and installing the newest version of Firefox fixed it.

---

### Post by Mightyspider on 2007-04-26
Hi guys thanks for the threats thats been send i saw that some people asked me why i want to uninstall ubuntu?

Hey im not leaving the linux just like that i want to learn how to use it prop.Im going to install vista now on my pc and then i will go for red hat aswell so i want to remove ubuntu and then install red hat after uninstalling ubuntu.

But i would like windows to stay on m pc aswell because im doing my studies in windows.

Well guys i will see what happens if i put vista on to my pc now so i will let everybody know whats going on ok but remember im not done with linux i will stay with linux i love it to bits.......


Keep Well
Cheers Guys
Mightyspider

---

### Post by lepz on 2007-04-26
Good luck with whichever you use. :)

---

### Post by teejayh on 2007-04-26
I tried this but my other OS is Windows Vista Home premium.  The Vista DVD does not do anything with commands (it tries to fix problems itself).  But I do need to uninstall ubuntu now and then reinstall it later.  Would someone give me some instructions on how to do this and change the mrb so that ubuntu is not listed as a boot option anymore?  Thanks!

---

### Post by Demz on 2007-04-26
> **teejayh said:**
> I tried this but my other OS is Windows Vista Home premium.  The Vista DVD does not do anything with commands (it tries to fix problems itself).  But I do need to uninstall ubuntu now and then reinstall it later.  Would someone give me some instructions on how to do this and change the mrb so that ubuntu is not listed as a boot option anymore?  Thanks!
don't people ever use Google anymore? or a Forum Search utility

---

### Post by Josh1187 on 2007-04-26
I bought a laptop that has Xubuntu on it. How do I see if it still has Windows on it so I can boot into windows? 

dont know much about ubuntu?

---

### Post by teejayh on 2007-04-26
I searched both google and the forum here but all that I found were posts dealing with fixing the mrb in Windows XP (fixmbr).  I have Vista here and the Vista DVD does not work the same as the XP CD.

---

### Post by XTREEM|RAGE on 2007-04-27
> **teejayh said:**
> I searched both google and the forum here but all that I found were posts dealing with fixing the mrb in Windows XP (fixmbr).  I have Vista here and the Vista DVD does not work the same as the XP CD.

i would like to know that 2, i have vista business and ****** up my feisty :x
And wanna reinstall the thing!

---

### Post by robfuller on 2007-04-27
I count as one of the non-technical users who tried Ubuntu but had big problems with it on my laptop. I have been trying for a long time to work out how to uninstall it. I searched the Ubuntu documentation site and the wiki and couldn't find anything at all - but now I've can follow will_in_wi's instructions at the beginning of this thread.

But, one more question: I'm prepared to give Feisty Fawn a go, because it sounds like it's more likely to be able to deal with my laptop's wireless card. I've had a nightmare trying to upgrade to FF from within Ubuntu. How do I do a completely fresh re-install? Should I uninstall Ubuntu and remove the partition as will_in_wi described, and then start from scratch? Or is there some easier way?

Thanks very much,
Rob

---

### Post by am_pcguy on 2007-04-28
Vista is different and more difficult to restore the MBR than previous versions of Windows.

If you used Grub as your bootloader...
Go to [SUPER GRUB ISO Homepage]("http://supergrub.forjamari.linex.org/") and grab the Super Grub ISO.  Burn it to a CD.  Boot to the Super Grub disk, READ THE INSTRUCTIONS CAREFULLY!  Backup your MBR.  Then you will want to Fix 2000, XP, 2003 MBR, it should be under the Windows, or Advanced Windows option in the menu.  When the operation is complete (takes a second) exit the cd, eject the cd, reboot and no more Grub.

Hope that helps someone,  I searched for hours.  There is a file on the retail Vista disk bootrec.exe that has options to repair the Vista MBR.  I don't know of anyone with a laptop that has a retail Vista disk, you get restore CD's.

---

### Post by siya_kh1983 on 2007-04-28
I used windows... and will use in now and tomorrow. you and me and all of the people in world know that windows is a good OS but there is some thing wrong in another OS...
when I have OS course in university I find out there is a new and free OS in world ... I use the first Ver of ubuntu. and use it now. and will use it in tomorrow..
I had a lot of problem with this OS. but I solve them. when some people that use windows come and use ubuntu they say that this OS is so professional for some people like us that don't know how to use command line... righe that windows get people too lasy, but it is a good OS ...

I use asp.net and C# (windows programming and web programming). when u wanna write windows app , what can u do??? use Ubuntu to write a program??? in most university student learn programming... they know c++ and pascal, but they don't wanna use them until there is a visual c++ or visual c#.net...

I write this post becuase I research that why people in my country like windows...
they wanna install programs with just some click,,, they don't wanna download pre queste files for install...

I use UBUNTU and use ubuntu and learn ubuntu and tech ubuntu in my country that tomorrow maybe some people like this OS but there is a long way that this OS take windows... I hope that days come and All people in the world work with this OS.

UBUNTU is a god of all of the OS in the world because it's free and u and me and anybody in world can use it without any money...

---

### Post by Nythain on 2007-04-28
> **Demz said:**
> don't people ever use Google anymore? or a Forum Search utility
i guess that skill died along with chivalry, punk, courteousness, and most of all helpfullness

on another note, good luck with redhat, out of all the distro's i tried in a 3 month period, ubuntu (well kubuntu actually) was probably hands down the best out there for a newcomer like me.

i stopped using windows before vista came out, so i was unaware of the boot changes between it and xp... guess thats more great reason i dont rely on microsoft anymore.

to everyone who posted about how to just remove ubuntu to do a fresh install/upgrade, its really an easy matter up poppin in an install cd, starting the install, and telling it to format any of the following partitions you have created... /, swap, /boot, /home if you dont mind losing configuration files (wich wouldnt be to bad since you'll have newer/different versions of software installed, might cause conflicts if you kept the originals... just dont format any partitions where you have storage media, and continue on with the installation, it theoretically should be that easy

---

### Post by XTREEM|RAGE on 2007-05-10
> **Nythain said:**
> i guess that skill died along with chivalry, punk, courteousness, and most of all helpfullness

on another note, good luck with redhat, out of all the distro's i tried in a 3 month period, ubuntu (well kubuntu actually) was probably hands down the best out there for a newcomer like me.

i stopped using windows before vista came out, so i was unaware of the boot changes between it and xp... guess thats more great reason i dont rely on microsoft anymore.

to everyone who posted about how to just remove ubuntu to do a fresh install/upgrade, its really an easy matter up poppin in an install cd, starting the install, and telling it to format any of the following partitions you have created... /, swap, /boot, /home if you dont mind losing configuration files (wich wouldnt be to bad since you'll have newer/different versions of software installed, might cause conflicts if you kept the originals... just dont format any partitions where you have storage media, and continue on with the installation, it theoretically should be that easy

Yeah it is really that easy...but you cant boot to windows anymore :/
That's why....and you cant fix the mbr that easy anymore with vista ;x

But i'm an happy ubuntu feisty user + vista ;D

---

### Post by nilved on 2007-05-17
Is it possible to just go into something like Partitionmagic, erase your Linux partitions, and resize your Windows one? I want to make sure that there are absolutely no traces of Ubuntu left behind that could mess up anything.

Some bad experiences!

(and sorry to revive an old thread--I didn't think I really needed to make a new one.)

---

