---
title: "Xubuntu LiveCD Faliure"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2006-10-08
Greetings,

I just set myself to the task of creating a Xubuntu LivCD, and things did not go well.  I've made other bootable disks before (
GParted and Ubuntu), so I do know what to do.

So, I got ready to burn the ISO, and CDBurnerXP Pro 3 produced an error saying that the disk wasn't empty.  It was a new CD, but I figured it was just a bad disk (my CD drive also didn't behave as though it were a blank when I put it in).  I tried another, but it did the same thing.  Finally I tried the last CD I had on hand and it started burning.  I chose to keep the speed at x2 because it was my last CD and I couldn't do anything if it went badly.

It got done, and then I put it back the in the tray.  Instead of seeing a nice Xubuntu box like I was expecting, a window popped up asking what I wanted to do with this kind of disk.  I looked on the CD, and everything seemed to be normal.

Is my CD drive dying, or is this common Xubuntu behavior?  I didn't really want to try booting off of the disk until I knew for certain.  Yes, I also verified the checksum before burning.

Thanks!

---

### Post by Darklighter137 on 2006-10-08
Bump

---

### Post by Darklighter137 on 2006-10-08
Bump (sorry about doing this again).

---

### Post by crokett on 2006-10-08
If you explore the CD, what do you see?  When the window pops up asking what you want to do, what are your choices?

---

### Post by Darklighter137 on 2006-10-08
It strangely acts as though the CD is filled with pictures.  It has stuff like view slideshow of images, etc.

---

### Post by Darklighter137 on 2006-10-08
Everything appears fine except for two files on the disk:  One marked README, and another that says Ubuntu (no file extension, no bytes).

---

### Post by dolphinsonar on 2006-10-09
I know what your problem is.  You are in windows or mac when you are trying to run the Xubuntu live CD right?

The CD has to boot.  Restart the computer with the cd in the cd drive.  If it does not boot Xubuntu after that, then you have to edit the boot order of your particular computer to get it to check the CD drive before automatically loading the hard drive.

This is different for every computer.  On mine it consists of restarting, then pressing either F2 or F12.  When the menu comes up you are looking for something that says "boot order" or something like that.

Dont change anything else, just that one thing.  There should be a list, with your hard drive, cdrom drive, perhaps a USB in there etc..  The idea is to make the cd drive (with the Xubuntu disk in it) first, so that the computer checks there before checking your hard drive, thus booting Xubuntu.

Sorry if I completely missed your problem, but I am pretty sure this is it.

---

### Post by Darklighter137 on 2006-10-09
Thank you, but that isn't quite the problem.  When you insert Kubuntu or Ubuntu LiveCD's into a Windows machine, it boots up with a window offering to install some free software.  When that didn't happen with my Xubuntu CD, I became worried.

---

### Post by Darklighter137 on 2006-10-09
Bump

---

### Post by asmiller-ke6seh on 2006-10-09
What dolphinsonar says is correct. The Xubuntu/Ubuntu LiveCD also has Windows software similar to the Linux software that you can try - OpenOffice.org and Firefox are two of the most notable of these software pacjages.

You should check the boot order of your hardware as listed in the Boot ROM of your system. While each system can be a little different, when you reboot your system, and before your Windows operating system starts to load, you can press the Function key that is set up for your system that allows you to make changes to your system's Boot Rom setup. On many systems this is the <F2> key, while on other systems it might be the <F12> key, or maybe the <F6> key.

This will bring up a character-based menu of options. You will be looking for the option that controls the order of the devices (hard disk, DVD drive, CD drive, USB stick, etc) that will be examined during the boot process. If your Boot order reads the hard drive before it reads the DVD drive, you will not be able to boot into Ubuntu/Kubuntu.

Make sure that you only change the booting order of the drive devices - then save your changes. Insert the Ubuntu disk into the DVD drive and then reboot the computer. You should be able to watch the DVD drive start reading the Ubuntu disk before your PC starts to read the hard disk. If not, you still need to edit the correct boot order for the drives.

---

### Post by Darklighter137 on 2006-10-09
Thank you, but I understand these things and this is not my problem.  My question is this simply a bad CD that I've burned, or is my CD burner going out?  I've booted many LiveCD's--including Ubuntu and Kubuntu--and I know what it is supposed to happen, and the boot order is fine.  Since the disk seemed fine, and since the ISO is fine, and since I burned it at a very low speed, I am concerned as to whether you guys think my CD drive is starting to have problems, because the CD should work and yet it behaves as if it hasn't been burned properly.

Does my question make more sense now?

---

### Post by asmiller-ke6seh on 2006-10-09
I'd like to help. Please tell me precisely what happens when you place your disk into the CD drive and then reboot your system?

---

### Post by Darklighter137 on 2006-10-09
Because of the strange things that happened when I put it into the drive with Windows running, I felt that it would be a poor idea to try and boot off of it.

When I put the CD into my drive, Windows pops up with a dialog asking me what I would like it to do when a CD like that is inserted into the drive (it calls it a CD full of pictures).  Everything on the CD looks pretty much like the Ubuntu and Kubuntu CD's I have, except that there is a file called Ubuntu in the main directory that has no file extension and is 0 bytes in size.

Is this just a bad burn, or is my CD drive going out?  I've been concerned about it ever since I had to make a 16 disk recovery set for Windows (I have a new HP machine).  Like I said above, I've burned a few ISO's before and I had no trouble.  The MD5 sum has been verified, and I burned it on the x2 speed.  I am concerned because the software spit out two other disks, saying that they were not empty (they were fresh out of the box).

Thank you for taking the time to help. ^_^

P.S.  The drive reads regular CD's just fine.

---

### Post by asmiller-ke6seh on 2006-10-09
If you want to preview ubuntu without having to load it into your hard drive, you will have to boot into the LiveCD.

Think of it this way - there are two sides to this disk: one side contains Windows applications that you can load up from within Windows - the other side contains a trial version of ubuntu that loads up only if you boot up into that disk.

If you boot up into ubuntu, then you can play around and experience ubuntu; when you are ready to load ubuntu onto you hard disk, you can do that from within ubuntu.

The things that you described that happened to you is exactly what is supposed to happen if you have Windows loaded and then you place the LiveCD into your CD drive.

Try it - you just might like it.

---

### Post by Darklighter137 on 2006-10-09
But sir, isn't Xubuntu supposed to bring up a little window offering to install some Windows open source stuff, like the other two LiveCD's do?

---

### Post by blendmaster on 2006-10-09
I don't think so. I think it's the only one that doesn't, because I tried it without going into livecd mode like you and it doesn't. But I do know my cd works fine, so I'm pretty sure it doesn't provide the free software for windows functionality like the others. Hope that cleared something up.

---

### Post by blendmaster on 2006-10-09
> 
But sir, isn't Xubuntu supposed to bring up a little window offering to install some Windows open source stuff, like the other two LiveCD's do?


That quote goes to my last post. Sorry I forgot to put it.

---

### Post by Darklighter137 on 2006-10-09
Thank you, that was exactly what I needed to know. ^_^

---

### Post by blendmaster on 2006-10-09
You're welcome!

---

### Post by Darklighter137 on 2006-10-10
Thanks once again to all who helped--Xubuntu is awesome.

---

### Post by Lean 946 on 2007-08-17
I know your problem and I know it's a Bullshit (sorry the word).

The Ubuntu and Kubuntu Live CD's have some of that "presentation screens" on Windows, etc. Xubuntu  doesn't. It hasn't that so Windows will ask you what you want to do with that files. You have to cancel them. Restart your computer, load or keep load the LiveCD of Xubuntu on your CD Tray and, if your BIOS is correctly configured, you might see a introduction screen for Xubuntu Asking you if you want to load Xubuntu, or many other utilities, like check the CD for errors, etc.

Bye, and I hope this help you.

---

