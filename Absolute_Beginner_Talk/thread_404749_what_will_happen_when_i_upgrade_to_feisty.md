---
title: "what will happen when i upgrade to feisty?"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-04-08
I am planning on upgrading from Edgy to Feisty without wiping out my disk. Will my original home settings be preserved and all my apps in tact when I upgrade to Feisty?

---

### Post by Medieval_Creations on 2007-04-08
Everything on your home partition will stay the same.   Upgrading typically doesn't change any of the settings that you had setup in a previous install.  There may be a few applications that ask when updating or will run a setup program that might but for the most part it should go through without a problem.

I did an upgrade from Edgy amd64 to Fiesty amd64 with no problems.

---

### Post by Najand on 2007-04-08
Yes, but better to wait until the stable version is released. Installing unstable version might cause trouble and might destroy your data/settings.

---

### Post by thenme on 2007-04-08
> yup, the operating system installs to the root partition. you don't need to do anything to keep everything as it is. it naturally assumes the same setup. just tick the option to format the root partition, but DO NOT select the option to format your home partition.

also, make sure that you include your home partition when selecting the mount points.....otherwise it will put your home directory on the root partition.
i'm not too sure if i've explained that clearly enough, really. what i mean is, assuming that you've previously assigned your root partition is hda1, your home partition is hda2, and your swap partition is hda3, then make sure you assign your root partition to hda1 again, assign your home partition to hda2 again, and your swap partition to hda3 again.....so that its the same as before.

This is quote from ComplexNumber's in [this post]("http://ubuntuforums.org/showthread.php?t=404654&page=2") talking about not having to reset everything. I'm not sure if that includes apps. But if I had to guess I would say at minimum they will have to be updated.

I can say that there is a huge update when you install feisty though.

---

### Post by maestrobwh1 on 2007-07-23
Does this include anything that I added to configure ndiswrapper?  I had to perform some tricks to get acpi to work and for my broadcom wireless to start during boot. I don't remember how to do any of this and would rather not have do.  

I currently have an edgy install that works fine, so perhaps I should follow the old wisdom of, "If it ain't broke, don't fix it?'  Still, Feisty has proved to have  few advantages on my desktop over the previous edgy version.

---

