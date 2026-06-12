---
title: "Professional help?"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Scarfman on 2007-10-10
Alright, I posted yesterday about my troubles, and no avail.

I have been trying to install ubuntu on a 160GB external for a few days now, and at this point, I'm running in circles.

If there is anybody who can spare an hour or two to walk me through this on AIM or MSN, please tell me.

If not, I give up, and wasted a good chunk of money on an external HDD.

---

### Post by Dr Small on 2007-10-10
Professional ? >> [http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

---

### Post by Scarfman on 2007-10-10
Those are some pricy professionals you have there.
I guess "professional" was too strong a word?
Perhaps a well-educated individual with a bit of time to spare would be a better term for what I am looking for.

---

### Post by Dr Small on 2007-10-10
Perhaps.
I'll look at what your problem is, but you can not expect us to solve it immediately as we are  only amatures. Plus, we work for no pay.

But I'll look anyhow.

Dr Small

---

### Post by HermanAB on 2007-10-10
If it will make you feel better...

What you want to do is not easy.  I won't bother trying myself, since it will waste a lot of time.

However, I think that if you unplug all internal HDDs first, so that the external HDD is the only one, then it will install. Thereafter, to boot internal/external HDD, you have to change the BIOS boot sequence (or modify Grub on the internal HDD to chain load the external, if you can figure out how do that, which again, isn't easy).

Cheers,

Herman

---

### Post by Scarfman on 2007-10-10
Thank you

I'll summerize.

-Installed 6.10 to external via Live CD
-Ended up installing GRUB to XP(internal) resulting in error 17 when trying to boot linux
-Re-installed 6.10
-Worked, but now cannot boot to XP without having external plugged in
-downloaded MbrFix to fix XP boot, and it worked.
-Now linux wouldnt start (grub menu came up, but there was an error for each option)
-was frustrated
-Downloaded 7.04 Live disk
-Live disk gave me an X system error that I could not fix due to running off live CD (couldnt alter the xorg file and save it on reboot)
-Installed 7.04 to external via firend's computer
-Same problem with 6.10 (ran, but XP wouldn't run without having external plugged in)
-Friend got scared that I broke his computer (I fixed it the same way i fixed mine afterward)
-Popped external into my computer.
-Grub menu comes up, none of the options work.

Now Im back at square... six
This whole linux ordeal has spanned over a few days.

---

### Post by Scarfman on 2007-10-10
to Herman AB:

Yes, I have come to the realization that my task is more difficult that i assumed it would be. 

I figured out changing around the bios and stuff, and even messed around with GRUB settings.


If nothing else, I have learned a good deal about boot menus and master boot records.


Thanks for the input

Cheers to you as well.

---

### Post by mosiac on 2007-10-10
[http://ubuntuforums.org/showthread.php?t=479550]("http://ubuntuforums.org/showthread.php?t=479550")

Check this thread, this guy was doing the same thing as you and seemed to have the same problem when he removed the External, from what I read you need a Super Grub CD (I believe there is a link for that on there too) to put grub on th external so it doesnt screw with the internal drive.

If anything else its a decent jump point if you havent tried it.

Hope this helps a little.

---

### Post by Scarfman on 2007-10-10
Actually, I did try using the supergrup boot CD...
It didn't work for me (nothing changed at all), but i could try it again now that I have 7.04 instead of 6.10...

---

### Post by confused57 on 2007-10-10
I took the liberty to read your other thread & if I understand correctly, you get a grub menu when you boot first to your external hard drive.  If this is the case, try highlighting your Ubuntu entry, press "e" to edit, highlight the line with root, press "e" again, change root from (hd1,x) to (hd0,x), press "enter", then "b" to boot...x means leave this value as it is.  May not work, but worth a try.

---

### Post by Scarfman on 2007-10-10
alright, I'll try it

---

### Post by Scarfman on 2007-10-10
O_O

I think it may have worked, it's loading Ubuntu now...

---

### Post by Scarfman on 2007-10-10
umm... it looks like it worked, but it booted to command line instead of the ubuntu desktop, any ideas how to get to the desktop?

---

### Post by Dr Small on 2007-10-10
I don't know why it booted in CLI, but to start the X environment, type:
```
startx
```

By the way, does it say root@host ?

Dr Small

---

### Post by linuxlizard on 2007-10-10
I don't know if this will help or not, because I've never tried this with an external hard drive, but I think it should:

Install ubuntu and use the option to write grub to the root partition instead of the MBR. It's been a couple of years since I did this, and don't know where the option appears anymore during the install, but if you search the forum or ask, someone will know how to put it there instead of the MBR.

Install GAG boot manager (google it for free download) to the MBR.

Set up xp and ubuntu in gag- choose the partitions they are found on. 

Edit your grub config file in ubuntu /boot/grub/menu.1st so the timeout is like 1 sec so you don't have to sit through grub after selecting in gag.

As I say, I've never tried this with an external drive, but you can tell if it will work by running gag from cd or floppy and checking to see if you can locate the external drive.

---

### Post by Scarfman on 2007-10-10
it says scarfman@LINUX:~$

---

### Post by Scarfman on 2007-10-10
startx told me no screens were detected, so I put 

```
sudo dpkg-reconfigure xserver-xorg
```

and hit enter a bunch then rebooted...

now it gived me FATAL ERROR

CAUGHT SIGNAL 11


Im so damn close <.<

---

### Post by confused57 on 2007-10-10
> **Scarfman said:**
> it says scarfman@LINUX:~$

You could try entering:
```
sudo dpkg-reconfigure xserver-xorg
```
When you get to the video card driver, select "vesa" as the driver and after you've completed configuring your xorg, then you can try entering "startx", without quotes.

There might be a problem because you installed Ubuntu on a different computer with different hardware.

Check back if this doesn't work, you might be able to get the live cd working with a few tweaks.  What video card/chipset are you using?

Added:  See it didn't work.  Boot the live cd, when you get the xserver error, press "Ctrl+Alt+F1", this should get you to a command prompt, then enter:
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
```
Select "no" to auto-detect, then you  can probably go with the defaults, except choose "vesa" as the video driver.  After reconfiguring your xorg, then enter:
```
sudo /etc/init.d/gdm start
```

If you're able to boot to a GUI in the live cd, I would suggest reinstalling Ubuntu to your external hard drive; however, before you do I would recommend that you set your external hard drive to boot before your internal hard drive in bios BEFORE you boot up the live cd to install Ubuntu.

---

### Post by Scarfman on 2007-10-10
I dont actually know the specs of this drive, but vesa didnt work...

I'll try selecting different sets and doing startx

it has to work eventually....

---

### Post by confused57 on 2007-10-10
> **Scarfman said:**
> I dont actually know the specs of this drive, but vesa didnt work...

I'll try selecting different sets and doing startx

it has to work eventually....

You might want to post the specs of your computer...boot up the live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
lspci
```

---

### Post by Scarfman on 2007-10-10
Processor	 Intel® Centrino® Duo Mobile Technology
Intel® Core&#8482; Duo processor T2300 (2 MB L2 Cache | 1.66 GHz | 667 MHz FSB)

Chipset	 Intel® 945PM

Screen	15.4-inch Widescreen Ultrabright WXGA TFT

Memory	512 MB 533 MHz DDR2 (2 × 256 MB) SODIMM 

Expandable to 2 GB

Video	 ATI Mobility&#8482; Radeon® X1400 with Avivo&#8482; display technology

Video Memory	 128 MB HyperMemory&#8482;

Audio	 High definition audio

Hard Drive	80 GB HDD (5400 RPM) SATA


Here are my specs, what do you suggest my settings should be?


I can't run the live CD because i get the same x server error (installed on diff computer that didnt get the error)

---

### Post by frup on 2007-10-10
[http://www.phoronix.com/scan.php?page=article&item=753&num=1](http://www.phoronix.com/scan.php?page=article&item=753&num=1)

Is that relevent?

---

### Post by Scarfman on 2007-10-10
whatever you just sent me, I can only see the first 2 lettrs of each line for some reason....

---

### Post by confused57 on 2007-10-10
I'm not familiar with ATI graphics cards, but maybe this thread will help:
[http://ubuntuforums.org/showthread.php?t=459438&highlight=ati+x1400](http://ubuntuforums.org/showthread.php?t=459438&highlight=ati+x1400)

---

### Post by Scarfman on 2007-10-10
Nooooo

I have to install ubuntu AGAIN!?
this is horrible...
everytime i install i have to go and fix my boot record for my XP

is it absolutely necessary to do the reinstall? can't i just skip the install part since i already have it installed on the external

---

### Post by Dr Small on 2007-10-10
All you should have to do, is unplug the other drive from the motherboard, so only the external is plugged in. Install Ubuntu, and it can't mess up the XP boot record.

Dr Small

---

### Post by frup on 2007-10-10
> **Dr Small said:**
> All you should have to do, is unplug the other drive from the motherboard, so only the external is plugged in. Install Ubuntu, and it can't mess up the XP boot record.

Dr Small

I don't think the GFX card works with a feisty install if I am understanding everything. Seems upgrading from Edgy works though??? Possibly Gutsy beta's are a better option?

---

### Post by Scarfman on 2007-10-10
alright..... but will the internal just work again once I plug it in (i am not an expert on hardware)

---

### Post by Dr Small on 2007-10-10
> **Scarfman said:**
> alright..... but will the internal just work again once I plug it in (i am not an expert on hardware)
Umm.. If you plug it in correctly. Lol

---

### Post by Scarfman on 2007-10-10
alright, well I have to go now, but im going to try installing 6.10 on it again now that I can get it working. Hopefully this will work.

Thank you all for all your help!!!
90% chance i'll be able to get this to work now.



Again, thanks alot.

---

### Post by confused57 on 2007-10-10
> **Scarfman said:**
> Nooooo

I have to install ubuntu AGAIN!?
this is horrible...
everytime i install i have to go and fix my boot record for my XP

is it absolutely necessary to do the reinstall? can't i just skip the install part since i already have it installed on the external
I agree with frup, try reinstalling Edgy...however, set your external hard drive to boot before your internal hard drive, before you boot the live cd.  This way grub "should" install to the external hard drive's mbr.  There should be an "Advanced" option when you're prompted to install grub...what you can do is type in "/dev/sdb"(or however your external drive is recognized by the installer), without quotes, in the box.  Taking these precautions should avoid grub being installed to the internal hard drive's mbr.

---

### Post by frup on 2007-10-10
Setting the external to boot before the internal should solve the problem of the computer not booting without the external plugged in to shouldn't it? In much the same way as having boot from CD skips if no bootable cd is detected?

If it doesn't simply switching which drive to load from on the bios will do it and the windows installation shouldn't be affected at all?

---

### Post by skipbarker on 2007-10-10
> **frup said:**
> I don't think the GFX card works with a feisty install if I am understanding everything. Seems upgrading from Edgy works though??? Possibly Gutsy beta's are a better option?
I am running Feisty with an ATI X1600 and it works, it does however take some tweaking to get working properly.

---

### Post by justinmiller87 on 2007-10-11
> **Scarfman said:**
> Alright, I posted yesterday about my troubles, and no avail.

I have been trying to install ubuntu on a 160GB external for a few days now, and at this point, I'm running in circles.

If there is anybody who can spare an hour or two to walk me through this on AIM or MSN, please tell me.

If not, I give up, and wasted a good chunk of money on an external HDD.

I haven't read the entire thread, but one of the books I bought when I was looking into this is called Ubuntu Hacks. It has instructions for how to install Ubuntu on USB media. You might want to look into it. The most recent edition is based on the Dapper release.

---

