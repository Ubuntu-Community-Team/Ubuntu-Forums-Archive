---
title: "hiding ubuntu"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by patchido on 2007-11-24
how can i hide ubuntu... my dad uses this comkputer also and he doesnt want ubuntu and told me to remove it.... is it posible for programing my bios so that it will always start Windows unless i do something?

---

### Post by corevette on 2007-11-24
not quite answering your question, but why does he not want you using ubuntu? i can't really see why he wouldn't want you to...

---

### Post by patchido on 2007-11-24
he doesnt like the fact of having 2 operating sstems... and he thinks i will make the computer crash meaning he will pay a technitian for reapir -.-

---

### Post by PmDematagoda on 2007-11-24
You can make GRUB select Windows by default by changing the default value in the GRUB menu.lst.

---

### Post by overdrank on 2007-11-24
Speaking as a Father you should do what he ask and maybe use a pen drive to use Ubuntu or a external drive. :)

---

### Post by PmDematagoda on 2007-11-24
> **patchido said:**
> he doesnt like the fact of having 2 operating sstems... and he thinks i will make the computer crash meaning he will pay a technitian for reapir -.-

That is not true, if you break the Ubuntu installation it will not affect the PC or the other OSes, provided you make the other drives read-only in Ubuntu or by removing their entries in the fstab file. If you break a completely isolated Ubuntu installation, you will break only the Ubuntu installation, nothing else.

---

### Post by patchido on 2007-11-24
> **PmDematagoda said:**
> You can make GRUB select Windows by default by changing the default value in the GRUB menu.lst.

okok... and how do i do that??

---

### Post by PmDematagoda on 2007-11-24
> **overdrank said:**
> Speaking as a Father you should do what he ask and maybe use a pen drive to use Ubuntu or a external drive. :)

A possible idea overdrank, in fact, a good idea:).

---

### Post by PmDematagoda on 2007-11-24
> **patchido said:**
> okok... and how do i do that??

Post the output of:-

```
cat /boot/grub/menu.lst
```

---

### Post by patchido on 2007-11-24
> **overdrank said:**
> Speaking as a Father you should do what he ask and maybe use a pen drive to use Ubuntu or a external drive. :)

sounds good.... and how would i do something like that??? like i run the live cd.. and then? how do i manage to install it in the drive?

---

### Post by Taboo Mirage on 2007-11-24
I'd prioritize educating the father first and foremost rather than blindly following the uninformed "authority." =P

---

### Post by geirha on 2007-11-24
You can configure grub to boot windows by default. You do that by editing /boot/grub/menu.lst (**sudo gedit /boot/grub/menu.lst**) and moving the windows entry before the "### Automatic kernel list starts here"-line (or something similar at least) and near the beginning of the file there should be a line saying "default 0". This is assuming you have gutsy.

---

### Post by ubuntu27 on 2007-11-24
> **PmDematagoda said:**
> You can make GRUB select Windows by default by changing the default value in the GRUB menu.lst.

That's the answer to his/her question :)

Now, how do we do that?  How can he select Windows as a default OS in GRUB's menu.list ?

[That's something I don't know how to do. I'll take this thread as an opportunity to lean something new.]

Also, I think it is a good idea to reduce the time out for GRUB. So, reduce it to like 3 seconds. 
That way Windows will boot fast enough that his dad won't be able to see Ubuntu in the grub list unless he pays attention.

Open the **menu.lst**   by:

```
sudo gedit /boot/grub/menu.lst
```

and you will see something like this:

> 
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		**10**

Change the bold number with a lower one (e.g. 2 or 3)

---

### Post by gali98 on 2007-11-24
I agree with the people saying to just run it off a usb drive or an external drive. This will run almost exactly the same and your dad won't have to worry. However if you must know, you can edit the grub menu list by doing this in a terminal:
```
sudo gedit /boot/grub/menu.lst
```
in here you can set the windows partition to boot automatically by finding the "default" option. It is near the top and is followed by a number. Make this number the number the windows is in the list. Be careful though... The number starts with 0.
I.e. you probably have three kernels listed in grub. The ubuntu kernel first. The recovery kernel second. and the windows bootloader third. if you wanted the first to boot then put 0 by default. So if the windows  boot loader is third in the list, put 2 in front of default. 
Make sure that the "hiddenmenu" option (also near the top) is uncommented and you can put the timeout to a low number i.e. 1 or 2. Then if you wanted to boot into ubuntu just press esc when it boots and it will give you the menu. Hope this helps, but as I said before, it would be easier to just get a external drive.
Kory

---

### Post by patchido on 2007-11-24
this is too much and i dont want to go into hiding... maybe ill install it in an external drive... how much does it cost 70 dls?

---

### Post by PmDematagoda on 2007-11-24
An 80Gb external drive costs about 100$ here in Sri Lanka, a 4Gb USB drive is about 40$.

---

### Post by adamorjames on 2007-11-24
> **patchido said:**
> sounds good.... and how would i do something like that??? like i run the live cd.. and then? how do i manage to install it in the drive?

[http://pendrivelinux.com/](http://pendrivelinux.com/)

---

### Post by willca on 2007-11-24
Ask him for a brand new PC this Christmas. That will fix it for sure.

---

### Post by patchido on 2007-11-24
> **willca said:**
> Ask him for a brand new PC this Christmas. That will fix it for sure.

lol..... im not that kind of spolied key

---

### Post by overdrank on 2007-11-24
> **Taboo Mirage said:**
> I'd prioritize educating the father first and foremost rather than blindly following the uninformed "authority." =P

I would agree with that statement, that is why I phrased my response as speaking as a Father. ;)
But I believe the best way to convince other is to show them the versatility of Ubuntu. :)

---

### Post by PmDematagoda on 2007-11-24
> **overdrank said:**
> I would agree with that statement, that is why I phrased my response as speaking as a Father. ;)
But I believe the best way to convince other is to show them the versatility of Ubuntu. :)

True, if you tell us what your father does with the PC then we could help you to get your father to use Ubuntu.

---

### Post by patchido on 2007-11-24
> **overdrank said:**
> I would agree with that statement, that is why I phrased my response as speaking as a Father. ;)
But I believe the best way to convince other is to show them the versatility of Ubuntu. :)

lol.... if u knew my father.. he is the kind of dads from this celphoen conversation

dad.... be here at 12..

son..... dad.. 12 30 plz...

dad.. okok 11 30 

-.- lol

---

### Post by overdrank on 2007-11-24
> **patchido said:**
> lol.... if u knew my father.. he is the kind of dads from this celphoen conversation

dad.... be here at 12..

son..... dad.. 12 30 plz...

dad.. okok 11 30 

-.- lol

ME !!!!!!!!!!!! :guitar:

---

### Post by PmDematagoda on 2007-11-24
You can just try, if you say the right stuff about Ubuntu then your father can be convinced.

---

### Post by Depressed Man on 2007-11-24
I'd say make it one second. Theoretically if you hold the down key the moment GRUB would load up it would stop the time out. Though your still stuck with the problem of your dad seeing you use Ubuntu.

---

### Post by patchido on 2007-11-24
> **PmDematagoda said:**
> You can just try, if you say the right stuff about Ubuntu then your father can be convinced.

belevie me .... the 1 hour conversation we had about it was enough i better get an external drive.... can meanwhile i get an external drive use a 1 gb flash memory.. or is it to little?

---

### Post by PmDematagoda on 2007-11-24
> **overdrank said:**
> ME !!!!!!!!!!!! :guitar:

I'm glad that I don't have someone like you for a father:D.

---

### Post by patchido on 2007-11-24
> **PmDematagoda said:**
> I'm glad that I don't have someone like you for a father:D.

-.- ......... thx a lot

---

### Post by PmDematagoda on 2007-11-24
> **patchido said:**
> belevie me .... the 1 hour conversation we had about it was enough i better get an external drive.... can meanwhile i get an external drive use a 1 gb flash memory.. or is it to little?

A one hour conversation was not enough? Usually it takes about a minute to convert someone to Linux:). Anyway, as you said, the best bet would be to use Ubuntu through an external drive, but it will be difficult in doing that, and won't your father question you as to why you bought the drive in the first place?

---

### Post by patchido on 2007-11-24
i dont know if i love ubuntu that much or i just love forums and learning but i signed up yesterday to the forums and i have like 60 posts :O

---

### Post by Flying caveman on 2007-11-24
> **patchido said:**
> how can i hide ubuntu... my dad uses this comkputer also and he doesnt want ubuntu and told me to remove it.... is it posible for programing my bios so that it will always start Windows unless i do something?


Oh, Everything is starting to make sense now. [http://ubuntuforums.org/search.php?searchid=31901996](http://ubuntuforums.org/search.php?searchid=31901996)

I wouldn't want you to use my computer either.

You should get you Dad on the forum and He could have it fixed up in a few minutes.

---

### Post by patchido on 2007-11-24
> **PmDematagoda said:**
> A one hour conversation was not enough? Usually it takes about a minute to convert someone to Linux. Anyway, as you said, the best bet would be to use Ubuntu through an external drive, but it will be difficult in doing that, and won't your father question you as to why you bought the drive in the first place?

i told him that... i told him i was doing it .. what he does not want is for me to get ubuntu "in" the laptop so if i get the drive i am not perturbing the laptop or am i?? ...

PD: if i run external the computer stays untouched?

---

### Post by patchido on 2007-11-24
> **Flying caveman said:**
> Oh, Everything is starting to make sense now. [http://ubuntuforums.org/search.php?searchid=31901996](http://ubuntuforums.org/search.php?searchid=31901996)

I wouldn't want you to use my computer either.

You should get you Dad on the forum and He could have it fixed up in a few minutes.

link broken

---

### Post by adamorjames on 2007-11-24
> **patchido said:**
> i told him that... i told him i was doing it .. what he does not want is for me to get ubuntu "in" the laptop so if i get the drive i am not perturbing the laptop or am i?? ...

PD: if i run external the computer stays untouched?

yep, USB drive means it is untouched

---

### Post by Dark_X on 2007-11-24
I would like to say one thing... if you remove Ubuntu you have to rewrite the MBR.  If you don't you are screwed.

---

### Post by atlfalcons866 on 2007-11-24
break the windows installation =)

---

### Post by PmDematagoda on 2007-11-24
> PD: if i run external the computer stays untouched?

Yes, but make sure that you remove all the entries in the fstab file that concern the hard drives in the laptop so that they will not be mounted and would not be affected by a problem in Ubuntu.

---

### Post by patchido on 2007-11-24
> **Dark_X said:**
> I would like to say one thing... if you remove Ubuntu you have to rewrite the MBR.  If you don't you are screwed.

MBR? what is that??? plz explain urself im noobish :P

---

### Post by patchido on 2007-11-24
> **PmDematagoda said:**
> Yes, but make sure that you remove all the entries in the fstab file that concern the hard drives in the laptop so that they will not be mounted and would not be affected by a problem in Ubuntu.

didnt understand anything... im too noob at ubuntu 2nd day use

---

### Post by overdrank on 2007-11-24
> **Dark_X said:**
> I would like to say one thing... if you remove Ubuntu you have to rewrite the MBR.  If you don't you are screwed.

Great point Dark X
this guide will help
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Edit and as speaking like a Father again   Someone is in big !!!!!!!!!!!!!!!!!

---

### Post by Dark_X on 2007-11-24
> **overdrank said:**
> Great point Dark X
this guide will help
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Edit and as speaking like a Father again   Someone is in big !!!!!!!!!!!!!!!!!

Thanks for that link.  That will be very useful for me.

---

### Post by patchido on 2007-11-24
ok.. so to finish this up... what i need is to reset the partition table and then i unistall ubuntu and get my external drive then install ubuntu and buala.... :P

lol.. ok ... read about MBR or that thing and says i need the windows xp disk to rewrite my MBR... lamly i dont have such cd

---

### Post by adamorjames on 2007-11-24
> **patchido said:**
> ok.. so to finish this up... what i need is to reset the partition table and then i unistall ubuntu and get my external drive then install ubuntu and buala.... :P

lol.. ok ... read about MBR or that thing and says i need the windows xp disk to rewrite my MBR... lamly i dont have such cd

so then, Windows 98 Floppy Disk Method "(Works for Windows 98 or Windows XP without an 'install' CD)"

---

### Post by patchido on 2007-11-24
i have a little but very little problem... my laptop doesnt have floppy -.- lol

---

### Post by Dark_X on 2007-11-24
Super Grub. :P

---

### Post by patchido on 2007-11-24
**** what should i do??

---

### Post by overdrank on 2007-11-25
patchido let me commend you in trying to enlighten your father as I have converted my son with the help of the desktop effects and I have managed to convert my mother ( at the ripe age of 75 ) so do not give up hope. As for my daughter there is no hope, forever lost to windows. :(

---

### Post by scrooge_74 on 2007-11-25
> **patchido said:**
> ok.. so to finish this up... what i need is to reset the partition table and then i unistall ubuntu and get my external drive then install ubuntu and buala.... :P

lol.. ok ... read about MBR or that thing and says i need the windows xp disk to rewrite my MBR... lamly i dont have such cd

For the time being, change the GRUB so it boot into Windows automatically and put the time delay to 1 second or even 0 seconds so your father dont see much about Ubuntu. Then stick to the Live CD until you learn enough about Windows and Linux so you dont mess the computer and get blame for it.

If you dont know what MBR is and other stuff related to windows and you certainly dont know enough about Linux , stick to a Live CD for the time being, until you either know a lot more or you get your own computer.

And I am speaking as a father of a 12 and a 10 year old.  If your father dont know enough about computers and neither you, you are on your way for a couple of hard weeks of problems with your PC and with your father.

Try to convince him to get you the oldest slowest computer you can find. For using Windows it would be a horrible PC but for Linux it will be a wonderfull machine.

 So when you are well verse on the subject to the point that you can be your own IT manager for your family and your father gets to see how productive you are with that kind of old equipment he will see the light.

Keep reading and learning about it.

---

### Post by patchido on 2007-11-25
> **scrooge_74 said:**
> For the time being, change the GRUB so it boot into Windows automatically and put the time delay to 1 second or even 0 seconds so your father dont see much about Ubuntu. Then stick to the Live CD until you learn enough about Windows and Linux so you dont mess the computer and get blame for it.

If you dont know what MBR is and other stuff related to windows and you certainly dont know enough about Linux , stick to a Live CD for the time being, until you either know a lot more or you get your own computer.

And I am speaking as a father of a 12 and a 10 year old.  If your father dont know enough about computers and neither you, you are on your way for a couple of hard weeks of problems with your PC and with your father.

Try to convince him to get you the oldest slowest computer you can find. For using Windows it would be a horrible PC but for Linux it will be a wonderfull machine.

 So when you are well verse on the subject to the point that you can be your own IT manager for your family and your father gets to see how productive you are with that kind of old equipment he will see the light.

Keep reading and learning about it.

dont worry about that... what i want to do this moment is to uninstall everything realated to ubuntu includint grub and then get my drive but i really need to disappear ubuntu... i have tred to change the grub settings but i dont understand anything u say to me.. not u specially XD but i mean forum persons

---

### Post by Flying caveman on 2007-11-25
I would do what scrooge said .

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_default_Operating_System_boot-up_for_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_default_Operating_System_boot-up_for_GRUB_menu)

explains how to edit the boot/grub/menu.list so that you can change how long the menu is displayed and which operating system is the default.

---

### Post by patchido on 2007-11-25
> **Flying caveman said:**
> I would do what scrooge said .

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_default_Operating_System_boot-up_for_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_default_Operating_System_boot-up_for_GRUB_menu)

explains how to edit the boot/grub/menu.list so that you can change how long the menu is displayed and which operating system is the default.

but my dad will still manage to see taht 20 gbs are missing lol

---

### Post by patchido on 2007-11-25
now that i took my decicion is there a way of backing up all the things ive done to ubuntu settings and stuff like that or ill have to do it all over in my external?

---

### Post by patchido on 2007-11-25
i love learning... another question... if i have it running via external drive Grub will still be there???

---

### Post by tdrusk on 2007-11-25
honor thy father.

get your own computer.

---

### Post by patchido on 2007-11-25
> **tdrusk said:**
> honor thy father.

get your own computer.

sure i will...... -.- want to donate.????? not too much money just a laptop ..

sounds easy

---

### Post by Sawta on 2007-11-25
> **patchido said:**
> now that i took my decicion is there a way of backing up all the things ive done to ubuntu settings and stuff like that or ill have to do it all over in my external?

Although there is probably a work around to keeping all of these settings, I'm betting you that it would be much less of a headache for you if you just re-did the settings when you get your External HDD, besides, you've only been using it for 2 days..you couldn't of customized it *that* much, right?:lolflag:

---

### Post by patchido on 2007-11-25
> **Sawta said:**
> Although there is probably a work around to keeping all of these settings, I'm betting you that it would be much less of a headache for you if you just re-did the settings when you get your External HDD, besides, you've only been using it for 2 days..you couldn't of customized it *that* much, right?:lolflag:

check the number of my posts...... 2 days is enough for me to personalise it :D lol

---

### Post by Flying caveman on 2007-11-25
> **patchido said:**
> but my dad will still manage to see taht 20 gbs are missing lol

Deny Everything! 


"Looks like you need a bigger hard drive Dad"  ....... then ask if you can borrow his credit card

---

### Post by tdrusk on 2007-11-25
> **patchido said:**
> sure i will...... -.- want to donate.????? not too much money just a laptop ..

sounds easy

pawn shop. Buy the crappiest one. Put Debian Etch on it. Use the netinst cd. don't use the metapackages, instead use aptitude and install what you need. learn.

I wouldn't recommend backing up your settings. It's a pain and you will never learn from doing something once.

---

### Post by patchido on 2007-11-25
when i install ubuntu into my external drive the Grub will be installed in the external drive or internal???

i wish it could be in the external.. and wel.. how would i be running ubuntu]??

if the external is coneccted through USb the BIOS will get it alone or needs help?

---

### Post by scrooge_74 on 2007-11-25
Unless your PC can boot from an external USB drive you are still going to need GRUB to boot.

To get rid of GRUB you need a XP CD to re-instal the Master Boot Record (MBR).  When you  do that you can always use a Live CD to reformat the 20 GB partition into ntfs again and use it as a D: drive and tell your father that drive is for backing up things if at any point your XP install gets borked.

I like the idea from tdrusk, go to a pawn shop and get any old laptop they have (even a 7 year old will do). Convince your father to lend/give you the money since you want to develop your skils in IT.

That way you can mod that PC to your hearts content

---

### Post by dips_xe on 2007-11-25
> **patchido said:**
> i dont know if i love ubuntu that much or i just love forums and learning but i signed up yesterday to the forums and i have like 60 posts :O 

that's because you made 19 threads already, you can't be doing stuff like that.

anyway, if ubuntu is already installed then the best thing to do is follow the instructions on hiding ubuntu in the grub menu. don't try and remove it.

---

### Post by patchido on 2007-11-25
> **dips_xe said:**
> that's because you made 19 threads already, you can't be doing stuff like that.

anyway, if ubuntu is already installed then the best thing to do is follow the instructions on hiding ubuntu in the grub menu. don't try and remove it.

i have to.. right now i am in ubuntu... hided it but i dont plan on doing it for that long... i prefer on getting my external drive.. maybe not getting GRUB out

---

