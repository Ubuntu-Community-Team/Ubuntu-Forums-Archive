---
title: "Dual booting XP and Ubuntu"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by ChrisUK on 2007-04-06
Hi all.

I am new to Linux and have some questions.

Is it true that 7.04 is being released on the 19th of April?
If so, there is no point in me installing Edgy now, if a new version is coming out that soon.

I would like to dual boot Windows XP with Ubuntu but I don't really understand how... Is there a good guide anywhere?
I will be using XP just for games and Linux for pretty much everything else. So I will probably reformat XP first, then choose the size of the partition (this is where I get confused, when and what with do I resize the partition with?).

Also, once Ubuntu is installed, do I need to install any drivers for GFX card, WiFi, etc, etc? 
I would like a guide to explain what to do once Ubuntu is installed.

Will I need an antivirus and firewall?

Thanks in advance.
Chris

---

### Post by mac.ryan on 2007-04-06
> **ChrisUK said:**
> Is it true that 7.04 is being released on the 19th of April?

Yes.

> If so, there is no point in me installing Edgy now, if a new version is coming out that soon.If you are not in a hurry, you might wish to wait, as Feisty comes with some very useful gadgets for those new to GNU/Linux (especially for those migrating from XP). However, if you are in a hurry, you can still install Edgy, and the system will offer you the chance to upgrade to Feisty at due time...

> I would like to dual boot Windows XP with Ubuntu but I don't really understand how... Is there a good guide anywhere?It is more difficult to explain than to do it! :) The installation disk will do it for you (yet, giving you choices). If you want an overview of the installation process, have a look here:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

> I will be using XP just for games and Linux for pretty much everything else. So I will probably reformat XP first, then choose the size of the partition (this is where I get confused, when and what with do I resize the partition with?).You don't need to do that. Ubuntu will resize the partition without damaging your windows installation. Just make a defrag of your HD before to start the ubuntu installation....

> Also, once Ubuntu is installed, do I need to install any drivers for GFX card, WiFi, etc, etc?Yes. If you wait for Feisty, that version has a simplified procedure for doing all of that... anyhow... millions of other newcomers have managed with Edgy as well, so you shouldn't be scared, just know with Feisty is quicker/easier... :)

> I would like a guide to explain what to do once Ubuntu is installed.See the link above.
**[COLOR=Red]EDIT:[/COLOR]** sorry, I answered too quickly and misread your question. Things you might wish to do AFTER ubuntu will be installed are so many that it is impossible to give a single answer. Have a look to these two community-maintained pages (for Edgy and Feisty respectively) they are quite comprehensive...
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
[http://ubuntuguide.org/wiki/Ubuntu_Feisty](http://ubuntuguide.org/wiki/Ubuntu_Feisty)

> Will I need an antivirus and firewall?The firewall is always a good idea. Antivirus is not strictly necessary (GNU/Linux is essentially virus-proof), yet you might wish to install it to check the windows files (sent by friends with M$ stuff) that will transit on your machine.

Both the FW and the AV can be installed from within ubuntu (no need to download third-party softwares from around the internet...)

---

### Post by 67GTA on 2007-04-06
Check out these two links and you should be able to find what you need. If not then post back and we will do what we can. [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)  and  [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by Doug11 on 2007-04-06
> **ChrisUK said:**
> Hi all.

I am new to Linux and have some questions.

Is it true that 7.04 is being released on the 19th of April?
If so, there is no point in me installing Edgy now, if a new version is coming out that soon.

I would like to dual boot Windows XP with Ubuntu but I don't really understand how... Is there a good guide anywhere?
I will be using XP just for games and Linux for pretty much everything else. So I will probably reformat XP first, then choose the size of the partition (this is where I get confused, when and what with do I resize the partition with?).

Also, once Ubuntu is installed, do I need to install any drivers for GFX card, WiFi, etc, etc? 
I would like a guide to explain what to do once Ubuntu is installed.

Will I need an antivirus and firewall?

Thanks in advance.
Chris

There are many good guides to this. You just have to do a little searching in the forums, but if you are going to reformat, that makes it alot easier on yourself. Just when you are reinstall xp FIRST, just create an extra partition for your Ubuntu. Once that is finished, run your Ubuntu install disc, and GParted will find your xp partition and your extra partition. You will have to create another small partition for your swap>I usually give it around 2 gigs, then use the rest for your "/". This is a much easier way than trying to keep your existing XP and resizing it, then installing Ubuntu because chances are your grub will get lost somewhere and one of the two wil not end up booting and you then have another headache. As far as your WiFi, find out what you have on your machine, then search it to see what you need. Some work out of the box, some don't. As far as antivirus and firewall, I don't, but that's my choice as I'm the only one that uses this PC. In my opinion, Ubuntu is a learning experience and came become quite addicting. good luck and have fun.

---

### Post by siciliancasanova on 2007-04-06
There is an auto partition to set up dual boot when you install ubuntu.  It's one of the core and required steps for installing ubuntu so you won't miss this step.  You simply select how much you want to resize your NTFS.  If this route doesn't work for you, then seek out the guides to do it manually.

The topic of drivers in general will be only a general response.  I have an hp a1116 and found all my hardware to be compatable on 6.10 except for my broadcom 4318 wireless card.  However, I went up and installed Feisty and found that my broadcom is now supported off the install where as it wasn't with Edgy.  To find the most accurate guide for drivers would be to first get ubuntu installed, find out what isn't working and find guides for your specific problem.  Any problems I have found, the problem has already existed somewhere else and has been answered.  

This [psychocats site]("http://www.psychocats.net/ubuntu/index") really helped me with 6.10 as I was a completely new user to ubuntu.  It's a smaller, to the point guide for someone who has never used linux.  I'm sure others will reccomend the [ubuntu wiki]("https://wiki.ubuntu.com/"), which is good, but it's huge and found it easier to go into all of that once I got the basics down.

Also with the topic of firewall and virus', I have a firewall installed but the purpose of the firewall is not related to malware or spyware.  You will notice with ubuntu that when you need to do a change to something in the root, it will ask you for your password.  This keeps malicious programs from damaging your file structure.  I'm sure you've seen the Regedit changed around by some virus' on your machine, this would never be the case in ubuntu.

---

### Post by KIAaze on 2007-04-06
You can install Edgy Eft now and then upgrade to Feisty Fawn over the internet.
It's not necessaru to reinstall the OS. ;)

By the way, you can also install Feisty Fawn now, although it's still in the testing stage.
But if you are new to linux, I wouldn't recommend it. (and also because I got Beryl to work on edgy and never on feisty...)

> Is there a good guide anywhere?
Certainly!
Just google for it. ^^
I don't know which tutorial is the best, but I know there are a lot of them on the web...

Anyway, if I remember correctly, the Ubuntu CD offers you the possibility to repartition when you start the install and then takes care of everything for the dual-boot.
And it has a graphical interface. :)

> when and what with do I resize the partition?
Ubuntu will offer you this possibility.
And if you really want to do it before the installation, I recommend the [Gnome Partition Editor Live-CD]("http://gparted.sourceforge.net/livecd.php").

> Also, once Ubuntu is installed, do I need to install any drivers for GFX card, WiFi, etc, etc? 
Most things work directly, at least the necessary stuff like mouse, keyboard, monitor.
For other hardware, it depends on what you have.
I bought a WiFi card with an atheros chipset and it worked directly without installing any driver. (I also asked the vendor before to be sure of course)
Video cards will work, but you might not get full 3D acceleration directly.
NVidia cards seem to have better Linux support than ATI cards however.
ACPI support (i.e: hibernating, sleep, powersaving, etc) is also not always easy.

In any case, if you have problems with your hardware, the best solution is always to search google or ask on linux forums like this one.
If you intend to buy new hardware:
-check for linux compatibility on the internet
-ask the vendor
-or even bring a [Knoppix Live-CD]("http://www.knopper.net/knoppix/index-en.html") (or the [Ubuntu Live-CD/DVD]("https://help.ubuntu.com/community/LiveCD")) to the shop to test it directly. ;)

> Will I need an antivirus and firewall?
It's not necessary (I don't have them), but it's possible to install some.
I don't know any Linux firewalls, but as for antiviruses, there is ClamAV.

edit: me spent to much time typing... ^^'

---

### Post by ChrisUK on 2007-04-06
Wow!

Thank you soo much for all the info and help. I will read through the recommended guides which I am sure will help.

I do have another question, but this is about Windows.
I have looked in "Disk Managment" to check out my partition's and I was expecting to see just one big NTFS partition for Windows, but I noticed quite a few other partition's on there, which I think might be to do with my Dell laptop.
One of them didn't have a name and was taking up 4.64GB so I deleted it using the Disk Managment.
Now it is showing it as "Unallocated" but obviously I would want that 4.64GB added onto the Windows partition - can Disk Managment do this? Or do I need a program?
I guess I just really need to know how to resize my partition's within Windows, I am guessing Disk Management can't do this?

---

### Post by houstonbofh on 2007-04-06
This is important.  Never do thing until you know what you are doing.  Either you deleted the Dell restore partition, or the Dell diagnostic partition.  This is OK, as it is your system, but you can not use Dell System Restore CDs after that.  Another thing that can go is a Media partition to play DVDs without booting...

Why do I say this after the fact?  So that later you don't delete key stuff or overwrite key stuff.  If in doubt, ask.

Now the teacher mode is off...  Feisty is in the last rush, so daily updates are numorious, but you can install it now.  I am running it, and have no regrets.  Psychocats web page is also a must read.  If you are worried, read his section on partimage, and burn your clean Dell to a DVD.  No worries after that!  It can even be done from a Live CD.

Good luck, and have fun!

---

### Post by ChrisUK on 2007-04-06
> **houstonbofh said:**
> This is important.  Never do thing until you know what you are doing.  Either you deleted the Dell restore partition, or the Dell diagnostic partition.  This is OK, as it is your system, but you can not use Dell System Restore CDs after that.  Another thing that can go is a Media partition to play DVDs without booting...

Why do I say this after the fact?  So that later you don't delete key stuff or overwrite key stuff.  If in doubt, ask.

Now the teacher mode is off...  Feisty is in the last rush, so daily updates are numorious, but you can install it now.  I am running it, and have no regrets.  Psychocats web page is also a must read.  If you are worried, read his section on partimage, and burn your clean Dell to a DVD.  No worries after that!  It can even be done from a Live CD.

Good luck, and have fun!

Oooops!!

Thanks for the advice and help.
It turn's out it was the Dell's restore partition, which basically restores the Dell back to factory settings. I don't really think it is needed and it was taking up nearly 5GB of space.
I am usually pretty careful about these things, the other partition was named "MEDIADIRECT" so I knew it was to do with the Dell MediaDirect, but the partition I deleted was unrecognised/unnamed, so I didn't really think it was anything important.
Anyway, I don't think I would of used it so no big loss.

How easy is it to update from 6.10 to 7.04? Is it like Windows and you need to completely reformat and install the new version, or is easier to update?

Thanks again.

---

### Post by flight_master on 2007-04-06
Hi There,


Nope - it's much easier. It's kind of like going from 6.06 to 6.10, which was:

Update your sources.lst file (official mirrors will be made available upon release).

Opening a Console, and typing in:

sudo apt-get update
sudo apt-get dist-upgrade


When that completes, reboot, and you're running the latest version!


Best Regards,
Christian A. Herrnboeck

---

### Post by mac.ryan on 2007-04-07
Hi Chris, I also dualboot on a dell. Our systems might be different (mine is in the signature), but my experience is...

> **ChrisUK said:**
> It turn's out it was the Dell's restore partition, which basically restores the Dell back to factory settings. I don't really think it is needed and it was taking up nearly 5GB of space.

My "recovery disk" is just a plain windows installation disk. When I got my computer, I simply buldozed the HD (lot of crap bundle software was already pestering it) and had a clean reinstall.... So there is a chance you didn't delete anything important at all. At the contrary, you might have just sanitized your computer! ;)

> the other partition was named "MEDIADIRECT" so I knew it was to do with the Dell MediaDirect, but the partition I deleted was unrecognised/unnamedYes, the partition was to run the "quickboot" for watching DVDs, pictures, etc... (BTW: the partition is normally a FAT16). Anyhow, to run mediadirect you need also windows installed (mediadirect runs "bits" of windows installation)... and - at the time I was configuring my computer, I didn't find a way to have the computer triple-booting MD/XP/Ubuntu (some user might have come up with a solution meanwhile, though).

In my present configuration, if I now press the mediadirect key, I got a MD splash screen and then my dual-booting GRUB.

> Now it is showing it as "Unallocated" but obviously I would want that 4.64GB added onto the Windows partition - can Disk Managment do this?How to move the starting point of a partition is being discussed [here]("http://ubuntuforums.org/showthread.php?t=402778").

---

### Post by houstonbofh on 2007-04-07
For the record, I have several Dell systems, and none of them have restore or media partitions. :)  It was the "I didn't know what this was so I deleted it" part I was commenting on.

As to upgrades, it depends...  The closer you are to stock, the simpler it is.  If you have restricted driver, or complied drivers, or complied kernal programs that run at boot, you may have issues.  If everything is packages from official repositories, you are fine.

**Also the upgrade information you were given was wrong!**  There is a **huge** thread on the recomended upgrade method. It eliminates many problems.  The method mentioned above may work, or may not.  It has issues.  The official method has a lot of failsafes built in, and you want them!

**Offical Upgrade method:**
To upgrade to the next distribution, bring up a shell. (Applications --> Accessories --> Terminal) Type 'sudo update-manager -c' and follow the prompts.

---

