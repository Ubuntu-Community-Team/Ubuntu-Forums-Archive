---
title: "Install Ubuntu from FLASH DRIVE ????"
date: 2010-07-11
forum: Apple Hardware Users
---

### Post by 828688 Ben on 2010-07-11
Okay, this may sound totally insane and if this is completely undoable, please tell me.

Anyways, I am going to be install Ubuntu 10.04 LTS on my Power Mac G5. I have a rewritable cd and a 4gb flash drive. My original idea was to burn the iso file to the rewritable cd and then boot my mac from the cd. Well, the burning of the iso, to the rewritable cd worked fine. But, the booting from the cd is were I ran into trouble. 

I inserted the cd, rebooted and booted from the cd. Then the command prompt popped up. I then typed in 
"live-nospalash-powerpc64" and hit enter. Now I have done this a couple times before and in the past, it has successfully booted to the desktop. However, this time it did not. So i took out the cd and I see a big, deep scratch in it. You may say "well if you have no other cd's, why don't you just boot from the 4gb flash drive?". unfortunately my mac does not allow you to boot from flash drives.

So heres my question: can I burn the iso to the flash drive (don't worry, i know how to make it bootable) and then like before, restart my computer (with the cd in the drive and the now bootable flash drive still plugged in) and boot from the cd. Now, instead of typing in "live-nospalash-powerpc64" is there a command i can use to tell the computer to, from this point, continue booting like normal, except instead boot from the files on the flash drive instead of from the cd?

Is there such a command?

Thanks,
Ben

---

### Post by oldfred on 2010-07-12
Can you install grub2 to the USB flash? If so you can just copy the ISO to the USB and edit the grub loopmount command to include your extra parameters.

MultiBoot USB with Grub2 (boot directly from iso files)
Is full script for a few ISOs, I only used some commands to set up Flash drive.
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.

Auto installs a variety of ISOs
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by 828688 Ben on 2010-07-12
Ummmm, oldfred, what you are explaining to me is _way_ above my level of expertise. 

Just so you know (when you are re-explaining your answer for someone less advanced than you) here Is my current situation: 
I have a scratch cd with Ubuntu 10.04 LTS on it. On that cd, all that will load is the original command prompt, and thats it. I have access to _no_ other blank writable cd's. However, I do have access to a 4gb flash drive. My mac will not boot from a flash drive, so here's what I want to do:

Power on computer > hold down "C" key > boot from cd > get into the command line (the black screen with white text) for ubuntu 10.04 LTS > put in command(s) to continue booting ubuntu 10.04 LTS, _except from the flash drive_ > once I get to the desktop, install ubuntu 10.04 LTS on my mac.


Thanks,
Ben

---

### Post by oldfred on 2010-07-12
I think what you are doing is very advanced. Are you at a Ubuntu promt or a grub promt. The Ubuntu promt will not accept "live-nospalash-powerpc64" as those are boot settings normally added to a grub menu line.

Have you tried .
startx
 or
 sudo service gdm start

I know you can chroot into another system but I do not know how to start an installer just how to repair once chrooted into a system.

kansasnoob converted commands to one line with &, you have to edit to have the correct partition:
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by cariboo on 2010-07-12
Grub doesn't work with the ppc architecture, so don't even bother trying. I know there are boot cd's available that will allow you to boot from a usb device, even if the computer isn't capable of doing it, itself. I just had a quick look on google and it seems possible with the ppc too.

---

### Post by 828688 Ben on 2010-07-12
If you say: 
> The Ubuntu promt will not accept "live-nospalash-powerpc64" as those are boot settings normally added to a grub menu line
Then I must be in the grub prompt.


> Have you tried .
startx
or
sudo service gdm start
No, I have not tried either of those commands, but I doubt that they will work because my cd is actually scratched and not allowing my computer to read all the information on it. The farthest that I can make it is to the grub prompt, after that I start getting multiple errors.


> I know you can chroot into another system but I do not know how to start an installer just how to repair once chrooted into a system.

kansasnoob converted commands to one line with &, you have to edit to have the correct partition:
[http://ubuntuforums.org/showpost.php...2&postcount=10](http://ubuntuforums.org/showpost.php...2&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
To tell you the truth, I have no idea what "chroot" is.


Thanks for the help so far,
Ben

---

### Post by 828688 Ben on 2010-07-12
> Grub doesn't work with the ppc architecture, so don't even bother trying. I know there are boot cd's available that will allow you to boot from a usb device, even if the computer isn't capable of doing it, itself. I just had a quick look on google and it seems possible with the ppc too.
Okay, if you could find out how I could do that and explain it to me step by step (and keep it as simple as possible), that would be great!

Thanks,
Ben

---

### Post by sha.goyjo on 2010-07-12
Alright, a lot of confusion is flying around here. Ben, your computer does not use grub. It uses yaboot (Yet Another BOOT loader). This means that usage of grub (or grub 2 commands will be pointless for you.

For those of you wondering about the validity of this claim, ben is rocking a G5, which is a powerpc architecture chip. Yaboot has been for years the primary linux bootloader for powerpc arch's.

As for yaboot commands to boot from an external drive, I'm pretty sure it's possible. If I remember correctly you just have to enter a string for the hardware device and the partition. The difficulty comes in with the fact that you've already burned the one CD you have, which is the device that you want to boot from. Therefore it is impossible to change the yaboot.conf file on that cd to set a quick and easy option for booting from the USB drive.

Another unfortunate fact is that it doesn't seem possible (although [this is currently all I have to support this claim]("http://old.nabble.com/How-to-boot-from-yaboot-%27boot%27-prompt-td6504995.html")) to pass an initrd argument onto yaboot. So I don't know exactly how you'd be able to do this given the limited options provided by yaboot at boot time. I hate to say this, but you might be stuck in the situation of needing to get a new CD-R. I'm sorry for the bad news.

---

### Post by 828688 Ben on 2010-07-12
Okay, I'll purchase another cd. 

Thanks for the help,
Ben

---

### Post by 828688 Ben on 2010-07-12
Great news, I found another blank cd!
I successfully burned Ubuntu 10.04 LTS to the cd and verified it.

Heres my new problem:
As you know by now I am using Mac (Mac OS X 10.5 (Leopard)). Well I don't want to delete Mac off my system. But, when I was originally install mac on my system a left 10 GB of free space for ubuntu. Now, I want to install Ubuntu 10.04 LTS on that 10 GB partition. When I boot from the cd (everything works fine) and when I get to the desktop I click on the icon the install Ubuntu. When I get to the part to where I want to install ubuntu, that 10 GB is not available to me. I think that that is because I have that partition formated as MAC OS Extended (journaled). 

So, how do I delete a secondary mac partition and leave it as free space (meaning not re-formating it)?

Thanks,
Ben

---

### Post by linuxopjemac on 2010-07-12
You have to select manual partition from the installer. Then just delete the HFS partition and make three extra partitions ouf of that. One is the bootstrap (for yaboot), one for your / and one will be swap (take same amount as RAM memory). Then continue installation.

[http://mac.linux.be/content/yaboot](http://mac.linux.be/content/yaboot)

---

### Post by 828688 Ben on 2010-07-12
I got it installed!

Anyone who would like to help me get it running well, please go to this thread: [http://ubuntuforums.org/showthread.php?p=9581399#post9581399](http://ubuntuforums.org/showthread.php?p=9581399#post9581399)

Thanks for the help,   (Ubuntu rocks!)
Ben

---

### Post by sha.goyjo on 2010-07-13
*deleted

---

