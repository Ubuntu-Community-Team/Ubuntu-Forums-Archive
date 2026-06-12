---
title: "Still cant dual boot XP"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by eldar on 2007-04-24
Well I reinstalled XP. It worked fine. I then installed 7.04 and did not modify partitions and just did the guided using the largest continuous free space. SO nothing special.  Restarted and once again, I cant boot into xp but ubuntu works fine.

There has to be something missing, somehting I am not doing. In the grub menu, do I need to edit the xp boot line? I mean, this is getting really old and I need xp as I there are programs I must have and they do not work on ubuntu. SO ubuntu would be the one to go if I cant get this working. I mean I have a 200GB drive, more than enough space. 

Maybe I just need step by step instructions on this. There has to be something I am missing. I am running a bit of an old pc, it is 4 years old but still has the ram and everything else needed for hardware.  I have a gigabyte board with dual bios. I just dont see that as being an issue. 

Someone please give me a step by step hand as I dont want to throw ubuntu away just cause of this. I like how it works and would like to use it for most things if possible.:(

---

### Post by tchoklat on 2007-04-24
do you get a boot menu offering options to boot into?

---

### Post by eldar on 2007-04-24
The grub does come up. I get ubuntu then the ubuntu recovery(or something like that) then the ubuntu memtest. Then it says other operating systems and then lists windows XP.

---

### Post by Wee Nyaff on 2007-04-24
That's what mine does and I select the Windows choice hit enter and it loads Windows.

---

### Post by eldar on 2007-04-24
Ok here is a question. I am using XP HOME. Are you people using that or professional?

---

### Post by zvacet on 2007-04-25
Never mmind wich version you use.If it is on the list just hit enter and you will boot in windows.

---

### Post by eldar on 2007-04-25
I wish it was working that easy.
 How EXACTLY are you people installing it?
I install windows first and set its partition during the install.
I reboot and it works fine.
Then I put in the live cd and install on largest continuous space. Reboot and BAM cant boot windows. In ANY mode.
Ubuntu works though.

---

### Post by machoo02 on 2007-04-25
What happens when you select Windows from the Grub menu? Does it stall or tank in any way?  Please be a little more specific.

---

### Post by eldar on 2007-04-25
Well in normal mode, it brings up the xp with the loading bar which makes it about half way then blue screens with no particular error just saying to check for viruses and run chkdsk /f
In any safemode, it loads the drivers then blue screens with the same screen.

Keep in mind, it works fine before I load ubuntu. I have not tried it but I bet it will do this after any partitions are added but I may be wrong.

---

### Post by Emerzen on 2007-04-25
If you're comfortable reinstalling Ubuntu GRUB, you could try this:

Boot from XP cd into recovery console-> at command prompt (after logging in & if you haven't set an Admin password in XP just hit enter) type "fixmbr" w/o the quotes.  That will reinstall Windows bootloader overwriting GRUB.  You should then reboot w/o cd and it should go directly into XP.  If the XP bootloader can't boot the system, you could try rescuing the whole XP install from the XP cd, then reinstall GRUB.

---

### Post by eldar on 2007-04-25
I can try that. I tried it once before but the circumstances were different. After that though, what method do you recommend for reinstalling the grub?

---

### Post by eldar on 2007-04-25
Well darn it. Time to call it a night. have to work tomorrow morning. Post any ideas any of you can come up with and I can try them tomorrow night. Thanks guys, for all the fast responses. :guitar:

---

### Post by jdonat on 2007-04-25
> **eldar said:**
> Well I reinstalled XP. It worked fine. I then installed 7.04 and did not modify partitions and just did the guided using the largest continuous free space. SO nothing special.  Restarted and once again, I cant boot into xp but ubuntu works fine.

There has to be something missing, somehting I am not doing. In the grub menu, do I need to edit the xp boot line? I mean, this is getting really old and I need xp as I there are programs I must have and they do not work on ubuntu. SO ubuntu would be the one to go if I cant get this working. I mean I have a 200GB drive, more than enough space. 

Maybe I just need step by step instructions on this. There has to be something I am missing. I am running a bit of an old pc, it is 4 years old but still has the ram and everything else needed for hardware.  I have a gigabyte board with dual bios. I just dont see that as being an issue. 

Someone please give me a step by step hand as I dont want to throw ubuntu away just cause of this. I like how it works and would like to use it for most things if possible.:(



ok, step by step, from the start: 
boot off the  ubuntu live cd , to to the system menu>administration>Partition Editor.  

delete all the partitions you have on your hard drive. 

first make a partition for your WinXP installation, make it at least 10 GB.

at this point you could go two ways:

a) reboot and install XP on just that partition , after that is all finished, again boot into the ubuntu live cd, and choose to install into the biggest unpartitioned space, it should slice it up into the necessary partitions automatically.

***you can make the XP partition bigger if you want, it's up to you.

-OR-

b) stay in the live cd and manually make a partition for your ubuntu root "/" partition, also at least 10GB , then make a "swap" partition, make it twice whatever ram you have .  then make a "home" partition for ubuntu, make it as big as you want. 

the ubuntu installation should find the XP installation and add an entry in the grub menu for it. 



after all that you should be good to go .

---

### Post by flyboy284 on 2007-04-25
I know it will take you in a different direction, but have you thought about trying Wubi. I tried it and it worked flawlessly for me.  I had the drivers install, playing, music, videos, and even had XGL and Beryl running. It's only a beta but installs and uninstalls from windows and adds a boot option to the windows boot loader. I liked it and never had a problem with it.

---

### Post by Emerzen on 2007-04-25
[Here's a link to a thread that explains how to restore GRUB]("http://ubuntuforums.org/showthread.php?t=224351")

You just have to follow the post until the part where the text turns red and mentions an edit.  I'm assuming you did the default install and put GRUB on the MBR.  If you didn't, the rest of the thread is relevant.

---

### Post by confused57 on 2007-04-25
> **eldar said:**
> Well in normal mode, it brings up the xp with the loading bar which makes it about half way then blue screens with no particular error just saying to check for viruses and run chkdsk /f
In any safemode, it loads the drivers then blue screens with the same screen.

Keep in mind, it works fine before I load ubuntu. I have not tried it but I bet it will do this after any partitions are added but I may be wrong.

You might try editing your Window's entry in your /boot/grub/menu.lst, and use "rootnoverify", instead of  "root" and you can try removing the line with savedefault.

Another possibility would be to check your bios,  if there might be a setting for anti-virus protection.

---

### Post by nu2this on 2007-04-25
It looks to me like you're misunderstanding the grub screen I did when I was new & that was at 5.10 Breezy.
The way I'll propose to you is the simplest if you're new to all this though it may have a major bump.
1) if you haven't already run a restore reinstalling your XPHome one more time(thats the bump)
2) defrag the XP
3) after that insert your Feisty live disc 
4) reboot
5) click the install on Feisty just go with the defaults whatever it makes the partitions will be fine
6)after Feisty is installed reboot again
7)when you get to the grub screen Ubuntu will be highlighted it'll boot in 30 seconds if left alone. If XP is what you want. You then need to press the down arrow key on the keyboard until WindowsXPHome is highlighted  then press enter.
It'll be Windows first running a chkdisk then XP as you knew it it'll only run that chkdisk once.

---

### Post by iPirates on 2007-04-25
I got mine working by manually editing my partitions.
Gparted, which is the program that edits your partitions when you're loading Ubuntu, lets you manually configure how you want your partitions laid out and such.  All I did was create 2 new paritions. 

I added a linux partition formated in ect3, and as "/" as the mount point.
Then I added a swap partition, formatted as "swap".
I already had windows installed, so I just left that.
Then I flagged the linux partition as "boot", and that was it.
Windows, and Ubuntu both boot fine.

---

### Post by eldar on 2007-04-25
Well that is a lot of stuff to look at. 
Well I tried to redo the MBR from the recovery console. It loads a bit farther then craps out with the same blue screen. This a new install of XP so it is not a well used install.  I dont know if this makes any difference but I have one of the first XP disks WITHOUT any service packs. I do not see how that should affect things, but who knows.

So this is exactly how I did it before.

I put in the xp disk and then us it to set my partition and format it for ntfs.  then I install xp and go thru its config process. I reboot and it works fine.

I then put in the 7.04 live and run the installer. I let it do its own partition work and install. I Choose the 3rd option which is "Guided - Use largest continuous free space.

Finish install and reboot. Grub comes up. I can choose either OS. I choose ubuntu and it works fine. I choose XP and it looks like it will load but then blue screens.

I have tried to set the parts BEFORE installing anything but when I put in my XP disk, it does not "see" my parts that I made even if they are formatted for ntfs already. So  I still have to set the part anyways.  

On the blue screen, it will say to run a chkdsk /f but without even being able to boot into safemode, I cant do that. Maybe I should make an XP boot disk and try that? I am willing to try pretty much anything to get this to work.

---

### Post by confused57 on 2007-04-25
> Well I tried to redo the MBR from the recovery console. It loads a bit farther then craps out with the same blue screen. This a new install of XP so it is not a well used install. I dont know if this makes any difference but I have one of the first XP disks WITHOUT any service packs. I do not see how that should affect things, but who knows.

I remember someone else having the same sort of problem  because of this...the thread is so old, I'm not sure it's even still in the archives...but I think they may have needed to update their bios and install SP2?

Added:  I actually found the thread(see reply #13):
[http://ubuntuforums.org/showthread.php?t=223048](http://ubuntuforums.org/showthread.php?t=223048)
may not be your problem, though.

---

### Post by eldar on 2007-04-25
Now that I have not tried. Would be stupid if thats what it takes but then it is  MS! Thanks for that one, confused!

---

### Post by Emerzen on 2007-04-25
You should also fire up Ubuntu and run Gparted.  What do your partitions look like?  If you reinstall Ubuntu, I typically set up my partitions prior to install (with Gparted) then run a manual setup.  You have to select one partition as your / partition w/ ext3 (most likely) and a small one for swap.  I like having the control over this.  In any case, it sounds like reinstalling XP->SP2 might be the way to go.  There's also a way to fix the boot files from the recovery console (it rewrites your ntldr.exe etc...) but you'll have to search MS site for the instructions.  If that doesn't work, I'd try the reinstall.

---

### Post by eldar on 2007-04-26
Well now I really have to wonder. Ok last night I RE-installed XP then per a link from confused57, I installed SP2 and everything booted fine.

loaded the live disk and did largest continuous space and installed 7.04.

Rebooted and held my breath and selected XP. It delayed a bit and I was about to puke in frustration when XP loaded!!!!!!\\:D/ 

The whole issue was that I had not installed SP2! Which to me is completely STUPID!!! 
So now bot boot from grub and I booted both a couple times to make sure. 

So now I have to ask, does this really make me a NOOB?! 

Thanks to all of you for your imput and assistance and thanks to confused for his link!:guitar:

---

