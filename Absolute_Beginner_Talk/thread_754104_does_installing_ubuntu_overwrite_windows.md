---
title: "does installing ubuntu overwrite windows???"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by swimm3r137@gmail.com on 2008-04-13
Hi,

I'm obviously a complete beginner.  About 20 minutes ago, I began the download of the ISO installation file(7.10) from the download page.  Once it's done, I'm going to burn the file to a cd as instructed, so I can experience the live edition first.  After I burn the cd, run it, does this overwrite and/or delete my Windows OS and all the info on it??  I'm thinking no, but that brings me to another question..  What if I'm satisfied with ubuntu, and actually _wan't_ to delete windows (thank god)and just have ubuntu overwrite it and give me a fresh, clean computer again??  :)  How do I do this?  I mean honestly, the only thing I really wan't to save is my mp3 files, which I'll just put on an external hard drive, then sync them back to my new comp after my hard drive is wiped.  It sounds silly, but I really want to erase all the **** on my computer and start brand new again, with a new OS; brand new out of the box, quick again, and no windows =)~

thankyou!!

---

### Post by Zralou on 2008-04-13
Running the 'Live CD' won't affect you computer (unless you 'sudo' into something system related).

Once you reach the Ubuntu desktop, you have the option to install to the hard drive from there.  If you plan to install to the whole hard drive (i.e. overwrite windows) make sure you back-up anything in windows you want to save before installing Ubuntu.

Sara Lou

---

### Post by swimm3r137@gmail.com on 2008-04-13
Also, I play starcraft a lot, especially online on battlenet.  PLEASE tell me it runs fine with Ubuntu!!

---

### Post by sayakb on 2008-04-13
If you want to completely wipe out Windows, boot in to the LiveCD and run gparted (System->Administration->Partition Editor) to delete your Windows partition. Now install Ubuntu on that partition.

---

### Post by swimm3r137@gmail.com on 2008-04-13
> **Zralou said:**
> Running the 'Live CD' won't affect you computer (unless you 'sudo' into something system related).

Once you reach the Ubuntu desktop, you have the option to install to the hard drive from there.  If you plan to install to the whole hard drive (i.e. overwrite windows) make sure you back-up anything in windows you want to save before installing Ubuntu.

Sara Lou

So, let's say I have a 80gb capacity and its 70/80 full right now.  Hypothetically, if I were to click install in the live version, I would be back at like 5/80 if I didn't back up anything?  Sorry, I'm a clear n00b.  Also, Itunes runs linux right?  I assume so, considering mac is linux.

---

### Post by Zralou on 2008-04-13
I don't know the answer to that, but there are 'emmulators' that will run 'windows' programs in linux.  You've have to search the forums as to whether starcraft is usable in Ubuntu.

Sara Lou

---

### Post by sayakb on 2008-04-13
> **swimm3r137@gmail.com said:**
> So, let's say I have a 80gb capacity and its 70/80 full right now.  Hypothetically, if I were to click install in the live version, I would be back at like 5/80 if I didn't back up anything?  Sorry, I'm a clear n00b.  Also, Itunes runs linux right?  I assume so, considering mac is linux.

Mac is not Linux. Plus, iTunes might not run on Linux. Though there are some authentic iTunes executables for Windows. You might purchase it and run it with Wine (Windows Emulator)

To install Wine:```
sudo apt-get install wine
```

---

### Post by jbalazs on 2008-04-13
Try Wubi it's the easy way to Ubuntu

---

### Post by swimm3r137@gmail.com on 2008-04-13
> **LinuxIsInnovation said:**
> If you want to completely wipe out Windows, boot in to the LiveCD and run gparted (System->Administration->Partition Editor) to delete your Windows partition. Now install Ubuntu on that partition.

Ya the reason I want to wipe windows completely and just overwrite it with ubuntu is 1) Windows sucks 2) My computer would be terribly slow if I were to dual boot it (IF it worked) 3) who needs windows anyways?

---

### Post by visualdeception on 2008-04-13
[Yes, Starcraft works flawlessly in ubuntu. You have to install wine [sudo apt-get install wine] to use it though.  The issue about your hard drive, yes you will be down to about 5/80, i would try cleaning up some of the unneeded applications out of windows if you have to dual boot. But always make sure to backup your data before you run any sort of installation.

---

### Post by sayakb on 2008-04-13
> **swimm3r137@gmail.com said:**
> Ya the reason I want to wipe windows completely and just overwrite it with ubuntu is 1) Windows sucks 2) My computer would be terribly slow if I were to dual boot it (IF it worked) 3) who needs windows anyways?

 Dual boot does not slow down your computer. If you have enough free space, you might keep both Windows and Ubuntu (unless you are desperate to remove it :)). None of the OSs would affect the speed of the other under any circumstances.

---

### Post by swimm3r137@gmail.com on 2008-04-14
Unfortunately, I have to use the alternate cd to install because the live cd doesn't work with my laptop.  LIke I said in the beginning of this thread, I wan't to COMPLETELY overwrite my 80gb hard drive and delete everything thats there, including windows and all of it's applications and basically install with a CLEAN SLATE!!  Yay! :)  But, when I'm running the alternate version, I don't know what to do when the screen comes up about partioning.  Can anyone help me and guide me when the partion screen comes up?  I just want to install ubuntu and overwrite everything, just it's in wierd wording, so I can't figure which option to pick.

When it comes up, it says this:

I think I should use:

"Guided- Use entire disk"

After clicking this, it says-

"Select disk to partion: IDE1 master (hda)- 80.gb ic25no80atmro-40"
Is this the write method to delete and overwrite everything on my hard drive with ubuntu?


Also..... Does anyone know what "ESSID for eth1 means"?? It pertains to my wireless network.  After this then comes a screen asking for my wireless key, which I understand.

---

### Post by swimm3r137@gmail.com on 2008-04-14
Just posted edited version

---

### Post by jgrabham on 2008-04-14
> **swimm3r137@gmail.com said:**
> 

Also..... Does anyone know what "ESSID for eth1 means"?? It pertains to my wireless network.  After this then comes a screen asking for my wireless key, which I understand.

Yes, it is the "name" of your wireless network, and its on your second network card (eth1)

eth0 - first network card
eth1 - second network card

---

### Post by wpshooter on 2008-04-14
> **swimm3r137@gmail.com said:**
> Ya the reason I want to wipe windows completely and just overwrite it with ubuntu is 1) Windows sucks 2) My computer would be terribly slow if I were to dual boot it (IF it worked) 3) who needs windows anyways?

Swimm:

You can use this program to competely WIPE your hard drive.

Of course, make sure that that is what you really want to do before you start.

I recommend running it from a CD.

[www.killdisk.com](www.killdisk.com)

Good luck.

---

### Post by NikS on 2008-04-14
Yes, thats the correct oprtion if u wish to remove everything else and install ubuntu!!!

But, I have no idea about the wireless thing u said..

---

### Post by NightwishFan on 2008-04-14
It does not slow the computer to dual boot. Currently I have a triple boot setup.

---

### Post by swimm3r137@gmail.com on 2008-04-14
> **NightwishFan said:**
> It does not slow the computer to dual boot. Currently I have a triple boot setup.

Awesome.  The only real reason I'm choosing to not dual boot is because I think I can learn ubuntu, I hate windows, theres nothing on windows that I really want to keep that I havnt already put on my external hard drive (my mp3's) and (MAIN REASON) I wont have enough space once I put all the crap I have backed up on there

---

### Post by jmendez2 on 2008-06-12
Greetings,

In my Disk Manager screen I have the following:

Partition 1
Free Space -  Size (7.17 GiB (Free space not available))
Swap Partition -  Size  ( 2.89 Gib)

What does 'Swap Partition' mean and what is it supposed to contain?

Thanks!

---

### Post by snowpine on 2008-06-12
> **swimm3r137@gmail.com said:**
> Awesome.  The only real reason I'm choosing to not dual boot is because I think I can learn ubuntu, I hate windows, theres nothing on windows that I really want to keep that I havnt already put on my external hard drive (my mp3's) and (MAIN REASON) I wont have enough space once I put all the crap I have backed up on there

Good for you, quit Windows cold turkey! Just select "guided partition: use entire disk" and Windows will be toast.

You'll get one large partition for Ubuntu and a small partition for swap. Swap is basically like Virtual Memory in windows; Ubuntu stores temporary files in there to help your computer run faster. It is usually approximately twice as large as your RAM.

---

### Post by Lord Xeb on 2008-06-12
> **snowpine said:**
> Good for you, quit Windows cold turkey! Just select "guided partition: use entire disk" and Windows will be toast.

You'll get one large partition for Ubuntu and a small partition for swap. Swap is basically like Virtual Memory in windows; Ubuntu stores temporary files in there to help your computer run faster.

Yes, and depending on how you set up your swappiness, you can make it so that only big apps go into swap, or so that when your mem runs out, your swap is used, or something in between.

---

### Post by Sealbhach on 2008-06-12
There's a good visual guide here

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

 of the screens you'll see during the installation process.  The most important bit is

[IMG]http://www.psychocats.net/ubuntu/images/installinghardyplus11.png[/IMG]

The options are explained:
> 
This first option **(Guided resize and use freed space)** is ideal for users who want to set up a dual-boot (where you can choose whether you want to use Windows or Ubuntu each time you boot up your computer) but know very little about setting one up. You can just drag the division between Windows and Ubuntu to make the Windows installation as small or large as you want, and Ubuntu will fill up the rest of the space.

The second option **(Guided - use entire disk)** will erase Windows completely and install Ubuntu over it.

The third option **(Guided - use the largest continuous free space)** will make Windows as small as possible and install Ubuntu in the remaining empty space.

The fourth option **(Manual)** allows you to manually configure the partitions as you see fit. This is for intermediate to advanced users. 

---

