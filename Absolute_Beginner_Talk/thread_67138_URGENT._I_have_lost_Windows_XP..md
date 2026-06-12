---
title: "URGENT. I have lost Windows XP."
date: 2005-09-19
forum: Absolute Beginner Talk
---

### Post by Lukelabern on 2005-09-19
I **do**  have a back up of Windows XP Pro, but I want to use that as a literal last resort, as I still have important files on my Windows account since I backed up.

Yesterday, I tried the Live edition of Ubuntu (latest release) and loved it; so I decided to go for real. I did.

I set up a dual partition, allocating 10GB of free space to Ubuntu, and I am sure that is correct. Everything went smoothly...Until I logged on.

Firstly, it did not recognise my modem. So, I rebooted, but I didn't see my Windows OS. (I have tried to get to it through the GRUB menu, as seen in the last picture here: [http://www3.telus.net/linux4u/ubuntu3.html](http://www3.telus.net/linux4u/ubuntu3.html) )

But Windows is not there. So I went back into to Ubuntu, which opens by default now, if I don't press the ESC key at a certain time. I was greeted with "NETWORK ERROR: Ubuntu internet address not found. Adding Ubuntu to etc/host may fix this problem. Try again/Log in anyway"

I put in ubuntu as my network when I installed, by the way.

I pressed Try again, but nothing happened. So I press log in anyway. Only now, when I choose "disks" or "boot" from the actions on the top menu, nothing happens; nothing loads.

I am not even on my own computer, and I fear I may have to reinstall Windows XP which is really bad for me.

Please post any replies A.S.A.P. (also, I only can boot with GRUB, nothing else.)

And I could try and reinstall Ubuntu, if that's possible to help me save my Windows. Lastly, is there anyway to UNinstall Ubuntu?

Thanks, Luke.

---

### Post by UbuWu on 2005-09-19
Whatever you do, don't panic  ;-) To get into windows do the following: 

- In ubuntu open a terminal (applications -> system tools -> terminal). 
- From there type 'sudo gedit /boot/grub/menu.lst'. 
- In the file you will find a commented out (with a # in front of ebery line) entry for windows. Just uncomment this (remove the #'s) and save. 
- Now when you reboot, windows should be in the grub menu.

---

### Post by davmac on 2005-09-19
My guess is that windows is still there, but there was a problem with the installation of grub.

Try booting into Linux, and starting a terminal (applications -> accessories -> terminal) and typing (without the quotes);

"sudo cp /boot/grub/menu.lst /boot/grub/menu.backup"
"sudo gedit /boot/grub/menu.lst"

This should show you the configuration file for grub.

Somewhere in there will be the relevant entry for windows, possibly commented out with # at the start of the line. Perhaps something like;

# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1

Select this text and copy it to the bottom of the file, and then uncomment it by removing the #'s

Save it and reboot and hopefully you'll see windows as one of the available selections.

If you want to uninstall ubuntu you just need to delete the new partitions you've created and rectreate them as something else. There are plenty of tools around for doing this. My favourites are Knoppix and Ultimate Boot CD (you'll find them from Google).

Hope this helps,

Dave Mac

---

### Post by Mr_J_ on 2005-09-19
Google for R.I.P.
It's a live cd recovery linux!

---

### Post by Lukelabern on 2005-09-19
Okay; there's definetly a problem. I did what I was supposed to in the first reply, but I couldn't get past step one.

I typed "sudo gedit /boot/grub/menu.lst" but it replied "sudo: unable to lookup ubuntu via gethostbyname()"

I tried the advice in the second reply but got the same error, please help.

What now!?!?! I AM starting to panic.

Even newer problem: I can open the file "grub/menu.lst", but it is read only. How can I find an editable version? And are there any articles on this subject?

---

### Post by aysiu on 2005-09-19
Have you tried [this](http://ubuntuforums.org/showthread.php?t=24113)? It should work as long as you have the live CD and are able to boot from it.

---

### Post by Lukelabern on 2005-09-19
I no longer have the live CD, and I cannot burn any .isos on this laptop that I am borrowing now; nor from anywhere else.

Is there any way to, say, boot windows from somewhere other than ubuntu, like bios? REALLY need help.

---

### Post by aysiu on 2005-09-19
Are you able to boot into Ubuntu? Is the only problem that you

1. can't get into Windows
2. need Windows files

?

If that's the case, I'd mount the Windows drive and copy somewhere the files you need and then just use your Windows XP installer disc to wipe the whole hard drive clean again.

The instructions for mounting the Windows partition are here:

[http://www.frankandjacq.com/ubuntuguide/5.04/#mountunmountntfs](http://www.frankandjacq.com/ubuntuguide/5.04/#mountunmountntfs)

Do you have some place you could safely put those files (a USB drive or a CD)?

---

### Post by Lukelabern on 2005-09-19
I can't even use the terminal to do or run anything, anyway. I just want to get onto my Windows OS.

I do, however, have the full ubuntu installer on a CD; is there any way I can use that to un or reinstall ubuntu? Anything to get me onto Windows.

---

### Post by aysiu on 2005-09-19
[QUOTE=Lukelabern]I can't even use the terminal to do or run anything, anyway. I just want to get onto my Windows OS.[/quote] How did you do this, then?
[i]
I typed "sudo gedit /boot/grub/menu.lst" but it replied "sudo: unable to lookup ubuntu via gethostbyname()"[/i]

> 
I do, however, have the full ubuntu installer on a CD; is there any way I can use that to un or reinstall ubuntu? Anything to get me onto Windows. Yes, you could use it to reinstall Ubuntu. Considering how the first install went, it may not be any better, but it's worth a shot. As long as you pick the correct partitions and install Grub to the MBR, it's worth a shot.

Can I ask how you're accessing the internet now? Is it from another computer? Any chance you could download an ISO of [Knoppix](http://www.knopper.net/knoppix/index-en.html) and burn it from that other computer? Ubuntu Live can recover Windows stuff, but Knoppix is really a much better recovery CD.

---

### Post by Xian on 2005-09-19
[QUOTE=Lukelabern]Even newer problem: I can open the file "grub/menu.lst", but it is read only. How can I find an editable version? And are there any articles on this subject?[/QUOTE]
From the initial boot menu select the recovery mode option and that will drop you into a shell prompt. At that point you will have admin priviledges. Then you only need to edit the /grub/menu.lst file via the command line.

```
# nano -w /boot/grub/menu.lst
```
Make your edits then do a Ctrl+x on the keyboard to save changes.
Press the 'y' key to confirm.
Hit the enter key.

---

### Post by Lukelabern on 2005-09-19
I can OPEN the terminal, but anything I type, followed by the enter key returns that error message. 

How do I reinstall Ubuntu, then, I can try that.

I am on a laptop, using my asdl modem to get onto the internet. It is not mine, and I only have it for tonight to fix this. I cannot get files to or from MY pc, as it runs Ubuntu and seemingly not windows.

New update: I followed the advice in the post before this, and got into the file. I then followed the steps from the first reply, and when I rebooted and selected "Windows 95/98/NT/200", I got this error message: 

root (hd0,0)
 Filesystem type unknown, partition typr 0x83
makeactive
chainloader +1

Maybe I put something wrong: wrong number of spaces; the fact I'm using xp?

---

### Post by Xian on 2005-09-19
[QUOTE=Lukelabern]I can OPEN the terminal, but anything I type, followed by the enter key returns that error message.[/QUOTE]
This is a problem with your /etc/hosts file.
You need to change the first line to read like what is below.
Substitute what is in the " " with your actual machine name.

```
127.0.0.1 localhost "hostname of your machine"
```

---

### Post by Lukelabern on 2005-09-19
How do I reinstall?

---

### Post by aysiu on 2005-09-19
[QUOTE=Lukelabern]
How do I reinstall Ubuntu, then, I can try that.[/QUOTE] Put in the install disk and boot from it. Then press enter to start the installation process. Select your language and go through all the "obvious" steps.

At a certain point, you'll be asked whether you want to erase the entire disk or manually edit the partition table ([click here for what this looks like](http://www3.telus.net/linux4u/00002.jpg)). Make sure you **manually edit the partition table**.

Select your Windows drive (probably /dev/hda1) as mount point **/windows** and your previous Ubuntu partition as mount point **/**. Make sure to make the Ubuntu partition to be formatted as ext3.

Then, continue through the rest of the process. At a certain point, it will say (or *should* say that it recognizes Windows XP as another operating system. Then it will ask you if you want to install Grub to the MBR. Say **yes**, but also make a note about whether it says it recognized XP or not.

Then, reboot. It should work.

---

### Post by Lukelabern on 2005-09-19
How do I "boot" from the disk; usually it just skips straight to Ubuntu and shows the disc's files.

---

### Post by aysiu on 2005-09-19
[QUOTE=Lukelabern]How do I "boot" from the disk; usually it just skips straight to Ubuntu and shows the disc's files.[/QUOTE] You're going to have to set up the BIOS to boot from CD. Depending on what model of computer you have it could be any number of keys that get into the BIOS settings--Delete, F1, F12, Esc.

---

### Post by Lukelabern on 2005-09-19
I have booted from the disc, but now I receive this error "Network autoconfiguration failed".

---

### Post by aysiu on 2005-09-19
[QUOTE=Lukelabern]I have booted from the disc, but now I receive this error "Network autoconfiguration failed".[/QUOTE] Well, something's seriously wrong. I know that's no consolation to you, but it's true. Either you have some kind of hardware failure or the Ubuntu installer CD you have is a bum CD (somehow got corrupted either during download or burning). I don't know what you should do. Anyone have ideas?

---

### Post by Lukelabern on 2005-09-19
Well, I chose "skip for now" and continued. I have set up /windows for my windows xp, and / for the old ubuntu, like you said. It is now installing the base system.

---

### Post by Xian on 2005-09-19
[QUOTE=Lukelabern]I have booted from the disc, but now I receive this error "Network autoconfiguration failed".[/QUOTE]
Select the "Go Back" option and it will drop you to the installation menu.
Now choose to configure the network again from the list of steps.

It often fails on the first attempt on my box.

---

### Post by Lukelabern on 2005-09-19
I re-tried the network autoconfigure but it failed.

Right, I want out. I want to dump Linux and just run Windows XP. Do I have to reboot it or is there ANYWAY to go back to it?

---

### Post by Xian on 2005-09-19
If you have or know someone with an XP install disk you can repair the MBR.
Then after you boot into Windows just delete the Linux partition.

Boot from the Windows XP CD, press the key "R" in the setup in order to start the restoration console. Select your Windows XP installation from the list, and enter the administrator password. Enter the command "FIXMBR" at the input prompt and confirm the next question with "y". Finally, use "exit" to restore the computer.

---

### Post by Lukelabern on 2005-09-19
I have the disc. So I **have** to restore Windows to use it again? All I want to do is use Windows! Can you explain in more detail? I'm a little confused.

---

### Post by Xian on 2005-09-19
[QUOTE=Lukelabern]I have the disc. So I **have** to restore Windows to use it again? All I want to do is use Windows! Can you explain in more detail? I'm a little confused.[/QUOTE]
No, you are only resetting the MBR (which controls the booting of Windows) back to the way it was before you ever installed Linux. Just follow the directions below and ask back with any questions. I can't think of any way to make the instructions more clear. If you get stuck just let us know.

*Boot from the Windows XP CD, press the key "R" in the setup in order to start the restoration console. Select your Windows XP installation from the list, and enter the administrator password. Enter the command "FIXMBR" at the input prompt and confirm the next question with "y". Finally, use "exit" to restore the computer (meaning this just ends the MBR restore session).*

---

### Post by aysiu on 2005-09-19
Just state it a different way from Xian, what you want to do with the Windows installation disc is restore the boot record to Windows ownership. You're not restoring Windows itself.

---

### Post by Lukelabern on 2005-09-19
I booted from the disc, and got this: The following list shows the existing partitions and unpartitioned space on this computer. It then lists my three partitions, inckuding the main one, 190GB, where my Windows OS is supposed to be.

What's gone wrong?

---

### Post by aysiu on 2005-09-19
[QUOTE=Lukelabern]I booted from the disc, and got this: The following list shows the existing partitions and unpartitioned space on this computer. It then lists my three partitions, inckuding the main one, 190GB, where my Windows OS is supposed to be.

What's gone wrong?[/QUOTE] I don't know what that means, but did you check out [Microsoft's docuntation on fixing the MBR](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp)?

---

### Post by cbudden on 2005-09-19
[QUOTE=aysiu]I don't know what that means, but did you check out [Microsoft's docuntation on fixing the MBR](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp)?[/QUOTE]
 If you boot to the windows xp cd, select the recovery option.  Press 1 (probably) then enter the administrator password for windows.  then type fixmbr and then y  Then restart the laptop.
You can also do this with a windows 98 cd rom.  Boot to the cd, select boot from cd, select start computer with cd rom support.  When the prompt comes up type fdisk /mbr  Then restart.

---

### Post by Mr_J_ on 2005-09-20
not to sound stupid...
but, and I might not be getting this...

This all sounds like the windows partition is mistakenly addressed.

This hapened to me in another distro. It was lilo, and it was a weird distro, but the same idea stands!

What may have been is that Windows, in HDA1 partition1 is just not correctly addressed in the grub file... Sorta HDA1 and no partition choosen!

Don't know if this works on Ubuntu, but go Terminal and writte "Fdisk -l"; which should show you info on your choosen disk. **eg: fdisk -l hda1**

I am just a noobie, so this is wildly guessing... Does sound simple!

Sorta open SuperUser, or Root terminal should be an option somewhere in there!
Not on Ubuntu now... So I can't make sure!

Not totaly sure, but you could try "Su", **S**ubstitute **U**ser...
With no choice it goes to Root and all you have to do is input your password.

Have you considered this being a faulty driver, that is creeping in there, confusing things!

To set hostname... You use **hostame** <name>. Not that I believe it matters too much!


To get the files from the HDD just buy a external drive kit!
Should be 20$ up, mine was 18€ and it was only for a 3'5'' Harddrive, there are other for a laptop HardDrive. Not going to promise this is easy to find tho!

Mine was a bit hard to find!
You transform a HDD into a really big pen drive! you get the files from any computer with a USB socket...

---

### Post by Irony on 2005-09-20
As Xian suggests to restore the XP Bootloader (which will simply overwrite the GRUB bootloader);

*Boot from XP installation disc > press any key on prompt to boot from CD > after some time (10 minutes or so) options appear, press the R option for recovery console > press 1 to select Windows > admin password, enter if no password > at the command prompt type fixmbr > warning given, hit y for yes, hit enter > at prompt type exit > eject disc*

You should then be able to boot as you did before installing ubuntu. You can then delete the ubuntu partition from Windows by going;

*Start > Programs > Accessories > Disk Manager > Disk Management*

I think that is the order, I'm in ubuntu at the moment so can't remember the exact path. When you find the diagram of the partitions right click on the partition and click delete. Don't worry about deleting the C partition accidently as it won't let you.

---

### Post by David Marrs on 2005-09-20
This is an area of the installation procedure that could be made considerably easier, imo. I'm always tripping up over where to write the mbr and almost made the mistake (again) of writing the grub MBR to the linux partition and not the windows partition when installing hoary.

I think I'm right in saying that the active partition has to be the one that Windows is installed on in order for Ubuntu to dual boot correctly.

Incase you still don't understand, Lukelabern, here's yet another re-explanation of what's happened:

Your Windows installation is still present and is still working fine, but the computer doesn't know where to find it because the program that shows it where to find windows (the master boot record) is now pointing to Linux instead.

What should have happened is that, when the Ubuntu installer replaced the MBR with its own, it should have simply added its own signpost to Linux next to the one pointing to Windows and then you the user could have told the computer whether you want to visit Windows or Linux. Unfortunately, what happened instead is that the Ubuntu installer didn't see the Windows installation and so didn't think to include it as an option in the new master boot record.

---

### Post by davmac on 2005-09-21
<please ignore this one> Replied to the wrong thread and can't work out how to delete it!

Dave Mac

---

### Post by David Marrs on 2005-09-21
btw, congratulations on losing Windows XP. Many of us have been trying to work out how to do this for years now! :)

---

### Post by aysiu on 2005-09-21
[QUOTE=David Marrs]btw, congratulations on losing Windows XP. Many of us have been trying to work out how to do this for years now! :)[/QUOTE] I don't know how appropriate that comment is, in light of the OP's panic.

---

