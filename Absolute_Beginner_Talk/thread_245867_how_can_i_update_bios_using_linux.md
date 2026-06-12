---
title: "how can i update bios using linux?"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by meenasheskbrat on 2006-08-28
I need to update my bios because it seems to have got corrupted somehow and the keyboard will not work during boot.  I have downloaded and saved the latest bios update to the desktop but have no idea how to install them.  Any ideas please? I have an advent 7083 laptop with turion 64 mt-30 chip 512m ram and 40g hd and am running ubuntu for the first time.  This is my third day ubunting. It is soooo different to windows I feel like a two legged man at a one legged man's party, but I am happy to learn.
The bios update file is called '$331_B28BAN' and there are 9 items in the folder as follows:  '$331_B28BAN', '331_DOS.BAT', '331_WIN.BAT', 'AFUDOS.exe', 'AFUWIN.exe','filelist.txt', 'Ucoredll.dll', 'Ucoresys.sys', 'Ucorevxd.vxd'.
I can do it, I know I can, I just need to know how and then I'll be a happy ubuntu baby.

---

### Post by amo-ej1 on 2006-08-28
the easiest is to create a (free)dos bootfloppy and boot from this floppy (or  create a bootable cd which used this image) and flash it from there. Since these flashing tools require low level access to the hardware (which in linux is hidden from you by the kernel).

---

### Post by Crosbie on 2006-08-28
What website did you get it from?  They should give you instructions on how to do this... *very* carefully.

If I remember rightly from last time I did this, the idea is to boot from a DOS floppy disk to which you've added these programs, then run them from the floppy disk environment.  You should be able to create a bootable floppy disk from within Linux using an image file... but you'll need more expert help on this than I can offer.

Don't rush it - this can be a risky operation.

---

### Post by Metacarpal on 2006-08-28
It looks like those BIOS update files were written to run from Windows.  Do the instructions tell you to save them to a floppy, or do they say to run it from Windows?

---

### Post by amo-ej1 on 2006-08-28
considering the existence of a file AFUDOS.exe it smells like there is also a DOS version ;)

---

### Post by meenasheskbrat on 2006-08-28
Thanks for reply, the problem is I don't have a floppy and if I insert a bootable cd, when I boot, the computer gives the option to boot from cd or hard drive with the option to boot from hard drive as the default option however the keyboard does, not respond until the grub loads and by then it is too late so it always boots from hard disc.

---

### Post by ciscosurfer on 2006-08-28
First, you BIOS is probably not corrupted -- try getting into your BIOS when you boot your computer by either typing F2 or any number of other F-keys (it very dependent on whichever BIOS manufacuter you are using...consult your BIOS manufacturers Web site for further instructions on how to get into your BIOS...then make sure all setting are copasetic).  If I were you, I would check out the [GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html") and search for keyboard.

---

### Post by Crosbie on 2006-08-28
It should boot from a floppy though - and if you don't have a physical floppy, you'll need to pop out and buy one.  (They aren't expensive - I hope you aren't in the middle of nowhere.  it'd be better to wait if you are.)

Have you found the instructions from the page where you found the BIOS?  A link to that page would help us to help you. :)

Is it a USB keyboard, btw?  What model?  You're saying it doesn't respond until *after* GRUB?  When does it start behaving?

---

### Post by meenasheskbrat on 2006-08-28
I didn't notice any instructions to install. it is the laptop manufacturer's website.  If I buy a external floppy drive will I run into the same problems of having to hit a key to boot from it?

---

### Post by Crosbie on 2006-08-28
> **meenasheskbrat said:**
> I didn't notice any instructions to install. it is the laptop manufacturer's website.  If I buy a external floppy drive will I run into the same problems of having to hit a key to boot from it?

Not necessarily - it might be automated.  It's hard to tell unless you link to the website/instructions...

EDIT: Oh, you don't have a floppy *drive.*  Oops.  

Is [this](http://www.uktsupport.co.uk/advent/laptop/7083.htm) a)your computer b) the website you got the drivers from?

---

### Post by meenasheskbrat on 2006-08-28
the link to the download page for the bios is :[http://www.ecs.com.tw/ECSWeb/Products/ProductsDetail.aspx?MenuID=55&LanID=8&DetailID=562&DetailName=BIOS](http://www.ecs.com.tw/ECSWeb/Products/ProductsDetail.aspx?MenuID=55&LanID=8&DetailID=562&DetailName=BIOS)

---

### Post by meenasheskbrat on 2006-08-28
The keyboard is the internal laptop one but when I tried a usb wireless keyboard the same problem exists that the both keyboards will not work until the grub starts and so there is no access to the bios.I read about taking the cmos battery out to reset the bios. Is that a viable option?

---

### Post by meenasheskbrat on 2006-08-28
I think they are meant to run from windows.  Would a usb storage device work instead of a floppy or would I also need to hit a key to boot from the usb?

---

### Post by Crosbie on 2006-08-28
> **meenasheskbrat said:**
> the link to the download page for the bios is :[http://www.ecs.com.tw/ECSWeb/Products/ProductsDetail.aspx?MenuID=55&LanID=8&DetailID=562&DetailName=BIOS](http://www.ecs.com.tw/ECSWeb/Products/ProductsDetail.aspx?MenuID=55&LanID=8&DetailID=562&DetailName=BIOS)

Is that your laptop, or is it the one in [my link](http://www.uktsupport.co.uk/advent/laptop/7083.htm)?  They're rather different models, as far as I can tell.

---

### Post by meenasheskbrat on 2006-08-28
I went to a weblink to the manufacturer of the laptop from an advent support  forum ([http://www.webuser.co.uk/forums/showflat.php/Cat/0/Number/242739/an/0/page/1](http://www.webuser.co.uk/forums/showflat.php/Cat/0/Number/242739/an/0/page/1) make the advent laptops for Curries and Pcworld but they call the laptop a different name on their own website even though the laptop is identical to ne.

---

### Post by encompass on 2006-08-28
I had a problem similar... here is the crazy thing I did...
I added an old windows 95 HD I had in an old computer I was going to threw way... I loaded it in to "safe" mode and than run the file from there...
How did the file get on that drive?  I copied it with linux.  Then letthe drive boot alone without the main drive.
It worked, I danced for an hour and 32 minutes!
I think that would be your best way rather than making images and bottable flash disks.
You can do this with 95 or 98.  Or even Dos HDD.Tell me if you do it.
If you need to use windows to run the file... safe mode should do just fine for it.  Adn win95 98 ussually do jsut fine off any drive... just ignore all the driver requests.
Dirty, but good.

---

### Post by danderson3 on 2006-08-28
I solved this by adding a freedos boot option to my machine,
so there is a dos directory under /root and under it memdisk
and mini.ima files.  I'll see if I can dig up a URL to
the instructions.

David

---

### Post by Crosbie on 2006-08-28
Okay, they do seem to be the same.

Can you run by the basics of your problem again?

What operating system is currently on your laptop?

What do you see when the computer powers on - is there some phrase like 'press DEL for Setup' or whatever?

When does your keyboard become responsive?

Did it work before or is this the first time you've tried it?

Why do you actually need to use your keyboard at this point - to boot from a CD?

Sorry to be tedious but you've got me intrigued. :)

---

### Post by meenasheskbrat on 2006-08-28
Thanks I guess its off to ebay now to buy a wee hd. It had crossed my mind to do that. I just thought there might be a way through the terminal command line. But the hd way is probably the best as I am so new to the linux experience. Thanks for all the help from all you ubuntu helpists.  I'll whip my linux lion into submission until its as tame as a kitten but until then its hard disc swop time.

---

### Post by Crosbie on 2006-08-28
This was interesting, from the [UKT support page](http://www.uktsupport.co.uk/advent/laptop/7083.htm) I linked to.  It says there'a built-in recovery mode that you might be able to use.

From that page:

```
Restart your computer. Then Press F10 repeatedly until the message "Starting System Recovery" is displayed.
```

Of course if your keyboard really is knackered then this might not work.  if it does, I noticed that this should be possible:

```
Press the ALT and D keys at the recovery menu to access a command prompt. This will allow access to C: drive. The command prompt will default to c:\minint\system32 where you can run a variety of tools including CHKDSK.EXE.
```

This might allow you to run your flash utility programs from whichever folder you unzipped them to... but if your keyboard allows you to get to recovery mode, maybe this isn't necessary.

---

### Post by danderson3 on 2006-08-28
Here are the instructions to add a freedos boot option
from your existing HD/Grub:

[http://forum.matrox.com/mga/viewtopic.php?t=21139&sid=d1c83591c39b45daca3300b088b9cd41](http://forum.matrox.com/mga/viewtopic.php?t=21139&sid=d1c83591c39b45daca3300b088b9cd41)

David

---

### Post by meenasheskbrat on 2006-08-28
The onboard keyboard works fine after the ubuntu is booted. I am running ubuntu 6.06 and I installed it on a clean install so there is no manufacturers rescue partition on the drive any more. the keyboard did have a problem like this before and I just installed the bios update and it was fixed. This time it happened just after I installed a Pcillin antivirus and firewall,though I don't know if that was just a coincidence.  I thought installing ubuntu on a clean install would sort it so I did not sort it out before I installed, silly me. When the computer boots there is an option to hit Esc for setup but nothing happens. I want to use a bootable disc but again the keyboard is unresponsive at the press any key to boot from cd option.

---

### Post by Metacarpal on 2006-08-28
My take on this is that your BIOS isn't detecting your keyboard through PnP, but Ubuntu is - which indicates a flaw in how the BIOS is running.  Either it's a poorly designed BIOS, or it lost its ability to read the keyboard.  Either way, there's a good chance that flashing/updating the BIOS will fix it.

So best of luck to you using the freedos boot option to flash it out!!!

---

### Post by ciscosurfer on 2006-12-13
I have written a HOWTO discussing how to flash your BIOS.  You can find it here: [HOWTO: Flash BIOS, The Ubuntu Way]("http://ubuntuforums.org/showthread.php?t=318789")

---

### Post by Dusty545 on 2006-12-13
A USB floppy drive is unlikely to solve your problem as it's unlikely that the BIOS will be set to boot from a USB floppy as a default option..  if at all!

It almost sounds (pointing no fingers) that you've tried to flash the BIOS already and it's gone a bit haywire.  Always remember with things like the BIOS that if it's not broken, don't fix it.

If this were a desktop then the solution would be far simpler but that's not helping.

I'd recommend you contact Advent and ask them if there's a way that you can reset the bios (some have recommended removing all sources of power - including the CMOS battery for a few minutes) and go from there.

Also, the files that you listed in your original post include a series of DOS/Win files.  Given the precariousness of flashing the BIOS and your current situation, I'd recommend that you only use W*indows to do this.

---

### Post by ciscosurfer on 2006-12-13
> **Dusty545 said:**
> A USB floppy drive is unlikely to solve your problem as it's unlikely that the BIOS will be set to boot from a USB floppy as a default option..  if at all!

It almost sounds (pointing no fingers) that you've tried to flash the BIOS already and it's gone a bit haywire.  Always remember with things like the BIOS that if it's not broken, don't fix it.

If this were a desktop then the solution would be far simpler but that's not helping.

I'd recommend you contact Advent and ask them if there's a way that you can reset the bios (some have recommended removing all sources of power - including the CMOS battery for a few minutes) and go from there.

Also, the files that you listed in your original post include a series of DOS/Win files.  Given the precariousness of flashing the BIOS and your current situation, I'd recommend that you only use W*indows to do this.There is no reason that you have to use Windows to flash your BIOS.

If you want to completely reset your BIOS, then yes, removing the CMOS battery and then replacing it after a minute or so, will reset your BIOS.  Remember, the CMOS battery is what provides power to the real-time clock (RTC) and your BIOS' memory.

The clock typically provides a time-of-day clock and a multi-century calendar with alarm features. The RTC supports a varying amount of space (256 bytes is typical) of battery-backed CMOS RAM usually placed in one or two banks reserved for BIOS use.

I have provided a link in my siganture as my original post that describes how to flash you BIOS on your Ubuntu machine (no Windows partition/drive needed).  I describe how to do this on a floppy or a CD-ROM. :D

---

