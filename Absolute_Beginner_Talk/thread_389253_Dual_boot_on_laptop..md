---
title: "Dual boot on laptop."
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by Cokeman on 2007-03-20
Hello, I'm new here & new to Linux. I have used some versions of Linux before on a desktop. So now I have this laptop that came preloaded with Vista. I removed Vista, installed XP Pro. I need linux for modding my cellphone, Hoping I will get use to it enough I can eventually say bye to windows. Any way heres what I have done so far, & why I need some help.

1. Hard drive partitioned, formatted, I installed Xandros (latest) I did this cause I used 3.0 on my desktop & it worked good, having some issues in bash shell with the latest on my laptop.

2. I downloaded the latest 32bit Ubuntu, ran the llive cd & it seems to work, not all hardware is reconized. I don't need everything at the moment.

So now that you know what I've done heres where I need help.

1. I have dual boot now, so how do I remove the current Linux to install Ubuntu? I don't want to have to reinstall windows.

2. Once I get Ubuntu running I have to have access to my Windows files to work with in Linux.

3. All I need for driver is sound, graphics, 10/100 ethernet, keyboard, mouse, the basics. It would be nice if wifi, & memory card reader worked but not an issue if they don't.

So now that I got all that, I was wondering if someone can tell me what is edgy, dapper, that I keep seeing on the forums. Is it something I need for Ubuntu to work.

Thanks for any help you can give & sorry for so many questions, I do want to learn Linux as Windows is just a big pain in the....& no way I will go to Vista.

---

### Post by Zuph on 2007-03-20
Edgy and Dapper are just the code names for the various versions of Ubuntu.

Edgy is 6.10
Dapper is 6.06

Based on my experiences (and this is complete heresy), I've had better luck with laptop hardware using 6.06, but I've been using mostly older machines.  6.10 has newer drivers, software, etc.  Either should work for you, though.

---

### Post by hrp2171 on 2007-03-20
Hi,

To remove the current Linux distribution, just install Ubuntu on the same partition Xandros is on.  Even better, during installation just remove the Xandros partition(s) and tell Ubuntu to use all that free space for itself.

Ubuntu is very nice when dealing with any type of Windows partitions.  Based on my experience at my home computers and a laptop, it always adds an icon or two on the desktop pointing to the Windows partitions.  It's done it whether they were formatted as NTFS or FAT32.  Very nice feature.

I don't know which version of Ubuntu you downloaded, but 6.06 Dapper is the better choice for now until the next LTS(Long Term Support) version comes out.  Which should happen in about a year or so.  In the meantime, there are going to be interim releases like Edgy and the next one Feisty, that are meant for enthusiasts that want to play with the latest and the greatest that Linux has to offer.

---

### Post by mac.ryan on 2007-03-20
> **Cokeman said:**
> 1. I have dual boot now, so how do I remove the current Linux to install Ubuntu? I don't want to have to reinstall windows.

If I understood correctly, you want to keep the same partitioning scheme but get rid of Xandros and install Ubuntu instead. If this is the case, you should simply tell the ubuntu installer to format the partition before to copy ubuntu files on it...

After ubuntu will have finished installing the system, it will be the turn of GRUB (the program allowing double or triple or... boot). I never found myself in your exact situation, but I assume that:
[LIST=1]
[*]If GRUB (or LILO) was on the linux partition (i.e. if the linux partition was the first on the HD) you will have formatted it, so ubuntu will simply reinstall it and you won't have any problems.
[*]If the previous GRUB was on the windows partition, the ubuntu installer might recognise the previous version of GRUB and simply update its menu inserting the option for ubuntu.
[*]If the previous  GRUB was on the windows partition, but ubuntu won't recognise and update it correctly, you will have to edit the menu of GRUB. Besides the command-line options, there is also the possibilty to use GrubEd ([http://ubuntuforums.org/showthread.php?t=228104)](http://ubuntuforums.org/showthread.php?t=228104))[/LIST] > 2. Once I get Ubuntu running I have to have access to my Windows files to work with in Linux.

This is standard possibility in read-only mode. If you want write-mode enabled: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

> 3. All I need for driver is sound, graphics, 10/100 ethernet, keyboard, mouse, the basics. It would be nice if wifi, & memory card reader worked but not an issue if they don't.

Unless you have VERY strange hardware it should be straightforward. You will have to install proprietary graphic card drivers if you want to use 3D accelerated functions, but the system should work fine since after the installation.

> So now that I got all that, I was wondering if someone can tell me what is edgy, dapper, that I keep seeing on the forums. Is it something I need for Ubuntu to work.

As somebody already pointed out they are names of various release. I can't find the article again, but I read somewhere all names are adjective-animal couples. "Edgy Eft" but people use to use only the adjective "Edgy".

---

### Post by RudolfMDLT on 2007-03-20
Hi there,

> **Cokeman said:**
>  I removed Vista, installed XP Pro. 


Just out of curiosity, why?

> 1. I have dual boot now, so how do I remove the current Linux to install Ubuntu? I don't want to have to reinstall windows.

In step 5(could be 4 or 6 :) ), You have the option of manually partitioning your drive, choose this option and then delete anything Xandros. If you haven't already, create an EXTENDED partition and within in this partition pick how you would like to dice up the remainder of your drive. Write down or remember the name of the windows partition/s, ie, /dev/hda1

> 2. Once I get Ubuntu running I have to have access to my Windows files to work with in Linux.

In the install, after you have partitioned your drive, Ubuntu will ask you where you want folders mounted. Click the open dropdown and select /dev/hda1(or where ever windows is on). in the folder box enter "/windows" excluding quotes of course. and click next when done, Ubuntu will do the rest.

note - you will not be able to write to NTFS drives.


> 3. All I need for driver is sound, graphics, 10/100 ethernet, keyboard, mouse, the basics. It would be nice if wifi, & memory card reader worked but not an issue if they don't.

I'm 99% sure we can get everything to work! :)

> So now that I got all that, I was wondering if someone can tell me what is edgy, dapper, that I keep seeing on the forums. Is it something I need for Ubuntu to work.

They are different versions of Ubuntu. Dapper is older but more stable where as Edgy is the latest. I have just installed Edgy in a laptop with 0 difficulties so my best advice would be to try Edgy and if it doesn't work go to dapper!

> Thanks for any help you can give &[COLOR="Blue"] sorry for so many questions[/COLOR], I do want to learn Linux as Windows is just a big pain in the....& no way I will go to Vista

Thats what the forums are for! ask till your fingers fall off! ;)

Cheers,

Rudolf

---

### Post by Cokeman on 2007-03-20
Wow so much help. I had downloaded the Edgy version then as I didn't know what LTS was. 
Sounds like everything is pretty straight forward. I will read through all the links & info to make sure I understand everything.
I don't have to have write access to NTFS partition cause I can use my 2gb memory card as the files will be no bigger than 30mb so that not a problem.
The reason i removed Vista is cause most the programs I have & use daily refused to work (driver issues for the hardware) Example is my cellphones Vista wouldn't recognize them. I also hated the fact I had a laptop with 1gb of memory (-128 for agp) Vista is a memory hog, I didn't see anything in Vista that impressed me. So I got rid of it (after making a restore disc)

Again thanks for all your help, I will give all this a shot & post back with results.

---

### Post by Cokeman on 2007-03-20
Thank You so much. With all the great help it was as easy as 123. I do have a few questions, sure i'll have more later.

1. How do I get Bash Shell with root access?

2. When I installed it made me create user name & password, Did that make me Admin since I'm the only user?

3. Can I merge the items in the bottom panel with the top panel to remove the bottom?

Thanks again for all the great help. Once I start getting use to it I'll see if I can get all hardware to work, it fast thats for sure.

---

### Post by annda on 2007-03-20
1) precede your command with sudo (it will ask you for your password and remember it for a couple of minutes) or create a launcher (right click on the panel or desktop) with the command gksudo gnome-terminal

2) yes

3) right click on the panel, add/delete the items you need. remove the unwanted panel.

---

### Post by mac.ryan on 2007-03-20
> **Cokeman said:**
> 1. How do I get Bash Shell with root access?

Alternatively to the solutions given to you already by other users, you can type from any shell the command

```
sudo -i
```

This will effectively change the user to root@yoursystem.

**Be aware that this is a much more dangerous solution** than typing "sudo" in front of each command (i.e. use a root shell only if you really know what you are doing...).

---

