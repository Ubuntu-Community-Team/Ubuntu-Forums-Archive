---
title: "Possible to do these things with Ubuntu?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by DAXP on 2007-01-08
I have two main desktops. Well, three, actually, but I plan to sell it. >_> Anyway, I want to know if I can convert to Linux and still do these things, since I like Linux a good bit more than Windows, and one of the PCs has been getting a BSOD fairly often (I thought that was disabled for Windows XP o_O). Anyway, uses:

PC 1 (BSODs ahoy): Mostly media. Has two IDE HDDs, both 160GB. Fairly good specs. Programs often used are iTunes (perfer Media Player Classic, but pressing next with my remote makes it go to the previous song/video/etc.,..), BeyondTV (TV program, used with my TVTuner card. This is a very important program, though I'd be fine with trying anything similiar)..and..I think those are the only things I'm not sure about for Linux counterparts. Only other things are Azureus, GAIM, and Firefox, which I know I can use, and I'm 99% sure there's a media player I liked. >_> I do need to be able to use my remote, either a Firefly media remote or a Windows Media Center remote from my laptop (I still use said laptop, and pressing buttons CAN turn it on, even when it's not plugged into the laptop. Same for my 360. So I perfer the firefly). I also need to be able to use an IR transmiter thing, which lets me change the channel on my cable box with my PC. It's a USB-UIRT, if anyone knows of it. I also use this as my..device hub, I guess. My PCs are networked, and it has a 250GB HDD, 20GB HDD, and 80GB HDD plugged into it, along with an old printer I need to upgrade (it rarely works in Windows =/). I'd prefer to have all HDDs on the same file system, though it isn't needed. Especially if it's easier and stable for Windows to write to EXT3 (assuming I use that for the Linux HDDs) and Linux to write to NTFS.

Wow, this is longer than I thought. <_< Anyway, PC 2..

PC 2 (no BSODs): This one I'm not sure about. I use two 400GB HDDs in a RAID (0? 1? the one that lets em act as one, I can never remember. >_<). I use this for one main thing: Games. I love my PC games. I'll need to be able to play pretty much any PC game avalible, without dual booting (I end up staying only in Windows =/). I also need to be able to mount CD images. I know there is a command for .ISOs, though I forgot it, but I need to also have a way to mount .cue/.bins, and..actually, I think all of them are either .ISOs, .BIN, or .CUE. Doesn't matter if I have to conver the files first or just mount them. I've never used a Virtual Machine (is that even the right terminology? <_<), but that may be the best choice for me. I usually run Oblivion, FEAR, etc.,.. on max settings, would that be possible in any way with Linux? I'm fine with paying for Cedege if the game support is good, and there isn't much of a hit in graphics/framerate. I also would love to play my fames in 1920x1200, my usualy resolution. This is all assuming it works with me RAID HDDs. I have a spare 300GB IDE drive I could probably hook up, if needed. I'm not sure where I'd need to put the HDD, though, if someone could tell me. The mobo has one IDE cable, but I have only one IDE device, a DVD Burner. Would the HDD need to be the master or slave? >_>

Yar, I think that's everything...seems like it...I'm really looking for an excuse to go back to Linux. I just like it so much better, and loved learning new stuff as I went along to make my experiance better. If someone has good news for me, I'd be really happy and thankful.

But I don't think I have an Ubuntu CD, which means I'll have to download the image again. But that's fine with me if it'll work! I'll edit this post if I can think of anything else. Sorry that's it's so long, didn't think it'd be when I started. <_< If needed I can get the name of the TV Tuner I have, along with the name of any other part in me PCs. Just tell me.

Also, not sure if this is the right forum. If not, I'll copy and paste it in the right one, and delete this one.

---

### Post by yager on 2007-01-08
For the TV card, check on MythTV.  I have no experience with it personally but it can turn your computer into a full fledged TiVo like device.  That may be a little overkill, but check it out.

In the case of games, Check in the Games forum for some info.  There are many threads on different games and you may find what you need there.  A quick check on oblivion turned this thread up that refers to another site with detailed instructions on how to run Oblivion using Wine.
[http://ubuntuforums.org/showthread.php?t=222057&highlight=oblivion](http://ubuntuforums.org/showthread.php?t=222057&highlight=oblivion)

You may want to keep the game machine as Dual Boot.  During the install, downsize the Windows partition and do it that way for your game fix.

I have played with VMWare and it is cool.  The only downside though is that it is only experimental using DirectX which is what most games want.  Also installing Windows XP will require that you activate it.  Since VMWare appears to be a completely different computer from your original machine, you will have to contact M$ by phone to get the activation key to work.  Then as I understand it, your activation will fail on your base machine since the activation calls home to M$ and tells them all about your new "computer" to prevent future piracy of your activation key.  You could always roll your key from the 1st machine to the VMWare machine.  Oh and if you have an OEM version of Windows XP, the copy that shipped with the box, you may not be able to convince M$ that you are using the same machine since I doubt that the VMWare box has any of the same components being reported.

---

### Post by DAXP on 2007-01-09
I've talked to some other people, and I pretty much plan to do this:

For PC one, install Ubuntu and MythTV. This is assuming I can get the remote and USB-UIRT working with it. And it has most, if not all, of the functions of a Tivo already. <_<

For the gaming PC, I'm just gonna keep Windows. I hate dual booting, even though I love Linux. =/ I really, really hope some programmer will make a magical program that lets you emulate Windows programs near perfectly, or even just Windows games. Oh, that would make me a very happy person... And I wouldn't need to call to activate Windows, I have a CD with nine versions of it. One of them is Corporate, or something of the like, and it doesn't require an activation.

I do have one more question. I have a laptop as well, running Windows Media Center. This PC I wouldn't mind dual booting, as I don't use it much. Usually I let friends use it to play games, like WoW, Oblivion, WC3, etc.,.. It uses two 60GB RAID HDDs, in the same config as the second PC above. Does anyone know if it would be possible for me to either split the drives (JBOD config, I think that is called) or partition them so that I can have 60GB for Windows and Linux? I can either install the Windows that came with the laptop, or use a CD to install a different version. In fact, assuming I can install Linux to the RAID HDD, I think I could do this anyway. I'll do some testing with it, worst that can happen is that a friend will lose an Oblivion save he wanted to erase, and me waste time. 

One last question, I swear. For now. Is there a logical reason that downloads seem to go faster in Linux? It's always bothered me. Downloading the same file from the same server (not at the same time), Linux beats Windows by at least 10KB/s, which is a decent amount (for me, I like all the speed I can get, even if the downloads are already in the 100+KB/s range >_>). Not a bad thing, by any means, but I'm curious..

Wait, I was wrong. Sorry. <_< Would anyone have reccomendations on what to do in terms of partitions for my storage HDDs? I'd like as much as possible accessable by all PCs, but it doesn't matter too much. My setup (with what I'm thinking in parenthesis):

PC One (assume I install Linux)
20GB   USB (FAT32)
80GB   USB (FAT32)
160GB         (No clue. Either FAT32, EXT2, or EXT3, probably)
250GB USB  (See above.)

PC Two (Windows only)
800GB NTFS (so this will only be readable, but I plan to use ReiserFS for the Linux System Drive anyway, so they'll just have to settle to using the storage Drives as..brokers of a sort)

Laptop (also assuming I can install Linux, with the drives split)
60GB (not all in one partition, but most of it in ReiserFS)
60GB (NTFS, like the 800GB one)

Also, ReiserFS is best for Linux, right? I heard that long ago, but I don't even remember where. And there is no limit to the size of a FAT32 HDD, correct? I do not remember.

Anyway, going to make sure I don't have a current Ubuntu CD, and either start installing or downloading.

---

### Post by yager on 2007-01-09
Wow you sure like to ask alot of questions in one post.  To raise the odds of getting most answered, you may want to split them up some.

I am no expert on which format is best for the hard drive.  I would suspect that you will have many opinions and some references to benchmarks about why their favorite format is best.  EXT3 is the default and works fine for me.  No complaints.

As for your partition ideas, you may want to set up an extra partition for the /home directory and minimize the size of the Ubuntu partition.  This will keep all of your data separate just in case you have to reinstall Linux.  This could be a life saver.  Check this link for a good guide.

[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

In the case of the RAID drive, you should be able to turn RAID off in the BIOS and then have two 60GB drives.  You should check the documentation for your laptop.  Both drives of course will be be identical copies of your Windows XP install.  You leave one alone and install Linux onto the second drive.  If you want to boot through GRUB, you will need to install this to the first drive or for the short term, you can change the boot order of your drives through the BIOS.  I choose the second option because my wife and daughter would freak out if the computer were to start in Linux instead of Windows.

---

### Post by mdsmedia on 2007-01-10
Just in relation to the choice of filesystem for Linux.... I'm no expert, so this is simply thinking aloud:

There is a program for Windows which will allow it to read and write to/from EXT3.... I don't have a link but there are threads discussing this on the forums, and there is a script for Linux writing to NTFS, although I'm still not sure of its stability....I believe it has been used reasonably successfully, but more analysis would be recommended before using it.

My point is that if you're choosing between EXT3 and ReiserFS, would it be important to you whether you could read/write to/from each OS from/to the other OS?

If it's important, then on that basis I'd probably use EXT3 for Linux.

As I said, though, I'm not an expert on this and you should tread carefully before writing to either OS from the other.

The biggest drawback I can see with FAT32 is the limited filesize of 4Gig. If you can write to EXT3 from Windows, then maybe EXT3 is a better option than FAT32. I believe EXT3 and NTFS are better filesystems than FAT32 in other ways too, but FAT32 IS read/writeable from both OSs.

---

### Post by DAXP on 2007-01-10
Already keep a second partition for /home. Or did when I used Linux. But, I got impatient and went ahead and installed Ubuntu again. Yes, lots of questions. >_>

Still installing stuff, and haven't gotten around to getting me remote to work or MythTV, but I really like the Listen Media Player. Or Music player. Whatever.

And I just went with EXT3. I haven't formatted the external drives yet, though, because I want to copy everything first. Oh, that'll be fun...

Anyway, still have a few things to do. Since I won't be using the main HDD for much, I'm going to install a lot of...oh, crap, I forgot the word. Desktop managers, or something. Like KDE and Gnome. >_> And keyboard shortcuts to make, MythTV to install and get working. Woo. It better work right. It has to. If it doesn't.... <_<

Well, along those lines..one more question. Assuming WINE can run BeyondTV, the PVR program I used in Windows, could I keep that running all the time in the background? That's for a worst case scenario where I can't for whatever reason use MythTV.

---

### Post by macogw on 2007-01-10
It wouldn't make sense to have wine just running.  I'm not sure it can even run on it's own...The way wine works is you have to tell it WHICH program to run.  You could set the command "wine nameOfYourWinApp" in the sessions startup so that that Windows app is always running, I guess.

There's no Linux iTunes.  Apple wants to pretend they're the only alternative.  MPlayer is available though.

---

### Post by DAXP on 2007-01-10
Oh well, just have to hope MtyhTV works.

The only reason I used iTunes is because the next/back buttons worked right with it. <_< I like Listen much better, but I can't figure out how to make my keyboard shortcuts work. It has a media, play/pause, stop, etc.,.. buttonsm but only the play/pause works with Listen. The media button opens Music Player, and I assume next and back work in that program. But I haven't tried yet. >_>

---

