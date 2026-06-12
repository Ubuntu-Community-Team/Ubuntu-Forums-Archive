---
title: "Just Wanitng To Know A Few Things"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by NonStop on 2007-08-15
I'm planning on getting a laptop late September, which is going to have Windows Vista pre-installed.

I want to also get Ubuntu installed on there.

But, I have many quesitons before I go ahead:

1) Is it easy to create partitions? How do I do it?

2) I plan to have 1 partition for Vista (but its going to be pre-installed - can i just shrink the size of the partition it is already in?), 1 partition for Ubuntu, and then another for files and folders. Can both Windows and Ubuntu access the partition whcih has my files?

3) I've hear you cannot listen to mp3s for Ubuntu? Is this true?

4) Can one copy DVD's/CD's? Is th software to do that free and open-source?

5) Am I right in saying that all the software at SourceForge is free and open-source?

6) Is there a list of hihgly recommended free, linux software on this forum, or anywhere else?

7) Are there any better alternatives to the programs provided with Ubuntu (like I'm using Paint.NET instead of GIMP, is GIMP better?)?

8) How easy is it for the internet to work? I plan to have wireless by the time I get my laptop, and it should work for Windows, will it work for Ubuntu? What if I have toplug a phone line/modem into the back of the laptop, will Ubuntu still accept that?

9) Is Ubuntu easy to install? Is it similar to Windows in the form of its layout?

Cheers, and thank you for your time.

---

### Post by Hobo Joe on 2007-08-15
> **NonStop said:**
> I'm planning on getting a laptop late September, which is going to have Windows Vista pre-installed.

I want to also get Ubuntu installed on there.

But, I have many quesitons before I go ahead:

1) Is it easy to create partitions? How do I do it?

2) I plan to have 1 partition for Vista (but its going to be pre-installed - can i just shrink the size of the partition it is already in?), 1 partition for Ubuntu, and then another for files and folders. Can both Windows and Ubuntu access the partition whcih has my files?

3) I've hear you cannot listen to mp3s for Ubuntu? Is this true?

4) Can one copy DVD's/CD's? Is th software to do that free and open-source?

5) Am I right in saying that all the software at SourceForge is free and open-source?

6) Is there a list of hihgly recommended free, linux software on this forum, or anywhere else?

7) Are there any better alternatives to the programs provided with Ubuntu (like I'm using Paint.NET instead of GIMP, is GIMP better?)?

8) How easy is it for the internet to work? I plan to have wireless by the time I get my laptop, and it should work for Windows, will it work for Ubuntu? What if I have toplug a phone line/modem into the back of the laptop, will Ubuntu still accept that?

9) Is Ubuntu easy to install? Is it similar to Windows in the form of its layout?

Cheers, and thank you for your time.

I will answer as best I can.

1. Yes, it is, there is a program that does it quite simply and effectively.

2. This is where you are going to hit a snag. When Microsoft made Vista, they made it so that it installs 5 partitions, 1 of them being for Vista, and the others being the for the SOLE purpose of conflicting with dual booting, as the max number of partitions is 5. The only way to get around this as far as I know is to uninstall Vista, install Ubuntu, then RE-install Vista.

3. No, you can listen to MP3's in Ubuntu.

4. Yes, there is, and it's free.

5. Yes.

6. Well, just look around, there are different lists, spread around the forums and elsewhere.

7. Personally, I think GIMP is better, however, that's just my opinion. There are several others though if you want to try some alternatives.

8. In my experience, internet detection is 100% perfect, and 100% hands-off. In other words, I installed Ubuntu, and it worked. However, some people do have trouble with wireless, but for the most part, you wont' have to worry about it.

9. Yes, and no, respectively. The first thing you need to know when going into Linux is that Linux DOES NOT equal Windows. It is entirely different. From the GUI to the core of the OS, to most of the programs, it is different. In my opinion, it is MUCH better though.

Welcome to Ubuntu! :)

---

### Post by gentix on 2007-08-15
There are others who can answer these questions much better than I, but there are a few things (as a new Ubuntu user) I can say.

"1) Is it easy to create partitions? How do I do it?"
Yes.  You do it during the Ubutnu installation.  I'm having a little trouble, but I suspect thats a user blunder, not a Ubuntu problem.


"2) I plan to have 1 partition for Vista (but its going to be pre-installed - can i just shrink the size of the partition it is already in?), 1 partition for Ubuntu, and then another for files and folders. Can both Windows and Ubuntu access the partition whcih has my files?"
I'm fairly certain both the answers are yes.

"3) I've hear you cannot listen to mp3s for Ubuntu? Is this true?"
No, not entirely, you just have to do a little set-up work first.  Which, I understand, is fairly easy in Fiesty.

"6) Is there a list of hihgly recommended free, linux software on this forum, or anywhere else?"
Yes, actually, Ubuntu has a list like this of programs that can be installed natively, or are available on the repository.  Information like their popularity and a short description are included.

"7) Are there any better alternatives to the programs provided with Ubuntu (like I'm using Paint.NET instead of GIMP, is GIMP better?)?"
I'm not sure how to interpret this question.  I can tell you I found the Ubuntu paint program has a lot more features and cool things than MS Paint.

"How easy is it for the internet to work? I plan to have wireless by the time I get my laptop, and it should work for Windows, will it work for Ubuntu? What if I have toplug a phone line/modem into the back of the laptop, will Ubuntu still accept that?"
For me, the internet worked with 0 stet-up.  If its wireless, it will probably be the same for you.  Modems take a bit of set up, but not any more than in Windows really.

"9) Is Ubuntu easy to install? Is it similar to Windows in the form of its layout?"
Its a breeze to install.  The GUI isn't so different from Windows that you'll be paralized.  THere are just a few differences in where things are, and some really cool added features like mulitple workspaces and thnigs.


Like I said, I'm a newbie too, but I think this is how some of the veterans would answer these questions.  Also, the new version of Ubuntu is supposed to be coming out before long, and I'm told its even more user-friendly than Feisty.

---

### Post by Steve1961 on 2007-08-15
> 1) Is it easy to create partitions? How do I do it?

It's simple.  Download a copy of gparted live, burn the iso file to a cd, set your bios to boot from the cd, and away you go.  Alternatively just download a demo copy of windows software such as Acronis Disk Director - which allows you to do all partitioning within windows, even resizing your windows partition.
> 
2) I plan to have 1 partition for Vista (but its going to be pre-installed - can i just shrink the size of the partition it is already in?), 1 partition for Ubuntu, and then another for files and folders. Can both Windows and Ubuntu access the partition whcih has my files?

See above for resizing windows.  For ubuntu you need at least one partition for root and a small swap partition (say twice the size of your ram).  For a shared data partition create a fat32 partition that both windows and linux can write to.

> 3) I've hear you cannot listen to mp3s for Ubuntu? Is this true?

Not true.  You just need to install the codecs by fooloing the instructions here:

[http://ubuntuguide.org/wiki/Ubuntu_Feisty](http://ubuntuguide.org/wiki/Ubuntu_Feisty)

> 4) Can one copy DVD's/CD's? Is th software to do that free and open-source?

Yes and yes

> 5) Am I right in saying that all the software at SourceForge is free and open-source?

Not sure, but probably.  However, most of the software you need is in the Ubuntu repos.

> 6) Is there a list of hihgly recommended free, linux software on this forum, or anywhere else?

See the link to the Ubuntu guide.  Try it all and see what you like.

> 7) Are there any better alternatives to the programs provided with Ubuntu (like I'm using Paint.NET instead of GIMP, is GIMP better?)?

I think that's a matter of personal preference, but GIMP can do a lot more than Paint.NET

> How easy is it for the internet to work? I plan to have wireless by the time I get my laptop, and it should work for Windows, will it work for Ubuntu? What if I have toplug a phone line/modem into the back of the laptop, will Ubuntu still accept that?

Wireless will usually work after some configuration, but search teh forum here for answers once you get your laptop - there's bound to be someone with teh same model who's got it working.  Modems are a different matter and not something I have any experience of I'm afraid.

> 9) Is Ubuntu easy to install? Is it similar to Windows in the form of its layout?

Yes and yes (ish) - you can make it look however you want.

---

### Post by Hospadar on 2007-08-15
1) yes, Ubuntu will do that during the installation, there are a couple "guided" options, and you can also just manually pick the ones you want

2)Yes, you can shrink the vista partition.  If you want ubuntu and windows to share a partition, partition it ntfs and use "ntfs-3g" and "ntfs-config" packages to get full read/write support on ntfs partitions.  You could also use fat32 or even ext3 with some windows drivers for ext3 that are available.

3)Not true.  You have to install a couple codecs from the repositories.  The codecs are not installed by default because of legal reasons, but when you try to listen to an mp3, ubuntu will automatically find them and let you install them.  You may need to activate some extra repos, but that is very easy.

4)Yes, some of it is better licensed and dealt with than others, and some of it is a lot more share-ware-y but all of the important projects there are free and open source.

6) I'm sure there is around the interwebs somewhere, but this forum would be an excellent place to ask if you are looking for open source alternatives.  There is almost no application that does not have a great free open source alternative.

7) Actually gimp comes with ubuntu.  But for most apps, there are plenty of alternatives for the default that comes with ubuntu.  Also if you find yourself not liking the general layout, you can always try kubuntu, or xubuntu, or whatever other window setup you want.

8) Depending on the wireless card you may have varying degrees of success, most people's cards work out of the box, but many need tweaking.  If your card doesn't work, there is probably already a how-to either on this forum or on the ubuntu wiki, and if not, someone on this forum will definately be able to point you where you need to go to get it working.  It may take a little while, but you can get almost any card or setup working with a little research and help.  that said, 99% of wired lan setups work perfect right out of the box.

9) Definately.  The install boots you into ubuntu, so you can see if it works and what you will need (if anything) to be fixing, and then from there you install completely through the GUI (although if you like you can still do an terminal-based install).  The setup is pretty similar to osx or windows in many ways.  You will probably want to learn some command line basics, because often instructions are given for the command line since it is so much faster to do it that way than with a bunch of screenshots, although there is nothing that you will really need to do that cannot be done with a GUI.  You may also want to look at a few sites that explain the linux filesystem because it is significantly different than windows (Although generally you won't ever need to worry about the filesystem beyond your home folder.

---

### Post by NonStop on 2007-08-15
Thank you everyone for your replies. I appreciate it

EDIT: Is htis a good guide for having both Vista and Linux; [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by NonStop on 2007-08-15
Oh, and oes Ubuntu create it's own partition?

---

### Post by ugm6hr on 2007-08-15
> **NonStop said:**
> Thank you everyone for your replies. I appreciate it

EDIT: Is htis a good guide for having both Vista and Linux; [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

I've just read the link - and yes - it is accurate.  

Specifically - Vista can shrink its own partition (which is safer than doing it from Ubuntu).

One minor edit - if you plan to have a "Files" partition - prior to the "Install Ubuntu" stage - create an extra primary partition for "Files" (you pick a size).  The only question is what *format* to chose....

Given ntfs-3g supports reading and writing Vista NTFS format from Linux, you could go with that.  The "safe" option would be to chose fat32, but that would limit individual file size to 4GB.  Unfortunately, I believ fs-driver does not support Vista, so you will not be able to read the Linux partition from Vista.

Hope that makes sense.

Oh - and Yes - Ubuntu will sort out its own partitions.

---

### Post by Steve1961 on 2007-08-15
Wow, you learn something new everyday.  I didn't realise vista could shrink it's own partition!!

---

### Post by p_quarles on 2007-08-15
> 
2. This is where you are going to hit a snag. When Microsoft made Vista, they made it so that it installs 5 partitions, 1 of them being for Vista, and the others being the for the SOLE purpose of conflicting with dual booting, as the max number of partitions is 5. The only way to get around this as far as I know is to uninstall Vista, install Ubuntu, then RE-install Vista.
I have a dual-boot setup with Vista, and I can vouch for the fact that this information is incorrect. First, hard drives can only have four physical partitions. Second, OEM Vista is installed on a single partition. 

The only thing that should be done differently with Vista (vs. XP) is that it won't cooperate well with gparted. Much easier to use Vista's partition editor to create free space on the drive, and then install Ubuntu.

---

### Post by Steve1961 on 2007-08-15
> 2. This is where you are going to hit a snag. When Microsoft made Vista, they made it so that it installs 5 partitions, 1 of them being for Vista, and the others being the for the SOLE purpose of conflicting with dual booting, as the max number of partitions is 5. The only way to get around this as far as I know is to uninstall Vista, install Ubuntu, then RE-install Vista.

I can guarantee this is incorrect.  I installed vista myself into a single partition on my third hard drive some months ago.  XP, Ubuntu and Debian were already installed.  I then used easyBCD to point the vista bootloader (which installed itself in the mbr of disk 1) to the other operating systems.  I normally use grub but wanted to see if this method worked, and it does.

---

### Post by kirios on 2007-08-15
> **Hobo Joe said:**
> When Microsoft made Vista, they made it so that it installs 5 partitions, 1 of them being for Vista, and the others being the for the SOLE purpose of conflicting with dual booting, as the max number of partitions is 5. 
[COLOR="DarkRed"]Not true. Vista installs to 1 partition by default and, as ugm6hr has already pointed out, Vista can resize its C drive to create free space for new partitions (which can be formatted during the Ubuntu installation). [/COLOR]

> **Hobo Joe said:**
> The only way to get around this as far as I know is to uninstall Vista, install Ubuntu, then RE-install Vista. 
[COLOR="DarkRed"]If you install Vista AFTER Ubuntu, you'll have to install and configure EasyBCD to boot Ubuntu. Much easier to install Vista first and let GRUB auto-configure the Vista boot entry during the Ubuntu installation.[/COLOR]

---

### Post by NonStop on 2007-08-15
Well, Vista will be pre-installed anyways. Does Ubuntu create its own partition?

---

### Post by Hobo Joe on 2007-08-15
> **p_quarles said:**
> I have a dual-boot setup with Vista, and I can vouch for the fact that this information is incorrect. First, hard drives can only have four physical partitions. Second, OEM Vista is installed on a single partition. 

The only thing that should be done differently with Vista (vs. XP) is that it won't cooperate well with gparted. Much easier to use Vista's partition editor to create free space on the drive, and then install Ubuntu.

Well, apparently I was wrong, that was just what I heard from a friend who has Vista and dual boots with it.

You learn something new everyday. :\

---

### Post by kirios on 2007-08-15
> **NonStop said:**
> Well, Vista will be pre-installed anyways. Does Ubuntu create its own partition?
[COLOR="DarkRed"]After you resize the C:/ drive from within Vista, boot from the Ubuntu CD and choose Custom Partition when you get to the Partitioning menu. Right-click on the free space and create a new partition formatted as ext3 (default filesystem). Also create a small partition for swap memory (around the same size as the total RAM in your system).[/COLOR]

---

### Post by NonStop on 2007-08-15
> **ugm6hr said:**
> I've just read the link - and yes - it is accurate.  

Specifically - Vista can shrink its own partition (which is safer than doing it from Ubuntu).

One minor edit - if you plan to have a "Files" partition - prior to the "Install Ubuntu" stage - create an extra primary partition for "Files" (you pick a size).  The only question is what *format* to chose....

Given ntfs-3g supports reading and writing Vista NTFS format from Linux, you could go with that.  The "safe" option would be to chose fat32, but that would limit individual file size to 4GB.  Unfortunately, I believ fs-driver does not support Vista, so you will not be able to read the Linux partition from Vista.

Hope that makes sense.

Oh - and Yes - Ubuntu will sort out its own partitions.

So, Ubuntu creates its own partition, and then create your own files partition if I want to (I'm not so sure now, might just half the disk, one for Linux, one for Vista, as I heard Linux won#'t be able to pick up the partition with all the file son).

---

### Post by Hobo Joe on 2007-08-15
Ubuntu CAN make it's own partitions, however, it's a little less risky to do it yourself.
I think you should only let the install do it if you ahve a clean harddrive.

---

### Post by Steve1961 on 2007-08-15
> So, Ubuntu creates its own partition, and then create your own files partition if I want to (I'm not so sure now, might just half the disk, one for Linux, one for Vista, as I heard Linux won#'t be able to pick up the partition with all the file son).

Linux can read and write to ntfs with the ntfs-3g driver, but fat32 is thel solution I use.  Windows and Linux will both see that partition and be able to read and write to it without any special configuration.

---

### Post by kirios on 2007-08-15
> **Steve1961 said:**
> fat32 is thel solution I use. 
[COLOR="DarkRed"]I don't think Vista can be installed on a fat32 partition, so it would have to be an extra partition (fat32) for personal files to be accessible from either OS.[/COLOR] 

Edit:  
> **Steve1961 said:**
> For a shared data partition create a fat32 partition that both windows and linux can write to.

---

### Post by NonStop on 2007-08-15
All clarified here. Cheers

> **bodhi.zazen said:**
> Use the Vista disk manager to resize your vista partition.

Leave the free space unpartitioned.

The Ubuntu CD will partition and format the unpartitioned space. It will not overwrite vista unless you tell it to so best look at Linux partitioning terminology :

Partitioning : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Install guide : [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

