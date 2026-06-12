---
title: "Ununtu Repositories for 11.10 PPC"
date: 2011-11-07
forum: Apple Hardware Users
---

### Post by MacPenguin1972 on 2011-11-07
Hello,

I am trying to do an install of Ubuntu 11.10 for Power PC from the CD I created off the .iso file. I did a topic search but nothing seems to come up... or nothing that is in "plain English" for a novice like myself. I'm looking to learn here. :)

I have hit a "wall" of a sort and can't seem to find a current post to deal with this? 

Does anyone know the current repositories for Ubuntu 11.10 so I can set my system to download and update? Also if someone could share the "sudo" commands or command line commands for this I would very much appreciate it.

Also is there a place, like a website that frequently updates changes in the URLs for these repositories when the old ones go bad or don't exist anymore? 

Thanks,
MacPenguin

P.S. -- Sorry, that's UBUNTU repositories, not Ununtu! lol!

2nd P.S. -- BTW- I am looking strictly for Ubuntu under the Ubuntu name. Not any variant. I don't know enough about this to make "Lubuntu" or "Xubuntu", etc. work for Ubuntu. (In my mind they are different versions- suggests to me their CODE is also different - I could be wrong but until I know more about it...)  "Keep it simple" I figure. I admit again, I'm a total novice and trying to learn this stuff. Thx.

---

### Post by mikewhatever on 2011-11-07
Was there any problems with the install? The list of repositories is usually in /etc/apt/sources.list, and I really don't understand what wall you are talking about. Can you explain in plain English what the problem is.

---

### Post by MacPenguin1972 on 2011-11-07
> **mikewhatever said:**
> Was there any problems with the install? The list of repositories is usually in /etc/apt/sources.list, and I really don't understand what wall you are talking about. Can you explain in plain English what the problem is.

I got some kind of error when I was installing. Apparently it was trying to download from the repositories. I got an error saying they were bad or didn't exist. So I need to know how to change my Ubuntu to "direct" it to the right link for the repositories.

---

### Post by MacPenguin1972 on 2011-11-07
Based on the error. I assume the "list" it is working from is bad. How do I get Ubuntu to get the correct list or links?

Also, how do I find and/or edit this "/etc/apt/sources.list" please? Thx. :D

---

### Post by mikewhatever on 2011-11-07
Can we have a look at the sources.list first.

---

### Post by pauljwells on 2011-11-07
Hey MacPenguin1972. The mirror problem has been plaguing ppc installs for the last few versions :-/ It looks like the best way to install now is to use the mini iso. I haven't done this yet but I'm bracing myself to update my G5 to 11.10 in a couple of weeks.
rsavage seems to have the best handle on the various problems. You'd probably do well to read through this thread, read the links rsavage posts and then try again. It's what I'm going to do.
Post back with success or failure reports. There are so few ppc users now :-(
[http://ubuntuforums.org/showthread.php?t=1871320]("http://ubuntuforums.org/showthread.php?t=1871320")

---

### Post by MacPenguin1972 on 2011-11-08
> **mikewhatever said:**
> Can we have a look at the sources.list first.

First, I had to dump out of the install.  I got no list- a generalized error message.

Second, I do not know how to access this list. I am asking because I do not know.

I am currently using Mac OS X. I cannot access the list because I do not know how even if I was using Ubuntu.

---

### Post by MacPenguin1972 on 2011-11-08
> **pauljwells said:**
> Hey MacPenguin1972. The mirror problem has been plaguing ppc installs for the last few versions :-/ It looks like the best way to install now is to use the mini iso. I haven't done this yet but I'm bracing myself to update my G5 to 11.10 in a couple of weeks.
rsavage seems to have the best handle on the various problems. You'd probably do well to read through this thread, read the links rsavage posts and then try again. It's what I'm going to do.
Post back with success or failure reports. There are so few ppc users now :-(
[http://ubuntuforums.org/showthread.php?t=1871320](http://ubuntuforums.org/showthread.php?t=1871320)


I will give this a try. Sadly the only way to boot off a Mac that I know of is via an internal hard disk or a CD/DVD ROM. 

I figure if I can get this to boot off a disc I can see what happens.

(BTW- I tried exactly what the other user tried- that iso slighty larger than a CD- I burned it to a DVD and ran into the same issue)

---

### Post by mikewhatever on 2011-11-08
> **MacPenguin1972 said:**
> First, I had to dump out of the install.  I got no list- a generalized error message.

Second, I do not know how to access this list. I am asking because I do not know.

I am currently using Mac OS X. I cannot access the list because I do not know how even if I was using Ubuntu.

If you are in the live CD environment (does that work with the powerpc?), you can type **gedit /etc/apt/sources.list** in a terminal window to view the file.
To edit, type **gksudo gedit /etc/apt/sources.list**.

Having looked around, I could not find the live CD for Oneiric. The PowePC wiki suggests a minimal CD with no links to oversized ISOs. 
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)
Can you post a link to the ISO you've downloaded.

---

### Post by MacPenguin1972 on 2011-11-08
> **mikewhatever said:**
> If you are in the live CD environment (does that work with the powerpc?), you can type **gedit /etc/apt/sources.list** in a terminal window to view the file.
To edit, type **gksudo gedit /etc/apt/sources.list**.

Having looked around, I could not find the live CD for Oneiric. The PowePC wiki suggests a minimal CD with no links to oversized ISOs. 
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)
Can you post a link to the ISO you've downloaded.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

This was where I got it. But now it has version 12. 

Which, I am wondering how to use the Mini iso then set the repositories so it will download the necessary installation files from the correct place.

---

### Post by rsavage on 2011-11-08
> **MacPenguin1972 said:**
> Which, I am wondering how to use the Mini iso then set the repositories so it will download the necessary installation files from the correct place.
 
Seriously?

---

### Post by mikewhatever on 2011-11-08
> **MacPenguin1972 said:**
> [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

This was where I got it. But now it has version 12. 

Which, I am wondering how to use the Mini iso then set the repositories so it will download the necessary installation files from the correct place.

Well, doesn't matter. Can we have a look at your sources.list now.
One usually doesn't need to edit, set or change the repository list at the time of installation, especially on the mini iso.

---

### Post by rsavage on 2011-11-08
@mikewhatever It is not the sources.list that is the problem. There is a hack around at the end of the thread pauljwells posted that will fix the mirror error on the live cd I think. Whether MacPenguin has further problems with the live cd installer depends on the ata controllers in their computer.
 
@MacPenguin1972 So that you don't accuse me of having a God complex again, lets be clear I want you to successfully install ubuntu. But, for that to happen you have to actually read the threads people are giving you, not just the first post. I wrote quite a detailed guide to installing from the mini cd. You can't have escaped the links to it. If you don't understand something on there I'll be happy to explain it as I appreciate linux (like any new hobby) has a steep learning curve. But, you have to read it and try it out first otherwise you waste the time of people trying to help you.  Contrary to what you may think (and have posted before) we are not basement dwelling geeks with all the time in the world.

---

### Post by MacPenguin1972 on 2011-11-08
> **rsavage said:**
> @mikewhatever It is not the sources.list that is the problem. There is a hack around at the end of the thread pauljwells posted that will fix the mirror error on the live cd I think. Whether MacPenguin has further problems with the live cd installer depends on the ata controllers in their computer.
 
@MacPenguin1972 So that you don't accuse me of having a God complex again, lets be clear I want you to successfully install ubuntu. But, for that to happen you have to actually read the threads people are giving you, not just the first post. I wrote quite a detailed guide to installing from the mini cd. You can't have escaped the links to it. If you don't understand something on there I'll be happy to explain it as I appreciate linux (like any new hobby) has a steep learning curve. But, you have to read it and try it out first otherwise you waste the time of people trying to help you.  Contrary to what you may think (and have posted before) we are not basement dwelling geeks with all the time in the world.


Question:

How am I supposed to find relevant information to answer my questions about _**UBUNTU**_ in a thread about a RECODED version of the platform called **_LU_**buntu?

Two totally different codings and file structures in my mind. If Lubuntu is meant to be a  "lightweght" version of Ubuntu, it has a different file structure to make it so, doesn't it?

How then can one use instructions for that to work for the "bulkier" original version that needs more to work with from the sound of things?

My other problem is time. When there is a thread of 100 replies, that's a lot to sift through to find the single URL or sudo instruction(s) I am looking for to get the job done.

I'm not the reading kind, I am the hands-on visual type learner. I need to do it to lear, but I need the tools I need to get the job done. I'm the kind of guy who hooks up a stereo or a video entertainment setup without a manual-- only grabbing the manual when I get "stuck". That's what is happening here. 

Due to my work and class schedule I do not have time to read 100s of threads to find one answer.

You don't want to be confused of a God-complex, but you're still looking down on someone like me who is less skilled at linux than you. You know the answer but won't share it.

Some of us do not have the luxury of time to sit on these forums.

I STILL do not know how to set my Ubuntu to download the files it needs from the correct repository.

I am still waiting for osmeone to tell me the link or commands.

If you don't want to tell me fine, just say so.

---

### Post by pauljwells on 2011-11-08
Hey Macpenguin1972! I'm personally not exactly sure what answer you need:-/ The correct repo for powerpc should be ports.ubuntu.com - does this help?? This is what you need during the installation. If you could find and post the /etc/apt/sources.list file that mikewhatever mentioned it would help us to understand what state your machine is in.

Don't worry about the differences between the various *buntu distributions; their fundamental code bases are identical - the differences are only in the final layer of code that generates the screen display. All the ppc *buntus will use exactly the same repos and the individual flavours can be installed as meta-packages (which is just a package that causes lots of other packages to be installed. You can run xubuntu, lubuntu, ubuntu all on the same machine just selecting at login.

The mini iso route is the best way but it's still not easy. I've been doing this stuff for years and 11.10 is proving one of the most difficult distros to install ever, certainly in terms of *buntu installs.
Rsavage really is trying to help - he's put a lot of effort into helping me and others before now. He doesn't have a God complex - you just haven't been able to describe your problem well enough for any of us to understand what answer you need. That's why we're all fishing.

Some things are just HARD... 11.10 on ppc is one of them!

---

### Post by rsavage on 2011-11-08
Hey pauljwells, how do you know I haven't got a God complex?!  I just said I didn't want to be accused of having one!  

I'm surprised you are having trouble with 11.10 because since you fixed unity-2d you have God status!  

If somebody could post back if this [http://ubuntuforums.org/showpost.php?p=11409752&postcount=27](http://ubuntuforums.org/showpost.php?p=11409752&postcount=27) fixes the mirror server error than that would be good. 

If you still don't have a successful install then you may have to do further stuff [http://ubuntuforums.org/showthread.php?t=1872733](http://ubuntuforums.org/showthread.php?t=1872733) , but it all gets very complicated and in the end it is easier to get to 11.10 by upgrading.

---

### Post by pauljwells on 2011-11-08
> **rsavage said:**
> I just said I didn't want to be accused of having one! lol :-)

I'm working (4000 miles) away from home at the moment on a contract so I don't get much time on the G5 to try stuff. I'll be back next week for a few days and already have the mini isos downloaded ready to try. I'll be posting back with plenty questions!

I use a Thinkpad x220 on the road. Installing 11.10 on that was _such_ a breeze - on x86 everything really does _just work_

We are making life hard for ourselves with these old ppc machines...

---

### Post by MacPenguin1972 on 2011-11-08
(Post deleted by poster)

---

### Post by MacPenguin1972 on 2011-11-08
> **pauljwells said:**
> Hey Macpenguin1972! I'm personally not exactly sure what answer you need:-/ The correct repo for powerpc should be ports.ubuntu.com - does this help?? This is what you need during the installation. If you could find and post the /etc/apt/sources.list file that mikewhatever mentioned it would help us to understand what state your machine is in.

Don't worry about the differences between the various *buntu distributions; their fundamental code bases are identical - the differences are only in the final layer of code that generates the screen display. All the ppc *buntus will use exactly the same repos and the individual flavours can be installed as meta-packages (which is just a package that causes lots of other packages to be installed. You can run xubuntu, lubuntu, ubuntu all on the same machine just selecting at login.

The mini iso route is the best way but it's still not easy. I've been doing this stuff for years and 11.10 is proving one of the most difficult distros to install ever, certainly in terms of *buntu installs.
Rsavage really is trying to help - he's put a lot of effort into helping me and others before now. He doesn't have a God complex - you just haven't been able to describe your problem well enough for any of us to understand what answer you need. That's why we're all fishing.

Some things are just HARD... 11.10 on ppc is one of them!


That last line first-- I totally agree. and 12.04 seems to have the same issue.

Ummm..... with all due respect, I'm just trying to make this thing work! lol! I took a picture of the error on my last error attempt with my digital camera.  I believe you specifically have been trying to help, others I'm not sure.  One of them decided to insult me and told me to "go use Mint Linux" because "I can't handle this and fall apart when things go wrong" or whatever in a previous post then wonders why he got accused of a "God complex" and being a "basement dweller".

I used to hook up stereo systems or program VCRs without a manual. Only grabbing the manual when I want to know something specific. I'm that way with computers too. I'm asking for help because I'm stuck.

I'm just looking for straight-forward simple answers to this.

Example -- how to go into the command line or whatever to change the mirrors or direct Ubuntu to download its files from a known working mirror or repository. Those "sudo" commands or whatever to change those settings.

Then-- is there some website or some place where I can find out at any given time what those repositories or mirrors are since they seem to change frequently. 

Things like that. I hope posting the shot of the error I keep running into is helpful. 

Thanks again,
MP

P.S.  -- ports.ubuntu.com -- how would I set Ubuntu to access files from that location and download or update whatever it needs to update? Thx.

---

### Post by rsavage on 2011-11-09
> **pauljwells said:**
> Installing 11.10 on that was _such_ a breeze - on x86 everything really does _just work_
Boring init!  :)

---

### Post by MacPenguin1972 on 2011-11-09
NEW "bug report"  -- 9-Nov-2011

This is for the benefit of other novices like myself who have had the same issues or similar issues to using 11.10 or 12.04 Ubuntu installs either full or mini-iso.

Attempted to restore Ubuntu back to version 10.10 ("last good known working version")

Was unable to restore. In spite of wiping the created partitions clean for a clean install, the new install now boots into Open Firmware when selecting "l" for "Linux" at the boot prompt. This means a complete wipe and repartitioning of the entire boot drive to allow for an uncorrupted version of Ubuntu 10.10 to be installed and function. 

Note: Ubuntu 10.10 has no issues accessing mirrors to install programs from the disc as long as "install-powerpc64" is used on a clean "free space" partition created in Mac OS X on a freshly wiped hard drive. Since there is no way in either Mac OS X 10.4.11 Tiger to rewipe the original "free space" partition without wiping the whole drive (Disk Utility is an inept program for this purpose -- while it recognizes the partitions, it will not mount or wipe them) and there is no way to do it in the partition portion of the Ubuntu install program without wiping the Mac OS X side of the drive with it (attempting to wipe the individual paritions results in errors) it is not possible to reinstall 10.10 without a complete rewipe of the entire master drive. I am backing up all Mac OS X files to external drives to prepare for this inevitable, unavoidable, step in the restoration process.

The Ubuntu Forum, after spedning much time doing keyword searches for relevant posts, has no information to better remedy these issues. There are no alternatives to wiping the entire drive for clean installs of Mac OS X and Ubuntu. With the exception of one or two users, many of my attempts to get help have largely been met with arrogant mockery.

The mini-iso for Ubuntu 11.10 also boots into Open Firmware when attempting to install, after booting into Open Firmware the machine shuts down the USB port controlling the keyboard and mouse, making any further computer use impossible. A hard restart is the only known remedy.

Have been unable to get correct mirrors for 11.10 or 12.04 installs, also do not have the command line instructions to cause Ubuntu to draw files from the correct locations. Apparently the mirrors in the install iso no longer exist. The ports were created and the mirrors deleted after creation. Users, especially novice ones, are up the creek without a paddle trying to install these versions. 

It is safe to say Ubuntu 10.10 is the "end of line" for the Power PC Ubuntu user.

---

### Post by rsavage on 2011-11-09
> **MacPenguin1972 said:**
> It is safe to say Ubuntu 10.10 is the "end of line" for the Power PC linux user.

This is utter rubbish.

---

### Post by MacPenguin1972 on 2011-11-09
> **rsavage said:**
> This is utter rubbish.

So far, I still don't know how to do what I want to do. No one is helping, including you.

PaulJWells is the only one so far who has attempted to even offer something. He has offered a lot of information on previous threads I started that I am now going back over to see what I can do with them.

Unfortunately 11.10 is a lost cause for the Power PC user until someone who knows Linux well enough fixes that install iso or posts on how to do it. AND in a way that even the biggest idiot can understand it.

So far you still haven't given me any reason to think you don't have a God complex about this. You haven't offered one single technique like a command line code or internet link that provides direct answers to any of my questions, just go sit on your high horse!

Of all the posts I see, most issues are for laptops, or other systems. I don't see many dual processor G5 users on here having the same issues as me.

---

### Post by rsavage on 2011-11-09
Look the problem is you are refusing to read the documentation or the threads we link.  Mikewhatever and pauljwells have asked you to do things and you ignore them.  So ultimately how are we supposed to help you?

If you bothered reading the release notes for 11.04 and 11.10 then you will see ubuntu recommend installing ppc 11.10 by upgrading from a previous version.   System > Administration > Update Manager .  Click the 'Upgrade' button.  It is easy when you read the documentation.

---

### Post by MacPenguin1972 on 2011-11-09
> **rsavage said:**
> Look the problem is you are refusing to read the documentation or the threads we link.  Mikewhatever and pauljwells have asked you to do things and you ignore them.  So ultimately how are we supposed to help you?

If you bothered reading the release notes for 11.04 and 11.10 then you will see ubuntu recommend installing ppc 11.10 by upgrading from a previous version.   System > Administration > Update Manager .  Click the 'Upgrade' button.  It is easy when you read the documentation.


Look I really don't mean to be a jerk but I really don't know how to take you.

I'm going over your looooooooong Lubuntu thread trying to figure it all out- those side-scrolling text boxes make this hard to print out for sure, so I'm having to re-create it in a WP file in Open Office so I can be holding this in my hand when I try the install again. 

I probably won't try 11.10 again until I install a second internal drive in my Mac (which I hope to do soon) to boot from with no OS X whatsoever on it.  I am currently copying my OS X drive so I can wipe it all out to start over again. I have no other choice- can't wipe the original Linux parititions back to "free space" again.

You have made reference to directories in THIS post- but my question is-- what SUDO commands are used to force UBUNTU to do that?  I ask because even if clicking the "upgrade" button as you say, it is going to go wherever it was programmed to go. If the directory (or repository or mirror, etc.) happens to be bad, I need to know the correct directory it needs, then, how to go in and edit so it goes into the right place.

That is one of the things I have been after here all along.

Command line instructions to make this thing work. OR, how do I set the system to do what you are talking about?

And where do I go to set those parameters?

I am begrudgiinly looking at your 7 page thread abiout LUbuntu and not find these answers. I may have to run LUbuntu instead of Ubuntu- so much for using OpenOffice.org and GIMP, etc. :-P  Ubuntu comes with an office suite of it's own but I've gotten to like OpenOffice.org's stuff. Does anything Microsuck Orifice can do. What better way to thumb one's nose at Bill Gates? (besides using Ubuntu, not Windows)

I'm just thinking the programs I want to use may not work if I use Lubuntu, then I'll be back here trying to find answers to THAT problem. I'm afraid to go through all that and run into the scenario. So I am trying to learn this stuff so I can leave nothing to chance.

Looked at Kubuntu-- would be nice to have Ubuntu and Kubuntu to have the option of both Gnome and KDE desktops since I've used both when I had Red Hat Linux 9 about 6 years ago on an old PC I got dirt cheap.  Then I could use programs for either Gnome or KDE. (From what I remember back then, 2004-2005)

I also found another thread I started I completely forgot about about compiling. I just hope I can use those techniques on any program, pretty much.

---

### Post by rsavage on 2011-11-09
This is getting ridiculous now.  I've told you the 'official' way to install Ubuntu 11.04 and 11.10 is to install a previous version such as 10.10 and upgrade.  I've told you how to do this via the update manager.  In the unlikely event that your sources list is bad (the mirror problem is only on the latest live cds) this is what it should look like for natty [http://ubuntuforums.org/showpost.php?p=11266820&postcount=11](http://ubuntuforums.org/showpost.php?p=11266820&postcount=11) .  You've been told in this thread the commands to look it up, but they are also on that linked post.  This is the easy way.  The way you are supposed to do it.  The way to do it if you can't get the mini iso to work.

You've already said you can't get the mini iso to work with your G5.  I'm sorry about that.  I don't know the answer since nobody has ever reported such a problem before to my knowledge.  So I don't understand why you are going though the lubuntu thread and are intent on installing it??  The first post on that thread is kept up to date and so you are wasting your time going through the 7 pages.

You shouldn't have to wipe your hard disk to install again.  At the partition stage of the install you'll be able to reformat the partitions where you have previously installed ubuntu.  There are the options there to do it, because I've done it.

---

### Post by MacPenguin1972 on 2011-11-09
[QUOTE=rsavage;11441295]This is getting ridiculous now.  I've told you the 'official' way to install Ubuntu 11.04 and 11.10 is to install a previous version such as 10.10 and upgrade.  I've told you how to do this via the update manager. [QUOTE]

I have, with Ubuntu 10.04, discovered that the Update Manager is unreliable. It will work for only so long. It is only as good as the repositories and mirrors it is programmed to access. If those change, Update Manager becomes a useless feature without a hack of some kind to reset it to the right place.

I got to the point on 10.04 when I originally had it that I could no longer use the update manager to update Ubuntu 10.04. I could no longer take advantage of updates and as a result, the "sofrware center" feature became equally useless. Apparently they get their files from the same place?

I do not want to run into this problem on 10.10 or any other version. WHEN the Update Manager fails (and WHEN because they do change the repositories and mirrors as I have been learning) I want to know how to set the update manager to the new locations where it is to get the files. Obviously that is a command line thing, is it not? How do you FIX the update manager when it fails?

---

### Post by pauljwells on 2011-11-19
Hi all. I have a G5 dual core, plenty of experience with Ubuntu and no working 11.10 yet!! 11.04 installed perfectly well from the alternate installer (it lets you specify ports.ubuntu.com for the mirror) @MacPenguin1972 - 11.04 has the benefit of Firefox >3 so you get the sync function and you can run unity (if you want to). In many ways it is less reliable than 10.10 (CD mounting for example.) 10.10 installs fine from the alternate installer.

Right now I am installing 11.04 mini on a new partition with a view to immediately upgrading to 11.10. I tried the 11.10 mini but got an error related (I think) to the new ATA drivers in kernel 3 ...

I'll keep you all updated.

UPDATE

11.04 cli installed fine from the mini. Upgrade to 11.10 cli went fine but will only boot the 11.04 kernel. If I try to boot the new (3.0.0.12) kernel I get the brief white screen flash (ending with 'returning from prom-init') and then it just hangs with a black screen - no initramfs shell, nothing.

Linux root=/dev/sdb4 made no difference (This is the correct partition!) I'm not sure why it would since the old kernel boots fine surely the partition is found

I added pata_macio to the modules file but this made no difference. I ran ```
update-initramfs -u
``` which updated the new kernel's initramfs but still no dice.

Stumped... I seem to have a problem that is not covered by the various threads we've all been reading and writing on this.

---

### Post by zenstate on 2011-11-19
Just wanted to point out that "PPC" means Pocket PC to many.  PowerPC is the proper term for the RISC architecture.

---

### Post by pauljwells on 2011-11-20
> **zenstate said:**
> Just wanted to point out that "PPC" means Pocket PC to many.  PowerPC is the proper term for the RISC architecture.

Thanks for that gem :-/

---

### Post by pauljwells on 2011-11-20
I finally have 11.10 on my G5, after a fashion...

Mini iso 64 bit 11.04 installed cli
Upgraded to 11.10 cli
couldn't use tasksel because of a broken dependency in ubuntu-desktop. Had to install a lower version of unity-common then apt-get install ubuntu-desktop worked
rebooted (still the 'old' kernel only) and got a nice login screen but a mess of colours once logged in. Updated the unity-common package (which uninstalled ubuntu-desktop and unity packages, but these are metas so it doesn't matter too much)
Rebooted again and it all works, more or less. One weirdness is that the applet in the top panel shows I have no connection but I'm writing this on Firefox right now from the machine...

---

### Post by zenstate on 2011-11-20
> **pauljwells said:**
> Thanks for that gem :-/

My point is the average user out there doesn't know what PowerPC is and would know the term PPC to mean Pocket PC.  There are pocket pc OS's out there so when people use the PPC term it's easy to confuse people.  

Mac RISC CPU are PowerPC not PPC.  Try to understand the language we've all agreed on..

---

### Post by rsavage on 2011-11-20
> **zenstate said:**
> My point is the average user out there doesn't know what PowerPC is and would know the term PPC to mean Pocket PC. There are pocket pc OS's out there so when people use the PPC term it's easy to confuse people. 
 
Mac RISC CPU are PowerPC not PPC. Try to understand the language we've all agreed on..
 
Wow, you couldn't let it go could you? Seriously, you went to the trouble of registering with ubuntuforums just to tell us we're using 3 letters wrong?
 
Actually, PPC can stand for a lot of things in computing [http://en.wikipedia.org/wiki/PPC](http://en.wikipedia.org/wiki/PPC) . PowerPC is one of them. 
 
This thread is posted in the Apple forum "Discussions for users who are using Apple Intel or PPC based systems with Ubuntu". For the vast majority of people using the Apple forum they will fully understand that PPC is short for PowerPC. 
 
Pocket PC if I am not mistaken is a Microsoft term is it not (and one they have now stopped using)? You could equally argue that Pocket PC should only be abbreviated to P/PC to stop confusion.
 
Sorry if this is not what you want to hear.
 
@pauljwells Glad you got 11.10 working! I'm suprised you had to start with 11.04 because don't the G5's have sata?

---

### Post by pauljwells on 2011-11-20
My thoughts exactly @rsavage! Thanks for saving me from having to respond!
The problem with my G5 is the 3.0 kernel. There's a new world of 'obscure' I'm going to have to learn to solve this one I think - into the lair of the Debian kernel hackers...

By the way - the weird colours I reported was actually unity 3D running! (very badly, but it's a start) and I'm getting nearly 500fps on glxgears so the nouveau drivers are improving. Looks like there might be a future for PP, 'oops' I mean 'PowerPC RISC architecture' CPUs after all.


@zenstate - Please don't troll, and don't hijack threads. Come back if you have a technical question, or better still, a technical answer, (like how to get the 3.0 kernel to boot on a G5 for example) then you might earn the right to lecture us on minutiae.

---

