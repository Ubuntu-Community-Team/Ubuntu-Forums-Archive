---
title: "Downloaded Feisty, deosn't work on hp laptop"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by sneffers on 2007-04-19
I downloaded the feisty fawn release and burned it to a cd but It said 40% and didn't go any farther but it worked when I put the cd in on the computer. But when I put it in on my laptop it didn't work. It wouldn't read the cd. I changed the bios so that it would read the cd first but that didn't help. I can get the command line by hitting esc when it says "Grub loading please wait." but I need to find a command that will erase my hardrive. [SIZE="4"][COLOR="Red"]PLEASE HELP ME!!!![/COLOR][/SIZE]

---

### Post by siciliancasanova on 2007-04-19
You want to wipe out your hardrive?  Download and use the gparted live disk.  It's my choice of partitioning anyway.  Much more control than the live disk.

---

### Post by silverglade00 on 2007-04-19
You need to burn it again. Burn it at 4x speed this time. It sounds like you didn't get a good burn on the CD. I'm writing this from my HP laptop on Ubuntu 7.04 Feisty :)

---

### Post by nudnik on 2007-04-19
> **sneffers said:**
> I downloaded the feisty fawn release and burned it to a cd but It said 40% and didn't go any farther but it worked when I put the cd in on the computer. But when I put it in on my laptop it didn't work. It wouldn't read the cd. I changed the bios so that it would read the cd first but that didn't help. I can get the command line by hitting esc when it says "Grub loading please wait." but I need to find a command that will erase my hardrive. [SIZE="4"][COLOR="Red"]PLEASE HELP ME!!!![/COLOR][/SIZE]

You need to burn another CD; I think its obvious that the one you have is defective.  Get a good install CD and the partitioning of the drive  will erase the mess. Make sure you choose the "erase entire drive" option when installing, unless you have XP or something else installed you wish to save. In that case choose the resize option and reinstall over the failed installation. Remember the mascot.....see below. :)

---

### Post by kittyhawk63 on 2007-04-19
> **siciliancasanova said:**
> You want to wipe out your hardrive?  Download and use the gparted live disk.  It's my choice of partitioning anyway.  Much more control than the live disk.

Siciliancasanova,
Sorry for the bump. Can you boot to gparted or do you have to use it within Linux? Or is both routes viable?

---

### Post by siciliancasanova on 2007-04-19
You can boot within gparted.  Just start up and throw the disk in really quick.  I mean if you know absolutely nothing, maybe don't use it, but if you want to have control over what you're doing and see any errors on your drive I would recommend gparted.  It's a GUI to so nothing complex.

---

### Post by kittyhawk63 on 2007-04-19
> **siciliancasanova said:**
> You can boot within gparted.  Just start up and throw the disk in really quick.  I mean if you know absolutely nothing, maybe don't use it, but if you want to have control over what you're doing and see any errors on your drive I would recommend gparted.  It's a GUI to so nothing complex.

So, I take it that it works as a liveCD. Am I right?

---

### Post by siciliancasanova on 2007-04-19
Right the Gparted Live Disk would be the one you're looking for.

---

### Post by kittyhawk63 on 2007-04-19
> **siciliancasanova said:**
> Right the Gparted Live Disk would be the one you're looking for.

Thank you very much. This tells me that I "saved" gparted on my CD instead of "burning" it. Your information really helps.
kh

---

### Post by siciliancasanova on 2007-04-19
Oh yeah, .iso format :) 

At least you didn't say that you burned ubuntu as data to a cd and asked why it wasn't installing :)

---

### Post by sneffers on 2007-04-19
Ok I get none of the gparted stuff. If I wipe my hardrive I could probably get it to work because right now my edgy doesn't work because of some file system error and so it shows the ubuntu loading thing but after that it has an error and doesn't do anything else. My cd works fin on a different computer just not on the lpatop.

---

### Post by siciliancasanova on 2007-04-19
Gparted is a live cd partitioner.  It will allow you to reformat your hardrive outside of your attempts with the Ubuntu live disk.

Edit: [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

