---
title: "HI, had some questions to ask?"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by xxneilxx on 2008-04-18
I want to dual boot my Windows XP SP2 and Ubuntu, on my PC.

I have already seen the following links:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) 

And i have found them helpfull.

My question regards the fact that I currently have 2 Hard Drives on my PC. 
C: is my primary drive, it is 70 GB and has my XP, Applications, Games, COursework, Reasearch Papers etc on it.

My second harddrive is a 36 Gb, this is partitioned in to 2 Hard drives both 18 GB

D: was recently my primary drive but since a crash i instaled a new hard drive with XP on it. This drive has previous windows pplication etc, which are no longer in use. Therefore is is safe for me to just format the drive?

E: is used for storage of music, programs, games

1) How should i format my D: as an NTFS or a FAT32
2) I want to use UBUNTU for programming, internet, gaming, ADOBE CS2 etc. I dont want a lot of command line interface. Which version of Ubuntu would the members suggest.
3)When Ubuntu is installed in D: can i access my C: and E: and make changes from the D; drive?
4) Same as number 3) but this time i am in the C: using my XP so can i edit the D: 
5) I currently have an Nvida GForce FX 5200 installed on my PC, i dont have my driver CD for this hardware. When i install ubuntu on another hardisk would i have to install the same driver again
6) KNowing  Ubuntu is a sturdy system i am planning on using it for browsing etc
SO if my D: which contains ubuntu crashes, can i access C; xp and get the files from my D; drive
7) Do i need to burn the OS on a cd to install it or can i do it from my XP

Any help woulld be greatly appriciated:)

---

### Post by NR1224 on 2008-04-18
About your D: drive, you will need to check it to see if the drive is still usable and the crash is not a hardware problem, if not, its safe to format. Yes you will be able to see and edit all other drives in Ubuntu. You CANT use windows to edit linux, XP cant read ext3 partions, Ubuntu should automatically install drivers for your video card, yes, you need to burn the cd, i recommend waiting until 8.04 is released in less than a week and burning that
whew.... hope this helps!!:popcorn:

---

### Post by keratos on 2008-04-18
1) doesnt matter - installer will format it anyway
2) The latest! [www.ubuntu.com](www.ubuntu.com)
3) If FAT32 or linux then YES. If NTFS then you need the NTFS filesystem plugin "ntfs 3g"
4) XP cannot write to linux partitions natively.
5) It is supported.
6) Ubuntu latest (Hardy) is not "sturdy". What do you mean by "sturdy". Define! One mans sturdy is another mans unstable!! Notwithstanding, as for acessing files, see response 4 above.
7) Google "wubi"

---

### Post by ACMarina on 2008-04-18
Are you planning on installing to the D drive??  If so, let ubuntu take care of the partitioning for you..

1) How should i format my D: as an NTFS or a FAT32

****Let ubuntu do it for you

2) I want to use UBUNTU for programming, internet, gaming, ADOBE CS2 etc. I dont want a lot of command line interface. Which version of Ubuntu would the members suggest.

****I like Ubuntu, but Kubuntu might be a good option for you too.. try the liveCD version of both and see what you think

3)When Ubuntu is installed in D: can i access my C: and E: and make changes from the D; drive?

****To a degree, yes.. you'll have to be careful not to mess anything up though.

4) Same as number 3) but this time i am in the C: using my XP so can i edit the D: 

****Depends on the file system you use

5) I currently have an Nvida GForce FX 5200 installed on my PC, i dont have my driver CD for this hardware. When i install ubuntu on another hardisk would i have to install the same driver again

****That driver CD isn't going to help much with Linux, but it should work just fine without it.  You may need to do a little fine-tuning though..

6) KNowing Ubuntu is a sturdy system i am planning on using it for browsing etc
SO if my D: which contains ubuntu crashes, can i access C; xp and get the files from my D; drive

****Depends on how bad it crashes.  The only linux installs I've ever lost were cases where the drive itself died, and it wasn't worth the time or money to send it to a data recovery facilty.  Just back up what you need and you'll be fine..

7) Do i need to burn the OS on a cd to install it or can i do it from my XP

****You could use wubi and "basically" install it, but it wouldn't be the same as a full install..

---

### Post by jameswillmer on 2008-04-18
> 
1) How should i format my D: as an NTFS or a FAT32

it really doesnt matter
if you FAT32 you can read natively in either Ubuntu or windows
if you go NTFS you can READ natively in Ubuntu and after you install ntfs-3g WRITE as well
if you go EXT3 then native in Ubuntu and you can read/write in Windows after you install the free ext3 driver for windows

> 
2) I want to use UBUNTU for programming, internet, gaming, ADOBE CS2 etc. I dont want a lot of command line interface. Which version of Ubuntu would the members suggest.

Gutsy Gibbon = current version
CS2 needs WINE plus a bit of CLI to get working (i tried and failed but many others seem to have succeeded)

> 3)When Ubuntu is installed in D: can i access my C: and E: and make changes from the D; drive?

Yes
> 
4) Same as number 3) but this time i am in the C: using my XP so can i edit the D: 

Yes, see my answer to point 1)

> 
5) I currently have an Nvida GForce FX 5200 installed on my PC, i dont have my driver CD for this hardware. When i install ubuntu on another hardisk would i have to install the same driver again

Don't worry
Most times Ubuntu does this for you automatic although I don't know this exact hardware

> 6) KNowing  Ubuntu is a sturdy system i am planning on using it for browsing etc
SO if my D: which contains ubuntu crashes, can i access C; xp and get the files from my D; drive


Its not clear what you ask
If Ubuntu crashes then you can reboot
If Ubuntu crashes again then you can boot to CLI and try to fix things
If no luck then you can boot to windows

> 7) Do i need to burn the OS on a cd to install it or can i do it from my XP

You have the choice

1) via CD allows you to boot from CD to "test the OS" on your hardware
2) do it from XP is possible if you install WUBI and then install Ubuntu which installs Ubuntu just like 1 application on winxp partition.    Read the WUBI wiki page for pros and cons

If you are serious about Ubuntu I recommend 1)

---

### Post by Vadi on 2008-04-18
> **xxneilxx said:**
> 
1) How should i format my D: as an NTFS or a FAT32

**Ubuntu Linux uses it's own filesystem. Don't worry about formatting it now, during the installation, you'll be prompted to format and you can do it there.**

2) I want to use UBUNTU for programming, internet, gaming, ADOBE CS2 etc. I dont want a lot of command line interface. Which version of Ubuntu would the members suggest.

**All versions of Ubuntu are usable for that. I'd recommend starting off with Ubuntu (found at ubuntu.com)**

3)When Ubuntu is installed in D: can i access my C: and E: and make changes from the D; drive?
[B]
From Ubuntu, you'll be able to access all of them. From Windows, you'll be able to access all of them except the Ubuntu one (ubuntu can read windows drivers, windows cant read ubuntu ones)[/B]

4) Same as number 3) but this time i am in the C: using my XP so can i edit the D: 

**Same thing, you'll be OK.**

5) I currently have an Nvida GForce FX 5200 installed on my PC, i dont have my driver CD for this hardware. When i install ubuntu on another hardisk would i have to install the same driver again

**No, it'll find the driver for you.**

6) KNowing  Ubuntu is a sturdy system i am planning on using it for browsing etc
SO if my D: which contains ubuntu crashes, can i access C; xp and get the files from my D; drive

**Yep.**

7) Do i need to burn the OS on a cd to install it or can i do it from my XP

**Better to do it from the CD.**

Any help woulld be greatly appriciated:)

Let us know if you'll have any further questions :)

---

### Post by LeoSolaris on 2008-04-18
> **xxneilxx said:**
> I want to dual boot my Windows XP SP2 and Ubuntu, on my PC.

I have already seen the following links:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) 

And i have found them helpfull.

My question regards the fact that I currently have 2 Hard Drives on my PC. 
C: is my primary drive, it is 70 GB and has my XP, Applications, Games, COursework, Reasearch Papers etc on it.

My second harddrive is a 36 Gb, this is partitioned in to 2 Hard drives both 18 GB

D: was recently my primary drive but since a crash i instaled a new hard drive with XP on it. This drive has previous windows pplication etc, which are no longer in use. Therefore is is safe for me to just format the drive? Yes, since nothing on there is going to be used.

E: is used for storage of music, programs, games

1) How should i format my D: as an NTFS or a FAT32  If you're putting Ubuntu on it, it will be formatted by the install program as ext3
2) I want to use UBUNTU for programming, internet, gaming, ADOBE CS2 etc. I dont want a lot of command line interface. Which version of Ubuntu would the members suggest. Adobe CS2 is a window's program, although you can use open source alternatives like the Gimp or Inkscape. I do not know if Adobe CS2 will work under Wine or not. Most games for Windows will not, but there are those few.
3)When Ubuntu is installed in D: can i access my C: and E: and make changes from the D; drive? Yes. a new backend was put in in 7.10 that allows for reliable read/write to NTFS partitions. They will be called something else when you're looking at them from Ubuntu through, probibly hda and hdc.
4) Same as number 3) but this time i am in the C: using my XP so can i edit the D: Read/write to Ubuntu? You can, but it will require a program that reads ext2/3 and to have it running in the background when you want to access Ubuntu.
5) I currently have an Nvida GForce FX 5200 installed on my PC, i dont have my driver CD for this hardware. When i install ubuntu on another hardisk would i have to install the same driver again? Not exactly. You will be installing a driver for your video card, but it is not the same driver used in Windows. All you have to do is install it from the Restricted Drivers program that is included in Ubuntu.
6) KNowing  Ubuntu is a sturdy system i am planning on using it for browsing etc
SO if my D: which contains ubuntu crashes, can i access C; xp and get the files from my D; drive I am not sure what you're asking here...  If the drive itself dies, it's dead regardless of the OS on it. If you do not do anything extremely off the wall with Ubuntu, it should run till the hardware dies.
7) Do i need to burn the OS on a cd to install it or can i do it from my XP? If you wait a few days till 8.04 is out, you can install it from XP with Wubi. (You can also install it in XP and use it for a while till you get used to it, but it will be slower when run from XP till it is installed in it's own partition.)


Any help woulld be greatly appriciated:)


My personal opinion, wait till next week when 8.04 comes out and use that. Just do not let the imperfections scare ya. Most things are fixable, and those you can't fix, most likely will be fixed by an update at some point.

Just remember: It's not Windows. It's not perfect (yet), and that we are here for ya!

Leo

---

### Post by xxneilxx on 2008-04-18
Alright your responses have been helpful.
With regards to NTFS and FAT32, the installer will decide it. 

So if i chose an FAT32 Format i can only read D: from an XP partition but not write? NTFS format i can read and write my D: from both partitions XP and Ubuntu, provided that i install the plugin? Is this coming with the OS or do i have to download it?

**In terms of Kubuntu, Ubuntu, Edubuntu etc it is possible to mix and match isn't it? SO i will wait for the new Ubuntu 8.04 to come out**
But what about Desktop CD and Alternate CD? I want to install ubuntu as a proper OS which I can upgrade from the internet directly, So is the Alternate CD the one for Me?

**THanks for clearing up my Graphic Card situation, by the responses Ubuntu handles this without any trouble.**

*When i mean Sturdy, i just mean that is it less prone to crashes unlike windows. I am planning on researching, downloading, email etc on ubuntu. SAving the info on the D: and then rebooting to my XP. After this i get my file off of D: and use it on either C: or E:. BEcause of this suppose that i cannot access Ubuntu my just rebooting and i have to reinstall. Can i acess the still functioning XP and copy files off of D: on onto the XP partition.*

In my earlier statements my HDs are fine. I only have my old windows xp intalled on there but i dont need these. So ubuntu will automatically remove these andinstall itself. I have made backups but does ubuntu keep the documents which are game etc on the drive while installing.

I have decided to burn it onto a disk as these seems more easier than WUBI.

---

### Post by ACMarina on 2008-04-18
Ubuntu doesn't install to FAT32 or NTFS - it has it's own filesystem.  XP can read it if you install a plugin, and Ubuntu will be able to read the NTFS filesystems on the other drive..

Ubuntu is the core distribution that uses Gnome for the desktop manager.  Kubuntu uses KDE.  Edubuntu just has some tools that are geared for education.  Xubuntu uses XFCE.  You can install the other desktop managers as you wish, but most people will try one and stick with it.  If you're going to burn CDs anyway, I suggest making one of each and just trying them live.  You can see how things look and feel and decide what you actually want to install.

Now, I've had a glitch here and there, but I've yet to really have linux "crash" in the way Windows does.  I maintain an XP desktop for school, for example - the other day I got a blue screen, then all of my drivers disappeared and I had to spend a couple more days on and off trying to find them again.  Linux just doesn't do that.  

It sounds like you want to spend your "online time" in linux.  No problem there, just download what you want, surf the web, check your email, and don't really worry about viruses or spyware or any of that.  You could even download files, save them to a central area (like E: in your case, where you keep your data)

I've installed 8.04 beta and had no trouble.  I think you could too, especially since you've got a working XP install to fall back on if things don't go right.  Just take your time and make sure you don't accidentally partition the wrong drive or something :)

---

### Post by xxneilxx on 2008-04-18
Alright i just need to install 'ext3 driver' in my Xp system to edit my linux partition. Since you haven't had any trouble with the new Beta 8.04 I am gonna download it now. Since i have no spare CDs i will only be able to install tomorrow. Since every thing is pretty much the same i am gonna go with Ubuntu 8.04. For now i am just gonna have to burn the ISO to a disk, boot my PC with the disk and follow the screen.

---

### Post by Vadi on 2008-04-18
Yup, have fun!

---

