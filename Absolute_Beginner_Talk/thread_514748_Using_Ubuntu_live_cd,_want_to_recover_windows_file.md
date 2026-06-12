---
title: "Using Ubuntu live cd, want to recover windows files, due to windows not booting."
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Rabbitez on 2007-08-01
I have windows installed, I also have two partitions, one is simply a backup partiton, for extra music files etc etc.

I attempted to install Ubuntu on that partition, the one with music on etc, when I tried, (using the ubuntu manual install method)  it *seemed* to work.

BUT for some reason (yeah, I am an utter noob to Linux, though I like it, and I want to use it instead of windows) I managed to screw up, now, windows just won't boot. " Missing Operating System"

All I wanted to do was to dual boot windows & Linux. Now I have got myself in a bit of a pickle, and I need to backup some files I have on my windows partition, about 20gb total.

I have an external HD! So I plugged that in and wanted to be able to easily backup these files to it, but I don't have permission to apprently. :confused:

Basically, I have some files I need backing up, so I can re-install windows, then install Ubuntu after, dual booting them...

It would be heck of a lot easier just to get the windows partition working.
I am gonna get tid of that partition after, and just let Ubuntu make a partition after I installed windows again.


So can anyone help me backing up these files?

Again, (don't die of boredom :tongue:) but I can't just copy these files to my external HD, because I dont have permission to access it!

Thanks so much if you spent the time to read this

Really appreciate it (Sorry if I write in a confusing manner)

Rabbitez

---

### Post by razeshkale on 2007-08-01
No worries man!
you can recover your windows partition as well get hold of Ubuntu

try to go through guides available on net
google how to recover xp after installing ubuntu.

you get it
cheers

---

### Post by nitro_n2o on 2007-08-01
if you can't log in to ubuntu also try this [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
otherwise if it's only windows that is missing boot with your windows cd, go to recovery mode and type fixmbr [or google fixmbr windows] this should give your windows back, unless you deleted the partition and the whole system :)

---

### Post by logos34 on 2007-08-01
Open a terminal and type:

**sudo fdisk -l** (lowercase L)

Post it.

---

### Post by Rabbitez on 2007-08-01
Thanks for reading, but I think you have misunderstood a bit (my fault, I don't explain well)

You see, my Ubuntu installation..... doesn't exist.. heh...

I tried to install, but alas, it didn't work, somehow my Ubuntu installtion broke windows, so it won't load
Bios is fine and stuff, it's not that, but my pc can't find my windows installation...

it's there, I can see it in Ubuntu :P 

If I can get windows to boot up, then I can backup my important files, and then I can dual boot Ubuntu,

I wanna get rid of the 2nd partition cause I can't figure out how to put Ubuntu on it succesfully :tongue:

Then once windows is back and working, I can let Ubuntu resize the partition. :KS

peachy. 


Thanks

Rabbitez

---

### Post by Rabbitez on 2007-08-01
Geese, sorry nitro_n2o

I just saw your message, I will try that, looks promising :D

---

### Post by Rabbitez on 2007-08-01
What does windows mean when it says "error loading operating system?"

does that mean I am screwed?

---

### Post by logos34 on 2007-08-01
maybe, maybe not...post fdisk -l, that will show us your partitions, which one if any are flagged active/boot

---

### Post by Rabbitez on 2007-08-01
[IMG]http://img180.imageshack.us/img180/9430/diskkc4.png[/IMG]

here it is...

---

### Post by logos34 on 2007-08-01
see, hda1 should have that * boot symbol.  But that may not be all that's wrong here.

Let me get this straight: you meant for ubuntu to install to hda2, overwriting the ntfs data storage partition, and when you boot you can't get into either OS because you don't get the Grub menu screen, just 'missing operating system', is that right?

---

### Post by Rabbitez on 2007-08-01
Yup, that's right.

---

### Post by logos34 on 2007-08-01
I'd check to see the /boot/grub/menu.lst file is correct, then try reinstalling grub.  If that doesn't work then try to restore windows bootloader to get into xp, but that will lock you out of linux (unless you boot linux through ntldr).

First, change the flags:

System>admin>gnome partition editor

Right-click on hda1>manage flags>check 'Boot'.  Then hit the 'Refresh devices' button (under Gparted in the menu) and it should say 'boot' to  the far right column of hda1 only.  

Your menu.lst should have linux listed at (hd0,2) and windows entry pointing to (hd0,0).  Change if necessary.

**gksudo gedit /boot/grub/menu.lst**

save any changes and close.

Then, 

[B]sudo grub
root (hd0,2)
setup (hd0)
quit[/B]

Give that a shot.

---

### Post by logos34 on 2007-08-01
> **Rabbitez said:**
> [IMG]http://img180.imageshack.us/img180/9430/diskkc4.png[/IMG]


I just noticed something: hda1 slightly overlaps hda2 (12168  and your ubuntu root partition is awfully small.  what does

**df -h** 

show (root has to be mounted first)

Or Gparted show?

---

### Post by Rabbitez on 2007-08-01
She lives!!!!!!!!!!


"but that will lock you out of linux"

Come again? I don't have Linux installed, I was using the live CD

Anyway, I changed the boot flags, and it worked, which is pretty kickass...

Do you just mean it will cause Ubuntu to break during using the CD?

I looked at the menu.lst, but there was nothing there, so I guessed I had broken something or done something the wrong way, I restarted out of gnome, and windows now seems to be running *cough* smoothly *cough* 

Now I can back up my files... then I will use the gparted live cd to setup my partitions and get Ubuntu on my second partiton, makes it easier.. I think.


Thanks a lot for your help :KS

---

### Post by logos34 on 2007-08-01
oh, I thought ubuntu was actually installed on hda3...I'm reading a dozen different threads at any one time, so forgive me, they start to run together in my head...glad it's working now and you can get into windows.  It's all downhill from here hopefully, just backup, wipe the rest of the disk clean, create your linux partitions and away you go.

Edit: consider making a [separate /home partition]("http://users.bigpond.net.au/hermanzone/p14.htm").  

Good luck!

---

### Post by Rabbitez on 2007-08-01
Yeah, I can pretty much do it all the way from here, but, Someone I spoke to earlier said it was a bad idea to use the Ubuntu installer?

by that I mean the thing that compresses the windows installation, then makes a partition, and installs ubuntu.. he said it was cluttered or something, do you think I should stay away from that?

He told me to use gparted live CD, so I could do that, but is it really much hassle compared to just letting Ubuntu do it? 

thanks again for your help

---

### Post by thefoolisme on 2007-08-01
Well, since the Ubuntu installler uses gparted, there really isn't any difference.  I've used the ubuntu installer many times on different machines, for dual boots with success.  The key is to pay attention to what you're clicking on.  :-)  good luck

---

### Post by logos34 on 2007-08-01
> **Rabbitez said:**
> Yeah, I can pretty much do it all the way from here, but, Someone I spoke to earlier said it was a bad idea to use the Ubuntu installer?

by that I mean the thing that compresses the windows installation, then makes a partition, and installs ubuntu.. he said it was cluttered or something, do you think I should stay away from that?

He told me to use gparted live CD, so I could do that, but is it really much hassle compared to just letting Ubuntu do it? 

thanks again for your help

thefoolisme may be right that there is no difference between the gparted on the ubuntu install cd and gparted's own livecd, but my unscientific conclusion is that you're better off with the gparted livecd if only because it's a couple of releases ahead of the one on the ubuntu cd and thus has the latest bugfixes and added features, and the gparted livecd just seems to have less problems working with partitions--I don't know if this because it take up  less ram than the ubuntu install cd or what.  It's only a ~50 MB download.

---

