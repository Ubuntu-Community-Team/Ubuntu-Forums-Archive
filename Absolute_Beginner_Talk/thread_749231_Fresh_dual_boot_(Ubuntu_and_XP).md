---
title: "Fresh dual boot (Ubuntu and XP)"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Synkboy on 2008-04-08
Hi there, bit of advice needed.

Just built up a new PC, and I have a fresh 250gb HD in it, and I intend to do a dual boot of Ubuntu 7.10 and Windows XP.

Now someone advised me to put Ubuntu on first, as XP messes with the MBR when you try to install Ubuntu second.

Now this is double dutch to me, so could someone please tell me which to install first?, and does anyone have a good idiot proof guide I could follow?

Merci.

---

### Post by munkyeetr on 2008-04-08
Actually that's backwards, the *easiest* way is to install XP first...

1) Do all your partitioning work (1 for XP in NTFS, 1 for Ubuntu in ext3, 1 for swap, etc...)
2) Install XP
3) Install Ubuntu

By installing Ubuntu second, you will allow the GRUB boot loader to manage your boot menu. GRUB does a very good job of playing nicely with Windows. It doesn't work well the other way around. *Windows likes to pretend that anything that's not Windows doesn't exist.*

After the Ubuntu install, when you boot you'll see a list of operating systems you can choose to boot into.

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

---

### Post by bumanie on 2008-04-08
What you've been told is incorrect. It in fact is best to install before ubuntu as the linux bootlader will recognise your windows installation and give you a choice which to boot into. Windows definitely prefers the first partition on a hard drive. If windows is installed second, it will overwrite the linux bootlader and all you will do (without some editing etc) is boot straight into windows. 
Steps you need to consider
1) Install windows first
2) When installing ubuntu you have to have a / and swap partition, which ubuntu's self partitioing will set up for you, however it is prudent at the partitioning stage to choose manual so that you can set up  the mandatory / (5-6 gig is usually enough) and swap (1-2 gig). Then partition for a separate /home partition, which can be as large as you like. The advantage of this is that if the fikle system of ubuntu becomes corrupted for some reason, you can reinstall to / and all your saved data will be sfae in /home - you only have to format /.
3) If you are very new, this may sound very foreign so you should read a up things before going any further. Unfortunately many guides don't include the idea of setting up a separate /home partition. This is not to be seen as wrong, but a separate /home has advantages re data safety in the event of unforseen circumstances.
Hope this helps.
PS: You could pre-partition your drive with gparted live cd - it does both ntfs and ext3 (among others filesystem formats)

---

### Post by cifdtruckie on 2008-04-08
I actually was in your position just last week - and I was shown these guides which addresses the issue from start to finish!

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

and then

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

It was really not tough whatsoever, took me all of 30 minutes!

---

### Post by kolisikepu on 2008-04-08
All replied posts are correct.  Just in short, if you install windows 2nd over your Ubuntu, you can say goodbye to Ubuntu as you'll never see it again after that.

As already mentioned by one of the posts, what windows does it replaces the MBR (Master Boot Record) at installation making Windows the only OS on your system, so you'll never see your Ubuntu installation again unless you use boot disks for Ubuntu to fix MBR, but that's too messy.

Windows XP 1st and then Ubuntu 2nd.  If you plan in the future for Vista (similar to my setup), then install XP, then Vista and then Ubuntu last.

---

### Post by cifdtruckie on 2008-04-08
> As already mentioned by one of the posts, what windows does it replaces the MBR (Master Boot Record) at installation making Windows the only OS on your system, so you'll never see your Ubuntu installation again unless you use boot disks for Ubuntu to fix MBR, but that's too messy.

Windows XP 1st and then Ubuntu 2nd.  If you plan in the future for Vista (similar to my setup), then install XP, then Vista and then Ubuntu last.


Umm... yeah... that's completely untrue....

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

It takes about 5 minutes!

---

### Post by xxxamazexxx on 2008-04-08
> **kolisikepu said:**
> All replied posts are correct.  Just in short, if you install windows 2nd over your Ubuntu, you can say goodbye to Ubuntu as you'll never see it again after that.

As already mentioned by one of the posts, what windows does it replaces the MBR (Master Boot Record) at installation making Windows the only OS on your system, so you'll never see your Ubuntu installation again unless you use boot disks for Ubuntu to fix MBR, but that's too messy.

Windows XP 1st and then Ubuntu 2nd.  If you plan in the future for Vista (similar to my setup), then install XP, then Vista and then Ubuntu last.

:guitar: Yeah, that's exactly my installation sequence

---

### Post by thegreenblob on 2008-04-08
I personally find it easier to install XP first (using the entire hard drive), and then install ubuntu, cause it will automatically resize the windows hard drive and install its self with grub.

---

### Post by kolisikepu on 2008-04-08
> **cifdtruckie said:**
> Umm... yeah... that's completely untrue....

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

It takes about 5 minutes!

.... for someone like you and I.  Good luck to newbies though.  What I was trying to get at though was just install Windows first then Ubuntu :p

---

### Post by esttorhe on 2008-04-08
> **kolisikepu said:**
> ...you'll never see your Ubuntu installation again unless you use boot disks for Ubuntu to fix MBR, but that's too messy.

even with the live cd and selecting the option to repair the grub? :confused:

---

### Post by kolisikepu on 2008-04-08
> **esttorhe said:**
> even with the live cd and selecting the option to repair the grub? :confused:

Boot disk / Live CD.... same thing. :p

---

### Post by esttorhe on 2008-04-08
lol xD
mmmm, i was planning on installing xp for developing purposes i tried installing visual studio 2005 with wine but it keep saying that i have a trial version installed on my machine, which of course i dont, so i was planning to install windows... :(
mmm, there's no guide to repair the grub with the live cd, im still planning to give it a try

---

### Post by cifdtruckie on 2008-04-08
Yeah all I was getting at is that you may have sounded a bit on the scary side... lol

---

### Post by cifdtruckie on 2008-04-08
> **esttorhe said:**
> 
mmm, there's no guide to repair the grub with the live cd, im still planning to give it a try

Try this...
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by esttorhe on 2008-04-08
thnx, already reading, im going to try it as soon as i get home

thanx

---

### Post by kolisikepu on 2008-04-08
> **esttorhe said:**
> lol xD
mmmm, i was planning on installing xp for developing purposes i tried installing visual studio 2005 with wine but it keep saying that i have a trial version installed on my machine, which of course i dont, so i was planning to install windows... :(
mmm, there's no guide to repair the grub with the live cd, im still planning to give it a try

Go to cifdtruckie's post earlier and you'll see a link he has posted to help with configuring Grub/MBR after installing Windows.

> cifdtruckie 	 		**Re: Fresh dual boot (Ubuntu and XP)**
 		Yeah all I was getting at is that you may have sounded a bit on the scary side... lol

That was the idea with my tactics... :lolflag:

---

### Post by bumanie on 2008-04-08
It is possible to install windows after ubuntu and get both to boot, but is regarded as easier the other way around. May be you should read about grub [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
It is a large site, but very informative.

---

### Post by esttorhe on 2008-04-08
well, i have installed the other way around an is way too easy i know
but i have my laptop with ubuntu and everything working fine and nice, and myself as everyone else, do hate to format and loose everything :(

---

### Post by Synkboy on 2008-04-14
Thanks guys, your links to the guides were invaluable, now rocking it to Ubuntu 7.10(even though I am posting this on my xp laptop).

Many thanks!

---

