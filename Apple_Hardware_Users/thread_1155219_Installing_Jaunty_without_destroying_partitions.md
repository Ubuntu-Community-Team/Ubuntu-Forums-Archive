---
title: "Installing Jaunty without destroying partitions"
date: 2009-05-10
forum: Apple Hardware Users
---

### Post by Benboom on 2009-05-10
I am enjoying 9.04 so much on my old 450 mhz G4 that I thought I might install it on my 1 ghz machine. However, the issue of partitioning and Ubuntu has always kept me away from this because on this machine I cannot afford to reformat the whole drive that I would put linux on. It's got a 20 gig partition at the root which currently has an OSX boot system but which I'd be willing to lose; however, the rest of the drive has stuff which I absolutely don't want to have erased. The partitioning process in Ubuntu has always appeared to me to either set up a bunch of linux disks on the drive or one big disk (well, with some relatively tiny system bits, but I think you know what I mean). I can't figure out how (or if) I can just put the linux system on the 20 gig partition and still keep the rest as Mac filesystem.

I did some searching on this but must not have used the right terms as I haven't found much yet.

However, running the Live Ubuntu disk on the faster machine is a gas and I'd sure like to get it set up...but without losing what's on the rest of the drive. Is this possible?

Thanks.

---

### Post by buntuLo on 2009-05-11
hi Benboom, you could run the live cd and from that install Gparted as a partition editor. with it you can delete the MacOS partition. then you can launch the installer and choose for manual partitioning during the process. you might choose for a basic setup, setting up two partitions in that new 20gb free space: one with mountpoint root (/) formatted as ext3 or ext4, and a small one for swap. the rest of your disk will be readable/writable from within ubuntu on the original mac filesystem. obviously, back up your data first -even if you're not going to touch your data partition!
personally, i would copy the data out of the disk (two copies for safety) and delete also the data partition. while manual partitioning during the installation, you can assign to the last large partition the mountpoint /home, formatted as ext3/ext4.
last but not least, you'll have to follow the many threads and wikis to install refit or (in case you don't plan any dual boot) simply bless your new ubuntu partition (e.g. running the MacOS installation disk).
good luck! Lo.

---

### Post by Benboom on 2009-05-11
> **buntuLo said:**
> hi Benboom, you could run the live cd and from that install Gparted as a partition editor. with it you can delete the MacOS partition. then you can launch the installer and choose for manual partitioning during the process. you might choose for a basic setup, setting up two partitions in that new 20gb free space: one with mountpoint root (/) formatted as ext3 or ext4, and a small one for swap. the rest of your disk will be readable/writable from within ubuntu on the original mac filesystem. obviously, back up your data first -even if you're not going to touch your data partition!
personally, i would copy the data out of the disk (two copies for safety) and delete also the data partition. while manual partitioning during the installation, you can assign to the last large partition the mountpoint /home, formatted as ext3/ext4.
last but not least, you'll have to follow the many threads and wikis to install refit or (in case you don't plan any dual boot) simply bless your new ubuntu partition (e.g. running the MacOS installation disk).
good luck! Lo.

Thanks, but I'm a little confused. How can I install something from (Gparted) the Live CD if I don't yet have a linux partition? It sounds like a Catch-22. I agree about backing up data but in this case there's probably more data on the other partitions than I have space to back up to. I'm thinking I should go through the whole procedure on my old machine with a dedicated linux drive first, and I wish there was a wiki or something somewhere with specific instructions as I find the Ubuntu partitioning process very hard to understand if you don't just do a basic "format everything install". Every time I have tried the partitioning options it has appeared to me that the process would partition the entire drive, losing all data currently on it.

But on the old machine, for example, I have a 120 gig drive that's entirely free and I can't destroy anything on it through stupidity. :D So what I'd like to do is set it up with a 40 gig linux area that would hold all the partitions linux needs and leave the rest for the Mac - I don't need to boot OSX off this drive.

I know this is probably described somewhere; I just haven't found it yet.

Thanks!

---

### Post by buntuLo on 2009-05-11
> **Benboom said:**
> How can I install something from (Gparted) the Live CD if I don't yet have a linux partition?
when you run a livecd, you can install software. it will be installed only in ram (not persistent), hence you can use it straight away but not after a reboot. with Gparted, you can delete and create new partitions.
> **Benboom said:**
> Every time I have tried the partitioning options it has appeared to me that the process would partition the entire drive, losing all data currently on it.
there's an option for manual partitioning during the installation process.
> **Benboom said:**
> But on the old machine, for example, I have a 120 gig drive that's entirely free and I can't destroy anything on it through stupidity. :D So what I'd like to do is set it up with a 40 gig linux area that would hold all the partitions linux needs and leave the rest for the Mac - I don't need to boot OSX off this drive.
you can do that, again using Gparted from a livecd: you have to shrink the present partition and leave empty space (e.g. 40gb if you like), then again use manual partitioning during the installation and manually create two new partitions for root and swap. ALWAYS backup everything, especially before trying to shrink partitions!

---

### Post by Benboom on 2009-05-11
>when you run a livecd, you can install software. it will be installed only in ram (not persistent), hence you can use it straight away but not after a reboot.

Wow, that is cool! I didn't know that. I was trying to play with it on my bigger machine yesterday but couldn't even play an mp3 or aiff because the codecs aren't there, but this means I could install them temporarily. That's very neat. Thanks.

>there's an option for manual partitioning during the installation process.

Yes, but it's very confusing, and the dialog seems to imply that you will lose all data on the entire disk by doing it. I think this is one case of linux being unjustifiably opaque for beginners. I'll have to try it again on a disk that doesn't matter.

Thanks for explaining that.

---

### Post by ashmew2 on 2009-05-11
Hello benboom , 

There's a manual partitioning option when you are installing Ubuntu or Linux in general.
The OS X partition you mentioned , Its size is 20 GB and you are willing to lose it.
So you can just open up the partitioner and change the partition type to ext3/ext4 . The other partitions will remain untouched.

[www.psychocats.net/ubuntu/](www.psychocats.net/ubuntu/) For any related info.Just have a read there. If you dont get anything , just ask.

and OH , ill suggest backing up data because you never know with an OS install..

---

### Post by stream303 on 2009-05-11
> **Benboom said:**
> however, the rest of the drive has stuff which I absolutely don't want to have erased.

The trap has been set!  You MUST backup that data to something else, even with the best of partitioning instructions.

No shame in not being familiar with the manual partitioning process.  How about an easier method?

There are two ways you can do it, and the goal is to create enough *free space* to install Ubuntu on, and when it comes time for Ubuntu partitioning, tell the partitioner to use that free space.  When done, the system will install the yaboot boot loader, and should automatically detect OSX and offer it as an option durin the 1st-stage of the boot process, where you enter "L" for Linux, or "X" for OSX.

The first method (with your data backed up of course) is to shrink your existing OSX install.  You can do this with Linux tools, or you can go commercial with iPartition.

If you are up for reinstalling OSX, you could reinstall OSX to say just the first half of the drive, and leave the second half open as free-space.  One does this just before following through with an OSX install by going to the top menu bar, and using OSX's disk-utility to repartition the drive.  THEN, it drops back out and you can install OSX like normal.

Once OSX has been reinstalled to the first half of the drive, and verified to boot, you can follow up with an Ubuntu install telling the partitioner to just do it automatically on the FREE-SPACE.  You will then get the yaboot boot prompt choices for the OS afterwards.

But first, do you actually have more than 1 drive in that machine, and exactly what is it?

[http://www.everymac.com/](http://www.everymac.com/)

The reason I bring that up is that even though you booted and ran ok from the live-cd, a real install might be another matter IF that machine has more than one hard-drive controller, which can sometimes be a little rough for a first-time installer.

(The issue is not the amount of drives, but the amount of controllers - some boxes with multiple drives have only one controller, ie master and slave off one controller, whereas others have more than one controller, and sometimes yaboot can get confused, requiring you to go back in manually and fix the openfirmware paths, /etc/fstab and whatnot.)

I think the smart move would be to find out what your 1g machine is, and then evaluate if you want to take the risk.

---

### Post by mkvnmtr on 2009-05-11
The first few times you partition a drive or install Ubuntu manually it can seem very confusing. It is very easy to do it wrong. Back up and back up again. Then while you are running from the live disk open the partition manager and study your partitions. Don't do anything until you are sure what you need to do. Ask questions and study your partitions some more. When you are sure what each partition is and what you want to do make sure you have backed up to another drive the things you don't wish to lose and start. If you have backed up and you foul up no big deal you can just do it again until you get it right.

I hope I made you believe that you need to back up to another drive.

---

### Post by Benboom on 2009-05-12
Ha, I solved that problem the brute force way. I'm adding a 1 T hard drive to the system (man, they have come down in price!). This particular Mac is not the one I'm already running Ubuntu on but it is a very similar model - another old G4 Sawtooth (originally 400 mhz, now a 1 ghz Sonnet Encore) with a SATA card. It currently has 890 gigs of storage on three drives but after I add the 1 T disk I'll have tons of backup space and I'm going to put the Ubuntu stuff on the smallest drive, which is only 120 gigs, and it can all go to Ubuntu. The only way I can mess up is if I accidentally put it on the wrong disk and even I am not normally lame enough to pull THAT off. :D (I hope!)

---

### Post by stream303 on 2009-05-12
Um, ok.  Just be aware that machine has the 128gb root partitioning limitations, so you'll have to manually partition it with the special apple partitions first, and keep /root to about 120gb or so, and the rest of the drive can be used for /home and swap.

The nice thing is that you have the other machine to compare it with if you need a reference.  Or you could partition "using the whole drive" knowing that it will fail at first due to /root being too large, and then re-install, but this time just change the size of the root partition back down to about 120gb, the rest /home and swap.

I guess you'll know when you get there.

If you have *three* drives, you have an additional hard drive controller, and yaboot *might* get confused over this.  It is possible that you'll have the least amount of pain if you run with just one hard drive controller, and hang the two drives just off that one board.

The plot thickens! :)

---

### Post by Benboom on 2009-05-12
> **stream303 said:**
> Um, ok.  Just be aware that machine has the 128gb root partitioning limitations, so you'll have to manually partition it with the special apple partitions first, and keep /root to about 120gb or so, and the rest of the drive can be used for /home and swap.


I don't hink this applies because I will be using the PATA 120 gig drive for Ubuntu - the SATA 1 T and SATA 500 g drives will be exclusively Mac (and use the Intech driver, which works fine for Mac), as will the PATA 230 gig drive. If I have to I can take one of the IDEs out, but I can't see why that would be necessary. My G4 that runs Ubuntu now has the same drive setup (minus the SATA drives) so unless (as you mention) it gets confused by the different controllers I should think it would work. As you say, we will see.
But this way there is little danger of losing data through idiot error.

---

### Post by stream303 on 2009-05-12
I think you've been bitten by the bug - from what - nothing to having two ppc boxes up in a week or so?  Oh yeah, you're hooked.  The first install is free. :)

I look forward to seeing how that goes, especially with the updated cpu card.  If it works, you *gotta* post a picture of it!

---

### Post by Benboom on 2009-05-12
Yeah, you know what it reminds me of? My first "real" computer was an Amiga (I don't count the Timex Sinclair or the VIC 20 or the C64, even though I suppose technically they were "real") and I used the CLI a lot with that system; I am still really impressed by what you could do on one of those in the mid 80s. I ended up owning four of them and still have two 3000s in the closet. But when Amy died and I switched to the Mac I really, really missed that whole CLI thing even though there were CLI programs under OS Whatever and by the time OS X came around it was so different I just never got into using the unix side.

Anyway, I'm impressed by how well some things get done on the PPC even with a 450 mhz G4; others, not so much. For instance, I can't believe how long it takes in Ubuntu to open a simple Terminal window compared to the same machine under OS X; it's night and day. In general, I'd say that the subjective user "snappy feel" award goes to the Mac OS but there are a lot of things I like about using Ubuntu, especially the comparatively low memory requirements. The old G4 has a gig of RAM and it's more than enough. Under OSX I always feel it's just about the minimum you need to have the system function without lagging all the time.

Ubuntu didn't start to become more usable for my own purposes until I installed the KDE package; there's a lot of stuff in there that I would use on a regular basis (Kjots, for example - I had been looking for a linux version of MacJournal and here is Kjots - cool). I could never use even a faster version of this machine for my "real" computer work because I depend too much on Photoshop (and the plugins I have for it) as a photographer, plus the Mac really does have some very good other software available for it.

But since I really tried this out to see if the software would be able to do what my wife wants to do on a netbook I think I can say that she should be able to do everything she wants to do from inside Ubuntu; it's much more like Windows to her than the Mac's OS is, and she's used to Windows from work. But I don't relish the idea of trying to maintain a Windows machine when I know nothing about them and want to know even less. :D

Main thing is, it's fun. If you know what the behavioral term "intermittent reinforcement" means, you know why people get into this stuff.

---

### Post by stream303 on 2009-05-12
> **Benboom said:**
> For instance, I can't believe how long it takes in Ubuntu to open a simple Terminal window compared to the same machine under OS X; it's night and day.

Remember that you are running a combination of both Ubuntu and Kubuntu now I believe.  You might be better off reinstalling with just Kubuntu:

[http://cdimage.ubuntu.com/kubuntu/ports/releases/9.04/release/](http://cdimage.ubuntu.com/kubuntu/ports/releases/9.04/release/)

(There are scripts to remove unwanted desktops, but unless you are comfortable with it, this is the easiest.)

You might be able to just replace some of those resource hogs in KDE with bits from LXDE, such as Lxterminal, Leafpad, PcManFM (terminal, text editor, and file manager) without having to do anything drastic, and keep KDE intact.

But still, in the end you must match your environment to your machine.  You could even start tweaking things too such as shutting off the Evolution Calendar alarm startup service if you don't use Evolution etc.

Also, Ubuntu itself is heavier than other distros since they include so many user-enhancements, which may not actually be necessary for you.  With what you know about Ubuntu, you could try Debian's KDE environment for powerpc:

[http://debian.org/distrib/](http://debian.org/distrib/)

I can almost guarantee it will be a better fit.

If you want a taste of just a simple window manager environment, at the next time you login, go to the SESSION menu, and choose ICEWM.  Login and select "just for this session only".

You should be able to fire up some common programs from icewm's menu structure, and if they are not there you can pull them up without having to configure the menu's by going into XTERM and starting a program like pcmanfm:

```
pcmanfm &
```

> But since I really tried this out to see if the software would be able to do what my wife wants to do on a netbook I think I can say that she should be able to do everything...

Good - now you can claim that machine all to yourself. :)

Actually, if you choose Ubuntu netbook-remix or whatever it is they are calling it these days, you would find an even simpler environment, and should be more finely tuned to the minimal hardware that a typical netbook has.  Look into this rather than the regular Ubuntu.

I've even heard of some running Netbook remix on their desktops for the ultimate in simplicity, or for those who just don't have any patience with computers.

I have to admit you've taken to it like a duck to water - glad to see you are keeping it fun, because for most of us, thinking about tossing an iMac out the window is a regular thing. :)

---

### Post by Benboom on 2009-05-13
So far, the apps that I actually use from the KDE package seem to be a lot LESS hoggy than the ones in Ubuntu, which seems to be the opposite of what I expected from my reading. The System Monitor in KDE, for example, is much slimmer. And Kjots, while not having a direct equivalent in Ubuntu, is quick like a bunny - it's something I really like.

I tried the Kubuntu Live CD and thought the interface was slick...but too slick, if you know what I mean. I have also read that there is considerably more support and software available for Ubuntu, although I have no real way of knowing if that's true. I just know that Ubuntu has more forums dedicated to it and if I'm going to find help for specific problems I need those forums.

I'm not sure from your comment about ICEWM if that is something I can do in Ubuntu or if I would need to be running Kubuntu; I am interested in removing stuff I don't need/use but I figured that could wait a bit until I had more of a clue. I am really just flailing about at this point, although it is fun. :D

I had tentatively planned on using the Netbook Remix on the notebook but I am following the eeebuntu forums to see how people are doing with the machine we will probably get her - the Asus 1000he is still pretty new and I think the support for it will get better quickly as the user base expands.

---

