---
title: "Locked out of computer, not happy. (GRUB)"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by UbuntuDupe on 2006-01-27
Hi, I'm new to Linux, and someone recommended the Ubuntu distro.  I burned the install disc to a CD and booted off of it and did the whole installation process.  I installed GRUB for the boot loader.  And there's the problem.  Whenever my computer boots up, it says it's loading GRUB, and then it stops and says "Error 25".  It won't let me enter text or anything, I only seem to be able to shut down or restart.  This means I can't access either the Windows partition, or the newly installed Linux one.  So, my computer is currently useless and I have to use a borrowed laptop.  Very, very frustrating.

Before you make this even more frustrating for me:

-Yes, I meet the minimum system specs.
-Yes, I've tried re-installing, multiple times in fact.
-No, there was no error in burning the CD.
-Yes, I'm using the latest version of Ubuntu.

Anything about how to edit the boot loader on bootup would be nice.  Please provide whatever assistance you can in fixing this.  I really want to convert, at least partially, to Ubuntu.

---

### Post by amoser on 2006-01-27
Do you have access to date on your hard disk, using a live cd (Ubuntu Live CD).  If you do, can you go into your linux partion and post your /boot/grub/menu.lst.  It sounds like Ubuntu may have screwed up on you grub install. Error 25 refers to a problem with the Windows part of grub.

---

### Post by UbuntuDupe on 2006-01-27
[QUOTE=amoser]Do you have access to date on your hard disk, using a live cd (Ubuntu Live CD).  If you do, can you go into your linux partion and post your /boot/grub/menu.lst.  It sounds like Ubuntu may have screwed up on you grub install. Error 25 refers to a problem with the Windows part of grub.[/QUOTE]

I don't have a Live CD.  Naive me, I thought that by downloading just the install disc, I wouldn't be locked out of both Windows AND Linux.  But it's my fault, really.  I should *never* have believed all that crap about "providing access to all".

---

### Post by Iowan on 2006-01-27
Check [HERE](http://www.ubuntuforums.org/showthread.php?t=117271&highlight=grub+error+25) for info from a similar problem.

---

### Post by UbuntuDupe on 2006-01-27
[QUOTE=Iowan]Check [HERE](http://www.ubuntuforums.org/showthread.php?t=117271&highlight=grub+error+25) for info from a similar problem.[/QUOTE]

I followed those instructions, and when I got to the part where I could input text, it said:

"sh-3.00#"

So I entered:

grub install /dev/hda

and it said:

Probing devices to guess BIOS drives.  This may take a long time.
<after a long time>
Error opening terminal: bterm.

Now what?

Thanks for any assistance you can provide in helping undo the damage Ubuntu has done.

---

### Post by Xappe on 2006-01-27
another solution for you could be to boot the windows install disc, choose "repair existing windows install" (or whatever it's called). Then at the prompt type fixmbr (I *think* that's the command, i'm not really sure...haven't been using win for quite a long time).

Now the windows default mbr should've been written, and you should be able to boot windows, download a livecd and fix grub... :)

---

### Post by UbuntuDupe on 2006-01-27
[QUOTE=Xappe]another solution for you could be to boot the windows install disc, choose "repair existing windows install" (or whatever it's called). Then at the prompt type fixmbr (I *think* that's the command, i'm not really sure...haven't been using win for quite a long time).

Now the windows default mbr should've been written, and you should be able to boot windows, download a livecd and fix grub... :)[/QUOTE]

I don't know where my install disc is.  Again, I thought -- probably because of all the liberation/openness rhetoric of Ubuntu -- I wouldn't need Microsoft software to get Ubuntu to work.  Guess that's not the case.

---

### Post by Xappe on 2006-01-27
Well, actually you don't need Microsoft products. But I just thought that if you had your windows install disc at hand, it could be of use, since you don't have a live cd. 

Another thing you could try is a reinstall of ubuntu (and maybe check the md5 of the disc first). Remember to check the partitions so that you don't, by accident,  remove your windows partition(s).

---

### Post by UbuntuDupe on 2006-01-27
[QUOTE=Xappe]
Another thing you could try is a reinstall of ubuntu (and maybe check the md5 of the disc first). [/QUOTE]

So in other words, you didn't read my first post, in which I said that the disc is fine and I've tried reinstalling multiple times.  This just makes my day.

---

### Post by Xappe on 2006-01-27
oh, sorry, I missed those lines... :) Forget that last post of mine then.

---

### Post by cwaldbieser on 2006-01-27
[QUOTE=UbuntuDupe]I followed those instructions, and when I got to the part where I could input text, it said:

"sh-3.00#"

So I entered:

grub install /dev/hda

and it said:

Probing devices to guess BIOS drives.  This may take a long time.
<after a long time>
Error opening terminal: bterm.

Now what?

Thanks for any assistance you can provide in helping undo the damage Ubuntu has done.[/QUOTE]

Could you post the link to the instructions you are following?  There are a bunch of links embedded in the thread that Iowan linked to, and I am not sure what steps you are following.

---

### Post by UbuntuDupe on 2006-01-27
[QUOTE=cwaldbieser]Could you post the link to the instructions you are following?  There are a bunch of links embedded in the thread that Iowan linked to, and I am not sure what steps you are following.[/QUOTE]

I followed the instructions in the second post:

"Boot with your Ubuntu installation CD
On the boot: prompt, type rescue and hit enter
Follow the instructions on the screen
When the computer is ready, assuming that /dev/hda is where your /boot is located, type: grub-install /dev/hda"

---

### Post by cwaldbieser on 2006-01-27
[QUOTE=UbuntuDupe]I followed the instructions in the second post:

"Boot with your Ubuntu installation CD
On the boot: prompt, type rescue and hit enter
Follow the instructions on the screen
When the computer is ready, assuming that /dev/hda is where your /boot is located, type: grub-install /dev/hda"[/QUOTE]
Do you have any idea if you have an IDE hard drive, or a newer type, like a SATA?  My SATA drive gets detected as /dev/sda.  Since I am dual booting, /boot for me is specifically on /dev/sda2.  

I am not sure if the instructions want you to give the partition or the device (e.g. /dev/hda or /dev/hda2).

Also, providing any relevant info about your PC could help you out.  Useful items might include:
+ What version of Windows you were using.
+ Physical components of the computer (drives, motherboard, processor)
+ Maybe even manufacturer and model (someone may have the same stock brand and be able to help out).

---

### Post by UbuntuDupe on 2006-01-27
[QUOTE=cwaldbieser]Do you have any idea if you have an IDE hard drive, or a newer type, like a SATA?  My SATA drive gets detected as /dev/sda.  Since I am dual booting, /boot for me is specifically on /dev/sda2.  

I am not sure if the instructions want you to give the partition or the device (e.g. /dev/hda or /dev/hda2).[/quote]

I have three IDE hard drives, and I'm putting linux on the third (secondary master).  The boot loader is on ... well, all three now.

> Also, providing any relevant info about your PC could help you out.  Useful items might include:
+ What version of Windows you were using.

Don't see what difference that makes, given as I can't even get into Windows, and the problem is obviously due to GRUB.  Seems like a fishing expedition there.

> + Physical components of the computer (drives, motherboard, processor)

1250 MHz Athlon processor, Western digital hard drives (0 - 40 Gig with Windows, 1 - 80 Gig, 2 - 250 Gig currently set all for Ubuntu).

> + Maybe even manufacturer and model (someone may have the same stock brand and be able to help out).

???

Okay, why not just tell me how to get into the boot loader?

---

### Post by cwaldbieser on 2006-01-27
[QUOTE=UbuntuDupe]
Don't see what difference that makes, given as I can't even get into Windows, and the problem is obviously due to GRUB.  Seems like a fishing expedition there.
[/QUOTE]
Troubleshooting is a bit of a fishing expedition when you are not looking at the actual equipment and your best interface to the hardware is someone who is too angry or frustrated to cooperate.  Maybe when you have cooled down a bit, we could start on the right foot.

Sorry I couldn't help with your problem.

---

### Post by UbuntuDupe on 2006-01-28
[QUOTE=cwaldbieser]Troubleshooting is a bit of a fishing expedition when you are not looking at the actual equipment and your best interface to the hardware is someone who is too angry or frustrated to cooperate.  Maybe when you have cooled down a bit, we could start on the right foot.[/quote]

:shock:

Just yesterday I thought I knew what chutzpah was.

"Starting on the right foot" would include "not getting locked out of my computer because I installed a OS billed as 'Linux for Human Beings' ".  "Starting on the right foot" would include finding instructions that answer the frequently asked question of "how do I set up a new partition and install to that partition?". "Starting on the right foot" would include an Ubuntu forum that doesn't take me a week of trying to access from different computers and connections before it consistently loads.

Stop making excuses.  So I wouldn't answer what Windows version it is.  Can anyone think of any reason why one version of Windows over another would cause GRUB error 25?  No?  Okay then.

The problem is not the devices, or the Windows version, or getting the latest install CD, or scratches on the install CD.  The problem is the boot loader.  *The problem has already been diagnosed.*  You just want to chase all these wild geese because you don't want to admit that maybe this "access for all" OS has a serious problem.

Would somebody just tell me how to edit, modify, fix, whatever, the boot loader?  That's all.  It should be really simple, given the rigorous testing that they would put a software capable of locking you out of your computer through.

---

### Post by UbuntuDupe on 2006-01-28
bump

---

### Post by Stew2 on 2006-01-28
You are obviously so biased against Ubuntu that perhaps your best course of action would be to find your windows disc or borrow one from someone to fix your windows install. Please dont forget that the people on this forum are just ordinary users like yourself. They are not paid tech support, if you want thier help you should be patient, courteous and try to give them the info they require. Ubuntu works just fine, and most installs go flawlessly. Yours is the exception, not the rule.

---

### Post by UbuntuDupe on 2006-01-28
[QUOTE=Stew2]You are obviously so biased against Ubuntu that perhaps your best course of action would be to find your windows disc or borrow one from someone to fix your windows install. Please dont forget that the people on this forum are just ordinary users like yourself. They are not paid tech support, if you want thier help you should be patient, courteous and try to give them the info they require. Ubuntu works just fine, and most installs go flawlessly. Yours is the exception, not the rule.[/QUOTE]

Right.  I'm biased against Ubuntu.  I downloaded it, burned it to a CD, bought a new hard drive, installed the distro, locked myself out of my computer, spent countless hours getting help from my brother through each step of the way solely so I could have a real story about how a Linux distro fucked me over.  I was so willing to tarnish the reputation of Ubuntu that I did all that, devious schemer that I am.  And to top it all off, I literally, *jumped* at the chance to wait for "ubuntuforums.org" to load so I could be subjected to "advice" like "Can't get into your computer?  I know!  Go open Linux and post your menu.1st file!"  My doctor always told me my blood pressure was too low.

But it's no big deal, right?  So what if I can't get it to run?  I'm just one person. It's not like Ubuntu is intended to be usable by everyone, right?  It's not like I can believe what they say at ubuntu.com.

---

### Post by tageiru on 2006-01-28
Look, as has been said before, the people of this forum are not employees of Canonical and are not payed or in any way related to Ubuntu.

The people that has answered you in this thread have been doing so despite your attitute and that is commendable. Even though you might think that some of the advice that has been given is incorrect, they answered because they wanted to help you.

And please refrain from bumping threads.

---

### Post by cwaldbieser on 2006-01-28
Starting out on the right foot can also mean that you acknowledge that the problems you are currently facing are the result of your own actions.  

A prudent strategy when fiddling around with your computer is to have a plan B when something goes wrong.  A good plan might have included making sure you had your Windows boot disk handy in case you encountered problems.  Or having some sort of LiveCD like Knoppix that was known to work in case of an emergency.

Lots of people don't like to take the time to take simple precautions or think things through (this is not limited to installing computers, either).  They often feel frustrated when things did not work out textbook-perfect like they thought the ought to have.

In this situation, you got yourself into a jam, and asked for help.  Lots of folks wanted to help you, but you turned your frustrations on them.  I can't speak for others, but you very quickly erased any sympathy I had for you.  When someone is angry and not thinking clearly, they are not an easy person to help.

Obviously, you are facing a problem with the boot loader.  The practical thing to do at this point is to get your hands on bootable media (Windows boot disk of Linux boot disk, doesn't matter) that has tools on it that let you correct the problem.  If that is not an option, there is no magic button to press to reset your boot loader.

I asked for information that is relevant to the boot process and the state of your machine before you installed Grub.  The software itself works well enough for most people, so the key is to find differences in your environment that may have caused the error.  While I do not expect that there is a very high chance of success without alternative bootable media, it is higher than the 0% chance of success you will have if you cannot get your hands on bootable media.

---

### Post by mztriz on 2006-01-28
I really don't know exactly what you did so maybe you should watch this video
[http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu](http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu)

---

### Post by DiscoKiller on 2006-01-28
that vid is priceless. attitudes like UbuntuDupes shouldnt be tolerated by anyone. i find it hard to care that someone that obnoxious can`t use ubuntu, they deserve no more than windows.

---

### Post by Stew2 on 2006-01-28
[QUOTE=DiscoKiller]that vid is priceless. attitudes like UbuntuDupes shouldnt be tolerated by anyone. i find it hard to care that someone that obnoxious can`t use ubuntu, they deserve no more than windows.[/QUOTE]
Aw cmon, even windows doesnt deserve UbuntuDupes attitude! :)

---

### Post by UbuntuDupe on 2006-01-28
[QUOTE=cwaldbieser]Starting out on the right foot can also mean that you acknowledge that the problems you are currently facing are the result of your own actions.  
[/QUOTE]

And you've reached a new low.

I did exactly what the install instructions said to do, and it locked me out of my computer.  Period.  "My own actions" are not the cause of this problem, unless you want to roll into the defense of "you were stupid enough to follow the product's instructions".

Yes, perhaps I should have done a "test install" first.  I guess every user of Ubuntu is supposed to a buy a new computer, disconnected from their current one, and install to that one "just as a li'l check" to make sure software that has had thousands of eyes continually revising the source code didn't do something stupid, like, I don't know, make it so the install CD locks you out of your computer.  After all: what idiot thinks Ubuntu is reliable, right?

I guess next you're going to tell me that if drunk driver side-swipes me, "it's my fault for deciding to drive".  Or if I'm riding on a train that crashes, hey, it's my fault for riding a train.  

Now, I've never programmed for Linux OS's, but I think I can say that if a program automatically runs at startup, and is capable of locking you out of your computer, I'd have some way of bypassing it on startup.  I mean, that's just common sense.  (Doesn't say a lot for the programmers.)  But instead all I get is trite lines like "heh heh, you can't just remove a boot loader" or "why didn't you just have backup plan X that is mentioned nowhere in the install instructions?".

There's a really simple solution to all of this that should have been the second post: tell me how to edit the boot loader.  If you really want to expand the Ubuntu user base (i.e., if you don't use this forum merely to degrade people who are trying to get it installed), you'd tell me that.  You still have a chance.

---

### Post by mlissner on 2006-01-28
OK. Come back when you have bootable media like knoppix or the live CD. 

You were able to make the Ubuntu install CD. Go make the live CD like they told you to and come back when you have it. Seems simple enough.

Be nicer when you come back. You're directing your anger at people that were originally spending their time trying to help you. They did nothing to create the scenario you're in, so be nice.

Now. Since you're reading this, you have a computer at your fingertips. Use it to make a live CD, then post again.

Love, Peace and Joy,

Mike

---

### Post by towsonu2003 on 2006-01-29
take a look at this [http://support.microsoft.com/?kbid=247804](http://support.microsoft.com/?kbid=247804)

also, flaming those who try to help won't help you much. try to calm down. as you see, you're doing nothing but damaging your probabilities of getting help. just don't post your feelings if you can't calm down. 

Take a look at this wiki where there is a way to recover grub with the install cd:  [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows) (first section)

once you get your hands to a livecd, post the output of your own (not that of the livecd) /etc/fstab and the output of ```
sudo fdisk -l
```. also, note here if you have more than one hard disks. 

also, do a search in google.com/linux for grub "error 25" and try to find a link that is similar to your setup. that will be the quickest way to get help.

---

### Post by UbuntuDupe on 2006-01-29
[QUOTE=mlissner] You were able to make the Ubuntu install CD. Go make the live CD like they told you to and come back when you have it. Seems simple enough.

Now. Since you're reading this, you have a computer at your fingertips. Use it to make a live CD, then post again.

[/QUOTE]

From the fact that I burned a CD on my own computer it does not follow that I can burn one on *this* computer.  Come on, let's try not to embarass Berkeley with that kind of logic.

> Be nicer when you come back. You're directing your anger at people that were originally spending their time trying to help you. They did nothing to create the scenario you're in, so be nice.

You have an odd definition of "help".  If by "help" you mean "refuse to provide instructions on how to perform the logical next step", okay, sure, they helped.  You also have refused to answer the question of how to edit the boot loader.

Is it your position that I can't trust the instructions that are on the ubuntu home page?  That if I follow them, it's my own damn fault for being so stupid?  Odd position to take, if I say so mayself.

---

### Post by tokyovigilante on 2006-01-29
[QUOTE=UbuntuDupe]From the fact that I burned a CD on my own computer it does not follow that I can burn one on *this* computer.  Come on, let's try not to embarass Berkeley with that kind of logic.
[/QUOTE]
You're the only one embarrassing anybody (ie yourself) here.

Dude, your computer can't boot.

Logical next step: Go get bootable CD - Windows (any version you like), Ubuntu LiveCD, Knoppix CD. Stick in computer. Boot Computer.

---

### Post by towsonu2003 on 2006-01-29
Just stop flaming and search around. Use the install cd. Download a livecd. 

I'm outta here. Good luck.

---

### Post by dueY on 2006-01-29
[QUOTE=UbuntuDupe] You also have refused to answer the question of how to edit the boot loader.[/QUOTE]

I'm assuming you can create directories with a LIVE CD... someone correct me if you can't...

But I'm guessing your plan of action would be

```
sudo mkdir /media/buttes
```
```
sudo mount /dev/(partition with GRUB) /media/buttes -t ext3 
```
```
sudo gedit /media/buttes/boot/grub/menu.lst
```

---

### Post by phen on 2006-01-29
if your ubuntu install is not located on the primary master, you cannot use

grub-install /dev/hda

you have to use grub-install /dev/YOUR_UBUNTU_HARDDRIVE !

you should be able to find out which hdd is you ubuntu drive by starting the partition tool from the install cd. dont use it, just write down the drive name (hda or hdb or hdc etc...)

then try again. and please: don't complain about ubuntu and the "service" here, as long as you are not willing/able to READ the help you are supplied with completely:
> 
Boot with your Ubuntu installation CD
 On the boot: prompt, type rescue and hit enter
 Follow the instructions on the screen
 When the computer is ready, assuming that /dev/hda is where your /boot is located, type: grub-install /dev/hda
 
 As you have multiple drives in your machine, as long as the hard drive you installed on was the first drive in the boot order for your BIOS, then /dev/hda is correct. If this works, on re-booting your machine you should complete the install.


thank you very much for listening.

---

### Post by UbuntuDupe on 2006-01-29
[QUOTE=phen]if your ubuntu install is not located on the primary master, you cannot use

grub-install /dev/hda

you have to use grub-install /dev/YOUR_UBUNTU_HARDDRIVE !

you should be able to find out which hdd is you ubuntu drive by starting the partition tool from the install cd. dont use it, just write down the drive name (hda or hdb or hdc etc...)

[/QUOTE]

Ubuntu is on the third hard drive.  I entered "grub-install /dev/hdc"

It said:

"Thie files /boot/grub/stage2 not read correctly".

I can't edit stage2.  What now?

---

### Post by jonathanm on 2006-01-29
i think that you may have a problem with the hard drive.  if the stage2 is located on a bad block then it wont be able to be read.  This would then lead on to the grub not working.

Please be right, Please, i dont want to be flamed! :)

---

### Post by phen on 2006-01-29
that would be very bad luck... you can try to fsck.ext3 /dev/hdc (scandisk)  either in rescue mode of the installation cd (that should work, i think) or with a knoppix live cd!

jonathan: you might be right... i just checked the grub manual

Error Code 25:
source: [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)

25 : Disk read error
This error is returned if there is a disk read error when trying to probe or read data from a particular disk.

---

### Post by UbuntuDupe on 2006-01-29
[QUOTE=phen]that would be very bad luck... you can try to fsck.ext3 /dev/hdc (scandisk)  either in rescue mode of the installation cd (that should work, i think) or with a knoppix live cd!

jonathan: you might be right... i just checked the grub manual

Error Code 25:
source: [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)

25 : Disk read error
This error is returned if there is a disk read error when trying to probe or read data from a particular disk.[/QUOTE]

How can that be though?  It should be reading from the main hard drive (hda) I've always used.  And that hard drive is okay.

---

### Post by deavik on 2006-01-29
I'm sorry if you've mentioned it somewhere and I've missed it, but which drive is Ubuntu on? I think GRUB's second stage is installed in the Ubuntu partition, and the first stage on the MBR of hda.

---

### Post by UbuntuDupe on 2006-01-29
[QUOTE=deavik]I'm sorry if you've mentioned it somewhere and I've missed it, but which drive is Ubuntu on? I think GRUB's second stage is installed in the Ubuntu partition, and the first stage on the MBR of hda.[/QUOTE]

Ubuntu is on the third ide hard drive (hdc) (secondary master).  It would really suck if there's a problem with the hard drive were the problem because I already had to return one hard drive from the place I got it at for being defective.  In any case, error25 happens in stage 1.5.

---

### Post by phen on 2006-01-29
if stage1.5 is located on hdc, it looks like your harddisk is broken. try fsck.ext3! it will give you an idea of hdc's fitness...

next guess:
sometimes, harddisk vendors offer special floppys with a complete set of drive checking tools!

maybe you can fix it, or you can make sure whether it is a hardware problem or not..

---

### Post by AsshatAvenger on 2006-03-20
[QUOTE=UbuntuDupe]From the fact that I burned a CD on my own computer it does not follow that I can burn one on *this* computer.  Come on, let's try not to embarass Berkeley with that kind of logic.

You have an odd definition of "help".  If by "help" you mean "refuse to provide instructions on how to perform the logical next step", okay, sure, they helped.  You also have refused to answer the question of how to edit the boot loader.

Is it your position that I can't trust the instructions that are on the ubuntu home page?  That if I follow them, it's my own damn fault for being so stupid?  Odd position to take, if I say so mayself.[/QUOTE]

Goddamn dude, you're a ******* *** HOLE. I know it sucks when something goes south with your computer, but give the nice folks in here a break. No one has responded to your confrontational and sarcastic bitching with anything other that civility so far, which astounds me. 

I don't wish ill on people very often, and I certainly only speak for myself, not the community, but I hope your computer IS fucked, because regardless of whether it was your fault this happened (which I really doubt it was your fault), your attitude is deserving of nothing less than complete failure. Before you work on your computer anymore, you might try polishing up on your people skills.

Perhaps that windows install disk is up your ***....?

Did I just kill two birds with one stone? :-k

---

### Post by athiex on 2006-03-20
The simple answer to your question is: You cannot edit the bootloader until you are able to access it via some sort of bootable media. 

As an aside, this problem occurs with all OS's from time to time....no point being an jerk.

---

### Post by Bollotom on 2006-03-20
Heard about Linux a couple of years ago. Tride SuSE and couldn't get passed disk 2. Yesterday, saw Ubuntu, tried it and installed it side by side with WinXP with no input apart from password. Now that's what I call an easy install and in half the time of Windows. I think you really have to just keep plugging away, listen to good advice and don't believe computers can't go wrong.;)

---

### Post by sgbett on 2006-03-20
I had to go to the extreme lengths of registering here, just so i could reply to this post.

Whilst I am a hardcore gentoo user, and therefore by default completely biased against ubuntu ;) I have to take my hat off to you forum guys. Your persistence at leading this particular horse to the veritable oasis of a solution is admirable. Regardless of this old nag's desire to die of dehydration.

To me, that definately secures your spot as the #1 distro for linux first timers. Over at gentoo.org im not sure anyone would have had the patience :)

You win 1 star :KS

---

### Post by toxik on 2006-03-20
I too had to register, yet my voice falls exactly the same as previous poster.

Been using Gentoo for quite a bit of time now, so I prefer having pervertedly much control over my install (i.e. what package manager I want, what version of it, et cetera)

My first thought was as an operator over a rather large channel of incompetent flammers on IRC: How can you NOT scream at this guy? I suppose he fixed it, but what an admirable patience! It's even ridiculous ;-)

I might try Ubuntu sometime, and by the way, fun video :-P

---

### Post by bmichel on 2006-03-20
Check this on slashdot about this guy. Sometime it's better when some people just stay with Windows.

[http://slashdot.org/comments.pl?sid=180444&cid=14936948&pid=14936948&threshold=-1](http://slashdot.org/comments.pl?sid=180444&cid=14936948&pid=14936948&threshold=-1)

---

### Post by massivevoid on 2006-03-20
[QUOTE=UbuntuDupe]I have three IDE hard drives, and I'm putting linux on the third (secondary master).  The boot loader is on ... well, all three now.



**Don't see what difference that makes, given as I can't even get into Windows, and the problem is obviously due to GRUB.  Seems like a fishing expedition there.**



1250 MHz Athlon processor, Western digital hard drives (0 - 40 Gig with Windows, 1 - 80 Gig, 2 - 250 Gig currently set all for Ubuntu).



???

Okay, why not just tell me how to get into the boot loader?[/QUOTE]

Giving out more information about your computer is better than complaining about why it may not be the case. Every bit of information is useful to the people that are trying to help you. They are not laughing at your face that your computer is broken. They are here to help.

---

### Post by Aeon17x on 2006-03-20
[QUOTE=UbuntuDupe]Ubuntu is on the third ide hard drive (hdc) (secondary master).  It would really suck if there's a problem with the hard drive were the problem because I already had to return one hard drive from the place I got it at for being defective.  In any case, error25 happens in stage 1.5.[/QUOTE]
Indeed, it would suck.

Now, since the possibility of the hard drive being the problem has already been determined, do you have another working hard drive? If Ubuntu installed there just fine...

---

### Post by juanfgs on 2006-03-20
Hi everyone, i've read this thread this afternoon, and i also just registered to say thanks to this excellent Linux community that is the Ubuntu Forums(but it seems like some did this before :P ).
Keep the good work guys ! :)

---

### Post by patbuntu on 2006-03-21
I'm quite suprised that someone can ask for help then ignore all the suggestions from the community, instead choosing to alienate themselves by acting like a dick.  People here are trying to help, try listening to them.  From reading this thread, I conclude that your main problem is either:

1: There was an error burning your install cd.
2: Your hard drive is screwed.

As a last ditch attempt to try and help you, here are the full instructions for installing ubuntu alongside winxp.

1: Install windows (skip this step if you don't want it).
2: Download, burn and VERIFY the install cd.
3: Boot off said cd, and follow instructions and enjoy all kinds of buttery dual boot type goodness.
4: If you have any problems with the above steps, post your problems to ubuntuforums, then, and this is the important bit, follow the advice offered to you from fellow users.

As an extra hint, typing the phrase 'grub error 25' into google gives 889,000 hits.

-Pat

---

### Post by siddhesh on 2006-03-21
Hi,

Firstly, I'm not a Ubuntu user. I use Debian (Ubuntu's daddy you may call it ;-) ). I've been a regular Linux user since 2002 and the OP's arrogance kinda forced me to want to reply here.

Bootloader problems, though rare, are not at all the end of the world. Like most others have already posted here, they can be solved using the install media, be it the Windows install disk or the Ubuntu install disk.

A reinstall of Ubuntu must fix the loader problem unless you're not following the instructions right. Inspite of all efforts if it isn't working then try the windows fixmbr.

Windows fixmbr:

Boot with the help of a windows rescue disk and go into the recovery console. Once in there type the command 'fixmbr'. 

In this case you cannot give the excuse of 'I don't have the install disk' because **if you don't have the install disk then there's a question of how exactly you installed windows in the first place. Did you pirate the install CD or get it from some friend of yours? Thats illegal you know.**

Get a Ubuntu Livecd. You said that you can't access your computer at all, let alone download the CD. As far as I can see **you seem to have access to some computer here to be able to flame regularly on this forum as well as on Slashdot.**

If you cannot take to change well and always want someone to blame for everything then choose a branded product with support. In case of Linux you have Novell, Suse, RedHat, etc to do the needful for you. Free Software is for people with free minds, people who are willing to take the initiative to learn.

Lastly, its free as in Freedom, not as in Pizza (I don't drink beer ;-) ).

Siddhesh

--
[http://siddhesh.tk](http://siddhesh.tk)

---

### Post by r4ik on 2006-03-21
UbuntuDupe,
You could go get the Ultimate Boot Disk,

[http://fileforum.betanews.com/detail/Ultimate_Boot_CD_Full/1066657762/1](http://fileforum.betanews.com/detail/Ultimate_Boot_CD_Full/1066657762/1)

It includes a Super Grub part.
Also very usefull on Windows trouble shooting.
Good luck !

---

### Post by AtinLango on 2006-03-21
Try Super Grub Disk. You can even search and download and make a bootable diskette. I have used it several times to restore grub, though instructions are not very clear. If you choose to, then boot with the disk and look for some sequence like this:

Choose English Grub System … (press a key –e.g. spacebar when required)
Choose Install Grub in Hard Disk … (press a key –e.g. spacebar when required)
Choose Automatically Install (so many errors appear)
It says Successful
Reboot without diskette. OK. It has worked for me several times.


Alternatively, you can get back your windows running by using a Windows98 bootable diskette (download and create) - irrespective of what windows you are using. Boot with it and type

```
fdisk /mbr
```

to fire windows.

---

### Post by r4ik on 2006-03-21
I think it cant get any clearer,
Just in case where to get one,

[http://www.bootdisk.com/](http://www.bootdisk.com/)

---

### Post by catlett on 2006-03-21
You guys are better people than I am. I've been tryning to get to the end of the thread to get a piece of this guy and you have let it go by and are still helping. I guess that is why I'm drawn here. Since the fight is over I'll just make a quick point. UbuntuDupe is a dupe for not having a backup for his system. If he had a backup he would just have to install it and he could have his windows back and be on his way. Why someone would do something as complex as dual boot an OS and change their MBR without a backup is beyond me.God bless the Ubuntu people because you have the tolerance of JOB.

---

### Post by meborc on 2006-03-21
ok, this thread should die here... please don't post here anymore! :cool:

---

### Post by Danny Boy on 2006-03-21
Ubuntu Dope, your attitude is ridiculous! First off everyone here volunteers, that take their own free to help newbies like myself (&you). I posted a few problems myself and was either walked through it step by step or pointed to a link. This is a lot better than any Windows "support" I've ever gotten.

# 1: Anyone with half a brain knows that you should back up all important data regularly not to mention when fiddling around with little things like the *MBR*.  :rolleyes: 

# 2: You're ARE NOT installing to the average system, correct me if I'm wrong but the average system only has 1 HD, you have 3. 

[INDENT]I installed Ubuntu 3 times, once to test and other time to format and reinstall windows and partition again for Ubuntu. Finally after three days I decided to go with Ubuntu exclusively so I formatted the drive and did a straight install of Ubuntu. All the installs were very easy, really no room for error except in partitioning.  If the majority have no trouble installing, you screwed up. [/INDENT]

# 3: If you depend on Windows for this or that, you should always have a system disk at the ready. Windows is very pron to crashes, I cannot tell the number of times the sys disk saved my hide. 

# 4: Again If you depend on Windows that much why would you even bother installing another OS that could possibly completely screw up your Win installation? 

# 5: If you have three HD's you must know something about PCs they didn't just install themselves, you should be smart enough to backup your important data on an external HD that wouldn't be infected should a virus spread through out your system, or at least use CD/DVD-RW's. 

My suggestion to you If everything is that screwed. Accept that you've lost the information on your primary drive. Format it and do a clean install of Ubuntu, don't bother trying to partition for Windows. Once you get U installed try mounting your other drives and see what you can recover. 

Short of that.

Take you computer to a technician experienced in data recovery.

---

### Post by meborc on 2006-03-21
THIS IS VERY OLD THREAD... LOOK AT THE DATE IN THE BEGINNING!

this thread should die here... please don't post anymore! :-({|=

---

### Post by asdfasdf on 2007-03-05
I promise not to respond to this thread anymore. :popcorn:

---

### Post by Mr. Picklesworth on 2007-03-05
For future reference, this tutorial that I quickly found might be helpful: [http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html)
I haven't looked much into it, but putting a basic Linux kernel onto a bootable floppy should work; the super GRUB disk could also work, but it's a CD thing so not really as useful if you need it *after* something breaks. (And the interface I wound up with is terrible).

Just out of curiosity: Why can't Grub handle these errors in an easier fashion? It is a very bad thing to have screw up, so why can't the power of those recovery disks exist within Grub as a backup for when something goes wrong? "It doesn't work, look up this error code!" is not helpful when the only resource to look up that error code is the computer which doesn't work :b

---

### Post by genti on 2007-04-02
Ok I had a similar issue,

**Do a backup of the files first!!!**

Try this, boot from the Live Cd and chose recovery.
Then choose your partition as the destination. 
Choose shell in the installer environment. (This kind of gives you a B plan)
Once you see the shell type chroot /target. You will be in your old computer.
Type export TERM=linux
And then grub

choose your root (hd0) or (hd0,X) and then install grub wherever you want, MBR or the partition, (hd0) or (hd0,X)

This also solved another problem I had, with the 
The file /boot/boot/grub/stage1 not read correctly

for people who do not know what to do (like me, when in grub your can try help to see the available options)

---

### Post by jescis on 2007-07-23
[FONT=Times New Roman]I know this thread is old, sorry for bumping it.  But,  :lolflag: to the thread, and  to [/FONT]UbuntuDupe <in baby speak voice> want someone to hold your hand?</ end baby speak voice> BWahahaha :evil:

---

### Post by stalkingwolf on 2007-07-23
I will leave off most of my comments for Ubuntu dope and just raise a couple of questions.

He is not trying to dual boot.  From his comments winnowed from the ranting,raving,whining and crying,
he is trying to triple boot.  3 drives, 3 systems. So the question would be to start with How is the 3rd drive
jumpered?  As I recall it should be jumpered as a slave.

Again as I recall the second Os  should carry the primary grub install, then the 3rd added to it.



OK I'm sorry but I just have to say this,
I have tried to see this situation from the OP's point of view.  However I just can't get my head that far up my ***.

---

### Post by rev.tig on 2007-12-06
Sorry to resurrect this thread but I found it while searching for this exact error and symptoms.

Unlike the OP I did have a live CD and it did not help either,  I could use the recovery option and see all my files but could not resurrect grub at all.. all the paths and everything seemed fine.. 

I was at my wits end until I suddenly had a horrible feeling,   yes I went into my BIOS and discovered that my BIOS had reset itself and when it did it put my external hard disk (USB) above my internal one.   Oh how obvious I hear you cry! :)  but it is not when you had not changed anything and then one morning it just does not boot :)   Of course when you boot the live CD it finds the disks and puts them in the right order so it becomes transparent :) 

I hope this helps someone if they get this issue,  it is not an Ubuntu error and don't be too hard on yourself if you missed the obvious too :) 

:KS

Oh I even did the super grub disk thing too :)  Thanks for that Mr Picklesworth,  it did not save the day this time but I think it might come in handy down the line it is a great little tool :)

---

### Post by boborosso on 2008-01-01
I came to this thread because ubuntudupe is still linking his bad experiences with ubuntu in his sig on slashdot.
Thought you'd like an update.
Apparently the guy got back to windows, then tried to clean up a partition that held ubuntu data and erased data by mistake.
[http://slashdot.org/~UbuntuDupe/journal/190568]("http://slashdot.org/~UbuntuDupe/journal/190568")

Of course forgetting all the suggestions to backup data before attempting operations that he got earlier in this same thread, plus using a windows tool on a windows OS and having the thing erasing stuff is somehow ubuntu's fault :lolflag:
 
Of course grub shouldn't be the recommended choice to boot linux, he suggests bringing up the BIOS boot menu every time. Way practical, especially on one of my laptops where you have approx 1.5 secs to hit the key. Never mind bootloaders (lilo, grub, yaboot, aboot) working reliably in my experience, never mind the suggestion being ridiculous for the ever increasing number of spare linux boxes administered exclusively through ssh. 

To somehow counter ubuntudupe adventures with my completely ubuntu-unrelated experience, I have this laptop: cdrom not working at all, usb boot not working, windows not working well. But wait, realtek boot agent. So I got debian running on it as in this journal entry.[ http://slashdot.org/~marcello_dl/journal/191672]("http://slashdot.org/~marcello_dl/journal/191672")
Turns out windows not working well because the hard disk is not working well too. This laptop must have taken some beating when travelling across Europe. So, first installation went bad. Restarted the netboot installer, rescue mode, went to the shell, ran an fsck with bad block scan and erased all files without reformatting, so the bad blocks stay marked, and reinstalled again. HAL is having issues with the broken cdrom, fixed that too after a quick googling. 

Locked windows out of computer. Happy :)

---

### Post by stalkingwolf on 2008-01-01
After reading all of the OP comments both here and @ slash. I have come to the conclusion
that the OP is/was correct. It was a boot loader problem.  IMO the BOOT was Not properly loaded.

IMO THE BOOT should have been forcefully loaded into that orifice where his head resides.

---

### Post by maniac_X on 2008-01-01
C'mon people, give UbuntuDupe a break!  It's Windows fault!!! Windows makes you crazy and super frustrated after long usuage. He is just venting the only way he knows how....after probably years of training from the "finest" (read as sarcasm) OS in the world, amiright?! :lolflag:

Hopefully he is on his way to finding out if in fact it was his harddrive that caused the problem or not. If it was/is the harddrive, I hope he would give Ubuntu a second chance to prove itself worthy. If he actually has a chance to use Ubuntu, there may yet be salvation for him and continued use could possibly be considered therapy from that other fine OS (ROFl!)

ps. to UbuntuDupe..you mentioned that you have WD harddrives somewhere in the posts above I think. Don't know who you buy them from but if it's not a big retailer of computer stuff, I would be caustious about buying drives from an unauthorized reseller. You can run into problems getting warranty service in such cases.

---

