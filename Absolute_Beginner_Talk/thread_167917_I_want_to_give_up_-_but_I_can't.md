---
title: "I want to give up - but I can't"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by Sonlc on 2006-04-29
Ok, after many many problems that I've had over relitively simple things, I've decided to give up on linux altogether.  Alot of people on these forums have helped me greatly and I thank them for that, but these problems should never have been apparant in the first place.

All I want to do, is to reformat my hard drive and install Windows XP again.  The trouble is that I cant.  I insert the Windows XP disk at boot, and I get the error "Disk Error - Please restart".  I pannicked at first and thought my Windows CD was corrupt, so I tried my old Windows 98 Disk, and the same thing happens.  I'm stuck, and I can't go anywhere.  Can anyone help me at all? ](*,) ](*,) ](*,)

---

### Post by Koybe on 2006-04-29
It's sometimes happend with win XP after a linux install. I don't really know why. 
You can download a rescue CD like UBCD : 
[http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)

Then you can erase completly your MBR. Pay attention, you'll lost all your datas on your hard drive.

GL ;-)

---

### Post by Sonlc on 2006-04-29
Thanks for the reply mate.  Obviously I need an ISO to burn to disk.  The downloads come in 2 formats, one being a self extracting executable, the other being a zip file were you would have to compile your own ISO from it.  Both of these things are completely out of my grasp in linux.  Its a vicious circle.  Is there anything I could use that would just come as a plain ISO?

---

### Post by confused57 on 2006-04-29
Here's a thread that may help:

[http://www.ubuntuforums.org/showthread.php?t=83893&highlight=install+xp](http://www.ubuntuforums.org/showthread.php?t=83893&highlight=install+xp)

Is your bios set to boot from CD?

---

### Post by Sonlc on 2006-04-29
Confused57, That thread is in relation to Sata drives.  I dont have one.  My Bios is set to boot from CD.

I managed to burn the recovery ISO.  It still gives me a disk error.  Infact, after a few attempts, its not attempting to boot from CD at all now, its just going straight into GRUB.  Surely someone can help?

---

### Post by confused57 on 2006-04-29
Have you tried starting your computer with the Ubuntu install CD?  If it works,
couldn't you repartition the entire disk with ntfs, but not actually choose to install Ubuntu?   It may not work, but I saw it mentioned in the thread.

There's always the possibility there's a problem with your CD drive.

---

### Post by BoyOfDestiny on 2006-04-29
[QUOTE=Sonlc]Confused57, That thread is in relation to Sata drives.  I dont have one.  My Bios is set to boot from CD.

I managed to burn the recovery ISO.  It still gives me a disk error.  Infact, after a few attempts, its not attempting to boot from CD at all now, its just going straight into GRUB.  Surely someone can help?[/QUOTE]

Are you sure the boot order is correct? Make 100% sure that the CD is set to boot first. It doesn't make sense that it would go to grub unless your cd is not bootable...

---

### Post by Koybe on 2006-04-29
[quote=Sonlc]Thanks for the reply mate.  Obviously I need an ISO to burn to disk.  The downloads come in 2 formats, one being a self extracting executable, the other being a zip file were you would have to compile your own ISO from it.  Both of these things are completely out of my grasp in linux.  Its a vicious circle.  Is there anything I could use that would just come as a plain ISO?[/quote]
The zip file have an iso file in it... nothing to compile. Just burn it. ;)

---

### Post by Sonlc on 2006-04-29
I got the ISO onto CD, but it still gives me the error.  The boot sequence is defenately set to CD first.  And now, like I said, I'm not even getting the error anymore, Its just going straight to Grub.  If it makes any difference, I have a dual boot with Windows XP, which will not load properly because of an aggressive registry remover tool that I ran.  Ubuntu is still booting fine though.  Am I running out of options here?

---

### Post by htinn on 2006-04-29
It isn't enough to "get" the ISO onto the CD. It needs to burned in ISO mode.

---

### Post by confused57 on 2006-04-29
Those registry cleaners can sure mess up a windows system, at least your Ubuntu is still working.  If your XP, 98, or Ubuntu install disks won't boot up, a rescue disk probably won't either(I thought win98 install disk booted from a boot floppy 1st?).  Do you have another CD drive you could switch out, sounds like it could be a problem with the drive?  Iso files must be "burned as an image", not just copied to disk.  I don't really know, wish I could be of more help.
   It could possibly be the IDE cable connected to your CD drive.  You might want to try your hard drive as master on your primary IDE and CD drive as master on your secondary IDE channel or hard drive as master and CD as slave on the primary IDE, just make sure your jumper settings are adjusted for this.
Do you hear your CD drive spinning up when you're trying to boot up, may take several tries to get the CD drive to spin up when booting(try ejecting and closing the CD door when booting)?  Just trying to give you some ideas.

    Can you boot into windows XP safe mode?  If you can, you might be able to do a system restore of the registry.

---

### Post by Sonlc on 2006-04-29
yeah Its burned as an ISO.  Both the Ubuntu, Windows XP and 98 (se) Cds wont boot properly either.  I dont have a floppy drive so I cant test out any boot floppys.  :(

---

### Post by jonnyfive on 2006-04-29
It's because of how your harddrive is formated. It's in some format that works for linux but is unrecognizable to windows. Find some resource that will let you format y
our drive and partition it to ntfs or something and that should work.

---

### Post by Bartender on 2006-04-29
Wouldn't Darin's Boot & Nuke be the simplest thing to do?  Wipe the HDD clean and the XP CD should work fine, right?

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by jonnyfive on 2006-04-29
I don't think so. It's not about whats *on* the harddrive it's about how the harddrive is formatted.

---

### Post by halitech on 2006-04-29
maybe I'm completely off base but what does the HD formatting have to do with a CD not being seen and booting? I could understand if the CD was booting and windows coming up saying it can't find a HD to install on being a formatting peoblem but IMHO, this is either a CD problem or a CD ROM issue. 

If you go into the BIOS, can you try to autodetect the cd again? maybe the CD rom is on it's way out. Or from Ubuntu, can you access the drive? If both of those work, do the cds work in another drive on another computer? I think you should find 1 or the other doesn't work.

just my 0.02 worth

---

### Post by jonnyfive on 2006-04-29
No where did it say it was not reading the cd.
Here's the thing. Linux requires the Harddrive to be formated in a certain way.
This certain format is COMPLETELY different then what XP uses.
So when trying to run the xp install you are going to get a disc error because it doesn't recognize the harddrive.

---

### Post by halitech on 2006-04-29
> All I want to do, is to reformat my hard drive and install Windows XP again. The trouble is that I cant. I insert the Windows XP disk at boot, and I get the error "Disk Error - Please restart". I pannicked at first and thought my Windows CD was corrupt, so I tried my old Windows 98 Disk, and the same thing happens. I'm stuck, and I can't go anywhere. Can anyone help me at all?

Sonic, maybe you can shed a little more light on whats going on. Does the cd get recognized, starts the windows install then bombs out cause it can't read the HD or, when it's trying to boot the cd does it come up not readable?

---

### Post by htinn on 2006-04-29
[QUOTE=jonnyfive]No where did it say it was not reading the cd.
... So when trying to run the xp install you are going to get a disc error because it doesn't recognize the harddrive.[/QUOTE]

[QUOTE=Sonlc]Both the Ubuntu, Windows XP and 98 (se) Cds wont boot properly either. I dont have a floppy drive so I cant test out any boot floppys.[/QUOTE]

@jonnyfive: Excuse me, but what is your problem?

@Sonlc: Double-check the BIOS settings, and make sure you're not actually booting the floppy and/or hard drive first.

---

### Post by Sonlc on 2006-04-29
When I insert any cd for boot (Windows, Ubuntu etc) I get the error message "Disk Error, Please Restart".  I've tried on both cd/dvd drives.  There is not a problem with the drives, as I am using them fine in Ubuntu.  For some reason now, over the past couple of attempts, its completly ignoring the CD's altogether now and going straight to Grub.  I've also attempted the drive wiper iso that someone recommended in this thread, and that also gets ignored and goes straight to grub.  As I said, the bios is correctly configured to boot from CD, and I've even tried resetting the bios to default and changing the boot sequence.  Nothing works...

---

### Post by halitech on 2006-04-29
just out of curiosity, does it come up asking if you want to boot from CD? I know on my laptop, it will come  up with a message about boot from cd and if you don't press the enter or space bar, it boots from the HD.

---

### Post by Sonlc on 2006-04-29
Nah, no message at all, other than the error.

---

### Post by Mustard on 2006-04-29
At the moment its sounding like its a problem with the CD drive itself.

---

### Post by pshnfry on 2006-04-29
does grub give any options other than linux?

---

### Post by Sonlc on 2006-04-29
Yeah, it gives the usual failsafe/memtest/windows XP options.  As I said before though, both CD Drives are working fine as I am using them in Ubuntu for playing music and burning the drive wiper iso's onto.

---

### Post by halitech on 2006-04-29
ok, so lets recap. We have:
1. system with Ubuntu installed. 
2. CD Rom that works fine in Ubuntu
3. Install CD's from M$
4. System that refuses to boot from M$ CDs.

ok, answer is obvious. Machine is too smart to allow M$ back on it :D

(PS> Yes I know that didn't really help but thought maybe some humour would help ease the situation)

---

### Post by Buffalo Soldier on 2006-04-29
this is really weird.. hmmm. Sonlc, how about more details about your computer?
Brand? Model? Type of harddisk? Type/brand of CD drive? Slave/Master? stuff like that.

Some brand of computer, especially Compaq, requires that you use their own Windows XP installer. Meaning the generic OEM Windows XP installer won't work.

---

### Post by Sonlc on 2006-04-29
I'm not sure on the model of the hard drive.  I think it might be a Maxtor, but its at 80gb and 5400 rpm anyway.  As for the cd drives etc, its just the ones I got with the computer at the time (a few years ago).  Its an emachines 820.  It came with an OEM installer at the time, but I reformatted it from the off and used my own XP install, and I regularly reformat and install the PC as a matter of principle (which is why I dont really mind having to wipe my drive).

On the plus side, I've been wanting to upgrade to a new system for a while, and this may force me to do so, but obviously I'd rather not get to that stage just yet..

---

### Post by Sonlc on 2006-04-29
I'm not sure on the model of the hard drive.  I think it might be a Maxtor, but its at 80gb and 5400 rpm anyway.  As for the cd drives etc, its just the ones I got with the computer at the time (a few years ago).  Its an emachines 820.  It came with an OEM installer at the time, but I reformatted it from the off and used my own XP install, and I regularly reformat and install the PC as a matter of principle (which is why I dont really mind having to wipe my drive).

On the plus side, I've been wanting to upgrade to a new system for a while, and this may force me to do so, but obviously I'd rather not get to that stage just yet.

Btw, I really appreciate the help you guys are giving me

---

### Post by Buffalo Soldier on 2006-04-29
Not sure if this will help, but it seems this guy is having the opposite of your problem. [http://forums.amd.com/index.php?showtopic=72993](http://forums.amd.com/index.php?showtopic=72993)

---

### Post by Buffalo Soldier on 2006-04-29
from [http://www.linux-hacker.net/cgi-bin/UltraBoard/UltraBoard.pl?Action=ShowPost&Board=aoltv&Post=16&Idle=0&Sort=0&Order=Descend&Page=0&Session=](http://www.linux-hacker.net/cgi-bin/UltraBoard/UltraBoard.pl?Action=ShowPost&Board=aoltv&Post=16&Idle=0&Sort=0&Order=Descend&Page=0&Session=)

> Yesterday I solved this problem of not being able to boot from CD. I found that even though the bios was set to boot from CD or Floppy before HD, The drive setup was not showing the CD because it was set to "none". So I changed it to "Auto" - it displayed the CD drive and I was then able to boot from CD.

---

### Post by Sonlc on 2006-04-29
[QUOTE=Buffalo Soldier]from [http://www.linux-hacker.net/cgi-bin/UltraBoard/UltraBoard.pl?Action=ShowPost&Board=aoltv&Post=16&Idle=0&Sort=0&Order=Descend&Page=0&Session=](http://www.linux-hacker.net/cgi-bin/UltraBoard/UltraBoard.pl?Action=ShowPost&Board=aoltv&Post=16&Idle=0&Sort=0&Order=Descend&Page=0&Session=)[/QUOTE]

Gah, I just checked my bios, there is no auto option :(

Whats even stranger now is the fact that when I boot, it now keeps asking me to insert a system disk in Drive A:  (My floppy drive has been disabled for months and completly unplugged)

---

### Post by pshnfry on 2006-04-29
Does your bios detect the cd drive and report parameters and/or model in bios set up, not just the post?  If not, there will be some other method in bios for detecting and setting these parameters other than autodetect.  Read the motherboard manual (download it if needed).

Check for bios updates as well at the m/board manufacturer site, but only consider applying if fixes address any percieved problems.

---

### Post by confused57 on 2006-04-29
Sonic,
    Are you sure you want to give up on Ubuntu?  Where else can you find this kind of knowledge and willingness to help others and dual-booting XP with Ubuntu can help you rescue data on windows.  You've gotten advice from some of the more knowledgable gurus on this forum and people who are quite experienced with computers, windows, and Linux.  Ubuntu would take up only 5-10 gigs of hd and would be insurance to recover to your system.
 You wouldn't get this kind of support from Microsoft and it's free.
Hope everything works out for you...

---

### Post by Stew2 on 2006-04-29
Hello, very strange situation indeed :confused: . I noticed that you said that you use your own XP install disc to reinstall on a regular basis. Having used an emachine restore disc before, I know why you do that :) . Just wondering though if you still have your original emachine restore dics? If you do, I would give them a shot to see if you can boot from them, then you could always do a clean XP install again after restoring the original emachine configuration. Just a shot. Hope it works out for you. :) 

Regards,
Stew

Edit: Please disregard this post, after rereading all the posts I dont think the original restore discs will help, I just thought it was worth a shot as they have bailed me out when it seemed nothing else would work.

---

### Post by sophtpaw on 2006-04-30
[COLOR="Red"][/COLOR][SIZE="5"]just give up[/SIZE]

---

### Post by confused57 on 2006-04-30
Sophtpaw,
You must work for tech support at one of the major computer manufacturers, or used to.

---

### Post by catlett on 2006-04-30
Try plugging in your floppy drive. I think in some weird way your machine thinks it is accessing the floppy.
Here is what I'm thinking. If I leave a floppy disk in when I shutdown, the next time I boot, it won't. It gives me the error "not a system disk". I remove the floppy and restart. My machine boots fine. Your situation kind of sounds like it wanted a floppy removed but it is expecting another one to be put in.

Since you have a floppy drive and access to Ubuntu, you should be able to make a bootable floppy from your XP install disc. I'll try to find directions but you should be able to google it.
Also disregard whatever the Johnnyy.. guy was saying. It doesn't matter what format a hard drive is when you run an install disc. The install runs off the cd and will format the drive to what it wants.
You should be able to make an XP rescue floppy from your XP install disc and then run the install. The install will format your drive into an NTFS or FAT C partition and install.
If you can't boot from your floppy drive it's beyond me. Good luck.

---

### Post by indytim on 2006-04-30
Sonic,

If you want to take the "drastic" approach, you might want to consider doing a low level reformat of your HD.  A low-level re-format will completely wipe out your HD and zero fill it's contents.  Typically when I'm building a new PC or moving op systems ( like Windows->Ubuntu :D ), I do this.  You can find Seagate's tools at [http://www.seagate.com/support/disc/utils.html]("http://www.seagate.com/support/disc/utils.html") 

I believe they have both a CD version as well as a floppy.  If you take this route, make sure your bios is set up to boot from CD (you will need this when you re-build Windows).  After your hd has been zero filled, the Windows install CD should detect that you have a blank HD and want to format before it will start the Windows install.

One additional note, the zero fill operation takes a very loooong time to run.  I think the last time I did it on a 160g HD it was about 7Hrs.  Be patient.

IndyTim

---

### Post by bbarrons on 2006-04-30
if your bios settins are correct and you cant boot from the CD at the get go THEN your problem is with the CD-ROM. deosnt matter that you can use it in ubuntu.
nothing else matters. ubuntu wont effect your bios or boot options in any way UNTIL the hard drive is recognized in the boot sequence. You have a hardware problem.  So, the very first thing to do is uncable your hard drive, only have your CD hooked up to MB and then boot. If your CD wont boot then, try a different CD-rom. dont mount it. just hook up the cable to it, the power and set it on the top or rest it on a box or something. boot it again.  BUT before you do all this burn a bootable CD that has fdisk on it and mbr. FDISK will delete your non windows partition. I know, I have done it so many times on so many different machines. even emachines. then use mbr.
 here is a MS tut on using fdisk and mbr. IF you have a windows partition you should be able to get back to it without damage. if not fdisk can delete all partitions. mbr can repair the master boot record and you should be good to go.
[http://support.microsoft.com/kb/q69013/](http://support.microsoft.com/kb/q69013/)
 Also, maxtor makes a bootable CD and floppy for their drives. you might look on their website.
just my 2 cents..... hope this helps.
Bill

---

