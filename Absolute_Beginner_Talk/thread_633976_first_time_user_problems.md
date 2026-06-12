---
title: "first time user problems"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by blackbirdjohn on 2007-12-07
Hello I have just loaded and run the ubuntu 7.10 64 bit bootable disk and everything seems to work fine at first ie screen keyboard drives etc all recognised. it also found my wanadoo wireless connection which I eventually got configured after 4 reboots as when I inserted my wep key or password or username or email address and made any sort of mistake choosing the options the whole computer just froze no keyboard or mouse and no error just froze. once I sussed where each of the bits of information went it then connected fine, but when I went onto utube it requires a flash player which wont auto load on a 64 bit system so I googled and followed the various methods to install this using the dos type instructions but it now says the flash player wont run on a 64 bit system .Ok I will leave that for now and check my Ebay type in my username and password and were in but now I have no keyboard to type in a search but mouse functions fine . After hours of rebooting and reloading all of the above these problems are 100% repeatable. I am wary of installing to my hard drive at this stage but would booting and running from my hard drive solve any or all of these problems and will XP Pro still work ok?
system is DFI Infinity
latest bios
2 X 512 corsair pro series running dual chanell @ cas2 
Inno 7300gt video card PCI-E
philips ultimate edge sound card PCI
standard keyboard
usb mouse
I am absolute newbee so please assume total ignorance when replying 
thank you 
John

---

### Post by jordanmthomas on 2007-12-07
I would like to introduce you to the Return key.  It is on the right-hand side of your keyboard.

Anyway, if you are having a hard time getting flash to work on 64-bit and you are new, you can give 32-bit a try.  I wouldn't do this if I had more than 3 GB of RAM though since 32-bit OSs can only see 3.8 (I think?)

The locking up might be caused by the desktop effects, so try turning them off (system --> preferences --> desktop effects)

Overall, the system runs much better when actually installed.  Your Windows XP install will still work fine unless you mess up when you are installing.  Make sure you understand the part about partitioning to save yourself some pain.

---

### Post by Dynaflow on 2007-12-07
I had no problem running 32-bit flash while I was briefly experimenting with with 64-bit Ubuntu.  If you are having problems getting Flash tonight, you're not alone.  Adobe's done ... something ... with their Flash plugin again, and a lot of people are having experiencing trouble (read: wall-kicking frustration) getting the thing to install. 

Welcome to Ubuntu, by the way.  May I ask if there's a particular reason you want to run the 64-bit version instead of the 32-bit version?  Do you have >4 gigs of RAM or something?

---

### Post by viking777 on 2007-12-07
I don't understand your problems with Flash. I have a 64bit system and Flash player installs without any difficulty on it and you certainly don't have to use any 'dos type' instructions to do it - in fact if you do you are almost certain to fail as a newbie, something I wish Linux developers and programmers would come to realise.

Have you seen the 'Add Remove Programs' entry in the start menu? If you can't find it hit Alt/F2 and type 'adept_installer' (no quotes) in the run command. In the Adept search box type 'flash' and you will find it under the sub heading 'Others'. Adept will install it for you with a couple of clicks. 

Mind you this does assume that you are using a Mozilla browser, if you aren't you can get one of those from Add/Remove programs as well if you haven't got one already (firefox).

---

### Post by blackbirdjohn on 2007-12-07
Hello again thanks for the quick replies
To start at the begining I wanted to build a new rig to store approx 2000 lp recordings
it seemed simple enough get all the hardware assemble it and start recording but I purchased a copy of XP PRO which requires me first to input the security code from the cd package and then register with MS once you get it installed
However as this was a new build and I introduced each component part one by one XP kept requireing to be registered again and again to the extent that I now have to phone and convince someone that I am not a software pirate in order to get a new code
hence the linux trial
I tried the 64 bit version as I have a 64bit cpu seemed logical
Having done a lot of ubuntu googling I have actually ordered a 32 bit version and will try that when it arrives 
I apologise if I am rambling on a bit here but a lot of the forums have replies starting we need more information
thanks again 
John

---

### Post by Dynaflow on 2007-12-07
> **viking777 said:**
> I don't understand your problems with Flash. I have a 64bit system and Flash player installs without any difficulty on it and you certainly don't have to use any 'dos type' instructions to do it - in fact if you do you are almost certain to fail as a newbie, something I wish Linux developers and programmers would come to realise.

Ah, I see the problem.  I think he's trying to install Flash while just running the LiveCD, which I don't think can be done no matter what.

To answer part of the original question, yes, you do need to install the OS to download and install restricted components like that.  You don't have to pave over XP.  Just defrag the hard drives a couple times, and then follow the installation instructions that let you set up a new partition for Linux on your hard drive.  Windows should not be harmed; it'll just seem to have less storage space.  

Don't expect Flash tonight, though.  Adobe has to clean up its mess first.

---

### Post by blackbirdjohn on 2007-12-07
Thanks again folks 
I will wait for 32 bit version which I ordered a couple of days ago and try again
I did wonder if it needed to be installed on a hard drive as a lot of the initial problems arose inputing stuff in to boxes ie wep keys passwords etc which logically would need to be stored somewhere 
As the 64bit version appears to need a bit more setting up I will try the 32 bit and go from there
regards
John

---

### Post by hyper_ch on 2007-12-07
Why not downloading the CDs? Throught torrent it's very fast and you can start immediately.

---

### Post by blackbirdjohn on 2007-12-07
The post has just arrived with the 32bit version
as there is nothing on this computer I cant live withought I plan to install a dual boot XP/ UBUNTU system initially (another initialisation code from MS)

Should I reformat my hard drive and if so what file system ie FAT NFTS etc

which OS goes onto the hard drive first

if I eventually choose to use ubuntu exclusivley can I remove XP to get back the windows partition withought reformating the drive  again 
thanks again 

( the help and information on here is  a revelation )
John

---

### Post by viking777 on 2007-12-07
> **blackbirdjohn said:**
> The post has just arrived with the 32bit version
as there is nothing on this computer I cant live withought I plan to install a dual boot XP/ UBUNTU system initially (another initialisation code from MS)

Should I reformat my hard drive and if so what file system ie FAT NFTS etc

which OS goes onto the hard drive first

if I eventually choose to use ubuntu exclusivley can I remove XP to get back the windows partition withought reformating the drive  again 
thanks again 

( the help and information on here is  a revelation )
John

Much easier (essential?) to put XP on first. Ubuntu, when you install it, will acknowledge the existence of xp and will automatically include it in its boot menu. That doesn't work the other way round.

Ubuntu certainly and xp I think will format the drive for you when you install them so there is no need to do it seperately. You will have to partition it though, but Ubuntu and xp both contain options for that (ubuntu is easiest).

You can certainly reclaim your xp partition later if you decide to, gparted has tools to do that although I haven't used them so you might want to get some other advice there.

So basically install xp (if it is not there already) then install ubuntu and let it resize your xp partition for you to make room for itself.

Jobs a good 'un:lolflag:

---

### Post by daradib on 2007-12-08
FYI:

This is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by blackbirdjohn on 2007-12-10
Hello again folks
its been an interesting weekend
I ran the 32bit cd and  it loaded 100% no problems so then I installed to hard disk and allocated 50% approx 100gb of the drive to Ubuntu and started the load
It loaded up to 67% and machine froze 
I waited an hour and still frozen so re booted into live cd and tried again but this time it offered me 50% of 100gb ie 50gb so I knew it had done the format and partition the first time but it again froze at 67% 
I rebooted into the cd again and ran the check disk program on the cd and found a bad file.
OK dont panic go into xp and download another copy of the cd but the unfinished install(s) had not set up the dual boot stuff before it siezed up so no XP.
got an old hard disk with windows loaded and got onto net and downloaded the live cd  file and burned it onto a disc (and did the file check all ok) 
changed back to the 200gig drive and started again using the whole drive and got 100% load and a working machine 
I then configured my internet connection and downloaded the updates and nvidea video card files all went well 
Next I tried the flash player but the Adobe would not work at all (downloaded ok) so tried gnash and its codecs and this this works some of the time.
I have now read and printed MS excel and word files using the Ubuntu software
I have also copied digital photos to a cd using Ubuntu software 
I have had better help from other users than any helpline could ever offer.
and computing is fun again .
To anyone reading this and contemplating Ubuntu I would say that I am a 62 year old pig farmer and I got it up and running in a weekend albeit with a bit of help and a lot of googling and Bill Gates is going to have to produce something pretty spectacular to get me back onto windows
Thank you again for all the help
regards
John

---

### Post by blackbirdjohn on 2007-12-10
Hello again folks
its been an interesting weekend

I ran the 32bit cd and  it loaded 100% no problems so then I installed to hard disk and allocated 50% approx 100gb of the drive to Ubuntu and started the load
It loaded up to 67% and machine froze 

I waited an hour and still frozen so re booted into live cd and tried again but this time it offered me 50% of 100gb ie 50gb so I knew it had done the format and partition the first time but it again froze at 67% 

I rebooted into the cd again and ran the check disk program on the cd and found a bad file.

OK dont panic go into xp and download another copy of the cd but the unfinished install(s) had not set up the dual boot stuff before it siezed up so no XP.

got an old hard disk with windows loaded and got onto net and downloaded the live cd  file and burned it onto a disc (and did the file check all ok) 

changed back to the 200gig drive and started again using the whole drive and got 100% load and a working machine 

I then configured my internet connection and downloaded the updates and nvidea video card files all went well 

Next I tried the flash player but the Adobe would not work at all (downloaded ok) so tried gnash and its codecs and this this works some of the time.

I have now read and printed MS excel and word files using the Ubuntu software

I have also copied digital photos to a cd using Ubuntu software 

I have had better help from other users than any helpline could ever offer.
and computing is fun again .

To anyone reading this and contemplating Ubuntu I would say that I am a 62 year old pig farmer and I got it up and running in a weekend albeit with a bit of help and a lot of googling and Bill Gates is going to have to produce something pretty spectacular to get me back onto windows

Thank you again for all the help
regards
John

---

### Post by hyper_ch on 2007-12-10
For installation I recommend to use the alternate install cd. It doesn't look as pretty but normally the installation works better. It's also adviced that before you start the installation that you check the CD for defects. It's on of the options at the boot screen.

---

### Post by viking777 on 2007-12-10
Good news John, and well done for persevering\\:D/

---

### Post by daradib on 2007-12-10
Congratulations! Welcome to Ubuntu and the free and open source software world.

That said, please see [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397) for the Flash player problem (remove Gnash first through Synaptic Package Manager- System -> Administration -> Synaptic Package Manager).

---

