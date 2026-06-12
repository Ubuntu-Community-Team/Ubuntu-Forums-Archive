---
title: "Cloning Hard Drive"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Stunt Double on 2007-01-29
Is there a way to clone the hard drive on to an external USB hard drive?
I'm using Ubuntu Edgy Eft.

---

### Post by punx45 on 2007-01-29
do you just want to back up the data on the HDD or do you want to create an identical bootable drive in the USB drive?

---

### Post by Stunt Double on 2007-01-29
An identical bootable drive.

---

### Post by Marsolin on 2007-01-29
You could try [Ghost for Linux]("http://linuxappfinder.com/package/g4l"), [PartImage]("http://linuxappfinder.com/package/partimage"), or [g4u]("http://linuxappfinder.com/package/g4u").

---

### Post by punx45 on 2007-01-29
i haven't ever attempted this myself, but some of these links look like they might be what you are looking for:

[http://www.feyrer.de/g4u/]("http://www.feyrer.de/g4u/")  # this is the g4l homepage as Marsolin suggested.

[http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html](http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html) # a method using dd

[google search result]("http://www.google.com/search?hl=en&client=safari&rls=en&q=linux+clone+disk&btnG=Search")

might want to see if anyone else jumps in on this discussion before you try anything :)

not sure if the cloned drive being USB will affect its bootability.

# too slow, once again.

---

### Post by glabouni on 2007-01-29
dd is the command you're looking for
(no you're not looking for droïds!)

---

### Post by punx45 on 2007-01-29
be really careful if you decide to use 'dd'  it is often referred to as 'disk destroy' for a reason!

---

### Post by Greevous on 2007-01-29
Is it possible to clone your filesystem for installation on another computer? Say, if you wanted the exact same Ubuntu that's on a desktop to be installed on a laptop.

---

### Post by punx45 on 2007-01-29
yeah, disk cloning is generally used to deploy an install quickly on a number of machines, though i would imagine that with two machines that have different hardware, you will have some driver issues.   the image from the desktop *should* boot, but i wouldnt count on getting a gui etc. without some work.

---

### Post by e_james on 2007-01-29
I'm no Linux expert so I'm sure there are several reasons why my idea won't work but here's what I'm thinking.
Linux is the only OS I know which will let me create a FAT32 partition greater than 32GB AND do it on an external USB drive. I do it using Ubuntu (6.06) and gparted. Gparted appears to have the option to copy and paste partitions, why not use it? 
Maybe I just thought of a reason -- the Master Boot record?

---

### Post by Stunt Double on 2007-01-30
Thanks for the help. 
I have my Ubuntu installation pretty much the way I want it. But with dial-up, it took forever. With a spare drive, I'll be able to use it next time I inadvertently trash the main drive.

---

### Post by linuxjerk on 2007-04-02
All those still require the disk be unmounted to copy. Try G4U I got it to work on my system.
You can either do floppies or cd.
[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

---

