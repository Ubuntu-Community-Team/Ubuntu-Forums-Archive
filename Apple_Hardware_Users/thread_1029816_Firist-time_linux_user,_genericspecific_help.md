---
title: "Firist-time linux user, generic/specific help"
date: 2009-01-03
forum: Apple Hardware Users
---

### Post by onetrickmind on 2009-01-03
Hey ubuntu friends,
I've managed to get Ubuntu on my MacBook (1.5 years old I'd guess) in a dual-boot situation with rEFIt. Hopefully I can meet some fine people to help me out with some questions and problems I have.

In Mac OS X's disk utility I see that there is an OS X partition as well as three extra partitions. I'm aware of a swap partition and an ext3 partition, and two of the partitions seem to be empty. Do I need those anymore? Can I delete them and expand my linux partition?

Also, my sound is broken. Sound does not come from audio out and the internal speakers only make very quiet crinkly noises. I noticed a few places that said that a certain kind of MacBook Pro's sound can't work at all.

I also wonder if my wireless thingamajig is being fully taken advantage of. The signal strength indicator in ubuntu is half as strong as that in Mac OS X. I was downloading the ubuntu image in Mac OS X at 800-1050 MB/s but the updates in Ubuntu were only coming in at 100-60 kB/s.

I hope Ubuntu knows my computer has fans, because I can feel the laptop and am guessing it is at about 75-80 degrees C but I've never heard the fans turn on at all.

Another question I have is: "Where is everything?" My desktop is blank unless I plug in external drives. I listen to somafm.com and went there to get some streaming music since I have no files on this new partition. Firefox asked me how I want to open it and I couldn't navigate the file browser to find any programs. :(
 
I've got a few more questions like what I can use to video blog (editing and capture software) and how to customize my keyboard set up (I got command mapped to control but want to do more), but I think those are the essential questions and problems I've got.

Thank you!

---

### Post by 2hot6ft2 on 2009-01-03
> **onetrickmind said:**
> 
In Mac OS X's disk utility I see that there is an OS X partition as well as three extra partitions. I'm aware of a swap partition and an ext3 partition, and two of the partitions seem to be empty. Do I need those anymore? Can I delete them and expand my linux partition?
How can we answer about the partitions without knowing what they are and where they are?
A screenshot of your partitions would help to answer the question.
System>Administration>Partition Editor
then
Applications>Accessories>Take Screenshot
grab current window, save to desktop
and attach it to your post using the Manage Attachments at the bottom when making a post.
> **onetrickmind said:**
> I also wonder if my wireless thingamajig is being fully taken advantage of. The signal strength indicator in ubuntu is half as strong as that in Mac OS X. I was downloading the ubuntu image in Mac OS X at 800-1050 MB/s but the updates in Ubuntu were only coming in at 100-60 kB/s.
They didn't come from the same place and the iso is one big file but the updates are many small files.
> **onetrickmind said:**
> 
Another question I have is: "Where is everything?" My desktop is blank unless I plug in external drives.
Top left menus places for places such as drives, Applications for Applications and System for things that are System related.

There's a start and welcome.

---

### Post by onetrickmind on 2009-01-03
> **2hot6ft2 said:**
> How can we answer about the partitions without knowing what they are and where they are?
Ok, I added an attachment. Something happened and rEFIt didn't ask me to boot to ubuntu but I got a screenshot of the set-up from disk utility and it is attached. Disk utility thinks the partitions are Mac OS Extended Journaled and FAT, but ubuntu says they are ext3 and linux-swap.
Here is a report that came from the partition inspector that came with rEFIt:
> 
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    356229351  Mac OS X HFS+
 3      356229352    357123735  Basic Data
 4      357123736    389223345  Basic Data
 5      389223346    390721934  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    390721967  ee  EFI Protective

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+

Partition at LBA 356229352:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data

Partition at LBA 357123736:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 4, type Basic Data

Partition at LBA 389223346:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap



> Top left menus places for places such as drives, Applications for Applications and System for things that are System related.
Where can I find these things actually in the filesystem?

> There's a start and welcome.
Thank you very much 2hot6ft2, :)

---

### Post by 2hot6ft2 on 2009-01-03
> **onetrickmind said:**
> Ok, I added an attachment. Something happened and rEFIt didn't ask me to boot to ubuntu but I got a screenshot of the set-up from disk utility and it is attached. Disk utility thinks the partitions are Mac OS Extended Journaled and FAT, but ubuntu says they are ext3 and linux-swap.
Here is a report that came from the partition inspector that came with rEFIt:

I have never used a Mac so I have no idea what to make of that partition picture you got, but there are others here that will help with that I'm sure.

If you had taken it in ubuntu I could tell you.
> **onetrickmind said:**
> 
Where can I find these things actually in the filesystem?

Thank you very much 2hot6ft2, :)
Honestly I couldn't tell you. I used widows for 20 years and started using linux fairly recently. That part is still a mystery to me. Since you don't install and uninstall things like in windows or a mac you never really have to go looking in the filesystem for them.

And you're welcome.

---

### Post by 2hot6ft2 on 2009-01-03
Your list of the partitions has 5 listed while the pic as far as I can see only shows 4 so I can't tell where it is with that.

---

### Post by onetrickmind on 2009-01-03
I looked in System>Administration and didn't find anything about Partition Editor. I also checked System Tools under Applications.

---

### Post by 2hot6ft2 on 2009-01-03
> **onetrickmind said:**
> I looked in System>Administration and didn't find anything about Partition Editor. I also checked System Tools under Applications.
Really? Well let's get it installed then. It should be there. That's odd.
Anyway open a terminal
Applications>Accessories>Terminal
and put this in it
```
sudo apt-get install gparted
```
hit Enter then type in your password (it wont be displayed)
Hit Enter
When it finishes you can close the terminal it will be there in
System>Administration>Partition Editor

---

### Post by onetrickmind on 2009-01-03
> **2hot6ft2 said:**
> Really? Well let's get it installed then. It should be there. That's odd.
Anyway open a terminal
Applications>Accessories>Terminal
and put this in it
```
sudo apt-get install gparted
```
hit Enter then type in your password (it wont be displayed)
Hit Enter
When it finishes you can close the terminal it will be there in
System>Administration>Partition Editor

Ok, here is a screenshot.
When I was reading about rEFId it said there a hidden partition on every harddrive for EFI, or something. I think that is supposed to stay there.

---

### Post by 2hot6ft2 on 2009-01-03
Now that I can understand. So now we have.

sda1 = boot - EFI
sda2 = Mac OS
sda3 = ?
sda4 = Ubuntu
sda5 = Linux Swap

What is it you want to do here?
Do you want to do away with sda3 = ?
And resize sda4  = Ubuntu to fill that space?

Since I don't know anything about the rEFId, that will have to be your call and I wont take any responsibility. Just to make that clear. But see next post

I would leave sda1 = boot alone

---

### Post by 2hot6ft2 on 2009-01-03
Hold on sda1 = boot is labeled EFI so that should be your rEFId

---

### Post by onetrickmind on 2009-01-03
> **2hot6ft2 said:**
> Now that I can understand. So now we have.

sda1 = boot
sda2 = Mac OS
sda3 = ?
sda4 = Ubuntu
sda5 = Linux Swap

What is it you want to do here?
Do you want to do away with sda3 = ?
And resize sda4  = Ubuntu to fill that space?
I was wondering if we still needed sda3 and sda5, or if those were only necessary for the installation process.

---

### Post by 2hot6ft2 on 2009-01-03
> **onetrickmind said:**
> I was wondering if we still needed sda3 and sda5, or if those were only necessary for the installation process.
sda3 no I don't even know why it's there.
sda5 yes it's the linux swap partition.

---

### Post by onetrickmind on 2009-01-03
Gparted says that there are 150 mebibytes on sd3. I checked in the file browser and there is a folder that says "lost and found." I do not have permissions to open it, should I still remove this partition?

---

### Post by 2hot6ft2 on 2009-01-03
That's just the trash can and the files for that file system. If you're going to do away with that partition then it will all go when the partition does. If you're ready I have the instructions all set for removing sda3 and enlarging sda4.

---

### Post by onetrickmind on 2009-01-03
Ok, ready!

---

### Post by 2hot6ft2 on 2009-01-03
This needs to be done form the livecd since you can't do anything to a partition you are currently using, Unless you would rather do it from your Mac OS.

You don't have any extended partitions so it will be easy.

Boot from the livecd that you used to install ubuntu
Once you're at the live desktop go to
System>Administration>Partition Editor
select the sda3 partition, right click and select delete.
Click on the sda4 partition and click on resize/move
Use the slider to resize it into the space where sda3 was
Then click on apply changes to make them happen

When it finishes Close Partition Editor.
Click on the button in the top right corner of the desktop and select restart.

Remove the cd when it tells you to and hit Enter.
It will reboot into ubuntu and your partitions are done.

---

### Post by 2hot6ft2 on 2009-01-03
Did you make it back? Thought you got lost.:popcorn:

---

### Post by 2hot6ft2 on 2009-01-03
> **onetrickmind said:**
> 
Also, my sound is broken. Sound does not come from audio out and the internal speakers only make very quiet crinkly noises. I noticed a few places that said that a certain kind of MacBook Pro's sound can't work at all.
First to get your multimedia up to date.
The short version first.
Open a terminal
Applications>Accessories>Terminal
same old drill put this in and hit Enter
```
sudo apt-get install ubuntu-restricted-extras

```same as before type in your password (wont be displayed) and hit Enter
When it gets to the agreement hit Tab then Enter to accept the Java agreement.

The long way for later just to make sure you have everything for multimedia here. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Now that you have what's needed to play multimedia files we can address the NO sound issue here. [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

If still have no sound try these maybe one will help.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

> **onetrickmind said:**
> 
I've got a few more questions like what I can use to video blog (editing and capture software) and how to customize my keyboard set up (I got command mapped to control but want to do more), but I think those are the essential questions and problems I've got.
I haven't done any of this but I think people are using "cheese" yes that's it's name and you can get it in
System>Administration>Synaptic Package Manager just click on search and put in cheese and hit find.

Once it finds it you just select it and right click and Mark For Installation then the big checkmark to install it with whatever else it said it needed.

For the keyboard there's
System>Preferences>Keyboard
and
System>Preferences>Keyboard Shortcuts

If you don't already have these then in a terminal use
```
sudo apt-get install gnome-keyboard-properties gnome-keybinding-properties
```you should be getting the hang of this now.

That should pretty much take care of your questions that I could answer. So a bit more info to help you find your way around and answer questions you don't know you have yet,

New to Linux?
Here are some helpful things to bookmark for future reference.

Linux is Not Windows
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Ubuntu Linux Resources
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Linux alternatives to windows apps
[http://www.osalt.com/](http://www.osalt.com/)
[http://www.linux.org/apps/](http://www.linux.org/apps/)
[http://www.gimpshop.com/](http://www.gimpshop.com/)
[http://www.linuxappfinder.com/](http://www.linuxappfinder.com/)

Everyone asks coming from windows
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

Customizing and apps
[http://ubuntuforums.org/showthread.php?t=856190](http://ubuntuforums.org/showthread.php?t=856190)
[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)

Learning Linux
[http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485)
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid](http://ubuntuguide.org/wiki/Ubuntu:Intrepid)
[http://ubuntuforums.org/showthread.php?t=655207](http://ubuntuforums.org/showthread.php?t=655207)

Troubleshooting, multimedia and misc help
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
[http://tazbuntu.blogspot.com/2008/07/remove-old-kernels-in-ubuntu.html](http://tazbuntu.blogspot.com/2008/07/remove-old-kernels-in-ubuntu.html)

Welcome and enjoy

---

### Post by onetrickmind on 2009-01-03
Hm, this isn't good. It took a long time, but after I deleted sda3 and expanded sda4 rEFIt no longer detects that I have a linux partition on the computer. Do I need to install this again?

Also, when I was on the LiveCD I pressed Apple-R to reload the firefox window, but I was supposed to press control-R. It zoomed in to the screen a little bit. I pressed it again to undo but that didn't work, and I tried pressing Apple-E but that made two screens come up. :(

---

### Post by bryonak on 2009-01-04
You can zoom in/out by holding down the Apple button and scrolling.

Also you may have to reconfigure rEFIt, probably done best within OSX.
It seems to have saved the beginning position of your partition and tries to get info from there, obviously not being able to do so.


For the temperature/fans, try ```
sudo aptitude install lm-sensors
```and then```
sudo sensors-detect
```follow the instructions there and apply the changes at the end. Then you can check your fan speed and temperatures with ```
sensors
```There are a lot of GUIs for sensor reading (like conky), but let's keep it simple for now.


What you should always do when asking for help is including your exact Mac model. You can get it by typing this into a terminal:
```
sudo dmidecode -s system-product-name
```

About the wireless strength... If your MacBook is 1.5 years old, it's probably a 3.1. (I've got a MBP 3.1)
Apple has built custom Atheros cards into these, and those suffer from a minor processing bug in the hardware (the 2.x models as well), which makes your card unable to reach 100% signal strength.
OSX remedies this by cutting the scale off at somewhere around 75%-80%, while Ubuntu shows you the true percentage. This leads to the signal appearing stronger on OSX.



Just a bit of general info:

aptitude, Synaptic and the apt-tools are all front ends for the APT system, which manages your installed programs.
Aptitude is based on the command line and meant to unify/replace the apt-tools, which have been traditionally split up for different tasks. For example 'aptitude install firefox' does the same as 'apt-get install firefox', but for 'aptitude search firefox' you have to use 'apt-cache search firefox', because apt-get can't do searches.
Apart from that, they're equal, except that you have to type one letter less with aptitude (just typing 'apti' and then hitting the tab key).

Synaptic does exactly the same as aptitude, just via the GUI. Because "click System -> Administration -> Synaptic, then hit Search, type something, mark for installation, click Apply..." is much slower than "type sudo aptitude install some_application", you will get mostly terminal instructions here. But everything can be done with Synaptic as well.

Also if you want to install only user Applications, the Add/Remove tool in your main panel menu will offer you the same as Synaptic, but the entries are  rated and it's left out all the helper programs, libraries, utilities etc.


There is no folder like OSX' Applications on Ubuntu, but rather "metadata". You can see what you have installed by browsing through your main menu. You can also open the Add/Remove tool and choose "installed applications only" from the top, or do the same in Synaptic.
If you really want to look at the binary program files, you can always open Nautilus (the file browser, for example via the Places menu), hit Ctrl+L and type "/usr/bin". Or click on the "File system" in Nautilus' left panel and browse to the usr folder, then bin. But this folder is big and quite boring.

---

### Post by onetrickmind on 2009-01-04
Whoa! Very helpful bryonak! I talked to a friend today about that partition I deleted and he said it might have been the boot partition and that it would be easiest to reinstall. Whoops! I'll do this tonight unless somebody stops me.

---

### Post by bryonak on 2009-01-05
The Mactel support team does a very good job of providing [guides for installation]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation").

Here's one important step:
> 5. Reboot when done with the install, and in the rEFIt menu, choose the partition tool. It will attempt to sync the partition tables on your disk. Then SHUTDOWN the computer (not reboot), and start it up. You should be able to boot to Ubuntu now. If it seems to freeze on the tux logo, completely shutdown again and try one more time.

If selecting the partition tool in the boot menu fails, I'd search for a synchronize option in the rEFIt configuration tool within OSX.

The last resort would be completely reinstalling rEFIT, since that would make it scan the hard drive partition layout again, hopefully recognizing everything correctly.

Reinstalling Ubuntu isn't going to change anything within rEFIt, so it won't help in this case.
It's actually only necessary if you've overwritten crucial system parts, apart from that almost everything can be restored with APT and dpkg-reconfigure.


EDIT:
It just came to my mind that you might have had GRUB (the Linux boot loader) installed on that partition you deleted. Usually it's either on the same partition as Ubuntu or on the first partition of the hard drive, but it could be...
This can be solved by a simple "grub-install" from the liveCD, but first try the other things I've written.

---

### Post by cyberdork33 on 2009-01-05
Yes somehow you got an extra linux partition in there somehow, and resizing your Ubuntu partition caused the booting to break. You can reinstall grub and that might fix it, alternatively, since you install is so new, just use partition-editor to delete everything but the EFI and HFS+ (OSX) partitions and start the installation again, selecting to "use the largest continuous free space". 

Please check the "Before You Post" link in my signature to properly identify your mac version and find the appropriate documentation for you mac.

Good luck.

---

