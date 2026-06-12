---
title: "iMac G4 Ubuntu Help..."
date: 2009-01-08
forum: Apple Hardware Users
---

### Post by McFrostey on 2009-01-08
Ive had my iMac G4 PowerPC for about a year and I love osx... though the PC,Mac battle continues i got curious about a third party OS that gets little attention known as Linux. Since im new to linux and knew nothing about it i went straight to Ubuntu.com and downloaded the newest version then i realized it wasnt for my type of PowerPC. so i got the alternative version and got the disc. a Command Prompt Similar to DOS pops up and I hit enter.. when i get to something that says Mounting CD-ROM drive it fails installation since im VERY NEW:( to this command prompt stuff like this i have  no idea what to do if only someone could give me STEP BY STEP instructions i give you many THANKS:D

---

### Post by stream303 on 2009-01-09
> **McFrostey said:**
> when i get to something that says Mounting CD-ROM drive it fails installation since im VERY NEW:( to this command prompt stuff like this i have  no idea what to do if only someone could give me STEP BY STEP instructions i give you many THANKS:D

I guess you gotta' start somewhere right? :)

The good news is that your G4 iMac is using an Nvidia card, and is of relatively recent vintage so that will help out a lot.  Which model do you actually have?

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

Up front know that with PPC, flash is not perfect, and 3D is out of the question with the nvidia card.  Also, depending on the model, you may also have no suspend, nor hibernation.  In addition, you may also lack lcd panel control brightness.  Still want to continue?

Of course, iTunes and other proprietary Apple software won't run on it.  Which leaves basically a 2D experience running web browsers, email, etc - mostly general purpose stuff until you get your feet wet.

And, in most cases, ppc owners have to hit the commandline.  Thing is, that is so vast a subject, that perhaps a little practice up front right inside your own OSX might help determine if you are going to put up with it.

At the very least, you'll want to get some practice with the *nano* text editor in OSX - that same editor is available for use in Linux.  You may very well end up using that editor to custom-edit some system files that don't get written correctly due to hardware issues during installation for the ppc.

Call up a terminal in OSX, and edit some random text with nano:

```
nano mystuff.txt
```

Enter in some random lines of text.  Save it with CTRL-O and then exit the editor with CTRL-X.  Now you have a file you can learn to rename, move or even view with *less*:

```
less mystuff.txt
```

Q to quit less.  You see where I'm going, as we might be able to guide you through things, but you've got to want to do it - AND we may not be able to hold your hand 100% - there is always that chance that you'll brick your new G4 iMac despite our best intentions since we aren't actually in front of the machine. :)

You'll also need to actually make space for the installation.  Do you want to dual-boot, or wipe out OSX completely?  If so, you'll need to either resize your partitions, or reinstall osx to say half the drive, leaving the other half as free space and install Ubuntu to that.

Most of this kind of info is scattered across various wikis and in the threads here.  Perhaps peruse the threads and see that you may be jumping into - otherwise with your request one might become famous writing a book about Linux on PPC in just one thread. :)

Before you do anything - MAKE BACKUPS.  Do you have your original OSX installation disks in case you need to restore it after a botched Linux install?

Spend a bit of time looking into the threads here and see if this is really something you want to jump into.  Just being honest - not trying to dissuade you.

---

### Post by tiresia on 2009-01-09
I guess you downloaded Ubuntu Intrepid (8.10). The alternate version has a small bug, but it is very easy to solve it.
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

If you feel more comfortable with a grafical interface, you should download the Live-CD, desktop-Ubuntu Hardy (8.04.1).
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

As stream also remarks, if you want to keep MacOSX:
1. backup every important data.
2. start your computer from the Ubuntu-Live-CD pressing C
3. Choose the Icon 'Install' on the Desktop
4. Resize the partition and Install Ubuntu
---

Before doing anything: do you have a MacOSX Installer? 
Installing Ubuntu is not dangerous at all, and I'm sure you will enjoy it - since you can do things you can't do with a mac, and you will learn a lot. But if you make a mistake, it's safer to have a MacOSX Installer

---

### Post by mkvnmtr on 2009-01-09
You have some good advise from two experienced users. Like you I liked my mac os much more than windows. After several months on Ubuntu I seldom boot mac. I can do things I never thought about on a Mac. If you have time and the desire to learn to use a new os you will probably like it. Like they said back up and have the Mac install disks. I never screwed up my mac system but I did decide to reinstall twice and I got really good at installing Ubuntu.

---

### Post by McFrostey on 2009-01-09
> **tiresia said:**
> I guess you downloaded Ubuntu Intrepid (8.10). The alternate version has a small bug, but it is very easy to solve it.
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

If you feel more comfortable with a grafical interface, you should download the Live-CD, desktop-Ubuntu Hardy (8.04.1).
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

As stream also remarks, if you want to keep MacOSX:
1. backup every important data.
2. start your computer from the Ubuntu-Live-CD pressing C
3. Choose the Icon 'Install' on the Desktop
4. Resize the partition and Install Ubuntu
---

Before doing anything: do you have a MacOSX Installer? 
Installing Ubuntu is not dangerous at all, and I'm sure you will enjoy it - since you can do things you can't do with a mac, and you will learn a lot. But if you make a mistake, it's safer to have a MacOSX Installer
Well I attempted to Download the .ISO file you link'd and it wouldnt download correctly it said "failed to mount disc image" at the end of the download

---

### Post by McFrostey on 2009-01-09
Well Guys I have been successful I'm now running Ubuntu 8.10 on my iMac G4 and its great... since OSX was 3D I experienced some lag when opening up windows which was a pain now i can scroll through text with ease...:)
The software that comes with it is great for starting off and I plan on getting plenty more :D. I would like to thank you guys for helping im so very happy :D Kudos

---

### Post by stream303 on 2009-01-10
Glad to hear that G4 iMac is up and running!  Have fun!

---

### Post by Lime on 2009-02-18
I have recently installed Ubuntu 8.10 on my iMac G4 17".  All seems to be working well except the sound.  Initially, I got a red x on the sound configuration icon on the top toolbar.  I applied this change (from the ubuntu powerpc wiki) which resolved the red x issue... still no sound.  Any ideas?

From the wiki:

The Feisty install fails to add the proper sound module to /etc/modules. To fix this,

sudo nano /etc/modules

and the at the bottom add snd-powermac to the list. Ctrl-X and 'Y' to save. Reboot, and sound will work.

---

### Post by mkvnmtr on 2009-02-18
I have not heard of anybody having sound problems on the ppc macs. Be aware thet many times after an install some things are muted and you just have to turn them on. Be careful applying things from the wiki that are about older distros. They might not apply to your 8.10. If turning on the sound doesn't work for you you might want to start a new thread to discus your problem with something about your sound problem in the title.

---

