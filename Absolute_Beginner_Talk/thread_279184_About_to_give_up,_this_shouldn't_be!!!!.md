---
title: "About to give up, this shouldn't be!!!!"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by pminmo on 2006-10-17
After two days I'm about to give up on ubuntu.  Why? I can't get it to boot off the HD.  This shouldn't be this difficult!  And I'm a long way from computer illerate.

My problem.  Trying to install Ubuntu from a live cd on a windows xp machine and dual boot.  One HD, and no I don't want to go buy a second HD!

1st problem was downsizing the only partition on the pc.  I wasted a lot of time finding Gparted after trying to find something in the windows world, only to find out it is on the live cd!  So after reconfiguring the partitions several times, to get what I wanted I install Ubuntu, or at least I think I did! No where in the process in reasonable computer terms in english did it give me any option to install a boot manager.  So it constantly boots winxp.  I find supergrub, and still no luck.  The only thing that makes me think it's actually on the HD is rebooting with Gparted, shows the partition that I think I have installed Unbuntu in as having used disk space, plus when trying to install from the livecd after going through all the q&a screen it finishes almost immediately.

This should be an easy install, and if you want windows users my problem is pretty typical after reading ton's of posts related to dual booting. 

Anybody out there that can give me an idea of why I can't get dual boot to run?  And don't tell me to go read this or that post, as I've read posts for two days!:confused:

---

### Post by TmP on 2006-10-17
You sound preatty desperate ;)

Which version of Ubuntu are you trying to install?

Anyway, you should use Dapper drake. You probably run the LiveCD. Now all it takes is to partition your drive. I too have a dual boot, from one hdd. The first system was WinXP. It took bout half of my HDD. The other half was a different partition, with my files.   The first step was to defragment the disks using Win. Than backup your data. Because I still use Win as a promary system and wasn't familiar with virtualisation at the time, I decided to slice a 10Gb partition for Ubuntu, didn't bother getting a partition for /home directory, but took another 256 mb for a swap partition ( It actually should be 500 but no worries ). To do this use the gParted application provided on the LiveCD. You can edit the size of your partitions. Notice that it still may not be totally safe to edit the size of your NTFS file system partition ( thats why the defragmentation and the backup ). After you resize the Win partitions and create a large partition for the /root directory - which will hold your system , the small swap partition and any other partitions you care to make, you can simply proceed to the installation. 

It took me an hour with the hoary hedgehog, and about 40 minutes with dapper. Im using a laptop but had no problems. I didnt bother to bind the function keys though. 

What you can do is wait a little, cause the new Ubuntu comes out in a couple of days. And you can always find help on the forums!

Cheers

---

### Post by bulldog on 2006-10-17
Well on every 100 new users is always someone who can't get it together.

If the install is over after you answer some questions,you can be pretty sure there was no install of Ubuntu.

The reason..........I only can guess,you where there and should now.

Installing a new OS isn't that simple,or rather it is,but you need to know what your doing and take some precourtions before you install.

Just booting the live cd and thinking all comes well isn't smart.

But it isn't hard to do,believe me,I did it several times although I have to admit that my first steps with Linux where frustrating too.

But take your time and read carefully what is going to happen and if you don't understand the first time,try again.

If you're not willing to put some efford into it,well.... you have to ask yourself of this is what you want.

---

### Post by xpod on 2006-10-17
I found just leaving the ubunto space "unallocated" and then pointing the partitioner to the unallocated space did the job...

I too have had issues when creating all the partitions beforehand...
Generally though wherever im putting ubu just gets left unallocated and it works more often than creating them first....either from gparted on the ubu cd or from it`s own live cd..

Let ubu sort itself...plenty of time later for the extra`s partitions etc:D

> This shouldn't be this difficult! And I'm a long way from computer illerate.


neither am i mate....only been on a pc 7 months now....4\5 months of windows and 3 ubu so far..

Have a wee bit faith in yourself mate:D

---

### Post by vayde on 2006-10-17
Sounds like the first thing you should do is download the Gparted Live CD, boot to that, and see what you find there.  I realize it's on the Ubuntu CD, but if you get the image and make a dedicated CD, you will be sure you are messing with the partitions, and nothing else.

You may have already done this, but make sure you defrag your NT partition before you go messing around with partitions.

My recommendation is to defrag, use Gparted's dedicated live cd to shrink partition, and then when it comes time to install Ubuntu, just let it install itself into the free space.

The auto install stuff in Linux and Ubuntu have come along way, but sometimes its better to do it piece by piece the old fashioned way.

---

### Post by pminmo on 2006-10-17
V6.06

My partitions are ok. I've got Gparted live cd, it's the only thing that makes me think ubuntu is installed.  It shows the 4 partitions I setup, winxp (ntfs), ubuntu (ntfs), swap and dos(fat16).  Marked xp as boot, if I try to mark ubuntu as boot it can't find anything to boot.

Win xp boots fine.

---

### Post by bulldog on 2006-10-17
Well Ubuntu should be ext3.............not ntfs.

Do some reading again.

Just make some space [about 10-20GB] should be enough for a try out.

Let the space unallocated.

Boot live cd and answer the questions.

Come to the partitioner and let ubuntu use the unallocated space.

Then the install begins and takes half an hour.

At the end you get the message to reboot without the cd.

That's all to it.

---

### Post by vayde on 2006-10-17
> **pminmo said:**
> V6.06

My partitions are ok. I've got Gparted live cd, it's the only thing that makes me think ubuntu is installed.  It shows the 4 partitions I setup, winxp (ntfs), ubuntu (ntfs), swap and dos(fat16).  Marked xp as boot, if I try to mark ubuntu as boot it can't find anything to boot.

Win xp boots fine.

Ubuntu shouldn't be running on ntfs.  It's might be possible, but it's not what you want.

Blow away the ubuntu partition, and set it up so there's a healthy block of free space, and let the Ubuntu installer just do it's thing into that free space block.

---

### Post by TmP on 2006-10-17
Maby thats the problem!

Ubuntu shouldn't be on a NTFS partition.
You'll be better off with a ext2.
Actually you might consider looking into the whole Virtual Machine thing - youll be running Ubuntu in a window mode under Windows XP, or the other way around

---

### Post by bulldog on 2006-10-17
> **TmP said:**
> Maby thats the problem!

Ubuntu shouldn't be on a NTFS partition.
You'll be better off with a ext2.
Actually you might consider looking into the whole Virtual Machine thing - youll be running Ubuntu in a window mode under Windows XP, or the other way around

Glad you come around making him more confused as he is :D 

Let's keep it with ext3 that's Ubuntu default shall we?

---

### Post by pminmo on 2006-10-17
Well NTFS was the problem, I'm up and running.  I find it hard to believe with all the windowsXP users out there that there isn't a decent webpage at ubuntu that is titled Winxp to Ubuntu in a proment place!  I don't know where I missed that ununtu couldn't be installed on ntfs, I don't know why when the installer had to format the partition, it allowed it.

If you look at all the dual boot posts, it's obvious that lots of people are having installation issues.  

There are a ton of computers out there with XP instlled and no partition space.

I hope it goes better for my other tasks.

Computers are meant to be used.  You shouldn't have to be a power user to handle simple issues.  I've been heavily into coumputers since the early 70's.  Worked with minicomputer OS's, realtime OS, written code, written drivers, designed complex digital hardware, and been in that enviornment all this time.  Most users don't want to be command line driven, they want intuitive well designed interfaces.  ubuntu's desktop and operations seem excellent.  Documentation has a lot to be improved.

---

### Post by bulldog on 2006-10-17
Well it's not an Ubuntu thing,but a windows user thing.

They are expecting a **free** OS and are thinking they have some rights on it.

Well wake up!!

If you want to use Linux and especially Ubuntu,there are ton's of documentation on the net.

But you have to look for it,your browser will not be directed automaticly.

Ans supposing that there is a tutorial migrating from windows to linux,I pretty sure there's one.
But again **look for it**

But welcome to Ubuntu anyway.

---

### Post by bulldog on 2006-10-17
> **pminmo said:**
> Well NTFS was the problem, I'm up and running.  I find it hard to believe with all the windowsXP users out there that there isn't a decent webpage at ubuntu that is titled Winxp to Ubuntu in a proment place!  I don't know where I missed that ununtu couldn't be installed on ntfs, I don't know why when the installer had to format the partition, it allowed it.

If you look at all the dual boot posts, it's obvious that lots of people are having installation issues.  

There are a ton of computers out there with XP instlled and no partition space.

I hope it goes better for my other tasks.

Computers are meant to be used.  You shouldn't have to be a power user to handle simple issues.  I've been heavily into coumputers since the early 70's.  Worked with minicomputer OS's, realtime OS, written code, written drivers, designed complex digital hardware, and been in that enviornment all this time.  Most users don't want to be command line driven, they want intuitive well designed interfaces.  ubuntu's desktop and operations seem excellent.  Documentation has a lot to be improved.

If you did all that you didn't pay much attention.
I'm a simple user and didn't anything what you did and even I know it uses a different file system!!

If you think you're out the woods yet,you're in for a surprise though.

Most things are done with the terminal or commandline.

---

### Post by xpod on 2006-10-17
IF thats how confused someone gets after using pc`s for 30 years then im darn glad i only turned one on a few months ago.

Good luck anyway and welcome....you`ll soon  get your head round it and theres tons of good documentation out there all easily accsseible,thousands of "how to`s" and loads of good folks on here who gladly give their time to those willing to learn....and even some not so willing.

[http://www.google.com/linux](http://www.google.com/linux)

---

### Post by jkvv_1973 on 2006-10-17
I almost gave up on Ubuntu too...I just didnt have the time to trouble shoot...turns out it partitions automatically...and had some grub errors which I guess the SGD fixed...

I do agree that there should be a sticky on a simple install for UBUNTU...like I had to check the forums to find out that the important thing about partitioning was to keep it simple (root home swap)...but you wouldnt know that till you do some research(sometimes forced to because like this guy his partition is NTFS)...I know its free but you gotta take into consideration that people who want to try Ubuntu are usually Windowcentric...just my 2 cents

---

### Post by Henry Rayker on 2006-10-17
A problem with a "simple installation" sticky is that there really isn't going to be one set starting point. One user has WinXP, one has Win98, WinME, OSX, other linux distros etc etc etc. I found an installation guide for WinXP with no problem at all. A simple google search turned it up.

The documentation is just fine. Working as an engineering intern right now, I've seen MUCH worse documentation in industry. What most users want is a "hold my hand and do it for me" approach. When you're paying absolutely nothing for a piece of software, the amount of available documentation is far more than I would expect. Not to mention they'll even ship disks to you 100% free. This costs them money.

---

### Post by xpod on 2006-10-17
> .like I had to check the forums to find out that the important thing about partitioning was to keep it simple (root home swap).

I only learned what a partition even was a week or so before i first installed ubunto.....and on "checking" discovered that the even easier way was just to let ubunto insatll to whatever space you`ve created itself...or hd as it was for me at that time

I have since made home partitions of course along with all sorts of others but when i did`nt know jack about them that was the simple way for me..

---

### Post by bulldog on 2006-10-17
> **jkvv_1973 said:**
> I almost gave up on Ubuntu too...I just didnt have the time to trouble shoot...turns out it partitions automatically...and had some grub errors which I guess the SGD fixed...

I do agree that there should be a sticky on a simple install for UBUNTU...like I had to check the forums to find out that the important thing about partitioning was to keep it simple (root home swap)...but you wouldnt know that till you do some research(sometimes forced to because like this guy his partition is NTFS)...I know its free but you gotta take into consideration that people who want to try Ubuntu are usually Windowcentric...just my 2 cents

Totally agree with you,but there's always a but :D 

It's no excuse you're a windows user,we all where once.

If you want to learn a whole new operating system,you can expect some trouble.

I remember windows 3.1 very well coming from DOS,and it costed some efford to learn to work with it.

Same with W95 and so on.

Why should learning Linux been easy?
Cause we know Windows??

Get real,learning another OS is difficult and you have to put some efford in it,and not expect that you will be taking by the hand.

And everybody with questions will be supported on this forum.

But the altitude is important to begin with.

You should be aware the fault is not Linux but the user who try's to learn it.

Just my 2 cents.

---

### Post by pminmo on 2006-10-17
> **bulldog said:**
> Totally agree with you,but there's always a but :D 

It's no excuse you're a windows user,we all where once.

If you want to learn a whole new operating system,you can expect some trouble.

I remember windows 3.1 very well coming from DOS,and it costed some efford to learn to work with it.

Same with W95 and so on.

Why should learning Linux been easy?
Cause we know Windows??

Get real,learning another OS is difficult and you have to put some efford in it,and not expect that you will be taking by the hand.

And everybody with questions will be supported on this forum.

But the altitude is important to begin with.

You should be aware the fault is not Linux but the user who try's to learn it.

Just my 2 cents.

This isn't about learning another operating system.  It's about the keys to get there in the first place. Primarily an ntfs issue.
So the key should be Windows to Ubuntu.
  Your turn it to one of 6 positions:
   Winxp
   Win2000
   WindNT
   WinME
   Win98
   Win95   

Probably a wiki would do it.  Searching post after post after post is crap.  Might as well be a visitor in NY at night, no moon and all the power is out and your lost on the street.  Gonna tell that guy he needs to learn NY?

---

### Post by Sef on 2006-10-17
> This isn't about learning another operating system. It's about the keys to get there in the first place. Primarily an ntfs issue.
So the key should be Windows to Ubuntu.

If someone asks how to install Ubuntu, it is generally recommended to do a dual boot and [read this tutorial first before attempting an install.]("http://users.bigpond.net.au/hermanzone/")

---

### Post by pminmo on 2006-10-18
> **Sef said:**
> If someone asks how to install Ubuntu, it is generally recommended to do a dual boot and [read this tutorial first before attempting an install.]("http://users.bigpond.net.au/hermanzone/")

#1 I'm trying to be proactive and point out the problem helpfully, but I'm defintely getting the impression people in the know are either way to close to the problem to understand or....

Walk through this.  You find out about Ubuntu, so you go to the Ubuntu webpage, you look at the desktop information as that is what you are interested in.  You go through all the ubuntu site about what/where/how which includes a graphical install webpage.  You download it, burn the cd, boot the live disk and play with it.  NOWHERE does it say anything in that process about "read this tutorial before attempting to install!"  and NOWHERE does it give you a path for installing Ubuntu on an existing Windows system, and NOWHERE does it tell you you can't run Unbuntu on ntfs.
Since most Windows users would come via this webage [http://www.ubuntu.com/desktop](http://www.ubuntu.com/desktop) or the download page [http://www.ubuntu.com/download](http://www.ubuntu.com/download) shouldn't some information be put there?  

How about a simpified basics for transitioning from windows that at the top level that doesn't contain so much unecessary information?  And then links to the details for those whom it applies, reduce the information overload.

---

### Post by Coelocanth on 2006-10-18
While I can see your point, I think there is a certain onus on the person considering installing Ubuntu to do some research on Linux and Ubuntu to find out more about it and whether it would be something they want to try out. Even a quick google search would reveal that Linux cannot be loaded onto an NTSF-formatted partition. I find it hard to believe that one would assume a totally different OS would use the same file system as Windows. To use your NY analogy: no, not gonna tell that guy he needs to learn NY... but I would suggest it was foolish of him to travel to NY and not at least do a little research on the city beforehand. ;) 

But welcome to Ubuntu, good to hear you got things sorted out.

---

### Post by confused57 on 2006-10-18
This is probably one of the first websites an Ubuntu beginner should be referred to:

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

as well as the one Sef provided a link to:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

This forum is one of the best sources of information for "howto's", installing, troubleshooting, helpful links, etc.

Any questions before someone installs, troubleshooting after install, tweaking your system, how to add new software, configuration etc, etc...can usually be answered by "asking" here.  I'll admit, I've made my share of mistakes with Ubuntu...and I've learned through making mistakes, I was fortunate that I had an old test computer to learn on before I tried anything on my main computers...I realize that many(most) people don't have this option.

In my opinion, the above 2 links would probably provide most of the information a beginner would need to get started...I'd be interested if someone just starting with Ubuntu would agree, or not.  If so, maybe a way can be devised to point this out to people before they start installing?

---

### Post by pminmo on 2006-10-18
> **confused57 said:**
> This is probably one of the first websites an Ubuntu beginner should be referred to:

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

as well as the one Sef provided a link to:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

This forum is one of the best sources of information for "howto's", installing, troubleshooting, helpful links, etc.

Any questions before someone installs, troubleshooting after Ainstall, tweaking your system, how to add new software, configuration etc, etc...can usually be answered by "asking" here.  I'll admit, I've made my share of mistakes with Ubuntu...and I've learned through making mistakes, I was fortunate that I had an old test computer to learn on before I tried anything on my main computers...I realize that many(most) people don't have this option.

In my opinion, the above 2 links would probably provide most of the information a beginner would need to get started...I'd be interested if someone just starting with Ubuntu would agree, or not.  If so, maybe a way can be devised to point this out to people before they start installing?

Yes they would have helped, but... #1 it should be part of the ubuntu website. #2 it needs to be structured. #3 there is already a graphical install ubuntu webpage [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) so mainly it needs to be the windows precursor information.  i.e. partition information, shrinking ntfs, ubuntu file system and swap requirements, visability between each systems files, where to get gparted and other pertanent tools.  Put that infront of the graphical install page in the same simple format as the lead in ubuntu website pages.  A live ubuntu tools cd in .iso format for download would be a help.

---

### Post by _simon_ on 2006-10-18
Idealy the Live CD should have documentation to cover full installation be it as the only OS or as a dual boot. 

I think most people assume that anyone even interested in Linux is a little bit geeky so should be able to cope but as you've proved Ubuntu is attracting a wider audience now, one that needs a little more help.

FYI, NTFS is the NT File System first introduced by Microsoft for the Windows NT operating system. It was later used in Windows XP and replaced the FAT file system. The new Windows Vista was supposed to be using another new file system "WinFS" but I believe they have dropped this due to lack of time.

---

### Post by Soarer on 2006-10-18
I am glad the problem is sorted, and welcome to the Ubuntu community.

I am sure the documentation can be improved - what can't? Now you are a member of this community, maybe you could take that task on?

To be serious - what you were trying to do is not trivial. Think of it the other way around. You have Ubuntu installed & running happily. Now you want to install XP on the same drive & dual boot, using Windows documentation. How easy would that be? Would you try to install XP on an ext3 filesystem? Would the Windows documentation give you a step-by-step? Would there be a friendly XP forum to ask questions on?

And if you don't like the command line... how many MS fixes start 'press 'Start' and click 'run'? Type this command...

There is a learning curve with any new system - in a month or so you will wonder what the fuss was about. :)

---

### Post by xpod on 2006-10-18
The longer someone has used windows it seems the harder they find this at first,you`ll sooon be flying along im sure:D  
I know nothing really about any os or pc other than what ive crammed in in my few months using them but even i had gathered enough to understand it was completely different formatting requirements\filesystem...whatever it`s called;) 

Which you dont really even need to know.....the live cd does it all for you if you let it do the job itself.
It`s not something i recall "needing" to have right,it was done for me;) 

Have fun anyway m8...good stuff

---

### Post by gn2 on 2006-10-18
Ubuntu seems to be hugely popular at the moment.

I suspect this is largely because of the fact that it is entirely free, for an outlay of zero cash anyone can get quantities of CD's shipped anywhere.

Unfortunately (in my opinion) it seriously lags behind some other distributions in terms of ease of use.

I'm not the only person who wouldn't recommend Ubuntu as a first choice.

These forums are very active for a reason.....

---

### Post by pminmo on 2006-10-18
I wrote this simple illustration on my wiki as to my point of what is needed. [http://www.pminmo.com/wiki/index.php?title=Unbuntu](http://www.pminmo.com/wiki/index.php?title=Unbuntu) But the equivalent/better presented needs to be on Ubuntu.

---

### Post by devnulljp on 2006-10-18
> **TmP said:**
> Maby thats the problem!

Ubuntu shouldn't be on a NTFS partition.
You'll be better off with a ext2.
Actually you might consider looking into the whole Virtual Machine thing - youll be running Ubuntu in a window mode under Windows XP, or the other way around

What he said (about ntfs), but ext2 is old, use ext3, it's a modern journaled filesystem.

---

### Post by nik on 2006-10-18
> **pminmo said:**
> I wrote this simple illustration on my wiki as to my point of what is needed. [http://www.pminmo.com/wiki/index.php?title=Unbuntu](http://www.pminmo.com/wiki/index.php?title=Unbuntu) But the equivalent/better presented needs to be on Ubuntu.

Excellent! :) You went through this trouble, then do the work of writing that to make it easier for others. It's what ubuntu is all about :)

I agree with you that it probably should be easier to install. I can't put myself in your excact position, cause I tried installing linux many years back, and then I had to read up on almost everything to get it to work... however, the install should have told you not to use ntfs.

But, try installing ubuntu first, and then install win to dual boot... that's a lot more trouble...

Anyway, hope you like your ubuntu and stay with the community.

---

### Post by Mimsy on 2006-10-18
Okay, I'm really confused now... where in the install does it let you stop and create an ntfs-partition? Once you've started the install, Ubuntu makes a partition itself, of whatever size you tell it to, right. When it's that easy to set things up, why bother making partitions yourself?

/Mimsy

---

### Post by bulldog on 2006-10-18
> **Mimsy said:**
> Okay, I'm really confused now... where in the install does it let you stop and create an ntfs-partition? Once you've started the install, Ubuntu makes a partition itself, of whatever size you tell it to, right. When it's that easy to set things up, why bother making partitions yourself?

/Mimsy

I think he made the partitions before installing and let the partitioner not do his job.

He pointed the partitioner to a NTFS disk for the install,then the install stopped.

That's not strange to us,but confuses a window user I suppose.

---

### Post by Mimsy on 2006-10-18
Oh. That makes way more sense. That's what I get for reading forums from work, where I actually have to focus on the work and not the forums... :o

Note to self: Switch to decaf.

/Mimsy

---

