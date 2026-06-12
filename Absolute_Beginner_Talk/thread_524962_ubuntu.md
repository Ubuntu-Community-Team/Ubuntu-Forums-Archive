---
title: "ubuntu"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by pizza on 2007-08-13
I am installing ubuntu with wubi installer, I was wondering when I get the ubuntu installed with this program can I remove windows?

I want just ubuntu without windows

Your answer will be greatly appreciated
Matthew

---

### Post by blithen on 2007-08-13
When you use the Ubuntu installer on the live CD and choose "Full Hard Drive Partition"
And it will format your hard drive(Meaning delete everything on it) and it will have a fresh install of Ubuntu.

---

### Post by MockY on 2007-08-13
I have never used wubi, but as far as I know, you have to use the live or alternative CD in order to accomplish what you want.

---

### Post by blithen on 2007-08-13
I've never even HEARD of Wubi >_>

---

### Post by Bart_D on 2007-08-13
It installs Ubuntu "LIKE" an ordinary software program in Windows and you can choose either OS on reboot....it does it all in a few clicks, but performance is an issue unless you go through a further set of steps to create a dedicated partition(which you may have to create).  You don't have to use a LIVE CD and you can eventually wipe out Windows to ...sigh...finally...sigh...get the same speed(system performance) as would be gotten from a LIVE CD installation.

I was tempted to go with it a few days ago when I went to Ubuntu, but it was pointless for me since I knew I wanted to wipe out Windows  altogether.

---

### Post by Arthur Archnix on 2007-08-13
Unfortunately, no. It's not quite that easy yet. From the wubi FAQ:
> How does Wubi work?
Wubi adds an entry to the Windows boot menu which allows you to run Linux. Ubuntu is installed within a file in the windows file system (c:\wubi\disks\system.virtual.disk), this file is seen by Linux as a real hard disk.

This means if you remove windows, you'll also remove the ubuntu file stored inside the windows file directory. Like above, you'll need a live or alternate cd to achieve this, but give Wubi a spin for a bit first and see how it feels.

Edit: Sorry, Bart_D seems to have some first hand experience with converting a Wubi intall to a full ubuntu install. I'm just answering based on what I've read on the FAQ.

---

### Post by misfitpierce on 2007-08-13
Just download CD for live disc for your processor architecture ex.. 32 bit i386 or i686 and 64 bit x32_64 x64 ... Then boot up to disc and install.

---

### Post by pizza on 2007-08-13
wubi allows you to install and uninstall Ubuntu as any other application. The reason I asked this is because my cd/dvd drive don't work on my pc, I was trying to get around it but luckily I have 2 extra crap computers that I am not using :D


Thanks guys

That was the fastest replies I have ever had on a forum wooh! :guitar:

---

### Post by pizza on 2007-08-13
and even more replies while I typed lol thanks to the rest

---

### Post by pizza on 2007-08-13
Is there anyway to boot the live cd with out the cd? My cd drive is not working on that computer. I dont think its the drive, think its just the computer

---

### Post by MockY on 2007-08-16
First, make sure that you have your cd-drive as first boot device in BIOS. To get there, hit ESC, F1, F2, or F8 (depending on the BIOS vendor) during POST. Look for the boot device section and change it. Save and exit. It should now boot from the CD just fine.

Alternatively, you can set up an image on a another computer on your network, and boot of the network. This requires you to change the boot order once more in BIOS. Keep in mind though, many older computers don't support PXE boot and this second option is not an option at all.

Hope this helps.

---

