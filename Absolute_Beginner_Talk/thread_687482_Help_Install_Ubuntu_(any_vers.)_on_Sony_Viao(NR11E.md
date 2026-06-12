---
title: "Help Install Ubuntu (any vers.) on Sony Viao(NR11E/S)"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by kayel_justice on 2008-02-04
I need help. 

I'm sick of windows(VISTA especially), and I have a brand spanking new Sony Viao NR110E/S.
Problem is, I made a CD of ubuntu 7.10 off their download site and it freezes in the installation. 

Process:

1) Notebook is currently running Vista ( BAH!).
2) Restart with ISO CD in notebook.
3) Press enter on first option to Install Ubuntu.
4) Wait for something to happen.
5) Freezes with a weird looking scrambled image.
6) Then I restart and Vista loads.
7) Restart process to no avail.

PLEASE, I NEED THIS WHAT AM I DOING WRONG,
Help this nooBOT.

Thanks

---

### Post by bumanie on 2008-02-04
You will most likely need to use the alternate 7.10 cd or possibly you could think about using the 7.04 version of ubuntu, which generally seemed less problematic than 7.10 (from my personal experience).

---

### Post by (((X))) on 2008-02-04
Download that cd again, check image with Nero´s 
MD5-Checksum.

Download, install [http://www.ntfs.com/iso-burning.htm](http://www.ntfs.com/iso-burning.htm) 
use low burn speed.

Good luck

---

### Post by Vadi on 2008-02-04
Try selecting the safe graphics mode (or some other similarly-titled option).

Strange, because that laptop has the Intel X3100 video card, which generally is okay in ubuntu

---

### Post by kayel_justice on 2008-02-04
Thank you. I didn't know there was an alternate 7.10. But it seems like the 7.4 version may be cool.
Have you heard of anything like this happening to anyone else?

---

### Post by kayel_justice on 2008-02-04
Actually it's a NR11**0**E/S, that shouldnt make a difference though right?

---

### Post by bumanie on 2008-02-04
Yes, there are times when others have had difficulties with graphics upon the live cd starting installation. Some try the alternate cd, (which is text based) and usually works. They then worry about configuring their graphics card once the OS is installed. Others go back to feisty fawn and give up completely. I would try either the alternate cd or 7.04.

---

### Post by Vadi on 2008-02-04
You'd also want to look at launchpad.net/ubuntu to see if there's a bug report about this issue (probably is) and contribute any info you can, so they'll know & fix it

---

### Post by kayel_justice on 2008-02-05
7.10 Works.... thanks everyone for your help!.....
Now I need to start a forum that helps install my drivers, cuz my bluetooth, my usb ports and stuff dont work

---

### Post by Vadi on 2008-02-05
Try going to System - Administration - Restricted Drivers Manager. That should should help you out.

---

### Post by kayel_justice on 2008-02-05
Thanks....I'm running Atheros Hardware Access Layer(HAL), it says it runs a risk to me. Proprietary drivers it says .Is this bad or good, or normal?

---

### Post by kayel_justice on 2008-02-05
> **Vadi said:**
> Try going to System - Administration - Restricted Drivers Manager. That should should help you out.

Thanks....I'm running Atheros Hardware Access Layer(HAL), it says it runs a risk to me. Proprietary drivers it says .Is this bad or good, or normal?

---

### Post by bumanie on 2008-02-05
Is it graphic card drivers you are trying to install? Are your graphics not working properly? If not, before you go any further, please list your graphics card make and model. HAL giving you that warning does not sound healthy to me.
As for bluetooth, it should be enabled natively as bluetooth support is coded into the kernel. Sounds as though your usb ports are working now - that's good.

---

### Post by kayel_justice on 2008-02-05
I know this is a different matter so I started a thread called Sony Viao (NR110E/S) Drivers...
Thanks for everyones help

---

### Post by _Phineas_ on 2008-02-05
I had the same problem, you have to select start in safe graphics mode. Hope this helps :)

---

