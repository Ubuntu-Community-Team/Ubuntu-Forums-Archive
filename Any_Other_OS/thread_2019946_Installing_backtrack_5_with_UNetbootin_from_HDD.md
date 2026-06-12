---
title: "Installing backtrack 5 with UNetbootin from HDD"
date: 2012-07-06
forum: Any Other OS
---

### Post by Edenthinker on 2012-07-06
I'm installing BackTrack 5 using UNetbootin based on my windows 7 parition of my HDD. Open BT5 GUI and go to install. At first it would not install because it couldn't unmount /cdrom. So went in Terminal and typed in command sudo umount -l -r -f /cdrom. 

I stopped getting that message. And then remounted right before installation with the command. sudo mount -t fuseblk /dev/sda1 /cdrom

Not longer go the error about not being able to unmount /cdrom now getting an installer crash. 

RuntimeError: Install failed with exit code 1
Traceback (most recent call last):

File "/usr/shre/ubiquity/install.py", line 2566, in <module>
 install.run()
File "/usr/shar/ubiquity/install.py", line 353, in run
 self.copy_all()
File "/usr/share/ubiquity/install.py", line 685, in copy_all
 assert os.path.exists(fs_size), "Missing filesystem.size."
AssertionError: Missing filesystem.size.


Any help much appreciated.

---

### Post by Paddy Landau on 2012-07-07
I think you'd get more luck putting this thread into the [Other OS/Distro Talk forum]("http://ubuntuforums.org/forumdisplay.php?f=401").

---

### Post by matt_symes on 2012-07-07
*Thead moved to ***Other OS/Distro Talk**[]("http://ubuntuforums.org/forumdisplay.php?f=401")

---

### Post by gordintoronto on 2012-07-07
> **Edenthinker said:**
> I'm installing BackTrack 5 using UNetbootin based on my windows 7 parition of my HDD. Open BT5 GUI and go to install. At first it would not install because it couldn't unmount /cdrom....


This doesn't make sense. You are not installing to the CDRom.

Did you boot from the CD? Do you have free space on your hard drive, in order to make a partition?

I can't figure out what you were trying to say, with "UNetbootin based on my windows 7 parition of my HDD."

---

### Post by Edenthinker on 2012-07-07
I'm not booting from my /cdrom. /dev/sda is mounted at /cdrom. 

Also I have one HDD I got it already pratitioned. 60 gigs with windows 7 on it another 60 gigs open and formated for windows and then 20 gigs of free space. I'm using UNentbootin and it is mounted in the windows 7 partition. When I boot up in bios it shows two boot options from that partition being windows 7 and the other unetbootin. I click unetbootin and it boots up BackTrack5. I open the GUI and click install icon... in which Unetbootin which is mounted in my windows 7 partition attempts to install BackTrack 5 into the free partition by reformatting it.

So for now on..... /dev/sda1 has win7 and unetbootin on it... and /dev/sda5 IS THE FREE ONE I'm trying to install BT5 onto.

---

### Post by Paddy Landau on 2012-07-08
I have read your description, and I do not quite understand what you are doing, sorry.

UNetbootin is a program designed to make a bootable USB stick from an ISO.

UNetbootin is *not* designed to install a system onto a hard drive, nor is it designed for a dual boot. That is something that confuses me in your description.

You have [three options]("http://www.backtrack-linux.org/wiki/index.php/Main_Page") to install Backtrack 5 (which, incidentally, are the same three options for most popular Linux distros including Ubuntu):

[LIST=1]
[*][Install Backtrack 5 to a USB]("http://www.backtrack-linux.org/wiki/index.php/USB_Installs"). Provided you choose to have *persistence*, this means you can run it directly from the USB, and therefore it is portable between computers.
[*][Install Backtrack 5 into a virtual machine]("http://www.backtrack-linux.org/wiki/index.php/VirtualBox_Install"), e.g. [VirtualBox]("https://www.virtualbox.org/") (in your case, running from Windows). If you have sufficient RAM, this might be the best option for you if you are intending only to test Backtrack 5.
[*][Install Backtrack 5 onto your hard drive]("http://www.backtrack-linux.org/wiki/index.php/Hard_Drive_Installs"), in your case [dual-booting with Windows]("http://www.backtrack-linux.org/wiki/index.php/Dual_Boot_BackTrack_And_Windows7").
[/LIST]
You have said that you want option 3. For this, the typical method is either to burn the installer to CD or to install it to USB (see option 1, persistence not required). Then, boot from the CD or USB, and run the installer [according to the instructions]("http://www.backtrack-linux.org/wiki/index.php/Dual_Boot_BackTrack_And_Windows7") on Backtrack 5's website to install it to your hard drive.

Oh yes, one more thing. It is unusual and not recommended to mount /dev/sda as /cdrom.

I hope that helps.

---

### Post by Edenthinker on 2012-07-08
> **Paddy Landau said:**
> I have read your description, and I do not quite understand what you are doing, sorry.

UNetbootin is a program designed to make a bootable USB stick from an ISO.

UNetbootin is *not* designed to install a system onto a hard drive, nor is it designed for a dual boot. That is something that confuses me in your description.

You have [three options]("http://www.backtrack-linux.org/wiki/index.php/Main_Page") to install Backtrack 5 (which, incidentally, are the same three options for most popular Linux distros including Ubuntu):

[LIST=1]
[*][Install Backtrack 5 to a USB]("http://www.backtrack-linux.org/wiki/index.php/USB_Installs"). Provided you choose to have *persistence*, this means you can run it directly from the USB, and therefore it is portable between computers.
[*][Install Backtrack 5 into a virtual machine]("http://www.backtrack-linux.org/wiki/index.php/VirtualBox_Install"), e.g. [VirtualBox]("https://www.virtualbox.org/") (in your case, running from Windows). If you have sufficient RAM, this might be the best option for you if you are intending only to test Backtrack 5.
[*][Install Backtrack 5 onto your hard drive]("http://www.backtrack-linux.org/wiki/index.php/Hard_Drive_Installs"), in your case [dual-booting with Windows]("http://www.backtrack-linux.org/wiki/index.php/Dual_Boot_BackTrack_And_Windows7").
[/LIST]
You have said that you want option 3. For this, the typical method is either to burn the installer to CD or to install it to USB (see option 1, persistence not required). Then, boot from the CD or USB, and run the installer [according to the instructions]("http://www.backtrack-linux.org/wiki/index.php/Dual_Boot_BackTrack_And_Windows7") on Backtrack 5's website to install it to your hard drive.

Oh yes, one more thing. It is unusual and not recommended to mount /dev/sda as /cdrom.

I hope that helps. 

UNetbootin has a "Frugal Install" option: UNetbootin can create a bootable Live USB drive, or it can make a "frugal install" on your local hard disk if you don't have a USB drive. ([http://unetbootin.sourceforge.net/#install](http://unetbootin.sourceforge.net/#install))


I didn't mount /dev/sda as /cdrom the computer came that way (I think, I only ran into it saying that during this installer.) Also I'm not the only one that used the "Frugal Install" that ran into the same error saying it can not resize or format the partition because it cant unmount /cdrom and that /dev/sda was mounted to /cdrom. But I learned from them to fix the problem is that when you are re-sizing partition and formatting to put this code ( Sudo umount -l -r -f /cdrom ) into terminal and then when you are done partitioning and formatting to remount it. For the install. 

They do that because... since im using the "frugal install" which is based on my local HDD the installer in BT5 can't unmount it because UNetbootin which is hosting BT5 is hosting it on the /dev/sda as /cdrom. UNetbootin makes the mount BUSY. But i was told if you sudo umount /cdrom you can work with the partitions and then remount it and install from the local HDD. Its worked.... half way. I was able to resize and format the partitions but I was not able to install BT5 because of the error message posted in my first post. This leads me to believe that I have not correctly mounted /cdrom back because it says missing files. But I did the Man 8 Mount in the terminal and read how to properly mount something and I did it and terminal seemed to accept that code. And the installer acted as if /cdrom was mounted... (by telling me I couldn't resize partitions "something it only did when /cdrom was mounted.")but even that run the installer in BT5 gave the same error I posted in my original post. Since then the installer acts as if /cdrom not mounted.... ( allowing me to resize partitions.) and still gives the same error. Now i'm afraid to reboot my computer to explore other options of getting it on my computer, because... im thinking if /dev/sda is mounted to /cdrom and win7 is in /dev/sda and I unmounted /cdrom and my problem seems to be telling me that /cdrom (THUS win7) is unmounted won't when I reboot /cdrom still be unmounted (if it was when i shut down) and wont that inhibit me from booting up from anything inside that mount?

Again I really appreciate the time and effort I know this is not easy or desirable.

---

### Post by Paddy Landau on 2012-07-08
> **Edenthinker said:**
> UNetbootin has a "Frugal Install" option: UNetbootin can create a bootable Live USB drive, or it can make a "frugal install" on your local hard disk if you don't have a USB drive. ([http://unetbootin.sourceforge.net/#install](http://unetbootin.sourceforge.net/#install))
I learn something every day! Sorry for my mistake and thank you for the correction.

You have 20Gb on which to install Linux. That is more than enough for Ubuntu. I don't see Backtrack 5's system requirements, but [according to its forum]("http://www.backtrack-linux.org/forums/showthread.php?t=48473"), it is based on Ubuntu and therefore 20Gb should be more than enough for it.

Therefore, I would not use UNetbootin for a frugal installation. I would instead burn the Backtrack 5 ISO to a CD (I am assuming that you don't have a USB) and install from the CD onto your hard drive.

When you install Ubuntu, it automatically creates the boot and detects Windows, so it would automatically repair a broken bootloader. I have never used Backtrack 5, but again being based on Ubuntu I would imagine it does the same thing.

If you are worried that your bootloader is messed up, and you want to fix it before doing anything else, download and burn a CD of [EasyBCD]("http://download.cnet.com/EasyBCD/3000-2094_4-10556865.html?tag=mncol;1") (free to try) and fix your Windows bootloader.

I cannot comment on /dev/sda being mounted as /cdrom, because that is too weird for my understanding :redface:. Your /dev/sda has several partitions, whereas AFAIK a CD has none. To my understanding, they are not mappable (although you could mount an ISO as a CD).

---

### Post by Edenthinker on 2012-07-08
> **Paddy Landau said:**
> I learn something every day! Sorry for my mistake and thank you for the correction.

You have 20Gb on which to install Linux. That is more than enough for Ubuntu. I don't see Backtrack 5's system requirements, but [according to its forum]("http://www.backtrack-linux.org/forums/showthread.php?t=48473"), it is based on Ubuntu and therefore 20Gb should be more than enough for it.

Therefore, I would not use UNetbootin for a frugal installation. I would instead burn the Backtrack 5 ISO to a CD (I am assuming that you don't have a USB) and install from the CD onto your hard drive.

When you install Ubuntu, it automatically creates the boot and detects Windows, so it would automatically repair a broken bootloader. I have never used Backtrack 5, but again being based on Ubuntu I would imagine it does the same thing.

If you are worried that your bootloader is messed up, and you want to fix it before doing anything else, download and burn a CD of [EasyBCD]("http://download.cnet.com/EasyBCD/3000-2094_4-10556865.html?tag=mncol;1") (free to try) and fix your Windows bootloader.

I cannot comment on /dev/sda being mounted as /cdrom, because that is too weird for my understanding :redface:. Your /dev/sda has several partitions, whereas AFAIK a CD has none. To my understanding, they are not mappable (although you could mount an ISO as a CD).

Yeah I probably should just do the CD thing... Just don't have a burner so I should just go buy a USB drive.... just dont want to. lol  

I may have to use a whole other computer for this. Because i think I ruined win7 on my computer. Because after I gave terminal the sudo umount -l -r -f /cdrom command the ubuntu installer no longer recognized the win7 bootloader... which I'm fine with... because there are no important things on the Win7 partition other then Win7. The only problem is time because I have no avail computer to create a live usb or a CD. Even if I bought a USB I don't think I would be able to make it live with my computer because I dont think it would boot up to win7 considering the installation can no longer recognized Win7 bootloader. lol Oh the joys...  Thanks for your help. 

Sincerely,
 a guy trying to rid himself of the shackles of windows on a budget

---

### Post by Paddy Landau on 2012-07-08
> **Edenthinker said:**
> Just don't have a burner so I should just go buy a USB drive...
Well, you don't need a whole USB drive. A cheap USB stick would do as well. I recommend 2Gb if you just want it for the installer, and 8Gb or more if you want persistence to use as a mobile OS.

> **Edenthinker said:**
> ... i think I ruined win7 on my computer.
Are you no longer able to boot Windows? If that's the case, purchase a cheap CD, visit a friend with a CD burner (or your local library if it has one), and burn EasyBCD. Boot from that CD on your computer to repair the bootloader.

If you are absolutely certain that you no longer want Windows, you can do the same but with either Ubuntu or Backtrack 5 instead of EasyBCD.

EDIT: Or do Backtrack 5 anyway, install it, and let it automatically detect Windows and let you dual-boot.

---

### Post by Edenthinker on 2012-07-08
> **Paddy Landau said:**
> Well, you don't need a whole USB drive. A cheap USB stick would do as well. I recommend 2Gb if you just want it for the installer, and 8Gb or more if you want persistence to use as a mobile OS.


Are you no longer able to boot Windows? If that's the case, purchase a cheap CD, visit a friend with a CD burner (or your local library if it has one), and burn EasyBCD. Boot from that CD on your computer to repair the bootloader.

If you are absolutely certain that you no longer want Windows, you can do the same but with either Ubuntu or Backtrack 5 instead of EasyBCD.

EDIT: Or do Backtrack 5 anyway, install it, and let it automatically detect Windows and let you dual-boot.
Yeah I just found a computer with a burner in it. So I'm going to burn the ISO to the CD and boot from the CD and install from there. It would be nice to have a persistence to use as a mobile OS but I think I will want to use my phone as the USB storage device. And I will just figure that out separately. Thanks for the help. 

I love this community, so helpful. I swear the attributes displayed in the online open source community could benefit the whole world! Have an awesome day.

---

### Post by Paddy Landau on 2012-07-08
> **Edenthinker said:**
> It would be nice to have a persistence to use as a mobile OS...
In that case, you'd want a USB drive. It is so much faster than running from a USB stick!

> **Edenthinker said:**
> I love this community, so helpful. I swear the attributes displayed in the online open source community could benefit the whole world! Have an awesome day.
I love the Ubuntu Forums. The moderators have managed to keep the tone here friendly, polite and helpful.

---

### Post by Cheesemill on 2012-07-08
Bear in mind you either need to burn to DVD or use an 4GB or more USB stick.

The BackTrack 5 R2 ISO file is 2.8GB

---

### Post by MDCCLXXVI on 2012-07-08
Check out. [http://www.backtrack-linux.org/forums/forum.php](http://www.backtrack-linux.org/forums/forum.php)
For answers.

---

### Post by GreatDanton on 2012-07-08
And the system requirements are the same as they are for Ubuntu 10.04.

Good luck with your installation. I really like Backtrack 5R2.

---

