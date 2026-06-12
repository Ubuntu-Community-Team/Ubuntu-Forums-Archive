---
title: "considering making the switch"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by agengo02 on 2008-03-20
so my girlfriend's laptop is extremely slow due to butt loads of spywary and what not.  she only uses it to surf the net when im on my computer so i figured id just go ahead and format its hard drive and boot soley as ubuntu (ive got 7.04 fiesty fawn i think.)  my plan is to FINALLY buy a usb flash drive and grab all her music and picture files and temporarily store them on my computer while making the switch.  i feel pretty confident (through the use of tutorials) about getting it up and running, but still uneasy about fully getting rid of her xp in case i cant get her laptop to see my wireless router.  is it still a common problem that ubuntu/linux has a hard time finding routers?  can i get by without completely formatting the hard drive and pull the necessary files from whichever windows partitioned folder over to ubuntu AND have it run fast?  as of right now it runs extremely slow which we all know is ANNOYING!  thanks in advance and i look foward to eventually being free of microsoft's tyranical(sp) hold on me.

---

### Post by regomodo on 2008-03-20
any particular reason you are going to use Feisty (7.04)?  Even Gutsy (7.10) is going to be replaced soon

---

### Post by agengo02 on 2008-03-20
fiesty is the cd that i have onhand.  and i dont have any blank cds to burn to.  i figured i could just keep that one because she wont be doing any intense computing, just the usual surfing and music listening and what not.  why do you ask?

---

### Post by Sef on 2008-03-20
Fiesty will only be supported until October 2008.   Gutsy will be supported until April 2009.  Hardy Heron will be supported until April 2011 because it has Long Term Support.  Hardy becomes stable in April 2008.  (24 April, I believe.)  To upgrade from Fiesty, here's a [Howto]("https://help.ubuntu.com/community/GutsyUpgrades").   Then to update to Hardy, it would be similar.  I would wait a couple of weeks to upgrade to Hardy, then stay with it.

---

### Post by barbedsaber on 2008-03-20
If you want to know if ubuntu will detect hardware, just boot the live cd, and check. try and get onto the wireless network while in the live cd.

also

any particular reason that you want to format the hard drive, and not [dual boot]("http://en.wikipedia.org/wiki/Dual_boot")

hope that helps.

---

### Post by AndyCooll on 2008-03-20
A couple of points spring to mind.

Firstly, if her music files are kept on a separate partition (rather than merely being kept in a separate folder) it should be possible to install Ubuntu and (using the manual partition method) keep the music file partition.

Secondly, it has been a while since there has been an issue connecting to routers, Linux has supported most methods of encryption for quite some time.

Wireless card issues with laptops is another matter. This has improved considerably, however there are still a few wireless cards which can prove difficult. You'd need to provide us with more information about your wireless card for us to help you further.

:cool:

---

### Post by agengo02 on 2008-03-21
the whole reason for doing this is to improve the speed at which her computer operates.  if i dual boot will this just defeat the purpose, or can i still get good speeds AND have windows out there just in case?  thanks for the info so far guys.  

oh ya another question.  i dont have any blank cd's laying around but i have the 7.10 .iso file on my usb flash drive.  any way i can boot from that or put it on her desktop and boot it?

---

### Post by bumanie on 2008-03-21
Another option would be run ubuntu in virtualbox with windows as the host OS. Virtualbox will load an iso OS.
As for a dual boot system, it runs the same speed as it would if it was the only OS on a dedicated drive. 
Can't see why you couldn't install from a usb pendrive, but I can't tell you how to do it as I've never tried it, but there should be some documentation around if you do an internet search.

---

### Post by HermanAB on 2008-03-21
Hmm, the main problem here is that it is not your computer and that it is your girlfriend.  Therefore you have to be pretty darn sure that you will not lose important information.

If at all possible, obtain another (new or used) laptop disk drive, remove the old one, insert the new one and install Ubuntu on that.  You cannot lose data on a drive if it is lying next to you on the table.  If you are broke like most young people, join a user group and ask around, someone will have an old laptop drive for you for free.

---

### Post by candtalan on 2008-03-21
Dual booting to ubuntu will not slow down the pc running ubuntu. All that will happen is that an extra menu is offered when booting up, and (usually) after a default time  of 10 seconds, ubuntu begins booting. If the return key is pressed, the 10 seconds duration stops.

Please consider using the Live CD facilities to check out the particular laptop hardware responses to the ubuntu version you have. A live cd will not change anything unless you deliberately proceed to the install process.

Live cd will also run wireless, or not.....  use it to do a good check.

The important treason for using the latest ubuntu version is that the pace of devlopment is blisteringly fast, and wireless drivers are always improving.

It  is a very wise decision to get a backup copy of your (and hers...) data files - do it!

Good luck!

---

### Post by aysiu on 2008-03-21
Here's what I would do:

1. Run the live CD and see if there are hardware detection problems. If there are, and you don't feel confident you can solve them, reinstall Windows and make sure she uses a limited user account instead of the administrator account. This will prevent spyware and future slowdowns.

2. If the live CD has no hardware detection problems, have her play around with the menus and Firefox a little and ask her if she feels comfortable with this (reassure her that Ubuntu will run more quickly once it's installed--these is just a test session). If she's comfortable with it, install it. If she's not comfortable with it, go with the limited user account in Windows and load up her Windows with open source applications.

---

### Post by agengo02 on 2008-03-21
thanks for the great info.  i found what looks like a pretty good writeup for dual booting (i would post the link but i dont want to violate any T&C's.)  the music she aint that worried about, she just wants her pictures which i will back up on my flash drive.  

ok quick googling reveals that it IS possible to boot from flash drive, but alas im at work and for some reason they dont want to spend my day not working...the bastards!  

i found the 64-bit version of fiesty fawn and am thinking about booting that just to make sure itll all work on her computer.  so again thanks for all the helpful posts and replies.  yall got a smart group of people here.

---

### Post by agengo02 on 2008-03-21
> **aysiu said:**
> Here's what I would do:

1. Run the live CD and see if there are hardware detection problems. If there are, and you don't feel confident you can solve them, reinstall Windows and make sure she uses a limited user account instead of the administrator account. This will prevent spyware and future slowdowns.

2. If the live CD has no hardware detection problems, have her play around with the menus and Firefox a little and ask her if she feels comfortable with this (reassure her that Ubuntu will run more quickly once it's installed--these is just a test session). If she's comfortable with it, install it. If she's not comfortable with it, go with the limited user account in Windows and load up her Windows with open source applications.



good tip.  she has given me free reign as long as i can back up her pictures so its time for some laptop destruction!  or ill just get to geek out and mess around with linux...   :guitar:

---

### Post by candtalan on 2008-03-21
Be cautious about booting from a flash drive it can be a lot more complex than it first appears. It is much more certian and straightforward to dual boot using only installed hard drives.

---

### Post by agengo02 on 2008-03-21
ya i guess ill just stop being lazy and go get some blank cds.  would be pretty cool to have several different os's on different flash drives though.

---

### Post by billgoldberg on 2008-03-21
Ubuntu/gutsy has no problem seeing routers, it may have trouble making your wireless card work because the lack of drivers.

There is a list here with working wireless cards:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

PS: you should really consider buying some blanik cd's, and burn gutsy onto it. Or wait a few weeks and install hardy. Hardware support, speed, ... improve with each version, so it's better to use the new versions (in most cases).

---

### Post by agengo02 on 2008-03-21
well i have the iso file of gutsy gibbon on my flash drive.  i went ahead and downloaded it and will probably use that until hh is official.  ugh is it 8pm yet???  i wanna get my geek on.

---

