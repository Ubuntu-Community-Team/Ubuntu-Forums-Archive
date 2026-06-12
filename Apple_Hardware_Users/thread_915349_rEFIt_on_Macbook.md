---
title: "rEFIt on Macbook"
date: 2008-09-09
forum: Apple Hardware Users
---

### Post by Tigercat212 on 2008-09-09
Can you provide me with a guide on how to install Ubuntu on my Macbook and run in in a partition using rEFIt? Can I set OSX as the bootup disk and then setup a key combination that opens rEFIt?

---

### Post by cyberdork33 on 2008-09-09
> **Tigercat212 said:**
> Can you provide me with a guide on how to install Ubuntu on my Macbook and run in in a partition using rEFIt? Can I set OSX as the bootup disk and then setup a key combination that opens rEFIt?

Please try to stick to one thread.

rEFIt doesn't work like that. rEFIt just gives you a fancy menu at bootup to choose what OS you want (well and some other tools). You select OS X or Linux (or windows or whatever you might have installed) and then it boots into that OS. If you want to switch to the other OS you have to reboot. Go ahead and install rEFIt before doing anything else and you will see what I am talking about.

I have already directed you to some install tutorials. if you have a problem with something please post your specific issue.

---

### Post by Tigercat212 on 2008-09-09
> **cyberdork33 said:**
> Please try to stick to one thread.

rEFIt doesn't work like that. rEFIt just gives you a fancy menu at bootup to choose what OS you want (well and some other tools). You select OS X or Linux (or windows or whatever you might have installed) and then it boots into that OS. If you want to switch to the other OS you have to reboot. Go ahead and install rEFIt before doing anything else and you will see what I am talking about.

I have already directed you to some install tutorials. if you have a problem with something please post your specific issue.
Do I have to create a partition to put Linux on my Mac? So, I would create the partition, put in the CD, select the CD at startup and install on the partition?

---

### Post by cyberdork33 on 2008-09-09
> **Tigercat212 said:**
> Do I have to create a partition to put Linux on my Mac? So, I would create the partition, put in the CD, select the CD at startup and install on the partition?

yes you need to shrink the size of your OSX Partition in order to make room for the Ubuntu partition(s). Let's take things one step at a time shall we? Did you install rEFIt?

---

### Post by Tigercat212 on 2008-09-09
> **cyberdork33 said:**
> yes you need to shrink the size of your OSX Partition in order to make room for the Ubuntu partition(s). Let's take things one step at a time shall we? Did you install rEFIt?

Yes, I installed rEFIt. Next step?

---

### Post by schauerlich on 2008-09-09
See the link to the macbook wiki in my sig.

---

### Post by cyberdork33 on 2008-09-09
> **Tigercat212 said:**
> Yes, I installed rEFIt. Next step?

Ok next you need to resize your OSX partition, but before you do that you should backup you important files. messing with the hard drive partitions is always sensitive, and you might lose your install.

With that warning, You can proceed. Do you have Leopard? You can use Boot Camp to create your new partition quite easily.

---

### Post by Tigercat212 on 2008-09-09
> **cyberdork33 said:**
> Ok next you need to resize your OSX partition, but before you do that you should backup you important files. messing with the hard drive partitions is always sensitive, and you might lose your install.

With that warning, You can proceed. Do you have Leopard? You can use Boot Camp to create your new partition quite easily.

OK, I partitioned the drive. What do I do now?

---

### Post by cyberdork33 on 2008-09-09
> **Tigercat212 said:**
> OK, I partitioned the drive. What do I do now?

OK, I am assuming you used BootCamp?

If so, then you are ready to boot the Ubuntu LiveCD. You might want to make sure that your Mac has a hardwired connection for now since you will not have wireless working right away.

Once you boot into the LiveCD, go to System > Adminstration > Partition Editor

In this application (gparted) you will be able to see the partitions on your hard disk. You should have a small EFI partition at the beginning followed by your OSX partition (HFS+) and then a Partition that was made by BootCamp. Select this last partition and delete it. Only Free Space will be remaining. Apply changes and Exit gparted.

After that, start the Ubuntu installer and when prompted, choose to install to the "largest free space". At the end it will ask you to reboot. Go ahead and do that. It will still not boot into Ubuntu yet because of a bug in the installer. You will use the rEFIt partition tool to fix that problem. See this thread for details:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by Tigercat212 on 2008-09-10
How can I accept the option to install Ubuntu when booting from the Live CD. I am on my Macbook but pressing Enter is not doing anything.

---

### Post by pxwpxw on 2008-09-10
If the keyboard is not working for the live cd startup menu, you may need to update the macbook firmware, depending on the macbook model and age. Earlier versions had an issue with that. Info is on the apple web site , see the macbook wiki.

---

### Post by cyberdork33 on 2008-09-11
> **Tigercat212 said:**
> How can I accept the option to install Ubuntu when booting from the Live CD. I am on my Macbook but pressing Enter is not doing anything.
Pressing Enter? At want point? Do you mean in the rEFIt menu?

---

### Post by Tigercat212 on 2008-09-11
I updated my firmware and I will tell you what happens. 

@cyberdork33 In the main Ubuntu menu, this one:

[http://haacked.com/images/haacked_com/WindowsLiveWriter/InstallingUbuntuonVirtualPCforWindowsLov_C436/image032.png](http://haacked.com/images/haacked_com/WindowsLiveWriter/InstallingUbuntuonVirtualPCforWindowsLov_C436/image032.png)

It lets me press enter to select the language but I can't select any of the options such as Install Ubuntu.

---

### Post by pxwpxw on 2008-09-11
> **Tigercat212 said:**
> I updated my firmware and I will tell you what happens. 

@cyberdork33 In the main Ubuntu menu, this one:

[http://haacked.com/images/haacked_com/WindowsLiveWriter/InstallingUbuntuonVirtualPCforWindowsLov_C436/image032.png](http://haacked.com/images/haacked_com/WindowsLiveWriter/InstallingUbuntuonVirtualPCforWindowsLov_C436/image032.png)

It lets me press enter to select the language but I can't select any of the options such as Install Ubuntu.

From the picture, you seem to have booted into a virtual machine install, but I may be wrong. It does not look like a direct boot from the ubuntu cd, i.e. from a restart with no other system running. I thought you had decided to do the direct install.

---

### Post by cyberdork33 on 2008-09-11
> **pxwpxw said:**
> From the picture, you seem to have booted into a virtual machine install, but I may be wrong. It does not look like a direct boot from the ubuntu cd, i.e. from a restart with no other system running. I thought you had decided to do the direct install.
I think he did that just to get the screenie. (or just found the image online somewhere...)

Yes there is a keyboard bug that prevents the keyboard from working in the bootloader screen. However, if you do not select anything, there should be a timer that runs out and boot the default option (first one).

---

### Post by Tigercat212 on 2008-09-11
I thought that was just for the language? So, if I wait until it counts down from 30 sec it will automatically load?

Thanks,

Tigercat212

---

### Post by pxwpxw on 2008-09-12
Cyberdork -

I find this a bit confusing. 

I tried the timeout trick here on a macbook with the 704 desktop install cd, and it did not time out (not within 1/2 hour anyway).

Tigercat - 

Can you confirm that are you starting the installer cd by (a) restarting the computer with the install cd inserted while  (b) holding down the option key and then (c) selecting the cd icon when it appears to get to a screen like the picture you posted. (or was that your screen picture, very good picture).

---

### Post by Tigercat212 on 2008-09-12
Well, I am restarting and then pressing "C" on my Macbook to boot into the CD. That is what it says to do in the Macbook FAQ.

Is that not correct?

---

### Post by pxwpxw on 2008-09-12
> **Tigercat212 said:**
> Well, I am restarting and then pressing "C" on my Macbook to boot into the CD. That is what it says to do in the Macbook FAQ.

Is that not correct?

Yes thats fine, just wasn't sure.
So have you got the keyboard to work now, the firmware update was the answer to that in some cases, or just restart from the CD repeatedly until you get lucky. What is the situation now? Wheree have you got to?
And what is your macbook version/ date of manufacture.
Have you checked the CD on another mac - sometimes a bad burn can happen.

---

### Post by Tigercat212 on 2008-09-12
I seem to have lost my Ubuntu disk and I have no other disks left. Is it possible for me to emulate a CD and put the ISO on that and then run Ubuntu in the partition so I can install it?

---

