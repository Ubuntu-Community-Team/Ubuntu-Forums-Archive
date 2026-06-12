---
title: "Grub"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Valthinos on 2008-03-10
I had a problem with Ubuntu so I decided I would remove it and re-install it. I booted into Windows and used Partition Magic to delete my Linux partition and Linux swap. I restarted my computer and the GRUB menu doesn't show and instead I see a black screen with this:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 22

I can't even boot into Windows now, if anyone knows a simple way to fix this, it'd be so so so much appreciated.

---

### Post by Oldsoldier2003 on 2008-03-10
> **Valthinos said:**
> I had a problem with Ubuntu so I decided I would remove it and re-install it. I booted into Windows and used Partition Magic to delete my Linux partition and Linux swap. I restarted my computer and the GRUB menu doesn't show and instead I see a black screen with this:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 22

I can't even boot into Windows now, if anyone knows a simple way to fix this, it'd be so so so much appreciated.
boot from a windows disk and do fixmbr
that will resore a windows style mbr and from there you can boot windows normally until you decide to reinstall Ubuntu

---

### Post by marufaberlin on 2008-03-10
Grub needs a dir on the linux partition called /boot. If it doesn't find that, it comes up with "Error 22". Once you re-installed Ubuntu, a new Grub is installed and it will work perfectly. P.S: you don't need to format the linux partition before a reinstall, the installer does that for you.

---

### Post by sayakb on 2008-03-10
+1 to fixmbr
Insert the Windows disk and let it load. Press 'R' on the first screen for the console to load. Then select the detected Windows. You would be asked for Administrator password (which is by default blank, if not changed). After you get into cmd, type
```
fixmbr
fixboot
```

Reboot your PC.

---

### Post by ukripper on 2008-03-10
Easy way to fix grub error 22 is use super grub disk. it will help you fix your HD entries.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

or if you just want to use windows then you need your Windows Cd and boot into it  and in recovery console - **fixmbr** as posted above.

If it doesnt fix your problem use following steps:
1. Boot into XP Cd.
2. Go to recovery
3. Recovery console type: bootcfg /rebuild and then press enter
4. The first prompt asks Add installation to boot list? (Yes/No/All ) Type Y press enter
5. Enter Load Identifier:: Windows XP press enter
6. Enter OS Load options:.
Type /Fastdetect and press Enter.
7. Exit and reboot.

---

### Post by forrestcupp on 2008-03-10
-1 to fixmbr
I tried all of those Windows commands when I had that problem and they didn't work.  That's because the Windows boot loader comes after GRUB.

+1 to Super Grub
It has an option to restore the Windows boot loader.  It's the only thing I found that actually overwrites GRUB and works properly.

But if you're planning on reinstalling Ubuntu, just reinstall it with your LiveCD and it will fix all your problems.

---

### Post by Oldsoldier2003 on 2008-03-10
> **forrestcupp said:**
> -1 to fixmbr
I tried all of those Windows commands when I had that problem and they didn't work.  That's because the Windows boot loader comes after GRUB.

+1 to Super Grub
It has an option to restore the Windows boot loader.  It's the only thing I found that actually overwrites GRUB and works properly.

But if you're planning on reinstalling Ubuntu, just reinstall it with your LiveCD and it will fix all your problems.
-1 to not understanding...BOOT from windows cd (its a live cd)

---

### Post by ukripper on 2008-03-10
> **forrestcupp said:**
> -1 to fixmbr
I tried all of those Windows commands when I had that problem and they didn't work.  That's because the Windows boot loader comes after GRUB.


Grub comes first but once you fixmbr it overwrites Grub. That is why it is recommended to always install linux distro after windows.

---

### Post by Valthinos on 2008-03-10
Thanks for all the help everyone! I tried booting from the Ubuntu CD because marufaberlin said after installing Ubuntu again the problem would be fixed. However, I press f12 at the screen and choose to boot from CD but it gives me the same error. I also tried looking for the Windows Live CD but my house is kind of messy and I seem to have misplaced it, is there a site where I can get it and burn it on to a CD? Also, I went to the super grub site and I got lost, can someone tell me what I'm supposed to do there? 
Once again, thanks for all the help everybody!

---

### Post by ukripper on 2008-03-10
> **Valthinos said:**
> Thanks for all the help everyone! I tried booting from the Ubuntu CD because marufaberlin said after installing Ubuntu again the problem would be fixed. However, I press f12 at the screen and choose to boot from CD but it gives me the same error. I also tried looking for the Windows Live CD but my house is kind of messy and I seem to have misplaced it, is there a site where I can get it and burn it on to a CD? Also, I went to the super grub site and I got lost, can someone tell me what I'm supposed to do there? 
Once again, thanks for all the help everybody!

Download super grub cd image and burn it on a Cd and boot from it!

---

### Post by Valthinos on 2008-03-10
I put in the CD with super grub and I get a blank screen for a bit and then the error comes up again! What do I do? Also, is there someplace I can download the Windows CD? I could try that.

---

### Post by Duck2006 on 2008-03-10
You can try the ultimate boot cd.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

> I tried all of those Windows commands when I had that problem and they didn't work. That's because the Windows boot loader comes after GRUB.

No, in your MBR when you load grub then grub reside there, Then you load win then the win boot loader resides there.

---

### Post by Oldsoldier2003 on 2008-03-10
> **Valthinos said:**
> I put in the CD with super grub and I get a blank screen for a bit and then the error comes up again! What do I do? Also, is there someplace I can download the Windows CD? I could try that.

make sure your bios is set to boot from the cdrom first

---

### Post by forrestcupp on 2008-03-10
> **Oldsoldier2003 said:**
> -1 to not understanding...BOOT from windows cd (its a live cd)
Sorry.  What I meant was that if you are going to reinstall Ubuntu, you can boot to your Ubuntu LiveCD and reinstall it, and it will fix your GRUB problems.  But if you're not reinstalling Ubuntu, and you just want to get to Windows, you should download Super Grub, burn the iso to a CD, boot to your Super Grub CD and choose the option to fix or reinstall your Windows boot loader.  That's what worked for me.

> **ukripper said:**
> Grub comes first but once you fixmbr it overwrites Grub. That is why it is recommended to always install linux distro after windows.

I hear what you're saying, but the fixmbr command just doesn't overwrite Grub for some reason.  None of the commands that everyone says to use worked for me.  It's like it just fixed the Windows boot loader, which didn't need fixed, and it left GRUB alone.  When I had this problem, Super Grub is the only thing that worked for me, and I tried a lot of things, including EasyBCD, which didn't work.

---

### Post by ukripper on 2008-03-10
> **Valthinos said:**
> I put in the CD with super grub and I get a blank screen for a bit and then the error comes up again! What do I do? Also, is there someplace I can download the Windows CD? I could try that.

Did you burn it as image or data?

---

### Post by stchman on 2008-03-10
> **Valthinos said:**
> I had a problem with Ubuntu so I decided I would remove it and re-install it. I booted into Windows and used Partition Magic to delete my Linux partition and Linux swap. I restarted my computer and the GRUB menu doesn't show and instead I see a black screen with this:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 22

I can't even boot into Windows now, if anyone knows a simple way to fix this, it'd be so so so much appreciated.

Yes the command is:

```
fdisk /mbr
```

You will need to get a boot CD or floppy to do this.

---

### Post by Oldsoldier2003 on 2008-03-10
> **stchman said:**
> Yes the command is:

```
fdisk /mbr
```

You will need to get a boot CD or floppy to do this.

yep thats the tried and true method when all else fails :) i just hate telling people to use fdisk because its easy for them to "goof' :0

---

### Post by Valthinos on 2008-03-10
I made sure my computer is set to boot from CD before anything else but it didn't work. I'm downloading ultimate boot cd right now, I hope it works.. Also, it was an .iso file I burned on to the cd, that means it's image right? How do I check?

---

### Post by Oldsoldier2003 on 2008-03-10
> **Valthinos said:**
> I made sure my computer is set to boot from CD before anything else but it didn't work. I'm downloading ultimate boot cd right now, I hope it works.. Also, it was an .iso file I burned on to the cd, that means it's image right? How do I check?

burn image to cd, not copy. if you look at the cd and it has a directory structure in it then you did it right

---

### Post by Duck2006 on 2008-03-10
This should give you a bit more info.

[http://www.ultimatebootcd.com/faq.html](http://www.ultimatebootcd.com/faq.html)

---

### Post by Duck2006 on 2008-03-10
> **Oldsoldier2003 said:**
> burn image to cd, not copy. if you look at the cd and it has a directory structure in it then you did it right

+1

---

### Post by Valthinos on 2008-03-10
Um.. sorry, I'm not too great with computers, how do I check for a directory?

---

### Post by Duck2006 on 2008-03-10
The file you downloaded is it a *.iso?
Then it is an image file.

---

### Post by Valthinos on 2008-03-10
Yes, it's an .iso file and the error was still there when I booted from the cd.

---

### Post by Duck2006 on 2008-03-10
Then burn it as an image to a cd.
The last link will tell you haw to do that.

---

### Post by Valthinos on 2008-03-10
This is the right file?
 [http://www.download.com/UBCD4Win/3000-2086_4-10550208.html?part=dl-UltimateB&subj=dl&tag=button&cdlpid=10550208](http://www.download.com/UBCD4Win/3000-2086_4-10550208.html?part=dl-UltimateB&subj=dl&tag=button&cdlpid=10550208)

Also, it's an .exe file...

---

### Post by Jadd on 2008-03-10
> **Oldsoldier2003 said:**
> -1 to not understanding...BOOT from windows cd (its a live cd)
Actually, the windows CD is not a live CD, it's just a bootable CD. Can you run an entire system, with a web browser, games, in fact all the apps that will be installed, without touching the hard disk? Ubuntu, yes, Windows, nooo.

---

### Post by Duck2006 on 2008-03-10
If it is an *.exe file then it is self extracting file. You will needs windows to extract it.
You may be able to do it wine not sure.

---

### Post by Oldsoldier2003 on 2008-03-10
> **Jadd said:**
> Actually, the windows CD is not a live CD, it's just a bootable CD. Can you run an entire system, with a web browser, games, in fact all the apps that will be installed, without touching the hard disk? Ubuntu, yes, Windows, nooo.

(its a live cd) was used sarcastically since we were talking about booting to the cd- which would bypass grub completely

---

### Post by Valthinos on 2008-03-11
I found a Windows CD in a box of other CDs but I'm not sure if it's the right one. It looks like  this: [http://i2.iofferphoto.com/img/item/153/567/04/cd4dell.jpg](http://i2.iofferphoto.com/img/item/153/567/04/cd4dell.jpg) but it's red and it's XP Home Edition not Professional. Is this the CD I should boot from?

---

### Post by sayakb on 2008-03-11
> **Valthinos said:**
> I found a Windows CD in a box of other CDs but I'm not sure if it's the right one. It looks like  this: [http://i2.iofferphoto.com/img/item/153/567/04/cd4dell.jpg](http://i2.iofferphoto.com/img/item/153/567/04/cd4dell.jpg) but it's red and it's XP Home Edition not Professional. Is this the CD I should boot from?

It doesn't matter which Windows CD you use. PLus, XP Home should work equally good since you aren't actually installing Windows but just overwriting the boot record, I have fixed hundreds of similar problems w/ fixmbr and then fixboot, so it is definite that it would work. 
Fixmbr overwrites Grub on the Master Boot Location.. Just insert the Windows disk, wait for it to load, press R to enter recovery mode, select your windows version and type fixmbr and fixboot into the cmd.

---

### Post by Valthinos on 2008-03-11
My computer isn't detecting the CD in either drives.. I made sure the BIOS is set to boot from CD first, it doesn't even recognize the Ubuntu CD. I even pressed F12 and asked it to boot from the CD but I just get the Grub error. Also, I don't know what this is but it might help, I pressed IDE Drive Diagnostics and it came back with:
Primary SATA 

Drive 0: WDC WD1600JD-75HBB0

Does this mean anything?

---

### Post by Valthinos on 2008-03-11
I'm really desperate for help now.. I use my computer a lot and when March break is over, I'll need it to do work. I also have family pictures all the way back to 1999 on it. If someone knows why my CD drive isn't detecting the CD, please help. Once that's fixed, I can do the FIXMBR thing. All the help is appreciated!

---

### Post by dstew on 2008-03-11
What bootable CD's do you currently have in hand? Are you sure they are bootable (that is, can you boot the CD's in another computer)?

---

