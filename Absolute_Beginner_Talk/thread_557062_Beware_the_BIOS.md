---
title: "Beware the BIOS"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by trebornekmes on 2007-09-22
What they didn't tell me before I shelled out $10 for the DVD to try out Ubuntu was that it does not work with a BIOS dated before the year 2000.  Since there are no available updates to the BIOS, and since there doesn't seem to be any way to ask the Ubuntu folks a question, I guess I'm out of luck.  The moral to the story is ... check your BIOS date before trying Ubuntu 7.04.

---

### Post by mysticmatrix on 2007-09-22
> **trebornekmes said:**
> What they didn't tell me before I shelled out $10 for the DVD to try out Ubuntu was that it does not work with a BIOS dated before the year 2000.  Since there are no available updates to the BIOS, and since there doesn't seem to be any way to ask the Ubuntu folks a question, I guess I'm out of luck.  The moral to the story is ... check your BIOS date before trying Ubuntu 7.04.

Wait there does exist a way to boot BIOS which are pre2000. Just wait till someone comes along to answer how...

---

### Post by skymera on 2007-09-22
you PAID!?

why not download?

and i never knew about old bios :S

---

### Post by Warren Watts on 2007-09-22
I have installed 7.04 on two different boxes with pre-2k BIOS's and have never had an issue.  I had to force one of them not to load ACPI, but other than that I haven't had a problem.  

What sort of a message or error do you get when you try to use the live CD/DVD?

Is it an issue with the older machine not having a DVD-ROM?

---

### Post by Malta paul on 2007-09-22
You could try changing your BIOS Integrated Peripherals setting from Native mode to Legacy mode, then save settings and try you Ubuntu live disk.
Hope this helps:wink:

---

### Post by NIT006.5 on 2007-09-22
Yeah, I wouldn't think it's the bios date itself that's the issue - more likely one of the bios settings or maybe a compatibility issue with that particular bios?

---

### Post by Sef on 2007-09-22
> 
What they didn't tell me before I shelled out $10 for the DVD to try out Ubuntu was that it does not work with a BIOS dated before the year 2000. Since there are no available updates to the BIOS, and since there doesn't seem to be any way to ask the Ubuntu folks a question, I guess I'm out of luck. The moral to the story is ... check your BIOS date before trying Ubuntu 7.04.

What are your system specs?

---

### Post by Jimmyfj on 2007-09-22
I have and old pre2000 PII computer running Ubuntu 7.04 Feisty Fawn and had no issues with the install of that. It started out as a 6.06 Dapper, then I installed 6.10 Edgy and finally 7.04, all without any problem other that the very slow speed of the 266 MHZ CPU.

But we need some system specs in order to provide any help.

---

### Post by therandman on 2007-09-22
I actually had the same problem installing Xubuntu on an IBM Thinkpad 600.  Kept saying that the BIOS was pre2k, and it wouldn't install.   I can get a BIOS update, but it requires a fully charged battery (I don't plan on shelling out $ for that.)

---

### Post by philinux on 2007-09-22
Mine's a 1999 machine, the ony message I get is about acpi=force. Which I've sorted in grub

---

### Post by Duck2006 on 2007-09-22
> **philinux said:**
> Mine's a 1999 machine, the ony message I get is about acpi=force. Which I've sorted in grub

So is mine and i have just loaded 7.10 trail 5 and it works well.

---

### Post by southernman on 2007-09-22
I can confirm (in my case) of installing to a pre 2k bios machine... Dell V350 PII350Mhz.

Did not need to use "acpi=force", but it does give a POST message about the 2k cutoff... she (the machine) boots and runs perfectly fine

---

### Post by zach141 on 2007-09-22
> **philinux said:**
> Mine's a 1999 machine, the ony message I get is about acpi=force. Which I've sorted in grub

Ditto on this--my machine was new in 1998.  I get the "your BIOS is too old" and then the acpi=force.

What action did you have to "sort in grub"?  Mine just goes ahead on its own after a brief interval and the acpi=force message.  ??

zach

---

### Post by woodwardt on 2007-09-25
> **trebornekmes said:**
> What they didn't tell me before I shelled out $10 for the DVD to try out Ubuntu was that it does not work with a BIOS dated before the year 2000.  Since there are no available updates to the BIOS, and since there doesn't seem to be any way to ask the Ubuntu folks a question, I guess I'm out of luck.  The moral to the story is ... check your BIOS date before trying Ubuntu 7.04.

Well I don't know what MY problem is but I think that you may have answered it as it is an old bios!  Fortuneatly I just downloaded it and burnt the live cd alternate and found out without spending the $10.00 !

Thanks for the info then; seeing as I am not getting an answer in my post I might also assume from what you've said and from my experience that support is virtually non-existant except for the forum or for those that want to pay to play
:(

---

### Post by t4thfavor on 2007-09-25
Pre 2000 bios here also, and I have no problem. I wonder what the issue is. Maybe his machine is from before there was 256mb of ram available:)

---

### Post by trebornekmes on 2007-10-07
> **skymera said:**
> you PAID!?

why not download?

and i never knew about old bios :S

Good Point!  I tried that, but my burner was temporarily out of commission so I bought the disc.  Thanks.

---

### Post by trebornekmes on 2007-10-07
Hmmm ... It seems some are not having problems.  Perhaps the problem is peculiar to the BIOS in the IBM Thinkpad.  I see that at least one other Thinkpad is having the problem.  At any rate, I've still not been successful in getting Ubuntu to fire up on it.  Thanks.

---

### Post by trebornekmes on 2007-10-07
> **t4thfavor said:**
> Pre 2000 bios here also, and I have no problem. I wonder what the issue is. Maybe his machine is from before there was 256mb of ram available:)


This laptop has 128MB of RAM.  Is that the problem?

---

### Post by trebornekmes on 2007-10-07
> **woodwardt said:**
> Well I don't know what MY problem is but I think that you may have answered it as it is an old bios!  Fortuneatly I just downloaded it and burnt the live cd alternate and found out without spending the $10.00 !

Thanks for the info then; seeing as I am not getting an answer in my post I might also assume from what you've said and from my experience that support is virtually non-existant except for the forum or for those that want to pay to play
:(


Yeah!  At least I can't find any help.

---

### Post by trebornekmes on 2007-10-07
> **zach141 said:**
> Ditto on this--my machine was new in 1998.  I get the "your BIOS is too old" and then the acpi=force.

What action did you have to "sort in grub"?  Mine just goes ahead on its own after a brief interval and the acpi=force message.  ??

zach

What in the world does "sorting in the grub" mean?  Anyway, I don't get the acpi=force message.  I just get the message that my BIOS is pre-2000.

---

### Post by trebornekmes on 2007-10-07
You know what?  This laptop only has 128MB of RAM.  Is that the problem?

---

### Post by dptxp on 2007-10-07
Ubuntu Live CD shall not run with 128 MB RAM.
But you may have other problems too.
Try Xubuntu with alternate CD, make a SWAP partition of 512 MB to 1 GB with Gparted first.

---

### Post by Thunar on 2007-10-07
I've had a similar kind of situation where I installed Ubuntu 7.04 on an old P3 computer, and at first it gave me a message like 'ACPI UNABLE TO LOCATE RSDP', but it would continue to load afterwards. Then I went into the BIOS and enabled ACPI, and after that it gave me a different message like 'ACPI: BIOS age (1998 ) fails cutoff (2000), acpi=force is required to enable ACPI', but it STILL loads without a problem. 

Basically all it's telling you is that the 'Advanced Configuration and Power Interface' on your computer is out of date and adding the 'acpi=force' option to grub will basically force Ubuntu to use ACPI anyway. 

Now if what your saying is that Ubuntu will not run because of this, that is sort of unusual, but here are some things you can try (assuming you can not locate a BIOS update):

* Try to go into your BIOS, locate the 'Power Management' section, and disable ACPI.

If that doesn't work, maybe you should re-enable ACPI, or if you couldn't find that option in your BIOS, then try this:

* Edit your /boot/grub/menu.lst file and add acpi=force to your kernel line. For instance:

kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=857d1482-3bdf-4edd-86b5-483f3baf30e3 ro single acpi=force

If you can not boot Ubuntu you may have to do this using the live CD. If it says you don't have permission to edit the file you may have to type in something like this in your Terminal:

```

gksudo gedit

```

When it opens Gedit, click on 'File -> Open' browse to '/boot/grub/menu.lst' and follow the above instructions.

I would suggest NOT installing Xubuntu. From personal experience Xubuntu made me jump through endless hoops to do things Ubuntu does automatically. It is not a user-friendly OS for the novice Linux user, you will be in the Terminal for weeks pulling out your hair. Don't do it.

Besides, you've already paid for Ubuntu!

Lastly, if all else fails, and I know this sounds stupid, but maybe try installing Ubuntu from scratch using the Live CD and formatting the drive again. I say this only because Ubuntu SHOULD work out-of-the-box even on an older system, and an ACPI problem SHOULD NOT cause it to not boot.

If after installing if you get the message, but it boots anyway, just ignore it. It won't hurt anything. 

Hope this helps!

---

### Post by trebornekmes on 2007-10-13
> **Thunar said:**
> I've had a similar kind of situation where I installed Ubuntu 7.04 on an old P3 computer, and at first it gave me a message like 'ACPI UNABLE TO LOCATE RSDP', but it would continue to load afterwards. Then I went into the BIOS and enabled ACPI, and after that it gave me a different message like 'ACPI: BIOS age (1998 ) fails cutoff (2000), acpi=force is required to enable ACPI', but it STILL loads without a problem. 

Basically all it's telling you is that the 'Advanced Configuration and Power Interface' on your computer is out of date and adding the 'acpi=force' option to grub will basically force Ubuntu to use ACPI anyway. 

Now if what your saying is that Ubuntu will not run because of this, that is sort of unusual, but here are some things you can try (assuming you can not locate a BIOS update):

* Try to go into your BIOS, locate the 'Power Management' section, and disable ACPI.

If that doesn't work, maybe you should re-enable ACPI, or if you couldn't find that option in your BIOS, then try this:

* Edit your /boot/grub/menu.lst file and add acpi=force to your kernel line. For instance:

kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=857d1482-3bdf-4edd-86b5-483f3baf30e3 ro single acpi=force

If you can not boot Ubuntu you may have to do this using the live CD. If it says you don't have permission to edit the file you may have to type in something like this in your Terminal:

```

gksudo gedit

```

When it opens Gedit, click on 'File -> Open' browse to '/boot/grub/menu.lst' and follow the above instructions.

I would suggest NOT installing Xubuntu. From personal experience Xubuntu made me jump through endless hoops to do things Ubuntu does automatically. It is not a user-friendly OS for the novice Linux user, you will be in the Terminal for weeks pulling out your hair. Don't do it.

Besides, you've already paid for Ubuntu!

Lastly, if all else fails, and I know this sounds stupid, but maybe try installing Ubuntu from scratch using the Live CD and formatting the drive again. I say this only because Ubuntu SHOULD work out-of-the-box even on an older system, and an ACPI problem SHOULD NOT cause it to not boot.

If after installing if you get the message, but it boots anyway, just ignore it. It won't hurt anything. 

Hope this helps!


Thanks.  I'll give it a try.

---

### Post by trebornekmes on 2007-10-13
> **dptxp said:**
> Ubuntu Live CD shall not run with 128 MB RAM.
But you may have other problems too.
Try Xubuntu with alternate CD, make a SWAP partition of 512 MB to 1 GB with Gparted first.

I'll look into it.  Thanks for the help.

---

### Post by LowSky on 2007-10-13
shall I reccomend another distro of linux, like Puppy or DSL, they run very well on machines with as little as 64Mb of RAM

---

