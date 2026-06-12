---
title: "Installing issues - USB Error -110"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by parkylondon on 2007-01-03
Hi all

I've been looking and lurking for a few days and trying to resolve an issue I am experiencing with my installation of 606LTS.

I've created the install disk (and checked it out) and booted from the drive. All good so far!

I go through the Start or Install Ubuntu (option1) and it starts...

Attached is the screen shot - literally a photo! - of the screen as it hangs...

I am assuming there is a problem with the USB devices attached so I have tried disconnecting them all with no avail.

Anyone have any ideas on how I should progress? 

FWIW I am running a custom built AMD64 FX w/2Gb RAM +3x250Gb h/disks + WinXP Pro + twin SLI Nvidia grafix.

---

### Post by parkylondon on 2007-01-03
Hi please don't be scared to open the attachment - it's just a JPEG.... I could really do with some help. Thanks!

---

### Post by parkylondon on 2007-01-06
I guess I can't install Ubuntu.... <gives up, shaking head> shame...

---

### Post by ajmorris on 2007-01-06
the install shouldn't be trying to use the USB or SDD unless your installing to it or from it.

---

### Post by parkylondon on 2007-01-10
I am installing from an internal CD/DVD drive - I've even disconnected the USB peripherals from the PC to no avail. I am deeply puzzled.

---

### Post by parkylondon on 2007-02-04
I'm still trying to get this done! Surely persistence counts for something!

Does anyone know if having a wireless mouse and keyboard attached to the PC will produce the errors I am getting? It's the only USB device left plugged in now and I'm still getting the errors! 

I guess I'll just have to dig out an old skool wired mouse and keyboard and see if that helps.

Any help etc..

Thanks.

Parkylondon

---

### Post by shane2peru on 2008-01-22
I'm having this same problem, I didn't take a picture but I have the same errors except mine reads: ```
usb 5-7: device descriptor read/64, error -110
```  and then repeats itself about 5 times changing the 64 to an 16 after about 3 times, it really has slowed my boot time down, and it is a recent problem, I have had Gutsy installed and up to date for about 3 or 4 months (I think).  I have reversed any changes that I made recently and still get the problems.  Any ideas would be greatly appreciated!

Shane

---

### Post by miqie on 2008-01-22
USB seems to be a real issue with Linux on some computers.  I have been trying to get a flash disc to work for a week now.  I get the same type of error....device not accepting address.  Good luck!  Maybe someone will come up with a solution for this.

---

### Post by shane2peru on 2008-01-22
I have been using Gutsy on this computer without a problem for some time now, and all of the sudden this error pops up!  Kind of annoying, I'm considering re-installing, it is faster than waiting three days for an answer, the Original poster of this thread waited for almost a year, and still has not gotten an answer!

Shane

---

### Post by Phosphoric on 2008-02-03
No help to you all I know but have exactly the same issue as shane2peru except mine is on Feisty.  Been running OK for months but now on connecting my printer or camera, device recognition is really slow, over 1 minute, gets there eventually and then runs at normal speed. :confused:

I get exactly the same error message "blah blah device descriptor read/64, error -110" when installing the Gustsy live CD and the same effect on installing the Feisty live CD so I don't think it's a change in kernel.  I also don't think re-installing the OS will solve it either.

I'm at a loss and nobody here seems to be able to help.  I've found similar problems going back to 2005 and no recorded resolution.

Just another poor aspect of Linux/Ubuntu, I'm getting tired of having to accept that some things just don't work properly in Ubuntu.  :(

---

### Post by shane2peru on 2008-02-03
> **Phosphoric said:**
> No help to you all I know but have exactly the same issue as shane2peru except mine is on Feisty.  Been running OK for months but now on connecting my printer or camera, device recognition is really slow, over 1 minute, gets there eventually and then runs at normal speed. :confused:

I get exactly the same error message "blah blah device descriptor read/64, error -110" when installing the Gustsy live CD and the same effect on installing the Feisty live CD so I don't think it's a change in kernel.  I also don't think re-installing the OS will solve it either.

I'm at a loss and nobody here seems to be able to help.  I've found similar problems going back to 2005 and no recorded resolution.

Mine disappeared.  Well, I reversed a few things that I did to setup VirtualBox (and have usb access)  and now I don't get those errors.  Mine were on bootup.

> **Phosphoric said:**
> 
Just another poor aspect of Linux/Ubuntu, I'm getting tired of having to accept that some things just don't work properly in Ubuntu.  :(

  Keep your head up, at least we don't pay for the problems like when we used Micro$oft. :D  I can handle bumbs in the road, when the ticket is free, I can't handle the bumbs in the road when I paid for it. 

Shane

---

### Post by gh64 on 2008-02-04
godd someone pls help!!! having the same prob osoooooooooooo
some11 anyone pls

pls
     pls
pls
    pls
pls!

---

### Post by legend2440 on 2008-02-04
Parkylondon are you using the Ubuntu 386 or 64 livecd?

What do you get when you type
dmesg | grep usb

in terminal

---

### Post by gh64 on 2008-02-04
> **legend2440 said:**
> Parkylondon are you using the Ubuntu 386 or 64 livecd?

What do you get when you type
dmesg | grep usb

in terminal

just solved the problem..
[http://ubuntuforums.org/showthread.php?p=4265769#post4265769](http://ubuntuforums.org/showthread.php?p=4265769#post4265769)

thanks anyway

---

### Post by Phosphoric on 2008-02-04
gh64, 

I fail to see what that's got to do with the USB error -110 and indeed what the solution to your problem was. :confused:

Perhaps you could expand a bit on your solution.

Thanks

---

