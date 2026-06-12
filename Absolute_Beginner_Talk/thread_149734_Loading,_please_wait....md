---
title: "Loading, please wait...?"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by mwoeber on 2006-03-24
I am new to linux and after doing a little research decided to try out ubuntu, I really liked the live cd so I tried to install it.  Everything installs fine, but after I take out the install cd and start to load the packages I see the loading screen with the progress bar and then I am taken to a command type progress screen that says

savedefault
boot
Uncompressing Linux....Ok, booting the kernel.
Loading, please wait...

No matter how long I wait nothing happens, the computer freezes here every time.  I have an aopen XC cube with a 2.0 P4, 1 G RAM, Ati Radeon 9800pro.
I am pretty sure that I made the partitions right.  I even re-downloaded and burnt the iso because I thought maybe it had become corrupt at some point.  Any ideas as to what may  be happening and how I can fix it and get started with my new, Windows free life?  Any help or suggestions will be greatly appreciated, thanks.

Matt

---

### Post by Alpha_toxic on 2006-03-24
This is a strange one. I don't think there is that much you can do to make this particular cd run. Most likely this is due to some of your hardware that Ubuntu can't/don't want ot work with.
If the version that you have been trying to install is Breezy (5.10), I'd suggest trying Dapper (6.06). It's the latest one, but is still in development, so there might be some glitches.
The link for the latest Dapper is here [http://cdimage.ubuntu.com/releases/dapper/flight-5/](http://cdimage.ubuntu.com/releases/dapper/flight-5/). Better try the LiveCD, this way you'll test it without actually installing it. 

If this also doesn't work you can do 2 things: either try another distribution or send a bug report with the exact output that you recieve and your exact hardware (exact model of the mother-board, processor, ram, HDD...). The more info you give, the higher the chance is that the bug gets fixed. I think best thing is to do both (get another distro and send a bug report). And who knows, may be in the next release it will work :)

---

### Post by mwoeber on 2006-03-24
If it is a hardware issue then how is it possible that the live cd runs so well?  It even detects my wireless network card and gets me online.

---

### Post by Alpha_toxic on 2006-03-25
[QUOTE=mwoeber]If it is a hardware issue then how is it possible that the live cd runs so well?  It even detects my wireless network card and gets me online.[/QUOTE]
Sorry, I didn't notice that you've tried the LiveCD.
If it worked then the only place where the problem might be is your HDD. It's the only part that the LiveCD doesn't use. So if you give me more info about how exactly you have partittioned the HDD, is it ATA, SATA, external or whatever else, how many HDDs do you have, are you trying to dual-boot with windows... well everything about your HDD configuration, I might be able to help.

---

### Post by mwoeber on 2006-03-26
I'm using an 80 G SATA internal drive.  The partitions are set up as follows

#1 primary 10 GB (bootable) ext3  /
#3 primary 65 GB  ext3 /home
#2 primary 1.5 GB swap /boot

That is the last partition set up I tried.  I've also tried the ones that ubuntu sets up automatically

I'ts my only HDD and I'm not dual booting.

---

### Post by xXx 0wn3d xXx on 2006-03-26
If the live cd worked then you should try re-burning the ISO, (Possibly redownloading it), burn it at a slower speed and then reinstall. Hope that helps :)

---

### Post by mwoeber on 2006-03-26
[QUOTE=mwoeber].....I even re-downloaded and burnt the iso because I thought maybe it had become corrupt at some point......
Matt[/QUOTE]

yeah, I already tried that ;)

---

### Post by Alpha_toxic on 2006-03-27
There is sth wrong with this line
#2 primary 1.5 GB swap /boot
You can't have your swap mounted as "/boot". It's either not formated as swap or not marked as /boot. Try reinstalling and make sure you format this partition as swap.

---

### Post by mwoeber on 2006-03-29
Ok, my swap is no longer my /boot
I still get the same problem.  It looks like it's back to windows for me.

From what I've read ubuntu is supposed to be the easiest linux to install.  If i can't get this going than it's hopeless.

---

### Post by Mustard on 2006-03-29
[QUOTE=mwoeber]Ok, my swap is no longer my /boot
I still get the same problem.  It looks like it's back to windows for me.

From what I've read ubuntu is supposed to be the easiest linux to install.  If i can't get this going than it's hopeless.[/QUOTE]

Fair enough. :)  Linux is not for everyone.  It does take a bit of patience and a willingness to learn.

---

### Post by trent dillman on 2006-03-29
WAIT!

Did you try passing different options to grub? Like, noapic, noacpi?

---

### Post by Alpha_toxic on 2006-03-29
Just as a side-note:
Ubuntu is NOT the easiest linux distro out there. It's much easier than Gentoo and Arch, but it's not the easiest. Hell, it's not even on [distrowatch's list of distros recommended for beginners]("http://distrowatch.com/search.php?category=Beginners&origin=All&basedon=All&desktop=All&architecture=All&status=Active"). If you really want the easiest one try [PCLinux]("http://www.pclinuxos.com/") or [Xandros]("http://www.xandros.com"), though then you'll miss the actual fun of tweaking it ;)

Back on your porblem (if you haven't really given up):
I don't know how you managed to put both the swap and the /boot on one partition (I tried to, and Ubuntu's installer didn't let me :confused:). Anyway what I think happend is this:
You somehow managed to put the /boot partition in the swap. /boot is where your boot loader will loook for it's configurations and where the image of the kernel is, swap is the "paging file", so obviously they CAN'T be on the same place. Even if now you remove the /boot part from the swap (thus telling Ubuntu that it's not supposed to boot from there), it will still not know where to boot from. I'm not sure if there is another solution, but a clean reinstal. This time, when you come to the partitioning part of the installation, just mark the partition you want to install Ubuntu on as "/", the big partition as "/home" (this is not needed actually, but is a smart move), and format the small one as "swap". If this doesn't work, you are definitely doing sth out of the ordinary (I'm not saying "wrong"). Also note that if the LiveCD worked, it's 99,99% chance the installation will work, too. The only thing that can cause problem is some very "strange" HDD configuration (like external HDDs) and you rs is looking pretty "normal".

---

### Post by mwoeber on 2006-03-29
trent dillman: No, I did not try that.  In fact I have no idea what that means

Alpha_Toxic: I may have just copied that info into the forum wrong.  I have tried to use the automatic partitioning and I've also tried to use the manual partitioning.  Ubuntu only needs 3 partitions right?  The /boot, the swap and the /home?  Shouldn't there be a root partition.  That is one thing that has had me confused.

---

### Post by Alpha_toxic on 2006-03-29
It actually needs only 2 partitions: "/" and swap. The "/home" is roughly the equivalent of "Documents and Setting" in Windows. It's a good thing in general to put it on a separate partition, as this way if you need to format the "/" partition all your files and information are safe on another partition. If you don't specify where the "/home" should be, it's automaticaly created inside "/". "/root" is sth else, and it's also auto-made in "/".

I'm sorry I can't help any more right now, but I got some damn flu and I'll be going to bed now :( . I'll see what I can do tomorow...

---

### Post by NotGrayt on 2006-04-28
I had the same problem, and found somewhere in this forum that after removing the cd to reboot, you need to put the cd back in while the program is loading.  Make sure its in before that screen comes up.  Worked for me.

---

