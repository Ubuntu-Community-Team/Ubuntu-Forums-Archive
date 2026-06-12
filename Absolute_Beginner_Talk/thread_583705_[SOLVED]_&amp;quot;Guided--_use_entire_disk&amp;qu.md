---
title: "[SOLVED] &amp;quot;Guided-- use entire disk&amp;quot; Wiped out Vista??"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by wispygalaxy on 2007-10-20
[FONT="Book Antiqua"][COLOR="Blue"]Today, I installed Ubuntu 7.10 from the burned CD R I had.  Vista was shut down, and I was in Ubuntu.  However, I selected "guided -- use entire disk" during installation.  I think I wiped out my whole hard drive, and I can't find Vista.  I cannot dual boot.  Whenever I start the laptop, I go directly into Ubuntu.  Is there anyway for me to restore Vista along with my files?  I use a Toshiba laptop called Satellite A205-S4607 System Unit and Windows Vista Home Premium OEMAct.  I'm very new to Ubuntu, and please excuse my inexperience.  Thanks for helping!  :)[/COLOR][/FONT]

---

### Post by shae on 2007-10-20
I just have to ask.  What did you think "Use **entire** disk" meant?  No you cannot recover your vista partition after you erase it.  If you have an install disk for vista, you can reinstall it.

---

### Post by multifaceted on 2007-10-20
When you selected "Use entire disk"... that pretty much means, it's going to use your **_entire_** Hard Disk and will delete all data as a result. To dual boot, you need to make a partition or "area" for Ubuntu to be installed, leaving room for your Vista system. Or next time, choose "Guided -Resize Partition" --to make space for Ubuntu and leave your Vista intact.

If you really want Vista back, your only choice at this point is to reinstall with the Windows recovery disk that came with your laptop (assuming it's new)

---

### Post by wispygalaxy on 2007-10-20
> **shae said:**
> I just have to ask.  What did you think "Use **entire** disk" meant?

Well, I thought that it referred to using the whole CD R.  But I guess it was talking about the C: Drive.  I did not get a notice saying that my hard drive would be wiped out.  Can I restore my files by any chance?

---

### Post by fissionmailed on 2007-10-20
You say that like it's a bad thing. ;)

---

### Post by shae on 2007-10-20
> **wispygalaxy said:**
> Well, I thought that it referred to using the whole CD R.  But I guess it was talking about the C: Drive.  I did not get a notice saying that my hard drive would be wiped out.  Can I restore my files by any chance?

Pretty much, no.

---

### Post by kamitsukai on 2007-10-20
no i dont believe you can recover your files....

---

### Post by kshane on 2007-10-20
> **wispygalaxy said:**
> Well, I thought that it referred to using the whole CD R.  But I guess it was talking about the C: Drive.  I did not get a notice saying that my hard drive would be wiped out.  Can I restore my files by any chance?

You **cannot** restore what was there.  It's gone.  And if you're going to make a dual boot with Vista, make sure you install Vista ***FIRST*** and ***don't use the whole disk*** so there's room for Ubuntu.

Good luck!

Kevin

---

### Post by justinmiller87 on 2007-10-20
> **wispygalaxy said:**
> Well, I thought that it referred to using the whole CD R.  But I guess it was talking about the C: Drive.  I did not get a notice saying that my hard drive would be wiped out.  Can I restore my files by any chance?
Can *you* restore your files? Judging from this accidental blunder you've gotten yourself into, I'm going to go out on a limb and guess no. Is it possible? Maybe. There are people out there who have the ability and are trained to find files and restore disks that have been wiped and deleted, even with a DoD-level wipe. The thing is, these people work for or are contracted by people in the FBI or some other governmental agency to find evidence and things. I would suggest finding one of them to probably help you. So in all actuality, you're stuck. If you bought it at a place like Best Buy, you can take it into the Geek Squad and they should be able to restore it for you if you're unsure, but you've lost any personal data on the disk.

---

### Post by shaft350x on 2007-10-20
Welcome to the forums.  Sorry that you joined after such circumstances, but at least you know where they are so next time you have a question you can come ask before you do something.  It is generally easier to get help with something you're about to do rather than what you've done.  Google and forum searches are also helpful in tracking done solutions.

On a side note, for Ubuntu you can create a /home partition so if you wipe out Ubuntu (not the whole disk though) you'll still have your files.  There are some decent resources on that around here.

---

### Post by Duck2006 on 2007-10-20
When or if you get vista in stalled again, partition your drive from within vista and the install ubuntu and use the partition you have made.

---

### Post by multifaceted on 2007-10-20
Way to pick someone up after they fall, people....

Belittlement, doesn't help the situation.

---

### Post by eoghanmurray on 2007-10-20
You can use a hex editor and image cloner to regain your data. i have used this method quite a lot with newbies' pcs. unless you're willing to spend about 3 days constant hacking, tough. it's tricky. all you can hope for is that you havent written to the bits of disk that vista was on on - if so, you've lost it. sorry.
formatting/deleting only wipes the indexes that os'es use to find data. hex editors access raw sectors.

plz forgive spelling etc - im on a 3inch pda ;)

---

### Post by Kensey on 2007-10-20
> **wispygalaxy said:**
> Well, I thought that it referred to using the whole CD R.  But I guess it was talking about the C: Drive.  I did not get a notice saying that my hard drive would be wiped out.

This is a valid point.  The installer should do a number of things that it apparently didn't do here:

[LIST]
[*]Specify which kind of disk it's going to wipe out (hard drive, DVD-R, USB drive, etc.)
[*]Look to see if a filesystem appears to already exist and identify its type to the user
[*]Give the user one more "Are you REALLY REALLY sure you want to COMPLETELY DESTROY ALL DATA on this existing $FOO filesystem?" before it actually does anything.
[/LIST]

---

### Post by n3tfury on 2007-10-20
> **Kensey said:**
> This is a valid point.  The installer should do a number of things that it apparently didn't do here:

[LIST]
[*]Specify which kind of disk it's going to wipe out (hard drive, DVD-R, USB drive, etc.)
[*]Look to see if a filesystem appears to already exist and identify its type to the user
[*]Give the user one more "Are you REALLY REALLY sure you want to COMPLETELY DESTROY ALL DATA on this existing $FOO filesystem?" before it actually does anything.
[/LIST]

^^that's a good idea, considering the implications if not read correctly.

---

### Post by VinylPusher on 2007-10-20
This is a glaring error of omission from Ubuntu. I used the text-mode installer and the only reason I didn't lose any data was because I had a fresh HD to install to.

Ubuntu detected Vista on the other HD, but not XP which I was already dual-booting. To get to XP, I have to select to boot Vista and then use Vista's bootloader to select 'Previous version of Windows'.

Hardly elegant.

If this part of the installer isn't entirely rewritten, for humans, Ubuntu 7.10 is going to get absolutely ripped to pieces by reviewers.

---

### Post by wispygalaxy on 2007-10-20
Thanks for trying to help me, everyone.  :razz:  I have a HP computer that came with a Windows Vista disk.  Is it possible for me to install Vista on my laptop using that disk?  I bought my laptop in June 2007.  If I can do that, do I need to install anything extra?

---

### Post by WiFi Ed on 2007-10-20
> **wispygalaxy said:**
> Thanks for trying to help me, everyone.  :razz:  I have a HP computer that came with a Windows Vista disk.  Is it possible for me to install Vista on my laptop using that disk?  I bought my laptop in June 2007.  If I can do that, do I need to install anything extra?

The Vista disc that came with your HP is tied to that computer. It will install on your Toshiba but probably won't be able to be activated :( If a Vista disc came with your Toshiba use that one. If not, contact Toshiba and ask for a Vista disc for your laptop. They should send you one, but you might have to make a couple of phone calls to their Support people to get it. Be polite but firm, and ask to talk to someone higher up on the food chain if necessary.

Best wishes for a speedy recovery:)

P.S. Being a laptop, your Toshiba will probably need a few special drivers also, be sure to ask Toshiba about that when you talk to them...

---

### Post by wispygalaxy on 2007-10-20
> **WiFi Ed said:**
> The Vista disc that came with your HP is tied to that computer. It will install on your Toshiba but probably won't be able to be activated :( If a Vista disc came with your Toshiba use that one. If not, contact Toshiba and ask for a Vista disc for your laptop. They should send you one, but you might have to make a couple of phone calls to their Support people to get it. Be polite but firm, and ask to talk to someone higher up on the food chain if necessary.

Best wishes for a speedy recovery:)

Thanks for that response!  I guess there is no hope for my files.  Oh well, I can still get that disk. Do I have to pay anything for it?  And for the special drivers, does that cost anything extra?

---

### Post by SonicSteve on 2007-10-20
> **kamitsukai said:**
> no i dont believe you can recover your files....

Truthfully, if you were wiling to pay $$$$$$$$$$$$$ from what I understand the data is probably still there and somewhat recoverable it just isn't practical unless your data is worth ridiculous amounts of money to you.

Thats why when you wipe a hard drive with an erasing utility some will offer DOD erase which means US    Department Of Defence erase. If a passing over a hard drive once was good enough to destroy the data they wouldn't have come up with this kind of standard.

---

### Post by Officer Dibble on 2007-10-20
It's highly unlikely you will get any of your data back, the entire filing system had to be changed to install Ubuntu on that drive which means every bit of that disk has effectively been written to, and thus overwritten.

It is also very unlikely that you will be able to use your Vista disk on your laptop as recovery disks are designed to be machine specific.

Please don't think I am being smart, but for future ventures in system changes, always make back-ups of important data.

So, what I would suggest you do now, if you would still like to use Vista is install it on your computer again, resize the partition it was installed on using Vista's own partition editor, and then when installing Ubuntu choose the Guided mode that uses all contiguous space - not entire disk. Choosing the option for guided contiguous space will use up the space you allowed with Vista's partition editor - it will look for an area of the drive that isn't being used at all.

If you have any doubts or questions about an install feature, drop you thoughts into the Absolute Beginner section of Ubuntu Forums and you should get friendly and helpful advice.

Hope it goes as smoothly as you would like it to. :)

---

### Post by eoghanmurray on 2007-10-20
try a hex editor/data recovery application or get someone to do it for you. it takes a looong time but its worth it. if you have photos on that machine, youll want those back - photos are irreplacable.

QUESTION: Why don't you have a backup? or several? surely you have one SOMEWHERE???

hope you get it sorted out.

---

### Post by n3tfury on 2007-10-20
> **eoghanmurray said:**
> 

QUESTION: Why don't you have a backup? or several? surely you have one SOMEWHERE???



??? MOST people don't backup until they've lost data at least once.  this is not uncommon.

---

### Post by WiFi Ed on 2007-10-20
> **wispygalaxy said:**
> Thanks for that response!  I guess there is no hope for my files.  Oh well, I can still get that disk. Do I have to pay anything for it?  And for the special drivers, does that cost anything extra?

Worst case should be to pay shipping and handling, same for driver disc, but they'll most likely just send them for free.

As for your lost files, yeah, that's pretty much hopeless now. Been there, done that!!

Your next accessory should be a low-cost external hard drive to backup the irreplaceable stuff (pics, documents, stuff like that). Less than $100.00, good insurance to have.

---

### Post by snickers295 on 2007-10-20
if you want to spend some thousands of dollars for bills, games etc. you can.
in installing, disk means hard drive and cdrom, means CD.

---

### Post by Sef on 2007-10-20
To dual boot from the Live CD, read [Psychocats Ubuntu]("http://psychocats.net/ubuntu/index.php").

(A link to the Illustrated Dual Boot is provided for installing by the alternate cd, if you so choose that method.)

---

### Post by SonicSteve on 2007-10-20
> **wispygalaxy said:**
> Thanks for that response!  I guess there is no hope for my files.  Oh well, I can still get that disk. Do I have to pay anything for it?  And for the special drivers, does that cost anything extra?

Most PC's come with either a "restore" CD or an actual OEM holographic windows CD/DVD. In recent years though I've seen computer sellers like Acer for example offer the initial installation only on the Hard Drive itself. They then strongly encourage you to "burn" an image of your initial windows installation. Each vendor is different and I don't know what HP is up to these days. My compaq from years ago came with restore disks.

If you have a restore CD or the actual OEM disk you have to configure you HP to "boot" from the CD/DVD drive and have that disk in the drive when you turn the computer on. I would recommend that you call HP about this.

---

### Post by Maestro23 on 2007-10-20
> **SonicSteve said:**
> Most PC's come with either a "restore" CD or an actual OEM holographic windows CD/DVD. In recent years though I've seen computer sellers like Acer for example offer the initial installation only on the Hard Drive itself. **They then strongly encourage you to "burn" an image of your initial windows installation.** Each vendor is different and I don't know what HP is up to these days. My compaq from years ago came with restore disks.

If you have a restore CD or the actual OEM disk you have to configure you HP to "boot" from the CD/DVD drive and have that disk in the drive when you turn the computer on. I would recommend that you call HP about this.

So many of my friends with Vista have been burned by this.  They didn't take the time initially to burn those discs.

---

### Post by cappii on 2007-10-20
The Vista DVDs that came with your computer "MAY" work on your laptop.  However, be smart, and take the time to visit the website and get the Vista Specific drivers for your model of Laptop... specifically your LAN and / or wireless drivers.  The rest can get d/led from the website once you're up and going.  MAKE SURE THAT THE VISTA DRIVERS ARE AVAILABLE, YOU WILL BE SORRY IF YOU PROCEED WITHOUT DOING THIS!!!!  I was too lazy to read all of the posts, so if you posted your laptop specifics, i missed them, however, I strongly suggest AT MINIMUM:
1.8 GHz Centrino or equivalent processor
1 GB DDR memory

If ya have that, the rest should be okay.  If not... don't bother.  It will be too slow to be useful.  Also note:  you have like 21 days to register the laptop with Microsoft, or most of your stuff stops working.

It's gonna be easy to find out:  put the DVD in and reboot the computer.  It will prompt you to press any key to boot from CD / DVD.  If your laptop will not work with that DVD, you'll know within seconds.  It'll say that it's not compatible with this manufacturer.

Either way, Good luck.  Don't give up on Ubuntu.  It's wonderful, and beats the smithereens out of Vista :D:guitar:

---

### Post by Shazaam on 2007-10-20
I don't know if it's possible but would testdisk help with the op's problem, or would that restore ONLY the partition info and not the files?

---

### Post by n3tfury on 2007-10-20
that won't recover files.

---

### Post by steveneddy on 2007-10-20
> **eoghanmurray said:**
> You can use a hex editor and image cloner to regain your data. i have used this method quite a lot with newbies' pcs. unless you're willing to spend about 3 days constant hacking, tough. it's tricky. all you can hope for is that you havent written to the bits of disk that vista was on on - if so, you've lost it. sorry.
formatting/deleting only wipes the indexes that os'es use to find data. hex editors access raw sectors.

plz forgive spelling etc - im on a 3inch pda ;)

What? Oh, yeah. Why don't you jsut throw her is the deep end? 

steveneddy - Hey! I just wrecked my car, what do I do?

eoghanmurray - Well, my buddy has an F1 race car that you could drive . Maybe that will help you get your car repaired.

](*,)=D>

---

### Post by steveneddy on 2007-10-20
> **eoghanmurray said:**
> try a hex editor/data recovery application or get someone to do it for you. it takes a looong time but its worth it. if you have photos on that machine, youll want those back - photos are irreplacable.

QUESTION: Why don't you have a backup? or several? surely you have one SOMEWHERE???

hope you get it sorted out.

What are you, like 12 and you read about this in X Files mag or something?

The data is lost. The file system changed when she installed the new/different OS.

She **will** have to reinstall.

To the OP - You lost your data. OK? If you can, reinstall VISTA, then make a partition on your hard drive. It's like dividing up a room. Try to read a little about it before you do it, but it is quite easy.

When you want to dual boot with Windows, Windows want to be the first one on the hard drive, because Linux doesn't care where it is. Just make a paertition at the end of the hard drive and make sure that you also make a swap partition, also.

Your data is lost, but you can start from scratch, like most of us did in the beginning, and get Vista and Ubuntu on the same 'puter.

Ask all the questions that you need to ask and search the forums for answers.

:popcorn:

---

### Post by LaRoza on 2007-10-20
> **steveneddy said:**
> What are you, like 12 and you read about this in X Files mag or something?


The process described above works, assuming the data is still there. It is usually not worth the trouble, time, and headaches. But you can open a disk with a Hex Editor, like [http://mh-nexus.de/hxd/](http://mh-nexus.de/hxd/). If you recognize, or search for certain offsets, you can find files. I never tried this with a large disk, and only if I was familiar with the disks contents. 

Essentially, the OP's data is lost, but don't knock a solution, even if it is not practical in this case.

---

### Post by justinmiller87 on 2007-10-20
> **steveneddy said:**
> What are you, like 12 and you read about this in X Files mag or something?

The data is lost. The file system changed when she installed the new/different OS.

She **will** have to reinstall.

The data is probably not completely gone, but more of a pain to try to recover for the layman. [http://en.wikipedia.org/wiki/Data_recovery](http://en.wikipedia.org/wiki/Data_recovery)
Yes, she'll probably have to reinstall and for all intents and purposes the data's gone, but don't make the claim that it is impossible to get it back until you've physically inspected the drive and failed to get anything off of it. There's software that *may* be able to get stuff back after a DoD wipe, and in most cases after a single wipe, so it's probably feasible to recover something, but just extremely difficult. If I were in her situation, I wouldn't bother trying anything though.

---

### Post by Duck2006 on 2007-10-20
When i have use the hole disk the only part of the disk that i can't recover info from is the part that has been writen to.

---

### Post by Blue_Lander on 2007-10-20
I work for a PC repair service, and have recovered several hard drives after a format  and OS reinstall. So I know for a fact the data is not without a doubt lost.  

The program I use at work is called EasyRecovery Pro. It is commercial software, and rather expensive, but maybe there are some free programs out there that can do the same things it does. 

Also, I know for a fact that Toshiba packs restore discs in with their laptops, I see them everyday. I can't vouch for how *long* they've done it, but I know they do now anyways. Maybe go dig through your box or paperwork if you have any. It may turn up. Wish i had more for ya.


Good luck.

---

### Post by justinmiller87 on 2007-10-20
If you want to see if you can salvage something, and you want to use an offshoot of Ubuntu to do it, look at [Ubuntu Rescue Remix](http://ubuntu-rescue-remix.org/). I've personally not used it and only found it in my research in trying to help you out. I have lost a lot of data in my computer time yet still don't back up, lol. (I know, don't come begging for sympathies, I'm not, don't worry.) But you can try that if you want, or just reinstall, count your losses, and hope for the best next time.

---

### Post by Frak on 2007-10-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubiquity/+bug/155185](https://bugs.launchpad.net/ubiquity/+bug/155185) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				A bug has been filed about the Ubiquity Installer.

---

### Post by wispygalaxy on 2007-10-20
I'm pleased that so much people cared about my situation here, thanks.  I didn't have anything important on my laptop because I didn't have it for long.  I keep my photos on a CD, and my Word documents are on my USB drive.  I just lost my Internet bookmarks,  iTunes library, videos, and some programs.  

What I will do is go to my college tech center and ask if they can install Vista on my laptop again.  I will keep Ubuntu on it ;) because why should I be mad at the OS when it was my silly error of choosing to use the entire disk during installation?  

If the college cannot help out, I will search for the disk.  There is a chance that I have it.  From there I will install Vista.  

If there is no disk, I will call Microsoft and ask them to send me a installation disk.  I'm not sure how much it will cost; do you guys know?  Should I ask them for any other programs/disks/software?  If I need those, will they cost anything?

Then I will install Vista again.  Hopefully, Ubuntu and Vista will live in harmony this time....

One last thing... I have no sound on Ubuntu.  I went into alsadisk, and un-muted "Caller I" and "Off-Hook".  But it goes back to mute.  I did this:  (copied from the _Comprehensive Sound Problem Solutions Guide_) 

[COLOR="Teal"]Do this step to ensure that your alsamixer settings are reloaded with each boot. First make sure you have your settings just the way you like them in alsamixer. Then do
Code:

sudo alsactl store 0

or if this is your nth sound card (where n is the number of soundcards in your computer) replace 0 with n-1.
[/COLOR]

I plugged in zero after "sudo alsactl store".  When I open alsamixer, it still says mute for those two!  Otherwise, I'm perfectly happy with Linux!  :)

Once again, thank you for the input.  I can look at this as a learning experience, actually.
:D

---

### Post by steveneddy on 2007-10-20
The point I was making is the simple fact that the OP didn't realize what was meant by the word "disc" and supposing that she could recover her data sucessfully on her own is ludicrous. 

If she needs the data for something significant, then get the disc to a professional data recovery service or she could actually loose the data forever.

Chances are that most of the remaining data is corrupted and unrecoverable since she went to another file system. There is a very small chance that she may be able to recover data, but it is unlikely that she would be sucessful on her own.

But, I may be wrong. I would concider the data gone forever and move on to reinstalling Windows and **then** dual booting the PC after a new partition is installed.

I am a professional manager, I run a business and a small network and I would never try on my own to recover data from a disc. My data is too valuable and we pay professionals when this service is needed. We currently back up to DVD daily and only use the DVD's four times. After one month, all of the backup DVD's are wiped and shredded.

I didn't say that these recovery programs aren't sucessful, just the fact that the OP was obvously a new person to computing (not advanced) and the OP shouldn't even try to recover her own data without a little experience.

That said, I wish the OP lots of luck in whichever path she decides to choose.

---

### Post by Frak on 2007-10-20
They should give you the pirate price, which is $30 for XP, and $90 for Vista. Never tell them that you installed Linux though, that is information they don't need to know.

---

### Post by OldTimeTech on 2007-10-20
Don't call Microsoft for your Vista disk, call the company who made your laptop, they should send you a the recovery disk, that will have all the software they sent with the machine plus Vista....and if they didn't send it with the laptop originally, then all they should charge you for is the postage!

---

### Post by Blue_Lander on 2007-10-20
Windows Vista can be bought retail in stores if you don't want to order it, but it is pricey either way. I would first call Toshiba and see if they can send you actual recovery disks for your specific computer, they're usually much cheaper. 

 Toll-free Technical Support

    * Computers: (800) 457-7777


EDIT:
Beaten to the punch. Twice, lol. 

Frak is very right. Do NOT mention Linux at all. Although it is illegal, many companies refuse to service a computer that has had a different Operating System put on it.

---

### Post by justinmiller87 on 2007-10-20
I'm glad you were able to take your mistake and look at it in a positive manner. If you have iTunes, I'm led to believe you have an iPod. If you really want the Open Source experience, I suggest looking into a program called Rockbox. As long as your iPod didn't come out in the last few months (iPhone or later), or isn't ancient, you can use it. You get more games, and you can use formats such as MP3, MP4, WMA, and the open source OGG. Catch is you can't watch videos on it, but you can dual-boot between the iPod and the Rockbox software if you just want to put videos on there. The best part is it's drag and drop so you wouldn't have to use iTunes software in Windows or gtkpod in Ubuntu. You can look into it at [http://www.rockbox.org](http://www.rockbox.org) It takes some getting used to though. I've been using it for a few days and still am not, but I'm starting to like it better.

---

### Post by Blue_Lander on 2007-10-20
> **justinmiller87 said:**
> I'm glad you were able to take your mistake and look at it in a positive manner. If you have iTunes, I'm led to believe you have an iPod. If you really want the Open Source experience, I suggest looking into a program called Rockbox. As long as your iPod didn't come out in the last few months (iPhone or later), or isn't ancient, you can use it. You get more games, and you can use formats such as MP3, MP4, WMA, and the open source OGG. Catch is you can't watch videos on it, but you can dual-boot between the iPod and the Rockbox software if you just want to put videos on there. The best part is it's drag and drop so you wouldn't have to use iTunes software in Windows or gtkpod in Ubuntu. You can look into it at [http://www.rockbox.org](http://www.rockbox.org) It takes some getting used to though. I've been using it for a few days and still am not, but I'm starting to like it better.

Gutsy has some very nice programs built-in that can easily scan and manage iPods. But, I suppose any true open source junkie would do a full switch to Rockbox ;)

---

### Post by justinmiller87 on 2007-10-20
> **Blue_Lander said:**
> Gutsy has some very nice programs built-in that can easily scan and manage iPods. But, I suppose any true open source junkie would do a full switch to Rockbox ;)
Yeah, now that I know this, I'm considering re-ripping all my CDs into ogg from AAC. I can sacrifice the few items I got from the store.

*Edit* We're getting off topic.

---

### Post by Frak on 2007-10-20
> **justinmiller87 said:**
> Yeah, now that I know this, I'm considering re-ripping all my CDs into ogg from AAC. I can sacrifice the few items I got from the store.
Use FLAC, even though its big, I find it better than OGG.

---

### Post by wispygalaxy on 2007-10-20
[COLOR="Indigo"][SIZE="2"]Did you guys read about my sound problem?  That's the only thing wrong with my Ubuntu OS right now.  I would love the help, since I'm on YouTube everyday.  :-D[/SIZE][/COLOR]

---

### Post by steveneddy on 2007-10-20
> **wispygalaxy said:**
> [COLOR="Indigo"][SIZE="2"]Did you guys read about my sound problem?  That's the only thing wrong with my Ubuntu OS right now.  I would love the help, since I'm on YouTube everyday.  :-D[/SIZE][/COLOR]

Heck no....this a geek forum. We are still arguing about the best way to recover your data!

You might want to start another thread.

I'm just kidding. 

I don't have an answer for you on this one, but it may be a Flash issue.

---

### Post by multifaceted on 2007-10-20
> **wispygalaxy said:**
> [COLOR="Indigo"][SIZE="2"]Did you guys read about my sound problem?  That's the only thing wrong with my Ubuntu OS right now.  I would love the help, since I'm on YouTube everyday.  :-D[/SIZE][/COLOR]

Did you by any chance have your sound card disabled in Vista? That was an issue I had before.

Either that, or try searching the forums for similar situations.

-Cheers

---

### Post by Duck2006 on 2007-10-20
All i saw was a data prob what was the sound prob?

---

### Post by wispygalaxy on 2007-10-20
> **steveneddy said:**
> Heck no....this a geek forum. We are still arguing about the best way to recover your data!

You might want to start another thread.

I'm just kidding. 

I don't have an answer for you on this one, but it may be a Flash issue.

LOL, ok.  This thread is too long anyway.  If I get that sound question answered, I'll be good for now.  

I just hope I can find that Vista disk...

---

### Post by justinmiller87 on 2007-10-20
Shh. This thread's been hijacked. It's not about you anymore.


Just kidding. :)

---

### Post by steveneddy on 2007-10-20
> **justinmiller87 said:**
> This thread's been hijacked. It's not about you anymore.




Are we allowed to say this in from of the newbies?

:popcorn:

---

### Post by wispygalaxy on 2007-10-20
> **justinmiller87 said:**
> Shh. This thread's been hijacked. It's not about you anymore.


Just kidding. :)

[COLOR="Green"]Haha, that is true.  Thanks for helping, but I will post a new question about my sound problem so people don't have to read pages and pages of posts.  Take care everyone!  8-)[/COLOR]

---

### Post by justinmiller87 on 2007-10-20
> **wispygalaxy said:**
> [COLOR="Green"]Haha, that is true.  Thanks for helping, but I will post a new question about my sound problem so people don't have to read pages and pages of posts.  Take care everyone!  8-)[/COLOR]
If you're happy with the results of this thread, toss [solved] at the front of the subject line on your first post. Take care!

---

### Post by Frak on 2007-10-20
> **wispygalaxy said:**
> [COLOR="Green"]Haha, that is true.  Thanks for helping, but I will post a new question about my sound problem so people don't have to read pages and pages of posts.  Take care everyone!  8-)[/COLOR]
Could you reply to the bug post as a testimonial, it would help further the severity.

---

### Post by steve_c on 2007-10-20
As someone mentioned, the data *can* be recovered, in spite of what some people here are saying.

In fact it's highly likely that any PC repair shop will be able to retrieve most of your data using a simple data recovery program like Easy Recovery Studio, R-Studio, etc. You could also purchase those programs and try them yourself if you'd like.

These programs will usually recover any data that hasn't been overwritten. Just reformatting the filesystem shouldn't cause too much of a problem. The problems come when new data is written to where the old data used to be on the hard drive. Therefore it's generally a good idea to use the disk as little as possible until you get it recovered because the more you use it the more likely you are to reuse a spot with data from the Vista install.

*Even if* the data were overwritten with new data it's possible these programs could still get it, though your odds are reduced.

And even if these programs can't get it, there's always a professional data recovery service like Drive Savers. However those are generally cost-prohibitive for most individuals (usually a few thousand dollars). But if you're rich or it's super-important data, the option is there.

Just wanted to clear that up for some people, as well as for the original poster.

---

### Post by steve_c on 2007-10-20
> **Kensey said:**
> This is a valid point.  The installer should do a number of things that it apparently didn't do here:

[LIST]
[*]Specify which kind of disk it's going to wipe out (hard drive, DVD-R, USB drive, etc.)
[*]Look to see if a filesystem appears to already exist and identify its type to the user
[*]Give the user one more "Are you REALLY REALLY sure you want to COMPLETELY DESTROY ALL DATA on this existing $FOO filesystem?" before it actually does anything.
[/LIST]

Seconded that there should maybe be some kind of clarification. Since Ubuntu is, after all, aiming to be marketed to the masses as a simple Windows-alternative OS.

---

### Post by wispygalaxy on 2007-10-20
> **Frak said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubiquity/+bug/155185](https://bugs.launchpad.net/ubiquity/+bug/155185) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				A bug has been filed about the Ubiquity Installer.

Yes, this bug exists.  It's like a new animal species was discovered or something, LOL.  :biggrin:  Thanks for helping out the novices!

---

### Post by Frak on 2007-10-20
> **wispygalaxy said:**
> Yes, this bug exists.  It's like a new animal species was discovered or something, LOL.  :biggrin:  Thanks for helping out the novices!
Thank You, it helps further Ubuntu releases become even better.

---

### Post by candtalan on 2007-10-20
> **Kensey said:**
> This is a valid point.  The installer should do a number of things that it apparently didn't do here:

[LIST]
[*]Specify which kind of disk it's going to wipe out (hard drive, DVD-R, USB drive, etc.)
[*]Look to see if a filesystem appears to already exist and identify its type to the user
[*]Give the user one more "Are you REALLY REALLY sure you want to COMPLETELY DESTROY ALL DATA on this existing $FOO filesystem?" before it actually does anything.
[/LIST]

I heartily support what you say. 
I have noted that various versions of ubuntu have had different installer defaults and options. If anyone has the time and facility, I think that 6.06, 6.10, 7.04 versions, all offer slightly different options when presented with a windows partition. iirc 7.04(?) initially requires a 'use entire disk' radio button and *then* gives a resize your windows partition display.

It will be important to be clear what the version 7.10 (currently very new) offers in the various situations.

---

### Post by markbeverley on 2007-11-13
I've also fallen victim to this. I would say I'm fairly competent in computing having installed several previous versions of Ubuntu. When installing I selected the first option assuming it would give me options on what partitions to use for the OS (I was doing it in a bit of a rush). Shortly after it started I got the feeling all was not well and cancelled, but alas I was too late.

---

### Post by purebuilt on 2007-11-26
I don't know why they keep messing with the partitioner. It was great to just be able to slide to the size you wanted for the main partition (even though it was confusing that what was left was for Unbutu). I would really like to install it on my Vista system too, but I don't want to use the cryptic manual settings. I've been searching for over an hour on the forum and no one explains exactly how to do it.

Can't use a system you can't install safely. :(

DB

---

