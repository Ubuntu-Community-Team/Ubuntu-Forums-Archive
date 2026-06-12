---
title: "Need answers re: lost files in Win XP, options for recovery"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by mceven on 2007-06-04
Hello and thanks in advance to anyone who can help me out.

Here's my situation:  my son (12 years old) took it upon himself to install Ubuntu on our home computer without consulting his mother or I.  I came home from work this afternoon to find our computer totally different from what it was (Windows XP) and now I can't find our files, and we can't get websites to operate correctly (i.e. Youtube). 

I'm not computer illiterate: I'm fairly proficient with Windows; I know what Ubuntu & Linux are and I'm actually not opposed to keeping this an Ubuntu machine as long as we can all figure out how to do all of the things our family normally does on the computer.  My son was trying to set up a dual-boot machine whereby he could use and experiment with Ubuntu and the rest of us could use Windows as normal.  After hours of tinkering today, I think he erased Windows as there's no option to select it as an OS when we reboot the computer.  My fear is that our files on the laptop's C: and D: drives are gone as well -- I can't locate anything in Nautilus like I used to, I'm hoping the files are just located somewhere else.  

Here's the details on our computer:  Sony Vaio PCG-FRV37 laptop; two separate, internal hard drives of 40GB each; one external hard drive of 250 GB.  My son did not back up the C and D drives before installing Ubuntu onto the external (G:) drive, and the last time I had backed up our computer was a few months ago.  Therefore, I can locate pictures and other important files up to that point -- no problem accessing things on the G: drive, but I can't find anything familiar on the C: and D: drives.  Ubuntu doesn't seem to recognize that there are two separate internal drives, for that matter.  

All of that preface aside, here's my litany of questions:

1) are the files on C: and D: lost?  If so, damn.  That sucks.  
2) If not, how do I locate them?  We organized our pictures with Picasa, and I can't find the program files for that (though I know I could just download it again).  Also, all of our bookmarks in Firefox are gone -- can I somehow import them from whereever they were saved in XP?  
3) Are we just missing a very simple solution here?  Maybe he did create a dual-boot setup and I just can't figure out how to switch it to XP. 
4) If we're now stuck solely in Ubuntu, how do I install plugins and codecs for media and video, etc?
5) Can I do a reverse and retroactively install Win XP to establish a dual-boot system or would it be easier to wipe the whole computer clean and start fresh?

Assistance on any of these starter questions would be greatly appreciated.  Again, I'm not opposed to sticking with Ubuntu -- the only program it seems we can't use that we did on XP is Itunes, and there seem to be alternatives for that -- although we can't play most of our music files yet.  All we use this computer for is office applications (we've been using OpenOffice on XP for a couple of years), Picasa to organize photos, Internet access, and Itunes/music management.  As long as I can figure out how to do those four tasks and somehow recover the files we've created and saved in the last 3 months, I'm fine with this.

Thanks again and I apologize for sounding like a total noob.

---

### Post by Ek0nomik on 2007-06-04
This question may help you:  [https://answers.launchpad.net/ubuntu/+question/2178](https://answers.launchpad.net/ubuntu/+question/2178)

You might need to format your drive back to NTFS to recover the files, but I am not certain.  A simple search in Google for, "file recovery ubuntu", will give you plenty of useful results on the matter.

If you want to see how your partitions are setup, you could run the command in a terminal (Accessories>Terminal)

```
sudo fdisk -l
```

or you could install gparted and look at your partitions graphically.  To install gparted:

```
sudo aptitude install gparted
```

If you want to install codecs, this is a good thread to help you get started:  [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

If you want to dual boot XP and Ubuntu, I would suggest wiping out your drives and starting fresh.  I would install XP first, then Ubuntu.  It's just a bit easier this way for booting purposes. (If you have more specific questions regarding partitions setup, again, just reply and ask)

Music is very easy to get working on Ubuntu.  I have music playing on my box 24/7.  :)

Picasa is very easy to install on Ubuntu, in fact a single file is all it takes. (Link: [http://picasa.google.com/linux/thanks-deb.html](http://picasa.google.com/linux/thanks-deb.html))

iTunes can be done on Ubuntu as well, and it should be painless.  Amarok is a great music program that should allow you to add and delete music off your iPod.

If you have more specific questions, feel free to ask.

---

### Post by Rocket2DMn on 2007-06-04
have you checked the available drives/disks in /media/

When I installed I was able to see my windows partition there.  Using ntfs-3g I was able to read/write correctly from it.

---

### Post by Ek0nomik on 2007-06-04
If you don't understand what info is given to you after you run the fdisk -l command, copy and paste your output onto the forum and I or someone else will help translate.

---

### Post by Lucifiel on 2007-06-04
If your son installed onto 1 drive, there is no way he could have erased the contents of the other drives.

Edit: You can try and open up System ====> System Monitor (think System monitor is in one of the menus under System. I don't have Ubuntu right now, sorry.). And use it to check all the partitions.

---

### Post by Marious on 2007-06-04
You might be out of luck on this one, I imagine what happen was that he over wrote your Windows partition by accident and I am unsure if the files what where there are recoverable because other data has been written over it. I hope this is not the case and perhaps others have a solution for you to recover the data but it seems that it might be a tough issue. I hope your most important files where back up if you cant recover them from this event, I always keep a handy external hard drive for such cases. If you invest in one, just get a new external case, and a hard drive much cheaper than those premade.

As far as doing all your daily activities on a computer, there are many web site's that list programs to use in Linux that do the same in Windows the following is a good site to look at for such programs.

[http://www.libervis.com/wiki/index.php?title=Table_of_Equivalent_Software](http://www.libervis.com/wiki/index.php?title=Table_of_Equivalent_Software)

Good luck and enjoy Ubuntu its a great system.

Marious

Edit: Sorry did not read all your post, if he installed it on a different Hard Drive the data should be there, if you can't boot into XP and it still there during startup hit one of your F keys not sure which one it is for your machine, normally something like F8 or 10 and make it go to the Boot Menu this is no GRUB is present.

---

### Post by mceven on 2007-06-04
thank you so much, ek0nomik, for your replies.  I typed the fdisk -l command and received the following output:

> Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7132    57287758+  83  Linux
/dev/hda2            7133        7296     1317330    5  Extended
/dev/hda5            7133        7296     1317298+  82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS



I'm not sure what it means.  I'm guessing the hda1 is the external G drive, and the hda2 and hda5 are the internal drives?  

Rocket2DMn:  I looked in that directory and only found a folder pertaining to the G: drive and two pertaining to the CD/Rom drive.

---

### Post by Lucifiel on 2007-06-04
Also, there's another option: G Parted.(Gnome Parted editor)

Basically, it's under System Tools.

Also, Picasa can also be downloaded. 

You can use Songbird to play your songs. Or Exaile. Or Amarok and so on. Just experiment around.
To install Songbird, use this tutorial from Aiysu's site(Psychocat mreeeoooww)
[http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird)

To install Exaile , use synaptic manager. 


And welcome to the world of Linux! :D

---

### Post by Lucifiel on 2007-06-04
To browse hda1 and hda2, use Nautilus.

Go to /media/hda1 and /media/hda2. 

From what I know it is near-impossible to recover files which have been overwritten on ext3. Not sure about ext3 overwriting Ntfs.

Also, you don't need to dual-boot WinXP 'cos you only use a few limited programs, right? There'll likely be a replacement for them or you can use them in Linux.

---

### Post by Ek0nomik on 2007-06-05
> **mceven said:**
> thank you so much, ek0nomik, for your replies.  I typed the fdisk -l command and received the following output:



I'm not sure what it means.  I'm guessing the hda1 is the external G drive, and the hda2 and hda5 are the internal drives?  

Rocket2DMn:  I looked in that directory and only found a folder pertaining to the G: drive and two pertaining to the CD/Rom drive.

Can you also post the output of:

```
df -h
```

---

### Post by mceven on 2007-06-05
Thanks for the tip:  I did the system monitor accessory and 2 drives (?) show up: 
"/dev/hdal - ext3, total 53.8GB" and "/dev/sdal - ntfs, total 232.9 GB".  

I still don't know what that tells me.  

I'm going to start trying the recovery utilities from the above link.

---

### Post by mceven on 2007-06-05
Sure:

> Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              54G  9.8G   42G  20% /
varrun                220M  108K  220M   1% /var/run
varlock               220M     0  220M   0% /var/lock
procbususb            220M  128K  220M   1% /proc/bus/usb
udev                  220M  128K  220M   1% /dev
devshm                220M     0  220M   0% /dev/shm
lrm                   220M   33M  187M  16% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1             233G   54G  180G  23% /media/LACIE


Sorry if things are misaligned.

---

### Post by Marious on 2007-06-05
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

[COLOR="Lime"]
Device Boot Start End Blocks Id System
/dev/hda1 * 1 7132 57287758+ 83 Linux
/dev/hda2 7133 7296 1317330 5 Extended
/dev/hda5 7133 7296 1317298+ 82 Linux swap / Solaris[/COLOR]

By the looks of it he made the partitions on your main hard drive, HDA1 is your main partition with Linux on it, HDA2 is the rest of your drive and then just the required Swap file. Sorry but it looks like your data might be lost. 

[COLOR="Lime"]Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes[/COLOR]

SDA normally indicates a SCSI or SATA Drive or an external drive. But maybe the others can tell you more.

Device Boot Start End Blocks Id System
/dev/sda1 * 1 30401 244196001 7 HPFS/NTFS

---

### Post by Wake Rider on 2007-06-05
It is a bit late now, but I would suggest a separate computer for your son so he can experiment with Ubuntu without harming your main computer. I was thinking about Linux for a while, but held off until I was able to get an upgrade box so my learning would not cause problems on my laptop or Father's computer. 
I sincerely hope you are able to recover your data.

---

### Post by Marious on 2007-06-05
I hope not to many important files where lost, but never give up on linux its great and it gets better when you really get into it later on after all the hurdles you have to get over. For everyday use its not to terribly hard some things do get a bit harry but for the most part you did the right thing by posting to this forum. 

Marious

---

### Post by mceven on 2007-06-05
By "main hard drive," do you mean what was formerly the c: and d: drives inside the computer (40 GB each)?  Is Ubuntu understanding them as a single drive?

Thanks for the tips re: downloadable applications.  The only reason I wanted to go back to a dual-boot was because I thought I might be able to re-install XP and then magically find our picture files, etc.

---

### Post by Lucifiel on 2007-06-05
Hmmm... I wonder if there are any data recovery utilities for pulling out all overwritten data. I wonder if TestDisk can do the job. Any expert want to comment?

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Marious on 2007-06-05
Yes, and in your case it used the entire hard drive both C and D. During installation unless you tell it how to partition it will just make its own partitions and install Ubuntu, which is what looks like was done in your case. This is the default set up for the system when it is installed on a new hard drive or a hard drive that has previous data, so if he used the default installation then he overwrote windows, trust me I have done it myself before, where I have accidentally overwrote windows.

marious

---

### Post by mceven on 2007-06-05
OK -- facing facts now that I've probably lost this data, I'm trying to install a data recovery program as a last chance effort.  My new problem is that I have no idea how to install programs in Linux.  In Windows, I'd download a program, open it, and then the magical install "wizard" would ask me where I wanted to save the program files, then go ahead and install it.  In Ubuntu, I download a program and get files with strange extensions and I don't know how to install anything.  

Any final tips on this problem would be appreciated, then I can probably cut my losses and get other programs up and running.

Thanks

---

### Post by mceven on 2007-06-05
Never mind:  I just googled my question and got the answers I needed.  Thanks everyone for your help!

---

### Post by Ek0nomik on 2007-06-05
> **mceven said:**
> OK -- facing facts now that I've probably lost this data, I'm trying to install a data recovery program as a last chance effort.  My new problem is that I have no idea how to install programs in Linux.  In Windows, I'd download a program, open it, and then the magical install "wizard" would ask me where I wanted to save the program files, then go ahead and install it.  In Ubuntu, I download a program and get files with strange extensions and I don't know how to install anything.  

Any final tips on this problem would be appreciated, then I can probably cut my losses and get other programs up and running.

Thanks

Although having another user in the Ubuntu community is always great, I will point out that there are great file recovery programs for Windows.

I reformatted my external hard drive (fat32) before and lost all my data.  Lost all my data meaning, I have the whole drive free, and 0 bytes used on the drive.  I installed a program called File Scavenger (I believe it was version 3.1 at the time), and it got almost all of my music back (roughly 200GB).

If you were to do this, you need to make sure you format your hard drive back to NTFS though.  I think you will have much better luck if you do.

/ - / - / - / - /

To install programs with Ubuntu, you have a few options.  You know how you opened that terminal before?  Well, this is your best friend.

Try these out for size:

```
sudo aptitude search *your.program.that.you.want.to.find.or.see.if.it.is.available.in.the.ubuntu.repository*
```

```
sudo aptitude install *your.program.that.you.want.to.install.from.the.ubuntu.repository*
```

You can also go into System>Administration>Synaptic Package Manager

Synaptic is a GUI (Graphical User Interface) front-end for apt.  (Apt is a package (software) manager).  (Notice the apt in aptitude)

You can also compile programs yourself by downloading tar.gz files.  This can seem a bit scary at first, but once you have done it a few times it gets easier.  Search the forum for compiling, there are many threads that will show you how to get started.

Another file you might run into is a .deb file.  A .deb file is a Debian based file (Ubuntu is based off of Debian, another Linux distribution).  Another Linux distributions use different files (.rpm for an example).  A .deb file is very easy to install.  For an example, that Picasa link I sent you to earlier was a .deb file.  All you have to do is download it to your Desktop and double click it and it will install the program and needed library files.

If you have more questions, again, just ask.  :)

---

