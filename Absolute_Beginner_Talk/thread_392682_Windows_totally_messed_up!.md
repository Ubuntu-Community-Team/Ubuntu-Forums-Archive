---
title: "Windows totally messed up!"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-03-24
TOPIC RESOLVED

the main reason i started using ubuntu was because my windows xp os was bombarded with viruses and spyware after i was hit with a drive-by download.  what i need is to be able to scan my windows harddrive for viruses with a linux program (windows will barely boot) and be able to remove the spyware, adware, viruses, and other buggers.  could somebody either point me to a tutorial on how to do this or write one?  i'm a total n00b at linux, so go easy on me and keep it simple please.  :P

---

### Post by Zzl1xndd on 2007-03-24
The first question ill ask is can you already see your windows drives? if they are already mounted I believe that Avast and AVG linux versions will pick up windows viri. get on install and scan.

---

### Post by locke.dragon on 2007-03-24
they're mounted.  i used terminal to mount them.  i just can't edit or delete files.  and could you give me a quick run-down of how to install programs in linux?  i don't think it's as straightforward as 'click this and the program's installed' like in windows.  is it?  and sorry i'm asking such a beginner's question.

---

### Post by oilchangeguy on 2007-03-24
why not simply just wipe the hard drive clean and start fresh?

---

### Post by locke.dragon on 2007-03-24
because i have all my school work on it along with itunes music and other programs that don't work in linux.  so i'd like to clean up the windows portion of the drive and turn the maching into a dual-boot one.  if that's possible.  :P

---

### Post by Zzl1xndd on 2007-03-24
[http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)

Download the .deb version and it is that simple. then after its installed in the terminal type avastgui and it will bring up a menu for you then do a full system scan. and it should scan the drives you mounted as well.

---

### Post by oilchangeguy on 2007-03-24
are you running anti virus and spyware software, if so what? you can't repair windows by using linux.

---

### Post by STREETURCHINE on 2007-03-24
why dont you boot windows in safe mode and start digging out the crap from there ,you can run all your scans from safe mode and it gives all the spyware,virusus,adware and such no where to hide..it is what i do .

just a thought

---

### Post by Zzl1xndd on 2007-03-24
oilchangeguy is right really what I have suggested might find the problems but you would more than likely have to remove the offending programs/files by hand. it may be best for you to back up anything of importance and start over.

---

### Post by Zzl1xndd on 2007-03-24
> **STREETURCHINE said:**
> why dont you boot windows in safe mode and start digging out the crap from there ,you can run all your scans from safe mode and it gives all the spyware,virusus,adware and such no where to hide..it is what i do .

just a thought

Also a good point.

---

### Post by oilchangeguy on 2007-03-24
do you have access to a known clean machine? if so go to [http://free.grisoft.com](http://free.grisoft.com) and download and save the file to my documents, then burn it to cd. from your machine turn off system restore, reboot, and install the program from the cd you burned. and run a virus scan. also go to [www.lavasoft.com](www.lavasoft.com) and burn a copy of adware personal, install that and run a scan.

---

### Post by locke.dragon on 2007-03-24
the major problem is that my computer's a dell laptop and with dell being the EXCELENT company they are, they didn't send me a windows boot disk so i can't re-install windows.  and i'd rather not have to wipe my hard drive.  i've got avast! installed and running and it's doing a scan.  i'll let you know what it comes up with.  and on windows i'm running ad-aware se personal, spybot s&d, and windows defender.  and i've tried booting into safe mode, but it takes 20 minutes to even get into the log in screen and then it kinda freezes.  so i'm trying linux.  i'm crossing my fingers.

---

### Post by locke.dragon on 2007-03-24
avast! just came up and said it had found a virus.  when i told it to move it to the chest, it said it couldn't do it.  how come?

---

### Post by oilchangeguy on 2007-03-24
because it's possible your machine is so screwed up, that your virus software is also corupted.

---

### Post by Zzl1xndd on 2007-03-24
> **locke.dragon said:**
> avast! just came up and said it had found a virus.  when i told it to move it to the chest, it said it couldn't do it.  how come?

I thought this might be a problem, your windows drive is more than likely NTFS right? Linux can't Write to it and wont have permissions to remove things, I think there is a way around this but I hate to say I don't know what it is. I dropped windows all the way so it hasn't come up for me.

This might help : [http://opensourceroolz.wordpress.com/2007/02/26/writing-to-windows-ntfs/](http://opensourceroolz.wordpress.com/2007/02/26/writing-to-windows-ntfs/)

Can anyone confirm that this would be the problem?

---

### Post by Zzl1xndd on 2007-03-24
> **oilchangeguy said:**
> because it's possible your machine is so screwed up, that your virus software is also corupted.

he is scanning from his Linux partition.

---

### Post by oilchangeguy on 2007-03-24
> **tweakedenigma said:**
> he is scanning from his Linux partition.

and he says he's scanning from linux where in this thread?

---

### Post by Zzl1xndd on 2007-03-24
> **oilchangeguy said:**
> and he says he's scanning from linux where in this thread?

from the instructions I gave him on the 6th post.

---

### Post by oilchangeguy on 2007-03-24
> **tweakedenigma said:**
> from the instructions I gave him on the 6th post.

that does not mean he's at the present time running linux. and you can't even download this avast program to linux. so there's no way to scan windows for a virus from linux. if you could you'd have to be able to run both os's at the same time, and that's not possible!

---

### Post by Zzl1xndd on 2007-03-24
> **oilchangeguy said:**
> that does not mean he's at the present time running linux. and you can't even download this avast program to linux. so there's no way to scan windows for a virus from linux.

Ok for 1 there is a Linux version of Avast and the link was in that post you might wanna take a look. 2ndly you can scan from Linux if the drive is mounted as he said it was. As I pointed out I dont think it can fix it because Linux without some ad-ons can not alter NTFS partitions but I might be wrong on that point.

---

### Post by locke.dragon on 2007-03-24
i don't have to scan windows, just the drive partition it uses.  and i CAN access that from linux.  i downloaded the program to linux and it's presently doing a scan for viruses.  and yes i am using linux at this very moment.  windows will barely boot, and when it does, it's slow as anything and shows up with a bunch of unknown processes.

---

### Post by oilchangeguy on 2007-03-24
well, from your previous post you've only found one problem. and can't even delete that. so what do you plan to do now?

---

### Post by Zzl1xndd on 2007-03-24
> **oilchangeguy said:**
> well, from your previous post you've only found one problem. and can't even delete that. so what do you plan to do now?

There is no need to be rude. He came asking for help and we both are trying our best to help. just because the answer isnt forth comming yet others here might be able to add more to help.

---

### Post by oilchangeguy on 2007-03-24
not being rude, just asking a question. the bottom line is, his windows install is so screwed up there's no saving it. and he says he has no windows disc from dell. what about system restore disc's? so his best bet is to back up his files from windows, format the drive and let ubuntu have the whole thing.

---

### Post by dasunst3r on 2007-03-24
In the case of virus infections, I would highly recommend backing up your information and stuff and just starting over.  Remember that the Ubuntu LiveCD does have productivity tools so that you can finish up your assignments before you start reformatting!

---

### Post by Zzl1xndd on 2007-03-24
But Avast is finding the problems so it might be salvagable provided that my assumption is correct can you confirm what I believe the problem is? I mean I would love another linux/Ubuntu but all do my best to help anyone on any OS. Although I do agree back up and wipe would be the fastest way but if he/she doesn't want that option I will offer others.

---

### Post by Drakkor on 2007-03-24
Windows is spyware,virusus,adware, linux doesn't need all that crap !!

---

### Post by locke.dragon on 2007-03-24
thanks for all the help guys.  i think you're probably right about it being totally messed up.  i aborted the scan about half-way through and it shows me the list or stuff it found.  can you say 'smallest scroll bar ever'?  there were somewhere around a thousand problems.  i think i'm probably gonna end up taking your advice and starting completely over.  i'd like to do anything to salvage it though.  i have some programs that only run on windows that i'd like to still use that won't run in linux.  such as programming environments and such.  any suggestions on how to write to a ntfs formatted windows drive in ubuntu?  that's my main problem at the moment.

---

### Post by medad on 2007-03-24
Have you tried to start from a previous restore point in windows?  My step-father had a similar issue a few weeks back where his system was running very slow.  He started at an earlier restore point and was able to start from there to get his system cleaned out.

---

### Post by locke.dragon on 2007-03-24
that's a GREAT idea.  i hadn't thought of that yet but i used that technique the last time i got a virus.  the only problem is that windows will barely boot.  let alone let me do anything.  i'm gonna try that now.  i'll let you know how it all turns out.

---

### Post by outtaphase on 2007-03-24
While I would encourage you to load ubuntu at some point, I would suggest that you rid your Windows problems first by booting into Windows Safe Mode, and if that doesn't work I would try a Windows PE environment like Bart PE [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

### Post by locke.dragon on 2007-03-25
ok.  i tried doing the restore point, but windows will BARELY even start now and when i finally got to the restore point window and tried to re-boot to an earlier time, it gave me a blue screen saying that windows was shut down to prevent error.  there must be something in there that is keeping me from doing it.  i've heard of this bartpe thing.  is it safe?  cause it's my dad's pc and if i screw his up too, i'm deader than dead.

---

### Post by ramzai on 2007-03-25
IMHO your avast cannot do with virus because you don't have write access to your ntfs partition (you can't edit, rename, delete files, right?) So follow this howto - [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009) - check you can write to your partition afterwards, run avast and see what it can do.

---

### Post by halitech on 2007-03-25
seeing as how you have a dell and they didn't provide the software for restoring the computer, try giving them a call, explain things to them and they can hopefully send you a restore cd. It's also possible that you may have a restore partition on your drive that you can boot to and restore windows. Only problem being, it will restore back to factory which means goodbye linux partition if it's on the same drive

---

### Post by jon61484 on 2007-03-25
> **locke.dragon said:**
> because i have all my school work on it along with itunes music and other programs that don't work in linux.  so i'd like to clean up the windows portion of the drive and turn the maching into a dual-boot one.  if that's possible.  :P

I'm sure there is a way to get the programs you use in linux to accept the formats of your favorite files. I got a stock ubuntu dist. upgraded so I could burn/play/write MP3 files, ect. and I'm sure they have extensions or programs that can handle the formats you have all your data stored in.

...if you just wanted to stay in linux.

---

### Post by locke.dragon on 2007-03-25
ok.  i'm gonna try the ntfs-3g program to see if that works.  could anybody tell me in a simple way how to install a .tgz file?  i fell totally stupid asking this, but i'm new at linux so i have to.

---

### Post by Campingman on 2007-03-25
Hi 
Apologies if you answered this earlier but windows safe mode should be the best/easiest way of sorting this out, will it not boot into safe mode?

---

### Post by ramzai on 2007-03-25
tgz, or gunzipped tar, is just an archive. Unpack it using right-click menu, and follow instructions inside - usually README or INSTALL.

btw, I don't remember ntfs-3g install involving any .tgz archives.

---

### Post by locke.dragon on 2007-03-25
i've tried numerous times to boot into safe mode, but it took over 20 mins and still didn't get to the desktop.  does anyone know how long it's supposed to take to completely boot in safe mode?

---

### Post by Campingman on 2007-03-25
It does not take twenty minutes usually. It does take quite a while though 
When you boot into windows normally have you tried viewing the task manager and stopping the offending programs manually.  Once you have identified the bad programs you can enter msconfig at the run command and stop them starting at boot up, you should be able then to stop enough of them to use the desktop.  To do a proper virus clean up you should ideally run it from safe mode with system restore turned off.

---

### Post by josh420 on 2007-03-25
If you're that concerned with the schoolwork and stuff on your system, go spend 20 bucks on a 1 or 2 gb USB thumbdrive. 

since you have access to the windows filesystem from linux you can copy those files over to the thumbdrive. then you can decide what you want to do next as it relates to your windows partiton.

If you're feeling cheap, you could always burn a cd as well, if you have a burner drive.

---

### Post by locke.dragon on 2007-03-25
i think that's my only option now unless i get ubuntu to write to my ntfs windows drive.  and i've tried booting windows and stopping the offending processes, but they just start up again.  they apparently run copies of themselves so that it's impossible to stop them.  and i don't think safe mode's gonna work.  so right now my only options are fix it through linux or save the data and re-format.

---

### Post by Campingman on 2007-03-25
Sounds like it may be your only option, have you looked at the Knoppix live CD.  The latest version of Knoppix is said to be able to write to NTFS drives safely (recommended you back up any important data though).  
You may be able to run an anti-virus with more success in the Knoppix environment.

---

### Post by arron on 2007-03-25
Its funny how much time people spend to restore something, where it would save time to backup and install fresh.  Does your laptop have a windows serial sticker?  If so you can borrow a xp cd and use that to install (it has to be the same version i.e. xp home).

I have seen people spend hours trying to fix a bad virus or spamware, when i come and in 45 mins they are back up to par after a fresh install.  The long and short of it is, when a bad virus or spamware gets in, there is a 99.9% chance you will never get it out, and it will pop its ugly head out again somewhere.  Backup your data onto a cd (you can use a live cd to do this) and format and start fresh.  In the future keep the install programs you use on a cd, I even have game patches saved on a CD.  Then if my XP crashed, within 45 mins i was back to where i was at.


With all this said, give Ubuntu a go.  Aside from MS specific programming environments, you can program in linux.  There is a lot more programming, video / picture editing and tonnes of other cools stuff for free, and virus free.  There is NOTHING for free in the MS world, they have to make their $ somehow, and spam/spy ware is a good way of doing it.  When i asked people why they installed the software with spam, they always said because it was free.  

The Ubuntu community and the larger Linux crowd have a lot of geeks that love to code for free for whatever reason.  Linux has come far in the last few years and IMHO has passed MS some time ago.  

All you have to do is learn how to use it, find the programs you like to do what you do and your set.  100% free, 99.9% virus/spam/spyware free.  I made the switch last year, and after about 3 months of dual booting to xp, im now 100% MS free.

---

### Post by Ric95 on 2007-03-25
Ive been through that problem too. Good move setting up linux dual boot. :)
Once Windows gets to that point I doubt it could be fixed fully.
I found it best to just use linux to copy all my files onto the new partition( and burn the important ones! ) then restore the windows partition. In my case the windows restore didn't touch my linux partition, but I did need to re-run Grub to get the dual boot feature back.  
Then from windows you can get a small program that can read the linux partition and get all your stuff back there. 
   After going through this twice, I just stay in Linux now.

---

### Post by Campingman on 2007-03-25
Wise words arron,
"Sometimes it is easier to just start again"
 although I have found with Ubuntu that is not always the case!
Every install seems to be behave a little differently?

---

### Post by locke.dragon on 2007-03-25
i think i'm gonna have to re-format my drive.  it's not worth the trouble i'm going through.  could someone point me to a how-to on how to do this quickly, effectively, and safely?

---

### Post by raffytaffy on 2007-03-25
i suggest a low level format using dereks boot and nuke

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by halitech on 2007-03-25
why not just pop the cd in, reboot and tell the installer to use the entire drive? wipes out everything and if memory serves me correctly, newer drives will not allow you to do a low level format anyway so why waste the time trying?

---

### Post by arron on 2007-03-26
new drives wont?  How come?

I like that dban link, i think ill have to give it a look.

---

### Post by Biochem on 2007-03-26
As some pointed out Ubuntu cannot natively write to NTFS therfore it is impossible to clean windows virus
Have a look at [www.ntfs-3g.org](www.ntfs-3g.org)
The installation guide for Ubuntu can be found here:

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

It use repositories (Linux equivalent to a free software depot ready to install) so no compilation or other weard stuff. And don't be scared of the terminal, I was a month ago than realize I could just cut and paste the command form the web. It's that easy. 

Than you be able to modify the infected files with your anti virus (I understood you already have avast installed). 

I found quite a few virri on my old XP install that way:KS. But I used ClamAV because it was in the repo.

Good luck

---

### Post by locke.dragon on 2007-03-26
thanks, but i've tried installing numerous times on the live cd and it looks like i have to have ubuntu installed to my hard drive to do it.  is this true?

---

### Post by dawv on 2007-03-26
well.. with windows, digging out programs doesn't fix jack.... instead, it just causes your system to become incredibly unstable and eventually not even load.. even in safe mode (happened to me all too often).  Instead go into safe mode, and if your running SP2, then system restore to the last checkpoint you know it worked at.... it'll redo/undo every thing except saved work in the my documents folder... so viruses, .exe's   programs, get restored/deleted, and you work and important stuff is still alive.:cry: :? :| O:) :) :-D :lol:

---

### Post by locke.dragon on 2007-03-26
one problem.  safe mode won't start.

---

### Post by arron on 2007-03-26
I cant believe this is still a problem.  Burn your data with a live cd onto a cd.  Then get a xp cd from a friend and reinstall, use your serial number from your sticker.  Bam! back on the go in a hour!

---

### Post by locke.dragon on 2007-03-26
i realize this is what i should do, but i would like to save my installed programs and settings by eradicating windows instead.  what arron suggested is my last option and i'm probably gonna end up doing that, but i would like to at least try the other options first.

---

### Post by ramzai on 2007-03-27
If you have only ubuntu live cd, you have two options (to try to fix windows with ntfs-3g and any antivirus soft):
1. Actually install Ubuntu onto hard drive (if you have enough space on it)
2. Use another live CD with ntfs-3g and antivirus already out of the box - for example, latest Knoppix.

---

### Post by Biochem on 2007-03-27
With a little research I found a distro aimed at recovering down system. I haven't tried it so I leave to others the pleasure of commenting it. However their claim look interesting

Have a look:
 [http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12)

ntfs-3g is already installed and there is multiple viruscan utilitie. Seems to me that this is what you are looking for.

Good luck

---

### Post by locke.dragon on 2007-03-28
thanks for all the help guys.  but it doesn't look like i'm gonna be able to recover my system.  :'(  i backed up my data and i'm gonna order a windows xp install disk from windows (one didn't come with my machine) and re-install and then make it a dual-boot between xp and ubuntu.  thanks again!

---

### Post by arron on 2007-03-28
If you have to pay for the cd, find a friend and use the sticker serial number on your pc.  If not then and you have to pay, try ubuntu.  For most it has more than what they will ever need and it will save u some $.  Sorry to hear your going to lose all your stuff, but everyone has it happen once.  Then they learn to make backup of all install programs they use and their data.  Good luck with it though, but really give ubuntu a good try before you spend some money.

Biochem: Nice link!  That looks promising, I'm going to try that distro out and see what its got.  Could be very useful.

---

### Post by locke.dragon on 2007-03-28
arron.  i already backed up my data from within ubuntu.  and i'm planning on making it a dual-boot system anyways.  depending on how much they charge me for the disk (probably around 10 bucks shipping since i already own it) i may just make it an all ubuntu system.  thanks again!

---

### Post by MJWhiteDerm on 2007-03-28
There is another option, but it requires a cooperative neighbor.

Pull the hard drive.  Find a nice neighbor who is still running a Windows box.  Have him / her install it temporarily in the Windows box as an added drive and run Windows Spybot Search & Destroy, Nod32 (antivirus), and Adware on the drive to semi-clean it.  Then pull as many files off it in the neighbor's Windows box, just in case, and copy them to a CD.  Then put the drive back in your Windows system and see what you have.

I just did this for my neighbor. Their computer was essentially seizing anytime they tried to run it.  They went out and bought an IMAC, and then gave me a chance to fix their computer.   I put their hard drive in one of our Windows boxes, recovered their files for them, then put the drive back into their computer.  At that point, they were fed up with Windows, so I also converted that computer to an ubuntu system.

---

### Post by J11Gyro on 2007-03-28
Avast has an exe file that works well with mainstream virus on XP, I have run into this on my dads xp system more than once because of a nephew. The file avast has is basic and self supportive, you do not have to have avast installed.

---

### Post by locke.dragon on 2007-03-28
thanks for all the help you guys, but i'm done with trying to fix it.  i'm just gonna re-install and start over.  and i've already saved all my data using ubuntu.  thanks guys.  mods, please close this thread.  :P

---

### Post by kittyhawk63 on 2007-03-29
> **locke.dragon said:**
> thanks for all the help you guys, but i'm done with trying to fix it.  i'm just gonna re-install and start over.  and i've already saved all my data using ubuntu.  thanks guys.  mods, please close this thread.  :P

locke-dragon,
You can go to your first post click on edit->advanced edit and choose "resolved" and then "save". That will give people the idea that you have your answer. They may want to see what you did to resolve your problem. Mods may never see your request to close.
kh

---

### Post by cowlip on 2007-03-29
You can certainly install ntfs-3g onto the Ubuntu live cd, I've done it several times in Dapper Drake.  I've used the .debs provided by givre.  Also, I used ntfs-config to mount them easily.

The Feisty Fawn beta includes ntfs-3g and ntfs-config in the universe repositories.

---

### Post by locke.dragon on 2007-03-30
thanks for the tip!  i'm new to this forum and haven't delved into all the advanced settings yet.  :P

---

