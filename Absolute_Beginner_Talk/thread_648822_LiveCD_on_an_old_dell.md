---
title: "LiveCD on an old dell"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by boobahzone on 2007-12-24
Hi,

I am brand-new to Ubuntu/Linux, although I have been reading about it for about a month or so.  My brother has an old Dell computer with Windows XP that is having some trouble when it tries to load windows, so I thought this would be the perfect opportunity to format the hard drive and set up a Linux OS using Ubuntu.  I created the LiveCD and confirmed that it works on another computer; however, when I start the Dell with the LiveCD in the CD drive (it's not the DVD drive) I come up with the same error message that I get when I start the computer without the CD.  It says: “WARNING: Dell’s Disk Monitoring System has detected that drive 0 [which is my hard drive] on the primare EIDE controller is operating outside of normal specifications. It is advisable to immediately back up your data and replace your hard-disk drive by calling your support desk or Dell Computer Corporation.”  Then I press F1 to continue, and it tries to load Windows and always fails.  

My boot sequence starts with the IDE CD ROM Drive.  However, the warning I get suggests to me that it’s not even going off the LiveCD and just going straight into Windows.  The LiveCD should run regardless of the hard drive, right?  I want it to run the LiveCD so I can set up Ubuntu.  Does anyone have any suggestions as to what might be wrong and what I can do to address this issue?  The computer is a Dell Dimension 4550.

Thanks so much!

---

### Post by LaRoza on 2007-12-24
The computer may not have enough RAM. In that case, you should get the alternative disk, which is text based (but still straight forward)

Also, make sure your BIOS is set to boot from the CD drive.

---

### Post by boobahzone on 2007-12-24
In the setup it says I have 512 MB of RAM.  That should be enough, right?

---

### Post by LaRoza on 2007-12-24
> **boobahzone said:**
> In the setup it says I have 512 MB of RAM.  That should be enough, right?

Maybe. You could do it, if your video card has no problems. Installing with the alternative disk is faster and less likely to have issues anyway.

---

### Post by califman831 on 2007-12-24
yes 512 is enough, that the amount in my current system. If you really want to take the hard drive out of the equation for testing purposes, disconnect its data cable.

---

### Post by LaRoza on 2007-12-24
> **califman831 said:**
> yes 512 is enough, that the amount in my current system. .

Some systems have trouble running live disks, and the alternative disk often is the only way to install. Although 512 is enough, there still can be issues.

---

### Post by califman831 on 2007-12-24
yes you are correct, with some older systems i try out DSL, puppy, or xubuntu, a mix of distros.

---

### Post by boobahzone on 2007-12-24
Thanks LaRosa and califman, I am downloading the alternative CD image and will try that out and provide an update.  So, just for clarification, if my computer didn't have enough RAM, it would bypass the "boot from CD" route and go straight to the hard drive?

Thanks again!

---

### Post by LaRoza on 2007-12-24
> **boobahzone said:**
> Thanks LaRosa and califman, I am downloading the alternative CD image and will try that out and provide an update.  So, just for clarification, if my computer didn't have enough RAM, it would bypass the "boot from CD" route and go straight to the hard drive?

Thanks again!

Possibly. I have had such issues when booting a live disk, however, it was not a RAM issue.

---

### Post by boobahzone on 2007-12-24
Okay, so I restarted the computer with the alternative CD and I still get the same error message, then the machine tries to load windows again after I continue pass the warning.  So it doesn't work with the liveCD or the alternative CD.  Any ideas? 

Thanks so much!

---

### Post by LaRoza on 2007-12-24
I don't have experience with this error, but it sounds like the computer is preventing you from booting from CD's. Did you check the BIOS?

---

### Post by boobahzone on 2007-12-24
Wow... so apparently I just had the CD in the wrong drive, and it just needed to be in the CD drive that was labeled as DVD.  Thanks so much for your help! This is kind of an embarrassing learning experience. :)

---

### Post by califman831 on 2007-12-24
aw man i was thinking of that too, but assumed u tried switching it already LOL:lolflag:

---

### Post by boobahzone on 2007-12-24
Yeah califman, I tried switching it when I tried to install ubuntu yesterday, but the CD image was burned wrong that time, and then while I was troubleshooting that time I figured I would leave the CD in the drive marked as CD-ROM rather than DVD.  Oy!

Well thanks for all the help folks!  I will hopefully be on my way to my first Linux/Ubuntu experience and will have lots to contribute to the forum as I go on with it :).

Goodnight!

---

