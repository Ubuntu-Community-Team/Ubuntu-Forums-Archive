---
title: "Is LVM for a beginner?"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by MichaelZ on 2006-05-12
Hello,

I would like to ask if LVM could be used by a beginner or it is for more advanced users.

Thanks.

Best wishes,
Michael

---

### Post by yota on 2006-05-12
LVM is well documented, and simple configurations are pretty straight-forward, but surely you must have no fear of man pages and command line to use lvm effectively.

Moreover I think that "is LVM (useful) for a home computer?" is a relevant question too.

IMHO if you are a beginner looking to spend time to experiment with every piece of exotic linux stuff, willing to learn and not afraid of studying a bit maybe LVM is ok for you; if you're instead looking for the best setup for your home pc with the minimum effort necessary, maybe it's not.
Surely there're better things to start with, before have to deal with LVM.

So... what type of beginner are you? And what do you want to do with LVM?

---

### Post by s0cket on 2006-05-12
I wouldn't recommend a beginner get into LVM.  It can be a little bit daunting for even a seasoned admin who manage to avoid the topic of logical volume management through their career.  LVM has a huge amount of flexibility and hence a good dose of complexity.

I would recommend before you tackle LVM you hit the basics.  How Linux/Unix handles storage devices.  How block devices work and all the basic Linux/Unix file system tools.  How the kernel and init work with fstab in the boot process.

Once you feel confident in these areas you can safely move onto LVM concepts and tools.

---

### Post by MichaelZ on 2006-05-12
[quote=yota]
So... what type of beginner are you? And what do you want to do with LVM?[/quote] 
Hello,

Thank you for your reply.

I have not a lot of experience with Linux. The first time I have installed Ubuntu, I chosed LVM, not because it was suitable for me, but just to try it. Anyway, I just needed a system to let me learn and discover Linux, but also to let my build .deb packages for [CodeBlocks IDE]("http://www.codeblocks.org").

Successively I wanted to make some free space and give Gentoo a try. Unfortunately it was not easy, because of the LVM. Therefore, I have tried to remove it, by using lvremove from a Live CD. The command "worked", but then my Ubuntu refuse to start. The Volume Group was missing and so the /dev/mapper/Ubuntu-root.

Consequently, my system was broken and I was unable to restore it.

So, I decide to re-install Ubuntu. Playing a bit with LVM and manual partitioning shows me that I was unable to correctly set up my partitions (the installation refused to continue without errors and always brought me back the the partitions list).

This is why I asked if LVM was suitable for a beginner. I have heard that it is great and probably it is, but I still have some troubles to make it works.

Best wishes,
Michael

---

### Post by MichaelZ on 2006-05-12
[quote=s0cket]
I would recommend before you tackle LVM you hit the basics.  How Linux/Unix handles storage devices.  How block devices work and all the basic Linux/Unix file system tools.  How the kernel and init work with fstab in the boot process.
[/quote] 
Hello,

Yes, I think this is the way I should take. Especially at the beginning.

Thank you.

Best wishes,
Michael

---

### Post by catlett on 2006-05-12
[http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)
I found this site as a link off of the dual boot link I use [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm) It seems pretty thorough but I wouldn't  know the difference between good LVM documantation and bad documentation.:-k  Just thought I'd post it in case it is informative.

---

### Post by skippy81 on 2006-05-12
Good FAQ you posted there, I had no idea what LVM did until I started reading that link :p

---

### Post by user1397 on 2006-05-12
how do i know if i installed ubuntu with LVM or not? i don't remember...

---

### Post by mlind on 2006-05-12
[QUOTE=erik1397]how do i know if i installed ubuntu with LVM or not? i don't remember...[/QUOTE]

if command **df** shows any output of /dev/mapper/.. on Filesystems tab.
or try **sudo lvm lvdisplay**

---

### Post by user1397 on 2006-05-12
[quote=mlind]if command **df** shows any output of /dev/mapper/.. on Filesystems tab.
or try **sudo lvm lvdisplay**[/quote]
using these commands, i have comfirmed that i do not have LVM.
is this any disadvantage to me? or advantage?
(i'm a beginner-only been using linux since March 2006)

---

### Post by MichaelZ on 2006-05-13
[quote=catlett][http://www.tldp.org/HOWTO/LVM-HOWTO/]("http://www.tldp.org/HOWTO/LVM-HOWTO/")
I found this site as a link off of the dual boot link I use [http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm") It seems pretty thorough but I wouldn't  know the difference between good LVM documantation and bad documentation.:-k  Just thought I'd post it in case it is informative.[/quote] 
Hello,

Thank you for the links :). Very interesting.

The first I have found after I had messed up my LVM :(.

Anyway, yesterday I have tried to re-install Ubuntu without LVM and by dividing my hardisk into two parts. One for Ubuntu and the other for Gentoo. After installing Ubuntu, I tried to install Gentoo with the graphical installer. I selected the empty partition and chosen the "automatically partition" method. At the end, I have had a computer that only let me start Gentoo. Ubuntu was invisible in the Grub. Moreover Gentoo start in console mode. No desktop despite I have selected to install Gnome...

Best wishes,
Michael

---

### Post by mlind on 2006-05-13
[QUOTE=erik1397]using these commands, i have comfirmed that i do not have LVM.
is this any disadvantage to me? or advantage?
(i'm a beginner-only been using linux since March 2006)[/QUOTE]

If you've ever encounted a problem where you would need to redistribute free space
for some of your existing partitions, or you would like to install another linux distro
to separate partition, but you have found this suprisingly hard or tedious task to
do - then LVM is your thing.

With LVM I can dynamically modify size of my linux partitions, or even grab a chuck
of free space from other HDD and include it to my existing Logical Volumes
(like partitions) to use. Or if I want to install new test version of ubuntu on a exotic
filesystem, I just squeeze little space from my existing /home partition, create new
Logical volume, set it filesystem to JFS for example and install new ubuntu there.

Examples are maybe bad, but you get the picture. Managing your data/space
inside umberella called LVM is easier than with normal partition table stuff.


I'm actually suprised why Ubuntu installer doesn't yet use LVM by default
like current fedora does.

---

### Post by MichaelZ on 2006-05-13
[quote=mlind]If you've ever encounted a problem where you would need to redistribute free space
for some of your existing partitions, or you would like to install another linux distro
to separate partition, but you have found this suprisingly hard or tedious task to
do - then LVM is your thing.
[/quote] 
Hello,

LVM is a good thing. But if you are a beginner, I think not. For example in my case, I used LVM and did want to make place to install Gentoo. Well, I geve the wrong command and messed up my system.

I think that when you earn more experience, then LVM would be an interesting option for you.

Best wishes,
Michael

---

### Post by catlett on 2006-05-13
This is my grub menu section for Ubuntu.> # This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.12-10-386 (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu, kernel 2.6.12-10-386 (recovery mode) (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot
You need to edit Grub in gentoo to have an entry for Ubuntu. The debian install did it for me. If you are running Ubuntu Breezy then these entries should work for you. THE ONLY ISSUE IS WHICH PARTITION YOUR UBUNTU INSTALL IS ON. Mine is on  /dev/hda3 which is the 3rd partition of my first hard drive. Grub sees it as hd0,2. With grub everything is 1 behind linux because grub counts 0 as a marker. So you need to find the partition for Ubuntu and make the change from /dev/hda3 to yours and to change hd0,2 to yours.
You need to edit your grub menu list to do this. First see if your gnome manager is installed type ```
startx
``` This will launch the x window system if it is installed.
As for editing Grub, if this was Ubuntu you would do ```
sudo gedit /boot/grub/menu.lst
``` and you could put the new entry into grub.
I would assume gentoo doesn't have sudo. Then you would have to do ```
su
``` Enter the root password. Then ```
gedit /boot/grub/menu.lst
```
If you don't have gnome gedit won't work. Nano might be part of the underlying linux base and might work but I am just guessing about that. First try startx. If that works then go forward with gedit. You might have to go to the gentoo sight to see the command to install gnome from the console if it doesn't start. Again if this was Ubuntu you would type ```
sudo apt-get install ubuntu-desktop
``` Obviously Gentoo has a similar Gentoocentric command for the gdm but I don't know it.
Post what happens, hopefully someone can jump in.

---

### Post by catlett on 2006-05-13
I just looked at your post again. If you can get into a graphical environment in Gentoo you could mount your Ubuntu partition and then go to your grub menu.lst from Ubuntu and use those entries for your Gentoo grub menu.lst.
For the sake of brevity I'll assume you know how to mount a partition (if not we can deal with that later). Once the partition is mounted double click on it and you'll see your Ubuntu folders. Open /boot. Then open /grub. In grub double click on menu.lst/ This is the list grub made when you installed ubuntu. The entries should be the correct one (unless you moved ubuntu to another partition after you install it). Now open the Gentoo menu.lst as root in gedit and copy/paste the Ubuntu entries in. Save and reboot. Ubuntu will be in your Gentoo grub.

---

### Post by mlind on 2006-05-13
[QUOTE=MichaelZ]Hello,

LVM is a good thing. But if you are a beginner, I think not. For example in my case, I used LVM and did want to make place to install Gentoo. Well, I geve the wrong command and messed up my system.

I think that when you earn more experience, then LVM would be an interesting option for you.

Best wishes,
Michael[/QUOTE]

Hi Mike, it's true what you said. But you should always know what you're doing
when your issuing commands with root privileges.. I've screwed my system so
many times, so that I usually read the man page before doing anything that may
lead to loss of data. 

Accidents, like typos or brainfarts are another thing tho. IMO some linux apps lack
the "Are you really, I mean _really_ sure what are you doing!?  [Y/n]" -type of
questions.

---

### Post by MichaelZ on 2006-05-13
[quote=mlind]Hi Mike, it's true what you said. But you should always know what you're doing
when your issuing commands with root privileges.. I've screwed my system so
many times, so that I usually read the man page before doing anything that may
lead to loss of data. 

Accidents, like typos or brainfarts are another thing tho. IMO some linux apps lack
the "Are you really, I mean _really_ sure what are you doing!?  [Y/n]" -type of
questions.[/quote] 
Hello,

Yes, you are right. It would be better to read before and do after, but sometimes I am so curious that I do before :). Anyway, if what I have to do could dammage my system and I cannot allow this, then I read before the doc and eventually search in the some forums.

Yes, if before accepting some commands you get a warning message, it would be good. In my case, "are you sure that you want to perform lvremove -ff /devv/hda5 ? This would dammage your LVM" (or similar).

Best wishes,
Michael

---

### Post by MichaelZ on 2006-05-13
[quote=catlett]I just looked at your post again. If you can get into a graphical environment in Gentoo you could mount your Ubuntu partition and then go to your grub menu.lst from Ubuntu and use those entries for your Gentoo grub menu.lst.
For the sake of brevity I'll assume you know how to mount a partition (if not we can deal with that later). Once the partition is mounted double click on it and you'll see your Ubuntu folders. Open /boot. Then open /grub. In grub double click on menu.lst/ This is the list grub made when you installed ubuntu. The entries should be the correct one (unless you moved ubuntu to another partition after you install it). Now open the Gentoo menu.lst as root in gedit and copy/paste the Ubuntu entries in. Save and reboot. Ubuntu will be in your Gentoo grub.[/quote] 
Hello Catlett,

Thank you very much for your help :).

What I did was not so good. When I installed Gentoo, I selected the free partition and let Gentoo perform the partitioning. Anyway, this waste some space, because you cannot have more tha 4 primary partitions. Moreover, during the installation, I have chosen Grub (and not Lilo) and to install it into the MBR. I suppose that this has overwritten the Grub done by Ubuntu.

Anyway, the installation of Gentoo was not fully successful. Today, I retried to install before Gentoo and then Ubuntu. Unfortunately, I got problems with unpacking the portage. It seems that the archive is corrupted. Therefore, I have chosen to download the stage tarball and kernel source from Internet (the good thing is that my Internet connection is already configured :)).

To resume, I am now installing Gentoo. I have created a /boot partition (255 MB, primary) a /swap partition (1000 MB, logical) and a / partition (5600 MB, logical (if IIRC)). After finishing and if I did not get errors, I will try to install Ubuntu (and hope not to mess up the partition. It seems that I am good in messing up partition :)). I just hope Ubuntu will see the free space and let me created a primary /boot partion, a /swap and / partitions without overwriting the Gentoo ones.

Tomorrow, I will check if the installation of Gentoo was fine (now it is emerging the kernel sources) and will then install Ubuntu.

Thank you.

Best wishes,
Michael

---

### Post by catlett on 2006-05-13
Like they say "If at first you don't succeed, try, try again". If there is some special "trick", "procedure" or "nuance" to installing with LVM please post. I never did lvm manually, fedora did it by default so I don't know the process for installing manually.
Good luck.

---

### Post by MichaelZ on 2006-05-14
[quote=catlett]Like they say "If at first you don't succeed, try, try again". If there is some special "trick", "procedure" or "nuance" to installing with LVM please post. I never did lvm manually, fedora did it by default so I don't know the process for installing manually.
Good luck.[/quote] 
Hello,

Until now I did not advance. Gentoo installation always fails. Now I am giving a try with the command line installation. Anyway, it seems that when I select some options or press ok, it crashes :(.

I begin to think that I have a somehow corrupted live CD. Strange, because it seems to work fine.

Best wishes,
Michael

---

