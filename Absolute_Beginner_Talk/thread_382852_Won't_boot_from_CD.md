---
title: "Won't boot from CD"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Chris4 on 2007-03-12
I downloaded the Desktop CD from [here](http://ftp.ticklers.org/releases.ubuntu.org/releases/6.06/) [PC (Intel x86) desktop CD]. I then burned it to a blank CD using Nero.

I then went into the BIOS (by pressing DEL at boot-up), setting the CD-drive to first boot - then restarting with the Ubuntu CD in the drive. I have tried both my CD drives and all I get is this screen (with both), then Windows loads normally. If I disable everything other than the CD drive, I still get this screen, than it gives me safe mode options.

[[IMG]http://img410.imageshack.us/img410/5851/dsc00251xc4.th.jpg[/IMG]](http://img410.imageshack.us/my.php?image=dsc00251xc4.jpg)
> Boot from CD:
Boot from CD:
Note: I can't type anything when this comes up. I can't do anything (I don't think..). It goes after about 6 seconds.

Windows XP Professional SP2
AMD Sampron 2600+ 1.83 GHz
512 MB of RAM

---

### Post by sad_iq on 2007-03-12
I think you have to press ENTER when that appears(not sure though)...
 and what do you mean by safe mode? Windows safe mode? or is it something about Start or install Ubuntu... stuf ?If it's about ubuntu...then just press enter!!

---

### Post by Chris4 on 2007-03-12
I tried pressing enter, nothing happens. Tried pressing lots of keys, nothing happens.

More photos:

BIOS:
[[IMG]http://img379.imageshack.us/img379/5981/dsc00253go0.th.jpg[/IMG]](http://img379.imageshack.us/my.php?image=dsc00253go0.jpg)

Safe Mode screen which appears after the above BIOS screen, when everything is disabled apart from the CD Drive:
[[IMG]http://img515.imageshack.us/img515/1084/dsc00254gm0.th.jpg[/IMG]](http://img515.imageshack.us/my.php?image=dsc00254gm0.jpg) [[IMG]http://img49.imageshack.us/img49/4189/dsc00255vt5.th.jpg[/IMG]](http://img49.imageshack.us/my.php?image=dsc00255vt5.jpg)

---

### Post by Chris4 on 2007-03-12
I think it's the actual CD that is the problem.
I tried it on a different computer of mine and it done the same things, however when I disabled 'Boot other device' and only had CD-ROM as the first boot drive, the rest disabled, I got this error:
> DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER.
Pressing enter does nothing.

So, let me explain the steps I did to make the CD, tell me if I'm wrong.

1 - Download the ISO file from [http://ftp.ticklers.org/releases.ubuntu.org/releases/6.06/](http://ftp.ticklers.org/releases.ubuntu.org/releases/6.06/), the *PC (Intel x86) desktop CD* version.
2 - Once downloaded, insert blank disc.
3 - Burn the ISO file to the blank disc, by dragging the file to the empty space on the disc. Then use CD Writing Wizard to copy the file to the disc.
4 - Restart computer and disk should boot. If it does not, select CD ROM as first boot option from the BIOS.

Done all of that...

---

### Post by DaveyG on 2007-03-12
> **Chris4 said:**
> I think it's the actual CD that is the problem.
I tried it on a different computer of mine and it done the same things, however when I disabled 'Boot other device' and only had CD-ROM as the first boot drive, the rest disabled, I got this error:

Pressing enter does nothing.

So, let me explain the steps I did to make the CD, tell me if I'm wrong.

1 - Download the ISO file from [http://ftp.ticklers.org/releases.ubuntu.org/releases/6.06/](http://ftp.ticklers.org/releases.ubuntu.org/releases/6.06/), the *PC (Intel x86) desktop CD* version.
2 - Once downloaded, insert blank disc.
3 - Burn the ISO file to the blank disc, by dragging the file to the empty space on the disc. Then use CD Writing Wizard to copy the file to the disc.
4 - Restart computer and disk should boot. If it does not, select CD ROM as first boot option from the BIOS.

Done all of that...

I had the same problem when i first burned it on a disc, you need to burn it as an image..

---

### Post by Chris4 on 2007-03-12
> **Davey Goudou said:**
> I had the same problem when i first burned it on a disc, you need to burn it as an image..

Ok. I'll follow these instructions, see if it makes any difference:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by DaveyG on 2007-03-12
Download the Infra Recorder [here]("http://infrarecorder.sourceforge.net/?page_id=5") to burn it as an image...

---

### Post by DaveyG on 2007-03-12
I would also make sure your computer boots from the cd before the HDD in the Bios

---

### Post by Chris4 on 2007-03-12
Wasn't doing the CD properly. I used Intra Recorder and it worked.
Didn't need to change the order of what boots up, CD run automatically.

Thanks :)

---

### Post by DaveyG on 2007-03-12
No probs :biggrin:

---

