---
title: "Fedora 18 tryout"
date: 2013-02-23
forum: Any Other OS
---

### Post by offgridguy on 2013-02-23
After a failed attempt yesterday, I have fedora 18 installed today.
I don't even know what DE this , something new to me, to soon to pass
judgement on that.
   I will definitely have to do something to make the screen look more appealing.

But more to the point, I installed this distro because of this claim they
make in their advertising

> Desktop: Have you ever tried to use a new printer and been frustrated by error messages and having to hunt for the correct driver to install? With the new easy printing feature in Fedora 14, plug your printer in and Fedora automatically finds and installs the correct driver. This feature allows you to print in many different locations and churn out copies within minutes. It's one of several innovations in Fedora 14 that let you take better advantage of your system's hardware.

I thought, this sounds too good to be true, and you know what!!
It is too good be true,  but in spite of that, i will work with this
system for awhile to see if it stays or gets punted.

One major disadvantage of this OS when installing on a multi-boot computer
it uses a different partitioner, anaconda{I think}, only likes to install on LVM, needs a separate primary partition from my other OS's and seems
impervious to gparted's ability to edit, change or delete.

But it may have some redeeming features in there somewhere, I will be sure
to mention them if/when I find them.:):)

---

### Post by CharlesA on 2013-02-23
If the version of Fedora you installed was the default, it is running Gnome 3. :)

---

### Post by haqking on 2013-02-23
> **offgridguy said:**
> After a failed attempt yesterday, I have fedora 18 installed today.
I don't even know what DE this , something new to me, to soon to pass
judgement on that.
   I will definitely have to do something to make the screen look more appealing.

But more to the point, I installed this distro because of this claim they
make in their advertising


I thought, this sounds too good to be true, and you know what!!
It is too good be true,  but in spite of that, i will work with this
system for awhile to see if it stays or gets punted.

One major disadvantage of this OS when installing on a multi-boot computer
it uses a different partitioner, anaconda{I think}, only likes to install on LVM, needs a separate primary partition from my other OS's and seems
impervious to gparted's ability to edit, change or delete.

But it may have some redeeming features in there somewhere, I will be sure
to mention them if/when I find them.:):)

Fedora 18 runs rock solid for me, best distro to date for me in all aspects (and I am a long time Slackware, Debian/Ubuntu user and way back in the day Suse and others)

I am running x64 on modern hardware and not a single issue.

I am running latest Nvidia 313 driver and again great.

Referring to your quote which is about F14 and you are running F18 so out of context, however both my Brother Laser and Epson inkjet worked out of the box.

The fact you dont know what DE you are using even though you downloaded it....mmmmmm no comment.  The default is Gnome, i run the KDE spin.

Anaconda is the installer, you can choose any partitions you created with Gparted (I did) and I am multibooting. And like all Linux OS it does not require a primary, it can sit fine in either a primary or logical. And mine is not on LVM.

Everyones mileage varies for everything though of course

---

### Post by offgridguy on 2013-02-23
> **haqking said:**
> Fedora 18 runs rock solid for me, best distro to date for me in all aspects (and I am a long time Slackware, Debian/Ubuntu user and way back in the day Suse and others)

I am running x64 on modern hardware and not a single issue.

I am running latest Nvidia 313 driver and again great.

Referring to your quote which is about F14 and you are running F18 so out of context, however both my Brother Laser and Epson inkjet worked out of the box.

The fact you dont know what DE you are using even though you downloaded it....mmmmmm no comment.  The default is Gnome, i run the KDE spin.

Anaconda is the installer, you can choose any partitions you created with Gparted (I did) and I am multibooting. And like all Linux OS it does not require a primary, it can sit fine in either a primary or logical. And mine is not on LVM.

Everyones mileage varies for everything though of course
I have no intention of a flame war with anyone. I am sure fedora has it's share of supporters.  The quote regarding fedora 14 is out of context, but
it is the quote the seller used in their description selling fedora 18 on
ebay.  I was unsuccessful in installing to a pre-created partition, so
i let the installer use the free space, where it used LVM, that seems
to be format it prefers.
The anaconda installer didn't seem to give me the options that gparted does
but then I am not real familiar with it either.

One thing fedora does that no other OS has done is give me a warning message about the core temperature being to high.

edit; I wasn't real disappointed  in the printer , no other linux OS has managed
that , without some help either.

---

### Post by haqking on 2013-02-23
> **offgridguy said:**
> I have no intention of a flame war with anyone. I am sure fedora has it's share of supporters.  The quote regarding fedora 14 is out of context, but
it is the quote the seller used in their description selling fedora 18 on
ebay.  I was unsuccessful in installing to a pre-created partition, so
i let the installer use the free space, where it used LVM, that seems
to be format it prefers.
The anaconda installer didn't seem to give me the options that gparted does
but then I am not real familiar with it either.

One thing fedora does that no other OS has done is give me a warning message about the core temperature being to high.

LOL i wasnt flaming, I was merely making corrections to your statements as oppose to what could of been questions to make it clear to others who may be reading.  I am not a fanboy of anything, I just prefer specifics and facts thats all.

There have been alot of reviews about the renewed anaconda installer (which has changed in F18) specifically concerning the partitioner and I agree it is not the best.  But the reviews are from people who dont really understand the partitioning or mount points that well which is fair enough.  There are plans to address it in F19 i believe.  I personally always do my partitions in Gparted, I just used anaconda to mount the partitions I wanted.  I did play with the partitioner in a VM to see what it was like and like i say it wasnt the best ive seen.

Peace

Why would you buy F18 from ebay ? it is a free download.

---

### Post by CharlesA on 2013-02-23
I just did a netinstall of Fedora 18 and it let you do the partitions yourself, but when I did it, I had to select "reclaim space" before it let me create new partitions.

---

### Post by offgridguy on 2013-02-23
> **haqking said:**
> 

Why would you buy F18 from ebay ? it is a free download. Thanks for the reply.  Probably a lot of people wonder why I would buy from ebay.

The answer, My internet service plan only gives me 500mb , every additional 500mb or
portion thereof costs me an additional $10, monthly rate.  I am always over
the minimum 500mb.{who wouldn't be}.  I am not sure what size the fedora download is but say 1500mb, could cost me $30.

I do download and burn some of my own, but only when i can make it to the
public library.

---

### Post by offgridguy on 2013-02-23
> **CharlesA said:**
> I just did a netinstall of Fedora 18 and it let you do the partitions yourself, but when I did it, I had to select "reclaim space" before it let me create new partitions.Thank you for the info, were you able to use
the ext4, format?

---

### Post by haqking on 2013-02-23
> **offgridguy said:**
> Thanks for the reply.  Probably a lot of people wonder why I would buy from ebay.

The answer, My internet service plan only gives me 500mb , every additional 500mb or
portion thereof costs me an additional $10, monthly rate.  I am always over
the minimum 500mb.{who wouldn't be}.  I am not sure what size the fedora download is but say 1500mb, could cost me $30.

I do download and burn some of my own, but only when i can make it to the
public library.

Gotcha, well enjoy your rootkits and remote access trojans.....LOL

;-)

---

### Post by haqking on 2013-02-23
> **offgridguy said:**
> Thank you for the info, were you able to use
the ext4, format?

yes it supports all linux supported formats.  ext4 is default now with most modern Linux distros

---

### Post by CharlesA on 2013-02-23
> **offgridguy said:**
> Thank you for the info, were you able to use
the ext4, format?

I think it was ext4, but I didn't really look too closely all the distros I've tried so far have defaulted to ext4.

---

### Post by buzzingrobot on 2013-02-24
Fedora 14 is quite aged, at this point.  Fedora distributes only free and open source software.  If your printer, for example, requires a proprietary driver, then Fedora will, in fact, in my own experience, set the printer up correctly.  It won't work, though, until you install the driver.  Many distributions take a similar approach.

Anaconda is the Fedora installer, not just the installer's partitioner.  It defaults to LVM, but that is an option the user can change via the GUI.

Fedora is essentially a proving ground for new software sponsored by Red Hat.  New releases of Red Hat Enterprise Linux are based on Fedora. Fedora is intended to be pretty bleeding edge, releasing every 6 months.  Red Hat is intended to be very stable, releasing a new product once in several years.

You can stay very current with very new stuff with Fedora, just don't expect it to be without occasional issues. 

If you are going to use Fedora 18, you should read their posted list of common bugs and the release notes.

---

### Post by offgridguy on 2013-02-24
Thank you for the input, I noticed that other distro's such as
Manjaro and Sabayon use the same or very similar installer.
There is no doubt that most of the issues i have are due to lack of experience with these different install methods.

---

### Post by UltimateCat on 2013-02-24
Don't worry as you use and learn more about distro's you'll get better with all kinds of tasks. I did-

When I installed Fedora I choose **manual installation **I prefer it over allowing the installer to do it for me automatic is fine if your not in a dual boot with another operating system.

These Fedora pages should be of some use to you:

[http://docs.fedoraproject.org/en-US/Fedora/16/html/System_Administrators_Guide/ch-yum.html#sec-Checking_For_and_Updating_Packages](http://docs.fedoraproject.org/en-US/Fedora/16/html/System_Administrators_Guide/ch-yum.html#sec-Checking_For_and_Updating_Packages)

[https://fedoraproject.org/wiki/Releases/18/Schedule?rd=Releases/18](https://fedoraproject.org/wiki/Releases/18/Schedule?rd=Releases/18)

[https://fedoraproject.org/wiki/Communicating_and_getting_help](https://fedoraproject.org/wiki/Communicating_and_getting_help)

Enjoy your new distro!

---

### Post by Stinger on 2013-02-24
If you want Fedora with all the things working right out of the box, try the new [Korora 18 - Beta (Flo)]("https://kororaproject.org/download/") from the [Korora Project]("https://kororaproject.org/"). Comes in both Gnome and KDE flavours ;)
On the live image there is a nice introduction video to the new Anaconda installer made by Chris Smart, gives a good introduction to the partitioner too ( can be quite confusing if you haven't been introduced to it #-o )

---

### Post by offgridguy on 2013-02-24
> **UltimateCat said:**
> Don't worry as you use and learn more about distro's you'll get better with all kinds of tasks. I did-

When I installed Fedora I choose **manual installation **I prefer it over allowing the installer to do it for me automatic is fine if your not in a dual boot with another operating system.

These Fedora pages should be of some use to you:

[http://docs.fedoraproject.org/en-US/Fedora/16/html/System_Administrators_Guide/ch-yum.html#sec-Checking_For_and_Updating_Packages](http://docs.fedoraproject.org/en-US/Fedora/16/html/System_Administrators_Guide/ch-yum.html#sec-Checking_For_and_Updating_Packages)

[https://fedoraproject.org/wiki/Releases/18/Schedule?rd=Releases/18](https://fedoraproject.org/wiki/Releases/18/Schedule?rd=Releases/18) 


[https://fedoraproject.org/wiki/Communicating_and_getting_help](https://fedoraproject.org/wiki/Communicating_and_getting_help)

Enjoy your new distro!
Thank you for the links

@ Stinger, thank you for the input.

---

### Post by BBQdave on 2013-02-25
> **CharlesA said:**
> I think it was ext4, but I didn't really look too closely all the distros I've tried so far have defaulted to ext4.

Debian, Linux Mint and Ubuntu default to ext4 - Fedora defaults to LVM.

---

### Post by offgridguy on 2013-02-25
> **BBQdave said:**
> Debian, Linux Mint and Ubuntu default to ext4 - Fedora defaults to LVM.You are correct, Thank you

---

### Post by haqking on 2013-02-25
> **BBQdave said:**
> Debian, Linux Mint and Ubuntu default to ext4 - Fedora defaults to LVM.

> **offgridguy said:**
> You are correct, Thank you

Just remember that LVM in of itself is not a filesystem though.

You can use ext3, ext4 etc as your filesystems on your partitions that are on top of the LVM array.

---

### Post by malspa on 2013-02-25
I've got Fedora 18 (GNOME) running here. Looks very good so far (a little over a month since I installed it), but I'm not quite sure I'd go this far:

> **haqking said:**
> Fedora 18 runs rock solid for me, best distro to date for me in all aspects (and I am a long time Slackware, Debian/Ubuntu user and way back in the day Suse and others)

But I'd have a difficult time calling *any* distro "the best."

Anyway, the new Anaconda isn't perfect, but I installed F18 without too much difficulty; multi-boot set-up.

I normally create my partitions ahead of time, usually with GParted, sometimes with KDE Partition Manager.

---

### Post by haqking on 2013-02-25
> **malspa said:**
> I've got Fedora 18 (GNOME) running here. Looks very good so far (a little over a month since I installed it), but I'm not quite sure I'd go this far:



But I'd have a difficult time calling *any* distro "the best."

Anyway, the new Anaconda isn't perfect, but I installed F18 without too much difficulty; multi-boot set-up.

I normally create my partitions ahead of time, usually with GParted, sometimes with KDE Partition Manager.

I didnt say it was the best, I said the "best distro to date** for me**" meaning in my long running experience of Linux, F18 as proven itself to be my favourite and least problematic for "me" and so therefore my best.


I have no doubt others will not like it, wont get on with it or it simply wont work for them.

There is no best, only the best for "you". Everyone's mileage will vary as always.

Peace

---

### Post by malspa on 2013-02-25
> **haqking said:**
> I didnt say it was the best, I said the "best for me" meaning in my long running experience of Linux F18 as proven itself to be my favourite and least problematic for "me" and so therefore my best.

Sorry, I did notice that you said "for me," but didn't make note of that in my post. I understand that any use of the term "best" when it comes to Linux distros is gonna be highly subjective. No offense intended.

---

### Post by buzzingrobot on 2013-02-25
> **BBQdave said:**
> Debian, Linux Mint and Ubuntu default to ext4 - Fedora defaults to LVM.

Apples and oranges.

LVM is, basically, a way to partition drives to allow easy addition of more drives in the future.

Ext4 is a filesystem.

Two very different things.

Fedora does default to LVM, which is as reasonable as not defaulting to LVM, but changing that takes but one mouse click.

---

### Post by buzzingrobot on 2013-02-25
> **malspa said:**
> I've got Fedora 18 (GNOME) running here. Looks very good so far (a little over a month since I installed it), but I'm not quite sure I'd go this far:



If you like docks, look at the Dash to Dock extension.  Very nice.

---

### Post by offgridguy on 2013-02-25
All the input has gotten me curious, so I did a reinstall,  17 minutes from Live CD
in case anyone is interested.  I did manage to install to a previous partition, 20 gb.
Thanks to Charles A for the reclaim space tip.:D  Not sure why but this time I have an improved grub menu, does show my other options.

Can't say that I care for the gnome3 DE, any suggestions on how to dress it up?

One thing that I forgot to mention last time, the install allows you to set a root 
password, first thing.  I think this is a huge plus for anyone who wants control
of their computer, instead of vice-versa.  Do any other linux  distro's offer this option ?

Without a stopwatch I would say it compares with ubuntu 12.04 for speed. Not bad.

edit; I notice that there is no log out option, at least I can't find one with this DE.
Also noticed,that the 20gb partition I installed to is now 3 partitions, a 500mb boot,
a 3.1 swap and 17.1 for the system. It seems to want it's own swap, as there is now 2 swap partitions.  The size discrepency is probably due to there being a small amount of
unallocated available ahead of the 20gb partition prior to install. Also format is ext4.

---

### Post by ACubed10 on 2013-02-25
ok ok, I give.  Downloading Fedora 18.  Going to do a full install and actually try it out for longer than 5 minutes in a virtual machine

---

### Post by BBQdave on 2013-02-26
> **buzzingrobot said:**
> Fedora does default to LVM, which is as reasonable as not defaulting to LVM, but changing that takes but one mouse click.

There are three choices, can not remember how they are labeled. But something like this:
*Basic* or *Standard*
*LVM*
and *I can not remember the third choice* :D

I always chose *Basic*, it works best for my purposes.

---

### Post by Armann on 2013-02-27
> **offgridguy said:**
> 
One thing that I forgot to mention last time, the install allows you to set a root 
password, first thing.  I think this is a huge plus for anyone who wants control
of their computer, instead of vice-versa.  Do any other linux  distro's offer this option ?


Redhat, Centos and Fedora let you do this.
Enabling the root user in Ubuntu/Mint/Debian is really easy
but it's against the rules to post that here. :)

I really like Fedora but I don't really like Gnome 3... ;)

---

### Post by offgridguy on 2013-02-27
> **Armann said:**
> 

I really like Fedora but I don't really like Gnome 3... ;)

I hear you

---

### Post by malspa on 2013-02-27
> **Armann said:**
> I really like Fedora but I don't really like Gnome 3... ;)

The default download is GNOME; they also have KDE, LXDE, and Xfce spins: [http://fedoraproject.org/en/get-fedora-options](http://fedoraproject.org/en/get-fedora-options)

For my Fedora installations, I've been going back and forth between KDE and GNOME -- I installed F17 KDE, then F18 GNOME, for example. But I'm fine with GNOME Shell...

---

### Post by Armann on 2013-02-27
Yeah I know, I can't use KDE at all, that's just me, haven't really given it the time it deserves. ;)
Xfce is fine, I used to use Gnome for everything
but I can't accept them taking a lot of settings away
from the user and dumbing the whole window manager down.

---

