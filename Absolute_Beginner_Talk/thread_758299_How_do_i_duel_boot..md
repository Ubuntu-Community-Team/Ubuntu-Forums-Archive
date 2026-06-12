---
title: "How do i duel boot."
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by HebrewTheHammer on 2008-04-17
Hello my fellow linux community. 

I recently acquired a copy of...[SIZE="1"]windows xp[/SIZE]...from my brother for 6 dollars being that he is staff at a college.

I want to duel boot my 250 gig hard drive and give the windows portion between 20-50 gigs of that and use ubuntu for the rest.

I want linux to be installed first because i dont trust window with anything and im afraid that if i use windows to partition my hard drive windows will try and dominate it with its need to be alpha-software.

i know thats probably not possible but i have no idea how to go about doing this and i wont have access to these forums if i screw something up somewhere while trying to just figure it out myself.

any way what im trying to say is can someone post a site or give me step by step instructions on how to install linux, partition, and install windows, duel booting.

i have never done this nor seen it done nor ever seen a computer that has done it. I have no idea how this is done just heard about it on the internet.

if im missing something let me know

thanks in advance.

---

### Post by enigmaniac23 on 2008-04-17
I've used this site before.  One link is for duel boot if you have linux already installed and want to add xp and the other one is if you have xp already installed and want to add linux.

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by LeoSolaris on 2008-04-17
It is much much much easier to install XP first and let it take over the hard drive, then use Ubuntu's Gparted (not the one in the install process, at least not to 7.10) to partition XP down to size. Then do the Ubuntu install in the remaining free space. (or what ever set up you want to do, like /home in a separate partition) It's very simple that way. If you do it the other way around, it is a far more complicated endeavor.

---

### Post by enigmaniac23 on 2008-04-17
I couldn't agree more.  If given the choice, I would absolutely install xp first, and then ubuntu.  That the easier way to do it, as previously stated.

---

### Post by jualansandal on 2008-04-17
--

---

### Post by rsambuca on 2008-04-17
Definitely install XP first when given the option.  I would suggest that you partition the drive prior to installing, though, so you can avoid shrinking/repartitioning after you have already installed XP.  It makes no sense to partition after installation if you have a choice.

---

### Post by Alpinist on 2008-04-17
How do you duel boot?

First you throw down a gauntlet to challenge someone to the duel.  You set up two PCs side by side.  Then you get someone with a stop watch and a starter pistol.  Fire the pistol and both power buttons are pressed at the same time.  Whichever desktop comes up first wins the duel.

On the other hand, if you want to dual boot then the other posts in this thread are more helpful.

---

### Post by HebrewTheHammer on 2008-04-17
thanks dude.

do i have to reformat?

i thought i would. these dont really say

[EDIT] Figured that out.

---

### Post by HebrewTheHammer on 2008-04-17
> **Alpinist said:**
> How do you duel boot?

First you throw down a gauntlet to challenge someone to the duel.  You set up two PCs side by side.  Then you get someone with a stop watch and a starter pistol.  Fire the pistol and both power buttons are pressed at the same time.  Whichever desktop comes up first wins the duel.

On the other hand, if you want to dual boot then the other posts in this thread are more helpful.

thanks that was actually really original and quite funny...i needed a laugh today.
maybe i should learn to spell before i start programing computers.


and thank the rest of you. i will install windows first. and go from there.

---

### Post by jobsonandrew on 2008-04-18
Hi all,
Im thinking of doing the same thing, dual boot ubuntu 8.04 (when the final comes out next week) and XP Pro SP2 on a 320gb HDD..

Id like Ubuntu to be the 'Primary' operating system... that is to say, the most used.. and windows just for the odd game/app that really needs it.

Am I to understand the suggestion to be that I install XP first (taking the whole hard drive) and then use Ubuntu's installer to 'Shrink' the XP partition?.. If so, a couple of questions:

Doesnt Windows XP throw a spazz if you mess with it's partition like this.. and, will it have any performance hit on Ubuntu if it is not installed at the 'Front' of the drive.

Also, if I dual boot using this method, will I have the windows boot menu when I start the machine, or the Linux Grub menu?

Cheers!

---

### Post by ace007 on 2008-04-18
There's no impact of the location of the partition on performance.  Windows wont spazz out either.  You do have to defrag windows before you resize it in Ubuntu LiveCD.

EDIT: oh, Grub will be the chooser you see

---

### Post by jobsonandrew on 2008-04-18
hey! Thanks for the clear and concise answer! I'll get to work next week when Hardy comes out! ;)

Thanks!

---

### Post by rsambuca on 2008-04-18
Just to make things easier, I will suggest this ONE more time.  Partition your drive first, and then install the OS's.  Why would you install XP, just to mess with the partition right afterwards?

---

### Post by HebrewTheHammer on 2008-04-22
yeah so i am now have both my os' loaded onto my partitioned hard drive.

things look a little different on my existing linux(? wtf i just shrunk its partition) 

but im trying to play with my grub and cannot get it to load my

/boot/grub/menu.list

my menu.list is empty....nothing in it. no text at all.  and well thats not very good for my editing cause.  i cannot edit what is not there.

and according to my friends above i have to do this to be able to run my windows part.

what do i do?

---

### Post by HebrewTheHammer on 2008-04-22
oh wait

.lst

duh


now i put 

title Windows xp
root (hd0,1)
makeactive
chainloader +1

but its not there on start up...:(

---

### Post by lkraemer on 2008-04-23
Just a suggestion for dual booting.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
go visit this site and read about making a dual boot system.

Then when you partition the drive give XP enough to run since
you will rely on this until you are fully converted.
You can ONLY have 4 Partitions.  The first one being XP,
and the following three UBUNTU (/root /home /swap) versus
making one large partiton along with the swap.  This will allow
you to wipe the Root partition and not loose any of your data
that is in /home.  Just a suggestion.

/swap ~8 Meg (probably the smallest it will allow)
/home ~60 Meg more or less
/ ~20 Meg more or less  = ROOT Partition
Windows 40 to 60 Meg more or less

LK

---

