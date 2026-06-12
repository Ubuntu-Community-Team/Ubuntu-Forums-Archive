---
title: "CD Image downloaded - how to boot?"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by boomerian on 2005-12-07
I know someone can help with this. I downloaded the (617MEG) ISO file to a CD, but I can't seem to get the current (soon to be replaced) OS (Windows XP) to recognize the CD drive nor the CD to boot and begin the install.
I've ordered a couple of CDs, but after a week, I am eager to get going.
Have I neglected something?
Thanks in advance...

---

### Post by kilps on 2005-12-07
[I have not gone through downloading Ubuntu as I got my Shipit CDs but have tried this with other distros]

I take it you have written the ISO to disk? Then you need to reboot your computer with the CD in the drive and as long as your computer is configured to boot from CD before Hard drive the installation will start ...

---

### Post by linbetwin on 2005-12-07
Did you use software like Nero to burn the CD, or did you just copy the iso to the CD in XP?

---

### Post by boomerian on 2005-12-07
I'm guessing that I need to set up XP to boot from the CD drive before the hard drive, but I'm not sure how to do that. I thought that would be by default (as I recall other Windows versions interrupted during boot by a floppy left in the drive...).
I'm just eager to get something going until the CDs arrive from Ubuntu.
Will I have a similar problem getting those to boot (if I don't "fix" the XP before then...)?
Thanks to all for responding.:)

---

### Post by boomerian on 2005-12-07
I used XP, but I have Nero, too.

---

### Post by xequence on 2005-12-07
[QUOTE=boomerian]I'm guessing that I need to set up XP to boot from the CD drive before the hard drive, but I'm not sure how to do that. I thought that would be by default (as I recall other Windows versions interrupted during boot by a floppy left in the drive...).
I'm just eager to get something going until the CDs arrive from Ubuntu.
Will I have a similar problem getting those to boot (if I don't "fix" the XP before then...)?
Thanks to all for responding.:)[/QUOTE]

You dont configure XP to load the cd first, you configure the BIOS to. When you start up your computer it will say something on the screen where the logo of your PC maker is, something like "press delete to enter setup". Press whatever it says and make CD first.

---

### Post by aysiu on 2005-12-07
You can't burn the disk image with XP. You have to use Nero or some other CD burning program.

It should not be burnt as data. It should be burnt as a disk image.

[http://www.wizardskeep.org/mainhall/tutor/neroiso.html](http://www.wizardskeep.org/mainhall/tutor/neroiso.html)

---

### Post by linbetwin on 2005-12-07
It doesn't have anything to do with XP. You must set your BIOS to boot from CD-ROM first.

Put the Ubuntu CD in the CD-ROM drive, reboot your computer and press your DEL key. You should see the BIOS screen instead of XP. Look for "Boot priority" or sth like that and set it to boot from CD-ROM first. Follow the instructions in your BIOS, it should be easy.

---

### Post by aysiu on 2005-12-07
[quote=linbetwin]It doesn't have anything to do with XP.[/quote] It has a lot to do with XP if boomerian burned the ISO as *data* using XP's built-in CD burning "program" instead of burning the ISO as *a disk image* using Nero.

---

### Post by linbetwin on 2005-12-07
[quote=aysiu]It has a lot to do with XP if boomerian burned the ISO as *data* using XP's built-in CD burning "program" instead of burning the ISO as *a disk image* using Nero.[/quote]

I know, that was the first question I asked him. But if the CD is properly burned, it's not XP's fault that the computer doesn't boot from the CD.

---

### Post by aysiu on 2005-12-07
[QUOTE=linbetwin]I know, that was the first question I asked him. But if the CD is properly burned, it's not XP's fault that the computer doesn't boot from the CD.[/QUOTE] I took boomerian's response > I used XP, but I have Nero, too. to mean it was not properly burned. Before we can set up the BIOS, the CD has to be burned properly; otherwise, there's no point.

---

### Post by boomerian on 2005-12-07
Thank you both. You're both correct. 
I'll try again, to ensure I burn a disk image (via Nero) and instruct BIOS to boot from the drive.

---

### Post by aysiu on 2005-12-07
[QUOTE=boomerian]Thank you both. You're both correct. 
I'll try again, to ensure I burn a disk image (via Nero) and instruct BIOS to boot from the drive.[/QUOTE] Post again if you have any other issues that come up.

---

### Post by linbetwin on 2005-12-07
Open Nero Burning ROM, click Cancel in the New Compilation window that appears. In the Recorder menu click Choose Recorder. Make sure it's set to your CD or DVD writer drive, NOT Image Recorder, and press OK. In the Recorder menu click on Burn Image. In the window that appears navigate to where you downloaded Ubuntu, select the Ubuntu CD image and click Open.In the window that appears click on the Burn tab and select the lowest Write speed in the drop-down list. The burn process will take longer (about 10 minutes) but the lower the speed, the higher the chances of burning an error-free CD. Now click Burn.

Note: It is very important that you close other applications before starting the burn process and that you don't use your computer during this process!

At the end Nero will hopefully display a message announcing you that The burn process has completed successfully. Clink OK, then Done and you're done.

---

### Post by boomerian on 2005-12-07
Dear kilps, xequence, aysiu, and linbetwin,
Thanks so much for your clear and patient instruction.
I have been reading as much as I can, but apparently don't have the patience to wait for the 'Shipit' CDs. I'm going for it!
Learning new tricks, however slowly,
An old dog

---

### Post by boomerian on 2005-12-29
:D Finally found my problem - an old CD drive.  When I switched to a newer CD-RW "burner" the installation ran noticeably faster and did not hang up. 
For some reason the older drive was not reading properly/completely or fast enough, and the CD verification kept failing (causing me to think they were all improperly burned). I had tried iso's of Ubuntu/Kubuntu/Xubuntu, Puppy Linux, Vector and Gentoo, all of which got install started but not completed. Maybe I don't have so many "coasters" after all.
Xubuntu now installed fully, running somewhat slowly, but all I need now is some time to work with it and LEARN! (Expect additional questions.)
If this has happened to anyone else, and my frustration/lesson can help, then its my small step towards "paying it forward." Cheers,

---

### Post by Lord Illidan on 2005-12-29
[quote=boomerian]:D 
If this has happened to anyone else, and my frustration/lesson can help, then its my small step towards "paying it forward." Cheers,[/quote]

Cheers, thats how I and a lot of people spend the day on the forums.:D

---

