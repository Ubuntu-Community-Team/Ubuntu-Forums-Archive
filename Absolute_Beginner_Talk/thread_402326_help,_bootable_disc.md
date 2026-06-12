---
title: "help, bootable disc???"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Dragon665 on 2007-04-05
Hello to all,

Hope someone will help me because I'm getting sick Windows. Thing is I downloaded the iso of ubuntu 6.10 but when I put it on a cd-r and set it to bootable, when I try to boot it comes up with "Floppy Drive 1.44mb" then on a new line "EMM386 Caldera" and somecopyright stuff I think but then just sits there with the curser thing flashing away on the next line. Have I set the bootup right when I burned the disc? I set it to ISO Level 1 and Emulation type to Floppy1_44MB (95/98/ME boot images) local segment 7C0, Sectors to 1. Im using the CDBurnerXP Pro 3 to burn it. Can someone please help a n00b?

Thanks

Roy

---

### Post by Maestro23 on 2007-04-05
Burning the ISO: [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

After you burn it correctly, make sure that the CD/DVD drive is the first boot option in you BIOS.

---

### Post by wpshooter on 2007-04-05
Roy:

If I am understanding you correctly, it sounds like to me perhaps you have a floppy diskette in the drive.  If so, take it out.  Then you need to go into your BIOS and make your boot order like so:  1st - boot device = CD-Rom drive, 2nd boot device = Hard disk drive, 3rd boot device = Floppy drive.  I would not put any other boot devices after floppy drive unless you are doing something special.

Also, did you **BURN** the ISO image to the CD (as opposed to just **copying** it to the CD), it must be BURNED.

---

### Post by johnc4510 on 2007-04-05
Your statement is a little confusing, but it looks like to me that you have your bios set to boot from the floppy. It needs to be set to boot from the cdrom.

---

### Post by Dragon665 on 2007-04-05
In boot options I have cdrom set first and then hard drive, I dont actually have a floppy drive installed. Floppy drive is the emulation I used as the bootup option in the CDBurnerXP Pro 3 program I used. If I set it to boot but with no emultaion i get an error saying it cant boot up and to press any key to retry?

On another note I'm extremly impressed with the speed of a reply! Thanks very much for your help! :)

Roy

---

### Post by johnc4510 on 2007-04-05
Please refer to Maestro23's link to burning the iso. There are instructions there on the proper burning of the iso.

---

### Post by Dragon665 on 2007-04-05
Ok, I did what the guide said and wahoooo! it worked, however when I tried to boot into it it loaded and said that the graphics wasn't configured or someting. I have a Geforce 8800 GTS. Could that be why? or do I have to go into safe mode and set it up?

Thanks

Roy

---

### Post by insane_alien on 2007-04-05
why did you set it to emulate a floppy? i'm just curious. the guide linked to will tell you everything you need to know though,

---

### Post by Dragon665 on 2007-04-05
No, that was my mistake, When I click on Burn it has an option to have it bootable so i thougth that was it. I didnt even know of the 'Write from ISO image' button. That was my mistake
! :) But anyways its starts up now. But i get the grahics card error and need help on that?!?

Thanks again

Roy

---

### Post by Feba on 2007-04-05
boot it in safe graphics mode, install, then use google or search these forums for instructions on downloading nvidia drivers once you're running it off your harddrive. Should work.

---

### Post by Dragon665 on 2007-04-05
Ok, thanks for the fast reply, i'll try that now!

Roy

---

### Post by johnc4510 on 2007-04-05
Here is the how to for the nvidia binary drivers:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by tchoklat on 2007-04-05
google for the ENVY package to install your correct grafix drivers for the NVidia card

---

### Post by Maestro23 on 2007-04-05
> **tchoklat said:**
> google for the ENVY package to install your correct grafix drivers for the NVidia card

Envy: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

