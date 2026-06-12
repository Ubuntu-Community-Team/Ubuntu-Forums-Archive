---
title: "noob question"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by firsttimeubuntero on 2008-01-18
I want to install ubuntu in one of the partitions of my laptop, I have chosen to do it manually and in the options I'm told that I need at least 2GB as the boot loader, does this mean I have to create an extra partition of 2 GB? also what option should I choose for this bootloader? ext3 or something else?

---

### Post by PeterJS on 2008-01-18
Generally the bootload (grub) goes on to your root parition, so as long as your root parition is at least 2gb you should be fine, I personally would reccomend a larger root, at least 10, probably closer to 20 if you can get away with it.

---

### Post by zakirs on 2008-01-18
ant the format would be ext3 i suppose

---

### Post by vikram on 2008-01-18
yes

---

### Post by firsttimeubuntero on 2008-01-18
> **PeterJS said:**
> Generally the bootload (grub) goes on to your root parition, so as long as your root parition is at least 2gb you should be fine, I personally would reccomend a larger root, at least 10, probably closer to 20 if you can get away with it.

well the thing is I have 25 GB partition for Ubuntu so I can't really make it close to 20 GB for the root partition, and about my first question, do I have to resize the 25 GB partition into two? one partition (at least 2 GB for the root partition) and the rest for the actual Ubuntu?

---

### Post by benerivo on 2008-01-18
> **firsttimeubuntero said:**
> do I have to resize the 25 GB partition into two? one partition (at least 2 GB for the root partition) and the rest for the actual Ubuntu?

You only need the one partition for ubuntu. If you select the 25GB partition you have, to be used as root (/), it should put absolutely everything in to that partition. You will need another partition for a swap space partition, so i recommend splitting this 25GB to have 24GB for root and 1GB for swap.

---

### Post by nikoPSK on 2008-01-18
> **zakirs said:**
> ant the format would be ext3 i suppose

that's the generic, although there are others. :)

---

### Post by firsttimeubuntero on 2008-01-18
> **benerivo said:**
> You only need the one partition for ubuntu. If you select the 25GB partition you have, to be used as root (/), it should put absolutely everything in to that partition. You will need another partition for a swap space partition, so i recommend splitting this 25GB to have 24GB for root and 1GB for swap.

24GBjust for the root partition? that's a huge difference in comparison to what PeterJS suggested! I thought the root partition was supposed to be smaller than the other,in any case you are suggesting to split the 25 GB partition into two partitions, correct?

---

### Post by benerivo on 2008-01-18
> **firsttimeubuntero said:**
> 24GBjust for the root partition? that's a huge difference in comparison to what PeterJS suggested! I thought the root partition was supposed to be smaller than the other,in any case you are suggesting to split the 25 GB partition into two partitions, correct?

Virtually everyone needs a swap partition. so yes, two partitions are neccasary.

The root partition is the 'parent folder' of every single file and folder in an ubuntu installation (ie. there is no 'other'). You may choose to put a part of ubuntu in its own partition, such as /home or /boot, but there is no real need to do so.

---

### Post by firsttimeubuntero on 2008-01-18
> **benerivo said:**
> Virtually everyone needs a swap partition. so yes, two partitions are neccasary.

The root partition is the 'parent folder' of every single file and folder in an ubuntu installation (ie. there is no 'other'). You may choose to put a part of ubuntu in its own partition, such as /home or /boot, but there is no real need to do so.

I'm getting a bit confused here since I'm new at this, first you mention that two partitions are necessary, so then that means I should use a program like GParted and divide that 25 GB partition into 2 partitions, right? so that means one partition will have 24 GB (for root) and the other 1 GB (for swap), but then why do you mention in your second paragraph "there is no other, you may choose to put a part of ubuntu in its own partition, such as /home or /boot, but there is no real need to do so" 

Is it really 2 partitions?, or does 1 partition go inside of the other?

---

### Post by firsttimeubuntero on 2008-01-18
By the way, I thought the 2 partitions were supposed to be root (for admin use, install/changes on the system) and home (the one for your everyday use of linux) the reason for this is that I have heard from several  linux users that you can't mess up in linux as in easy as in windows since you are not really using the "root" partition but using the other one instead.

---

### Post by p_quarles on 2008-01-18
What PeterJS suggested was that you may want to create a separate /home partition, which would then be used to store your data. The operating system and its applications would be stored on the root partition. In this kind of setup, your /home partition would be the largest, as you would expect to need the most space.

The swap partition is different. It works much like "virtual memory" in Windows. It is essentially a space for temporarily storing information when not everything can fit in memory. Setting this above 1 GB is useless for most situations.

---

### Post by benerivo on 2008-01-18
There should be two partitions, and GParted is the best choice to make them with. One partition is root, which is displayed as '/', and is all of the ubuntu installation. The second would be a swap partition, which is a spare area for linux to use in the background when memory is low. It is of no importance to the average user, and acts only as virtual extra RAM when it is needed.

---

### Post by spawn270 on 2008-01-18
You will create 2 partitions one 24gb spot for root. The other 1gb spot for swap. You can tweak these anyway you like, but stick with this for now until you are more comfortable with the system. I am also fairly new to this too, so don't get downhearted.

---

### Post by firsttimeubuntero on 2008-01-18
ok these are the settings I chosed 



-Type for the new partition: 
Primary

-New Partition sizein MB:
24990

-Location for new partition:
Beginning

-Use as:
ext3

-Mount Point = ?


does everything check ok?

---

### Post by Xell Strider on 2008-01-18
In the mount point put  /  that is the main folder or if you want to see this way is the c:\  in windows

---

### Post by firsttimeubuntero on 2008-01-19
something went wrong and I got an error message during installation due to: bad optical drive, bad disc, old hard disk, etc. the worst part is that I decided to cancel the installation and reboot the computer so I turned the computer off and took out the live CD. When I turned the computer back on it didn't load windows and instead I got the message "Error Loading Operating System" :(

---

### Post by firsttimeubuntero on 2008-01-19
oh man, according to CCNA_student from this forum the "Location for new partition" should have been "end"

---

### Post by firsttimeubuntero on 2008-01-19
Fortunately, this was a fresh new install so I didn't lose any files on my windows partition, does anyone have any suggestion as what to do now? what I mean is, should I format the entire hard disk using GParted and create partitions for WinXP and Ubuntu again? and if so in what order would be better? install  WinXP first, or Ubuntu?

---

### Post by firsttimeubuntero on 2008-01-19
anyone?

---

### Post by benerivo on 2008-01-19
Always install XP before Ubuntu. Before that, load the live cd and set your partitions as you want them using GParted. Keep it simple and make three partitions -- one for XP (fat32 format, or ntfs if it allows you to), one for Ubuntu (ext3), and one for swap (swap) (1 GB will do).

Then reboot in to the XP cd and install it in to the fat32 partition (you may want to format it to ntfs instead, if you couldn't before). Then boot in to the live cd and install ubuntu (eg. root '/') in to the ext3 partition, and use the swap partition for swap. This should be fine, allowing ayou to dual boot.

---

### Post by louieb on 2008-01-19
> **firsttimeubuntero said:**
> Fortunately, this was a fresh new install .., does anyone have any suggestion as what to do now? 

Sure If were mine. This is what I'd do if I could start from scratch.
Partitions.[LIST=1]
[*]15-20GB For Windows
[*]10GB For Linux root /
[*]1-3GB For Linux /home (doesn't have to be very large for the most part this should only contain configuration files). A separate /home is very useful if you have to reinstall you won't loose all your configuration files.
[*]Extended partition - rest of drive  (the 2 below will go inside here).[LIST=1]
[*]1GB For Swap  unless a laptop and you want to hibernate then 1.5 x ram.
[*]Rest of drive use for a Data partition (use NTFS or ext3 depending on which OS you will use the most) Linux can read/write NTFS and XP can read write ext3. Its really nice to have your data in a separate partition works well for backup. and its a lot safer when and if you ever have reinstall XP or Ubuntu.[/LIST] [/LIST]:guitar:Install Windows. Install Ubuntu. Rock on.

---

### Post by firsttimeubuntero on 2008-01-19
I'm actually trying to install both WinXp and Gutsy Gibbon on a laptop for dual boot, thanks for the suggestions I'll try them out, I'm just glad I decided to experiment first with a new fresh install of Win XP than with a computer full of personal files, one last thing do you recomend using GParted and format the entire disk before doing anything else? I'm asking because of the error I get that says "Error Loading Operating System"

---

### Post by firsttimeubuntero on 2008-01-20
while trying to install I encountered with an error: 



the installer encountered an error copying files to the disk:

[Errno 5] Input/output error 

"This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drives lens, to check whether the hard disk is old and in need of replacemen, or to move the system to a cooler enviroment."

not sure what could be causing the problem since:

-The install CD was clean.
-I had burned the CD in 4x speed.
-The DVD drive lens should be clean since I've used it before to try the live CD for several hours, and I also used it to install WinXP again in my other partition.
-I purchased a new hard disk for this thinkpad and installed it myself. 

so that leaves moving the system to a cooler enviroment, but what does that really imply? the laptop has been running hot sometimes, but I didn't know this was an issue for installing.

---

### Post by lgambett on 2008-01-20
Hi friends,
I would suggest three partitions;
a / (root) partition of 5-7 Gb (A fresh Gutsy install takes about 4 Gb)
a swap partition of about the same size of the RAM (or 1,5 x RAM size, not very important)
the remaining space for a /home partition

It is **very** important for future reinstalls to have a separated /home partition !

---

### Post by GavinZac on 2008-01-20
try burning another cd. it may look clean but sometimes random stuff can cause them to skip out.

---

### Post by louieb on 2008-01-20
> **firsttimeubuntero said:**
> ...so that leaves moving the system to a cooler enviroment, but what does that really imply? the laptop has been running hot sometimes, but I didn't know this was an issue for installing.
My T30 ThinkPad runs hot. This caused random errors and sometimes freeze completely up.   Finally bought a cool pad haven't had any trouble with it since.

---

### Post by firsttimeubuntero on 2008-01-20
I burned a new Live CD and tried it once again, this time... 

IT INSTALLED! :)

I'll try it out and post with some feedback to see if everything is working fine

---

### Post by firsttimeubuntero on 2008-01-20
ok, after using it for some time I have some questions:

1) While I was installing Ubuntu from the live CD I didn't have the laptop connected to the internet, almost at the end of the installation I received a message about some security repositories/updates or something of the sort that weren't able to install since it couldn't access it through the web, is this something similar to windows update? and if it's important, how can I update it? 

2) How do I get the YouTube videos to play on my browser? it keeps asking me for a flash player, but I'm not sure how to install it in Ubuntu

---

### Post by GavinZac on 2008-01-20
Dont forget to say thanks [ ;) ](http://ubuntuforums.org/post_thanks.php?do=post_thanks_add&p=4174422)

If you're connected to the internet you can upgrade software on your computer from the centralised repositories: you can install updates for everything right from one little application, no need for windows update, adobe update, google update, norton update... and so on. its best to upgrade these but not essential, if everything works for you then feel free to leave it alone :)

If you try to watch a flash movie in Ubuntu, Firefox should show a little bar saying you need to install a plug in. Click this, and you'll be given the choice between Adobe's plug in (in theory, this should work better) or gnash, the free-as-in-speech alternative.

---

### Post by firsttimeubuntero on 2008-01-21
> **GavinZac said:**
> Dont forget to say thanks [ ;) ](http://ubuntuforums.org/post_thanks.php?do=post_thanks_add&p=4174422)

If you're connected to the internet you can upgrade software on your computer from the centralised repositories: you can install updates for everything right from one little application, no need for windows update, adobe update, google update, norton update... and so on. its best to upgrade these but not essential, if everything works for you then feel free to leave it alone :)

If you try to watch a flash movie in Ubuntu, Firefox should show a little bar saying you need to install a plug in. Click this, and you'll be given the choice between Adobe's plug in (in theory, this should work better) or gnash, the free-as-in-speech alternative.

thanks for the reply

---

### Post by firsttimeubuntero on 2008-01-21
by the way, is it possible to install del.icio.us buttons add on in firefox for Ubuntu? I can't find it on Add/Remove Applications

---

### Post by firsttimeubuntero on 2008-01-21
> **GavinZac said:**
> Dont forget to say thanks [ ;) ](http://ubuntuforums.org/post_thanks.php?do=post_thanks_add&p=4174422)

If you try to watch a flash movie in Ubuntu, Firefox should show a little bar saying you need to install a plug in. Click this, and you'll be given the choice between Adobe's plug in (in theory, this should work better) or gnash, the free-as-in-speech alternative.

I've tried both choices and I get the same message: 'flashplugin-nonfree'

---

### Post by firsttimeubuntero on 2008-01-21
I found something in Add/Remove Applications doing a search for "Flash" but it's not in the "Supported Applications" category, it's on "All available applications" category, does anyone recommend to download anything from the  "All available applications" category? I've seen some programs in there that are good (rated with 4 stars) but are not supported.

---

### Post by nikoPSK on 2008-01-21
yes, you can safely get things from all applications category. :)

---

### Post by spawn270 on 2008-01-21
I think you have to start from scratch. Sorry. Try booting from windows cd and see if you can do a recovery... I never tried it so I can't tell if it works or not. Also if you are getting frustrated with difficult install of ubuntu try xandros. The installer is more newbie user friendly. Hope this helps.

---

