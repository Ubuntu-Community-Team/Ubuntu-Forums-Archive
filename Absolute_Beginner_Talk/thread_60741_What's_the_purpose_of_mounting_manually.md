---
title: "What's the purpose of mounting manually?"
date: 2005-08-29
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2005-08-29
Hi I was wondering, what's the purpose for mounting everything manually in Linux?  Like the Floppy and CD-rom drive why haven't the various Linux Distro Communities made it automatic like in Windows.  

Linux has been around since the '80s right, by then someone should have been able to make such routine task automatic.  But by judging on the manual task you still have to do in this new Millenium, I'm thinking that all this trouble has to be for a greater purpose or something.

B'coz not having the Floppy and CD-rom drive mounted when you start the OS couldn't possibly save system resources that much right? #-o

---

### Post by odin on 2005-08-29
well I dont have to mount anything in my ubuntu.Just adding a couple of entries in /etc/fstab I have everything I need from the beginning.

I just guess that the mounting thing is for people who uses those devices not very often.I dont use them a lot since a have internet at home for example.

But as almost everything it depends on what you like and how you like it.

---

### Post by manicka on 2005-08-29
No, you don't have to do this with a default install on most distros. Most floppies,cdroms,dvds usb drives, cameras etc use hotplug to load automatically when needed

---

### Post by aysiu on 2005-08-29
Yeah, are you even using Linux? Because I don't have to manually mount CD-ROMs or USB drives in either Mepis or Ubuntu.

---

### Post by arnoct on 2005-08-29
It doesn't automount other partitions, though. I think this is more of the question he's asking.

---

### Post by KingBahamut on 2005-08-29
Again, thats an fstab entry correction though. 

So there really should be an issue. 

jingo, can you paste the contents of your fstab file in /etc into this thread, and then list the drive devices you want automounted ?

---

### Post by aysiu on 2005-08-29
[QUOTE=arnoct]It doesn't automount other partitions, though. I think this is more of the question he's asking.[/QUOTE] I just saw floppy disk and CD-ROM in the original post. But Linux (or KDE) does automatically make partitions appear (and they will automount if you click on them).

---

### Post by az on 2005-08-29
"Hi I was wondering, what's the purpose for mounting everything manually in Linux? Like the Floppy and CD-rom drive why haven't the various Linux Distro Communities made it automatic like in Windows. "

There is a supermount kernel patch that several distributions used, but nobody really like it and it can make your system unstable.

I am at work, now.  I can crash this windows 2000 computer my ejecting the cd when it tries to read it.

This is a 2.4 GHz processor with fast DDR memory.  The system still freezes for about twenty seconds when someone inserts a cdrom into the drive.  In ubuntu an a considerably slower system, there is next to no pause when I insert a cd and it gets mounted.


Before HAL and the various Gnome or KDE desktop ways of automounting CDs, there was automount which worked very well.  You basically assigned it a mount point and a device and it would mount the cdrom when you tried to acces the mount point in the file system.

That worked fine.




"Linux has been around since the '80s right"

90's, actually.


" by then someone should have been able to make such routine task automatic. But by judging on the manual task you still have to do in this new Millenium, I'm thinking that all this trouble has to be for a greater purpose or something."

People want a stable system.

---

### Post by chunk on 2005-08-30
[QUOTE=jingo811]Hi I was wondering, what's the purpose for mounting everything manually in Linux?  Like the Floppy and CD-rom drive why haven't the various Linux Distro Communities made it automatic like in Windows.  

Linux has been around since the '80s right, by then someone should have been able to make such routine task automatic.  But by judging on the manual task you still have to do in this new Millenium, I'm thinking that all this trouble has to be for a greater purpose or something.

B'coz not having the Floppy and CD-rom drive mounted when you start the OS couldn't possibly save system resources that much right? #-o[/QUOTE]
 I suppose one of the reasons is that you can mount many more different kinds of devices in linux than you can in windows. In linux you could can mount cdrom images, ftp servers, drives connected to other computers on the internet, or even cdrom images on ftp servers on harddrives which are connected to other computers on the internet :). The problem is where do you stop? Which devices should be automounted and which shouldn't you? You might have the freedom (read permissions) to mount the cd drive connected to your cousin's computer in California. Should that be automounted? You can certainly mount any ftp server which you can access on the internet. Should you automount all of those (that would take you a long time to boot up)?

Also, in linux, removable devices need to be unmounted before being removed. So if you're not really going to use the device then automounting will just make more work for you (by forcing you to unmount before removal).

---

### Post by aysiu on 2005-08-30
[QUOTE=chunk]
Also, in linux, removable devices need to be unmounted before being removed. So if you're not really going to use the device then automounting will just make more work for you (by forcing you to unmount before removal).[/QUOTE] They need to be unmounted in Windows, too, if you don't want to damage the device. I find it far more convenient to unmount in Linux than in Windows. 

In Linux (both KDE Mepis and Gnome Ubuntu), when I plug in a USB device (MP3 player or external hard drive), it shows up on the desktop as an icon. When I'm done with it, [I right-click on the icon and select "unmount,"](http://i22.photobucket.com/albums/b337/psychocats/ebc095a4.png) and the device unmounts and the icon disappears. 

In Windows, if I right-click on the F: or G: drive, [I get no such safely unplug option in the context menu.](http://i22.photobucket.com/albums/b337/psychocats/71c9d642.jpg) I have to click the weird white and green icon in the system tray and pick which device to "safely remove." Of course, even if I have only one item plugged in, [I see two or three different devices to safely remove, and none of them have descriptions--just "USB Device."](http://i22.photobucket.com/albums/b337/psychocats/f4ceff1b.jpg)

Give me Linux for external media *any* day.

---

### Post by N'Jal on 2005-08-30
Forgive me if I'm wrong but doesn't the whole mounting, unmounting thing have to do with being POSIX complient? All Unicies use the mount command (even OSX, but that automounts media, so it's possible to automount under BSD then), even Skyos (being POSIX complient mount's media etc.

---

### Post by jingo811 on 2005-08-30
Oh, I was merely asking these questions more in general.  I think I know by now from all the newbie posting I've done.  How to mount hidden partitions and such  :---) 
> Should you automount all of those (that would take you a long time to boot up)?
> People want a stable system.
STABILITY that's the word I was looking for!  I mean, for me learning to get a grip on the whole partition/Dual Booting trick took almost 2 years time.  Now if I want to CONVERT all the Bill Gates's in my town and free them from the Matrix.  :roll: 
I kindda have to have good arguments for them for switching to Linux.  And I think that it was pretty troublesome to have to get on the net in order to figure out how to put a:\ disk in and being able to read it at all.  In comparison to how things are done in Windows.

And all the Bill Gates's I'm trying to CONVERT won't be as stubborn as I'm in getting things to work.  In such an event they would say: "Why fix something that's not broken" or something like that.
But with the above 2 QUOTES in my arsenal, I'm slowly building up good arguments as to why things are so hands on in Linux compared to automatic Windows.

---

### Post by aysiu on 2005-08-30
[QUOTE=jingo811]
But with the above 2 QUOTES in my arsenal, I'm slowly building up good arguments as to why things are so hands on in Linux compared to automatic Windows.[/QUOTE] You may also want to print out the screenshots I linked to. Clearly, as far as unmounting goes, Linux is far more automatic than Windows is.

I think you're still missing out on something. You don't have to justify why Linux doesn't automatically mount media, because Linux *does* automatically mount media. If yours doesn't, you either have done something wrong or you have a really old Linux distribution.

---

### Post by jingo811 on 2005-08-30
Well I got the ISO image of Ubuntu around spring 2005 so most probably it's the 2:nd version of the 3 planned on their webpage.
> Clearly, as far as unmounting goes, Linux is far more automatic than Windows is. Well, for a newly turned Windows user, unmounting stuff isn't really whats on our mind the first time we load up Ubuntu.  In fact most Windows users using Linux the first time wouldn't even now about this **umount** concept.  Since they weren't messing with stuff like that in the first place in their previous OS lifes.

All I'm saying is that new Linux user just want everything simplistic to work without learning new procedures for things.  In this case merely reading files from a:\ without having to know that you either have to:
**1.** add a panel called *Diskmounter* which was totally new to me
**2.** or typing stuff in a program called *terminal*

I'm just trying to point out that, me thinks the reason for why Linux is having trouble getting sold in preinstalled PCs for the consumer market.
Is b'coz of the new procedures you have to learn for simplistic daily life operations.

---

### Post by aysiu on 2005-08-30
Did you even look at the screenshots I linked to? First of all, in Windows, you *do* have to unmount media--it's called making it "Safe to Remove," but it's the same principle. Did you ever notice that if you plug an iPod into a computer, the iPod display changes to "Do not Disconnect!!!"? You can't just plug in and unplug stuff at will. You have to unmount it no matter what operating system you're using.

In the illustrations above (please actually click on the links and look at the pictures), all I had to do in **Linux** was right-click (no terminal here--this is all done with the mouse) on the icon for my external media (which, by the way, *automatically* appeared on my desktop) and select "unmount volume," and it's gone.

In **Windows**, I had to double-click on some green and white icon and try to figure out which media to "safely remove."

I still don't understand your point. It's more automatic in Linux, and you don't need to use the terminal or some special application. The only difference between Linux's way of unmounting media and Mac OS X's is that in Linux you right-click and select "unmount volume," while in Mac, you drag the icon to the trash can. Why would it be intuitive in any way to double-click on some green arrow surfing on a white piece of paper to eject media?

Please go back and read [my original post on this subject](http://www.ubuntuforums.org/showpost.php?p=324742&postcount=10) and actually click on the links.

I'll admit that there's always a learning curve whenever you start using a new OS (I had a learning curve switching from XP to Mac OS X), but a lot of new Linux users also try to do things the hard way. For example, since there's no packaging system in Windows, a lot of Windows users are used to having to scour the internet to find basic third-party programs. So they download some .tar.gz and try to extract it, compile it from source and then run into dependency hell. What they don't realize is that you can just launch Synaptic, search for the software, and click to install it, and it will be downloaded and installed along with all its dependencies.

Who knows? Maybe for years you've been unsafely removing media from your Windows computer. In Windows you have to unmount, too. It's just called something different.

---

### Post by jingo811 on 2005-08-31
Well let us not stray away from my **main** question and add more info than needed to.  So I'm gonna try to rephrase my very first post, as I think I'm getting missunderstood here!

[I]Why does Linux supporters wonder why Linux isn't spreading to the PC-Consumer-Market consisting of **Ordinary-Joe-&-Jane**?
Why PC shops don't dare installing Linux in barebone PCs?[/I]

When simple tasks such as reading from your a:\ drive has to involve: 
**1.** digging in a jungle of FOLDERS, 
**2.** knowing which folder too look for, 
**3.** then LEFT and RIGHT(properties) CLICK without results. 
**4.** And then being forced to connect to the Internet and ask in forums,
**5.** Considering that your Internet connection worked correctly in the first place.[B]
6.[/B] Knowing in beforehand that you might need to know the commands:
mount /dev/floppy /mnt/floppy
**7.** That there's a click and point program for this called *Disk Mounter*

All this does a Windows user have to know before they even sit in front of a Linux PC their first time, and ppl wonder why instable Windows is still clinging on.  
And you might be right I might be using an OLD distro, but personally I don't think that an ISO from spring 2005 is that old.  Second you might be right I might be too RETARDED to LEFT or RIGHT click the a:\ device correctly in order to automatically mount it.

But then as a Window user sitting in front of a Linux distro for the very first time.  Shouldn't have to involve going trough steps 1-2 in order to SIMPLY read your diskette.  In comparison with poor Windows where you just click on a filemanager and directly/intuitively see an a:\ that works.
 [-o<  No hard feelings, I was forced into this  O:) Peace!?  \\:D/

---

### Post by aysiu on 2005-08-31
When I insert a floppy disk into my floppy drive [this icon](http://i22.photobucket.com/albums/b337/psychocats/c5a99b44.png) *automatically* shows up on my desktop *already* mounted. I didn't type in any commands. If anyone has to "dig through a jungle of folders," it's Windows users. Hm. Seeing the disk on my desktop already or having to click on "My Computer" and then on "A:"?

Normal users don't install Windows or configure it. Windows comes preinstalled on computers they buy.

Linux doesn't come preinstalled because companies like Dell and HP have deals with Microsoft whereby they cannot install any other OS (besides FreeDOS maybe) than Windows on their computers otherwise they lose the contract with Microsoft.

---

### Post by EnderTheThird on 2005-08-31
A floppy?  People still ***use*** those?   ;-)  I think Linux can be just as easy, if not easier, to use than Windows.  But if you *know* Windows, then it can be difficult to rethink your procedures when performing similar tasks in Linux.

> So they download some .tar.gz and try to extract it, compile it from source and then run into dependency hell. What they don't realize is that you can just launch Synaptic, search for the software, and click to install it, and it will be downloaded and installed along with all its dependencies.

*Raises hand*

Guilty!  Haha, I didn't know about Synaptic when I first tried Ubuntu last year.  I love it now though.  It's much faster than getting programs/packages separately, as with Windows, and it's FREE!  I get a fresh install of Ubuntu fully up and running in a fraction of the time that it takes me to install and configure everything in Windows.

---

### Post by aysiu on 2005-08-31
I'm guilty of that as well. After I read Roblimo's *[Point-and-Click Linux](http://www.amazon.com/exec/obidos/tg/detail/-/0131488724/qid=1125535795/sr=8-1/ref=pd_bbs_1/002-3725884-8615244?v=glance&s=books&n=507846)* book (about Mepis' Synaptic), I realized what a dolt I was.


jingo811, I think the real problem here is that you've extrapolated your one Linux experience with a particular distro on a particular computer with a particular floppy drive to be *everyone's* Linux experience.

When you don't know an OS well, you don't know what's supposed to work and what's not supposed to work. All you know is what does work and what doesn't work.

That's why my [What "using" Linux problems have people encountered](http://ubuntuforums.org/showthread.php?t=47675) thread was such a miserable failure. We're a bunch of Linux newbies here, so most of us don't know what's an installation/configuration problem and what's a use problem.

You think that having to mount the floppy manually is a using problem, but you don't realize it's a configuration problem. The floppy is *supposed* to mount automatically. However, in Windows, it's not that nothing ever goes wrong, it's just that people know right away if something's wrong and assume something's wrong with the installation, not the OS itself. If something goes wrong in Linux, they figure it's something wrong with the OS, not their installation of the OS.

For example, in my Windows installation, for some reason there's a dialogue box that says "faiLed" every time I log into the Guest account. Now, if I didn't know any better, and it was my first time using Windows, maybe I'd be like you and post on some Windows forum, "Hey, what's wrong with Windows? Why does it say 'faiLed' every time I log in? That's dumb. Linux doesn't do that."

Since I have used Windows for a long time, I know that message isn't normal. That doesn't mean the message will go away. In fact, even after I did a clean reinstall of Windows, the message didn't go away.

I'll give you another example.

In my Windows installation, every time I boot the computer, the screen ends up all fuzzy and distorted. In order to get it normal again, I have to use the "auto-sync" button on my monitor. I have to do this *every* time I boot into Windows (I don't for Ubuntu). If I didn't know better, I would say, "Hey, what's wrong with Windows? Why doesn't it autorefresh the monitor? Normal users don't want to have to press 'auto-sync' every time they want their screens just to appear normally!"

But I know better because I've used Windows for a long time that that's not the way it's *supposed* to be. If a Windows computer is working properly and configured properly, there shouldn't be a "faiLed" dialogue box on log in,  and the monitor should auto-sync itself and not be all distorted.

Likewise in Linux. The more you use Linux and/or Ubuntu, the more you'll get a sense of what's supposed to happen and how things should work. Maybe your configuration doesn't automount floppies and CDs. Sorry. But that's not the way it's supposed to be. That's not how it is for everybody's Linux installation. That's your Linux installation. Don't speak for us all because your Linux installation is messed up, and I won't speak for us all because my Windows installation is messed up.

---

### Post by EnderTheThird on 2005-08-31
[QUOTE=aysiu]I'm guilty of that as well. After I read Roblimo's *[Point-and-Click Linux](http://www.amazon.com/exec/obidos/tg/detail/-/0131488724/qid=1125535795/sr=8-1/ref=pd_bbs_1/002-3725884-8615244?v=glance&s=books&n=507846)* book (about Mepis' Synaptic), I realized what a dolt I was.


jingo811, I think the real problem here is that you've extrapolated your one Linux experience with a particular distro on a particular computer with a particular floppy drive to be *everyone's* Linux experience.

When you don't know an OS well, you don't know what's supposed to work and what's not supposed to work. All you know is what does work and what doesn't work.

That's why my [What "using" Linux problems have people encountered](http://ubuntuforums.org/showthread.php?t=47675) thread was such a miserable failure. We're a bunch of Linux newbies here, so most of us don't know what's an installation/configuration problem and what's a use problem.

You think that having to mount the floppy manually is a using problem, but you don't realize it's a configuration problem. The floppy is *supposed* to mount automatically. However, in Windows, it's not that nothing ever goes wrong, it's just that people know right away if something's wrong and assume something's wrong with the installation, not the OS itself. If something goes wrong in Linux, they figure it's something wrong with the OS, not their installation of the OS.

For example, in my Windows installation, for some reason there's a dialogue box that says "faiLed" every time I log into the Guest account. Now, if I didn't know any better, and it was my first time using Windows, maybe I'd be like you and post on some Windows forum, "Hey, what's wrong with Windows? Why does it say 'faiLed' every time I log in? That's dumb. Linux doesn't do that."

Since I have used Windows for a long time, I know that message isn't normal. That doesn't mean the message will go away. In fact, even after I did a clean reinstall of Windows, the message didn't go away.

I'll give you another example.

In my Windows installation, every time I boot the computer, the screen ends up all fuzzy and distorted. In order to get it normal again, I have to use the "auto-sync" button on my monitor. I have to do this *every* time I boot into Windows (I don't for Ubuntu). If I didn't know better, I would say, "Hey, what's wrong with Windows? Why doesn't it autorefresh the monitor? Normal users don't want to have to press "auto-sync" every time they want their screens just to appear normally!"

But I know better because I've used Windows for a long time that that's not the way it's *supposed* to be. If a Windows computer is working properly and configured properly, there shouldn't be a "faiLed" dialogue box on log in, the monitor should auto-sync itself and not be all distorted.

Likewise in Linux. The more you use Linux and/or Ubuntu, the more you'll get a sense of what's supposed to happen and how things should work. Maybe your configuration doesn't automount floppies and CDs. Sorry. But that's not the way it's supposed to be. That's not how it is for everybody's Linux installation. That's your Linux installation. Don't speak for us all because your Linux installation is messed up, and I won't speak for us all because my Windows installation is messed up.[/QUOTE]


Well said!

---

### Post by gravestone on 2005-08-31
I prefer mounting drives manually from the command line. Sorry but I've been using Linux for years and years.

The other reason for manual mounting, is that with encrypted file systems and encrpyted partitions, it is better to mount manually.

This is what I like about using Linux, is that YOU have the CHOICE whether you want to mount manually or not, unlike Windows which requres considerable registry hacking to stop the PC locking up when inserting a DVD or CD.

---

### Post by pinguimtux on 2005-09-03
I really don't see why is it troublesome to add a few lines to your /etc/fstab...And besides, Suse does that automatically during the installations process.

---

### Post by aysiu on 2005-09-03
[QUOTE=pinguimtux]I really don't see why is it troublesome to add a few lines to your /etc/fstab...And besides, Suse does that automatically during the installations process.[/QUOTE] I think the issue was about manually mounting things that are supposed to be hotplugged, rather than having things automount on bootup. No, it's not trouble to add a few lines to /etc/fstab, and when you plug things in after boot-up, they're supposed to just show up on your desktop mounted.

---

### Post by petr on 2005-09-03
I have an old vaio that has run Linux for 18 months now.  Nice.  Only issue is that I would like to use the memory stick slot that mounts directly on the PCI bus.  Not usb and no hot plug.   I can't for the life of me figure out what has to go in the fstab.  It appears to be magic - one just has to know which /dev it is.  Why doesn't the System->Administration->Device Manager just tell me?

Petr

---

### Post by UbuWu on 2005-09-03
[QUOTE=jingo811]
When simple tasks such as reading from your a:\ drive has to involve: 
**1.** digging in a jungle of FOLDERS, 
**2.** knowing which folder too look for, 
**3.** then LEFT and RIGHT(properties) CLICK without results. 
**4.** And then being forced to connect to the Internet and ask in forums,
**5.** Considering that your Internet connection worked correctly in the first place.[B]
6.[/B] Knowing in beforehand that you might need to know the commands:
mount /dev/floppy /mnt/floppy
**7.** That there's a click and point program for this called *Disk Mounter*
[/QUOTE]

Huh???? Have you ever tried Locations -> Computer -> Floppy ????

---

### Post by ad noiseam on 2005-09-06
I think that the biggest problem in this thread is that some people seem to have no problem at all with the hotplug system (their floppy or CD-Rom drives are mounted automatically, their disks or CD-Roms show up on the desktop, their cameras work up automatically in gThumb and so on).
On the other hand, some people do not have this. For some reason, my camera works with nothing at all on Ubuntu, I can not access my external DVD drive for the life of me, and while I can play music from my CD-Rom drive, I can't access data CD-R inserted in it. And in this case, yes, one can wonder why it doesn't work, and why you are supposed to browse newsgroups and forums for days before having something as minimal as reading a CD-R work.
I know that Linux is free and open source and Windows is not, and that therefore some efforts are required to make Linux work. However, there are things that more or less everybody can understand, and things that only people with computer science can deal with. And such a minor thing as reading data from a CD-Rom or a hard drive should not be something that requires hours or days of information-seeking.

Plus, there are things that people migrating to Linux from Windows don't need and won't miss (user icons, pretty drop down animations, office assistant...). But the whole issue of mounting something or having hardware function is a major one. I can work without an indicator of how much ink I have left in my printer. But I can't work without the ability to burn a CDR.

---

### Post by odin on 2005-09-06
[QUOTE=ad noiseam]I think that the biggest problem in this thread is that some people seem to have no problem at all with the hotplug system (their floppy or CD-Rom drives are mounted automatically, their disks or CD-Roms show up on the desktop, their cameras work up automatically in gThumb and so on).
On the other hand, some people do not have this. For some reason, my camera works with nothing at all on Ubuntu, I can not access my external DVD drive for the life of me, and while I can play music from my CD-Rom drive, I can't access data CD-R inserted in it. And in this case, yes, one can wonder why it doesn't work, and why you are supposed to browse newsgroups and forums for days before having something as minimal as reading a CD-R work.
I know that Linux is free and open source and Windows is not, and that therefore some efforts are required to make Linux work. However, there are things that more or less everybody can understand, and things that only people with computer science can deal with. And such a minor thing as reading data from a CD-Rom or a hard drive should not be something that requires hours or days of information-seeking.

Plus, there are things that people migrating to Linux from Windows don't need and won't miss (user icons, pretty drop down animations, office assistant...). But the whole issue of mounting something or having hardware function is a major one. I can work without an indicator of how much ink I have left in my printer. But I can't work without the ability to burn a CDR.[/QUOTE]


I have to say that I agree with you in most of the things you say.It is true that sometimes it's difficult to make some devices work but I can tell tell you something:It's more a matter of spending time working with it than having skills from the university or college.

I've studied computer science in the university and after all the years there my level  in doing anything in linux was almost 0.I had only a 4 hour per week course during six months and the only thing I can say about it is that I learnt how to install it,dual boot,add users and change permisions.Not many other things.I've been with Ubuntu and Debian full time (by full time I mean not using windows) for 5 months and everything I learned was by browsing the net ,asking in forums and getting help from friends that already knew about it.Yes,I had knowledges from school about how a computer works and networking and other stuff but nothing about everyday life with linux.
So after my experience the only thing I can say is:be patient and enjoy while you are learning.Frustrating at the begining but really nice when things get to work.

PD:I dont think at the end this post was for this thread but...

---

### Post by katiad on 2005-09-06
Well, I'm pretty new to *using* Linux, too (installed it abouta  gajillion times, but haven't spent more than a bagful of hours actually using it to do productive work)... but I have done a LOT of work on Windows machines... and I have to say this: I have met *many* people with CDR problems. Namely... problems like you describe - they can insert a music cd, but a burned cd with data on it can't be read in their computer - whereas, in their daughter's computer, it works just fine. Same with DVD players. And cameras. And printers. I spent hours and hours and hours making my printer work last Christmas... and it was *supposed* to be simple plug and play. It wasn't. ThaI've had *loads* of printer problems, and I had to spend hours online with tech support, and going through forums, and asking for advice. Just like you do with Linux. And I've worked with Windows all my life. I've had similar problems - a printer will work fine on one of my computers, but not the other. My camera will be recognized on one, but not the other. It's not a problem with the operating system itself, or even with the device. It's a configuration problem, like it was stated before. Something in that particular install, on that particular computer doesn't work right. Working in tech support, I experience a myriad of users who did not understand basic things such as... where to find the files on their floppy disks, or even how to save them to floppies, or cdr.

And having installed a number of linux distros over the years to toy with... I was shocked when I popped in an ubuntu live-cd and found everything working. My sound. My printer. My cdrs, my floppy drive. Things showed up on the desktop. I needed to configure nothing. It was easier than Windows. 

Unmount is a command that ensures no data is being written/recieved to the devices before you hit the eject button, or unplug your digital camera from its usb cord. It's protection most Windows users don't know about - because it's not safely and easily written into the system - as someone pointed out, it's not *intuitive* to click a strange icon and be faced with several choices to "safely remove", all of which are named the same thing. People don't know about it. And data is ruined all the time. In Linux, it's made more obvious in part because it *is* an important command. It's important to do this, for stability's sake. And it's really not such a difficult term and concept to learn. Before you eject, click "unmount". It may be unfamiliar to Windows users... but that doesn't mean Linux is behind on the times. What it means, really, is that there's a lot of people on Windows risking their data by unsafely removing volumes before it's safe to do so. :)

---

### Post by UbuWu on 2005-09-06
[QUOTE=ad noiseam]For some reason, my camera works with nothing at all on Ubuntu, I can not access my external DVD drive for the life of me, and while I can play music from my CD-Rom drive, I can't access data CD-R inserted in it. And in this case, yes, one can wonder why it doesn't work, and why you are supposed to browse newsgroups and forums for days before having something as minimal as reading a CD-R work.[/QUOTE]

Ubuntu is only around for a year now and it is great but there is still a lot of room for improvement left. You should file bugs about these in [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com) so the developers know about it and hopefully they will work out of the box in the next version of Ubuntu.

---

### Post by odin on 2005-09-06
[QUOTE=katiad]

 And it's really not such a difficult term and concept to learn. Before you eject, click "unmount". It may be unfamiliar to Windows users... but that doesn't mean Linux is behind on the times. What it means, really, is that there's a lot of people on Windows risking their data by unsafely removing volumes before it's safe to do so. :)[/QUOTE]

I completely agree with you.Even more,just right clicking on the icon you get on the desktop when you insert a CD there's an option saying (try to guess) EJECT so It cannot be so difficult once you know that option is there.Even for windows users when they are used to right click many times for many things.

---

