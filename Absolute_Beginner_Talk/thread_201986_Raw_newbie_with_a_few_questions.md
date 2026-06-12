---
title: "Raw newbie with a few questions"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by Z-man on 2006-06-22
Ok so I've decided to make the leap "sort of".  I'm going to partition my drive and dual boot XP Pro and Linux.  The distribution that almost every one has recommended to me is Ubuntu.  I wanna give this a shot, but I also wanna be sure that this is as close to windows in terms of functionality as possible "because I've been using windows ever since 3.11".  How much of a difference can I expect?  I already use firefox to surf, but after looking at the "New to Linux? Need a program?" stickie at the top of this forum, that's about the only Windows - Linux equivalent I recognize.  I want to start out with it resembling and working as much like Windows XP as possible so that the barrier to learning it won't be so high.  Any one have any thoughts or suggestions about how to ease the transition?

---

### Post by DR_K13 on 2006-06-22
[https://help.ubuntu.com/community/CommonQuestions](https://help.ubuntu.com/community/CommonQuestions)

---

### Post by aysiu on 2006-06-22
Best way to ease the transition is to go slow.

Play with the live CD for two weeks. Learn as much as you can about backing up data and installing operating systems.

Install a dual boot or install Ubuntu on VMWare in Windows. Play around with that for a while.

Gradually wean yourself off Windows. Don't rush into things.

---

### Post by Brunellus on 2006-06-22
Here's an important life lesson:

"having as much functionality" does NOT equal "using exactly the same software," especially if you're changing from one OS to another (windows to Ubuntu, say).  

A good general rule to help ease the mental transition is to stop thinking of specific software programs and start thinking of specific TASKS that you want to accomplish.  For example, instead of thinking Outlook, Word, Excel, Powerpoint, think:  E-mail, Word Processor, Spreadsheet, and Slideshow Software.

Then, you can ask yourself.  "I use Word, which is a processor for Windows.  What word processors are there for Linux?"

If you make this conceptual jump away from "programs" to "things I need to get done," you will discover that you know more about computers than you thought you did.

---

### Post by bruce89 on 2006-06-22
[QUOTE=Brunellus]Then, you can ask yourself.  "I use Word, which is a processor for Windows.  What word processors are there for Linux?"[/QUOTE]
This might help - [http://www.ubuntuforums.org/showthread.php?t=33183](http://www.ubuntuforums.org/showthread.php?t=33183)

---

### Post by Zikes on 2006-06-22
I've been using Windows for nearly a decade myself, and I can tell you that you'll be pleasantly surprised at how easy Ubuntu is to use once you get the hang of it.  It can be frustrating at first, but for all the problems I had it was still pretty fun to learn.

The first thing I had a problem with is the new drive setup/file system.  There is no more "C:" or "D:" drive, instead everything is located under "/" (called 'root').  From there your physical drives can be found under "/dev" which stands for "devices."  Drives have a relatively simple naming scheme.  Hard drives will be named hda, hdb, hdc, etc. and partitions on each hard drive will be named hda1, hda2, hdb1, hdb2, etc.  From here, each drive/partition can be "mounted" to nearly any other folder in the system.  Linux may have been aware of a drive, but mounting is how you gain access to it.  The process of mounting lets you assign a folder to act as that drive/partition, which is usually located in the /media folder in the case of removable storage such as CDs and USB drives.  Luckily Ubuntu will usually automatically recognize and mount media for you, and even provide an icon to access it on the desktop, but if you have a problem accessing a drive then you'll probably want to look into the "mount" command.  More information on the directories can be found here: [https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html#directories-file-systems](https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html#directories-file-systems)

Second, since you're using a Windows/Linux dual boot you'll probably have an issue with the filesystem format.  Windows XP defaults to NTFS, for which Linux support is experimental and unstable.  At current I believe you can resize the NTFS partition to make room for Linux without any problems, and you can read from NTFS just fine, but when it comes to writing to NTFS you may have some trouble.  An alternative, if you have the space, would be to create an extra FAT32 partition on the drive which can be used to transfer files between OSes or, if possible, reinstall XP onto a FAT32 partition.  As for the reverse, I'm not sure if Windows is able to access Linux's ext3 filesystem format, so it may be wise to use your Windows partition or an extra FAT32 partition for general document and file storage for both OSes.  A great tool for dealing with these partitions is GParted, which is best run from a LiveCD.  More info on that here: [http://www.linux.com/article.pl?sid=06/04/25/1917228](http://www.linux.com/article.pl?sid=06/04/25/1917228)

Thirdly, installing new programs can be a bit daunting at first, but there's a great guide for installing nearly anything you can imagine here: [http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

As for the general look & feel, the desktop environments are mostly the same.  By default Ubuntu installs with two "start bars" which are actually called "panels."  They're very customizable, and without problem I managed to combine the two into one that very closely mimics the Windows start bar.  Several built-in themes let you change the look & feel of the windows themselves, all of which have the controls you're used to seeing on a window with the minimize/maximize/close buttons in the upper-right, draggable borders for resizing, etc.

Well that should get you off to an easier start.  As Aysiu said it helps to play with the LiveCD for a while, and since you'll be sharing a drive with your Windows installation you probably don't want to just leap right into it without getting the hang of it first, but in either case make sure you back up everything important in your Windows partition.  Linux is highly configurable and powerful, but that just means it's just that much easier to shoot yourself in the foot if you're not careful ;)

---

### Post by mistrip on 2006-06-22
Looks like good advice.  I might nick it and post it somewhere else if that's ok.  Maybe i will be able to fix some of my probs too.

---

### Post by NinjitsuStylee on 2006-06-22
First of all I just want to give a bunch of high-fives to everyone who has responded to this thread, and also to you, for taking the leap to the unknown.

I've been using Ubuntu as my main system for a whopping...(drumroll please)...ONE MONTH!

So basically, I was where you were not very long ago.

And I gotta say, it's pretty fantastic.  This is saying a lot coming from a guy who not very long ago was relatively anti-linux (sigh, I won't go into it here).

Now, don't get me wrong, I'm not quite ready to join the hordes of penguin-costume-wearing linux zealots, because I still have my windows XP boot sitting on my hard drive and once in a blue moon I do need to go back into it to do a thing or two (although I'm trying to avoid it as much as possible).  


Here's the deal.  I totally agree with the fact that you're going to have to change your mentality to a "what can I do" one instead of "what programs should I use" one.  I also totally agree that you should dip your toes in the pool before you jump right in it:  try Ubuntu on a LiveCD distro...heck, try ANY liveCD distro.  Knoppix is another one of my favorites (and it was my very first introduction to Linux....sigh, meemmmoorieeeees).

I could address all your issues with programs and compatibility and whatnot but I'm going to cover something else that is quite important instead:

[B]Support!

[/B]My absolute favorite thing about Linux is its community.  Not necessarily the people in it, but the community in general.  Some people will have you believe that Ubuntu (or any flavor of Linux really) will do everything Windows can ("and better!") right out of the box.

I am going to tell you the grim truth right now:  this is usually not the case.  Everybody uses computers differently and saying that Ubuntu works 100% out of the box is a very generalized and sweeping statement.

For example, when I first started, I had to figure out the file system just like everyone else, and I also had silly hardware issues (such as getting my 5 button mouse to work properly in Firefox, etc).

All together, it has probably taken me a good 72 hours of tinkering to get things to work the way they want (although keep in mind, I did play around with pretty much everything :mrgreen:).

But I digress...back to the original issue.  The point is, while you are learning Linux/Ubuntu, you're going to need help.  It's good to see that you've come to the Ubuntu forums because that is a fantastic step.  I can't stress enough how great it is to sit in a chat room, ask a guy a question (from simple things like using the "ls" command to complicated things like compiling WINE from source) and having him and 5 other people give me straight answers.  It's like having an armada of tech support people!

But be warned.  Not everyone is helpful.  As a matter of fact, one of the original gripes I had with the Linux community in general was the vast amounts of egotistical bigots who lacked the skill to properly communicate ideas to newbies, or simply decided that it wasn't worth their time.

You'll probably run into a lot of this:

You:  "Hey, I was wondering, how can I get so-and-so from Windows to r-"
Zealot:  (cutting you off) "WINDOZE?!? M$!?!? EVIL EVIL EVIL! AAAGH GO DIE IN A FIRE YOU NOOB!!!!!! DON'T MAKE ME SEGFAULT YOUR A**!!"

Well, you get the idea, at least.  Don't be too upset by this.  In recent years, people have become MUCH more pleasant about helping others out (and these forums are probably the pinnacle of places to get help).

As far as converting from windows, again, take it slow.  I'm still in the conversion process myself (tonight I'm going to be moving more of my documents off of my windows partition and onto my FAT shared one, woo!) but I think I've come a long way.  My reasons for turning to Linux are a bit complicated, and I will say without any shame that when Vista comes out, I will probably run it....but not on this machine.  This machine I'm on now is going to stay a dedicated linux box.

Finally, don't get too caught up in doing things the "Linux" way.  I've been doing a lot of crazy things in Linux and yet I'm still uncomfortable when I have to use a program that doesn't have a GUI (which people would argue is the "Windows" way).  Personally, I'm all about doing things the INTUITIVE way.  Software should be designed so that people don't have to sit there and figure things out.  If things make more sense to me to do from a terminal, I use the terminal.  If I want a GUI, I should have one.  Linux is all about choice and IMHO these things are a part of that choice too.

Anyways, I've blabbed enough.  Good luck, and remember, all the Googling and chatting in IRC channels and searching on ubuntuforums.org will pay off in the end!

---

### Post by joe_lace on 2006-06-22
[QUOTE=aysiu]Best way to ease the transition is to go slow.

Play with the live CD for two weeks. Learn as much as you can about backing up data and installing operating systems.

Install a dual boot or install Ubuntu on VMWare in Windows. Play around with that for a while.

Gradually wean yourself off Windows. Don't rush into things.[/QUOTE]I've only ever used windows, I'm trained and certified with windows and I just made the switch a couple days ago.  I did the exact oposite of what aysiu is suggesting :P.  I just jumped right in.  Some of the issues I had starting off were file sharing with my wife's windows box, and sharing my printer with her as well.  I got both of those things working thanks to these excellent forums.  I think that the smart thing would have been to use the liveCD for a while but I have always been impatient.  Linux will definitely be an adjustment for you, but I think you will enjoy it.

---

### Post by Z-man on 2006-06-22
Wow that's alot of responses in just a short time.  Thanks :) .  I've read over what every one posted, and it looks like alot of useful information.  I have read a few things that have gave me pause tho.  Reading the Restricted Formats section of the Common Questions faq has me a bit worried.  Is it really that complex just to be able to play an mp3?  I would think that I could just install a program that plays mp3s, and it would work.  Also on the How to install ANYTHING in Ubuntu! page, installing anything not available thru Synaptic "not real sure what that is" looks REALLY complex.  I consider myself fairly competent with computers, tho I have only the most basic idea of how codecs work, and exe files work their magic, but this all looks really daunting.  I thought the basic differences between the two operating systems would be less, especially in something as common place as installing software.

Also I see several references to Dapper Drake, Kubuntu and Breezy Badger.  One of the largest barriers I faced in even thinking about installing Linux was all of the gad-zillions of choices available.  Narrowing it down to Ubuntu was based pretty much on recommendations.  I can't claim to have put a ton of research into it, it mostly amounted to asking some of my Linux using friends what I should install.  Seeing several sub-variations of Ubuntu "if that's what these are" puts me right back into the position I was in when I started.  

As to application replacement, I definitely think in terms of what I want to do, as opposed to what program I want to do it with.  But I have also invested a TON of time in finding Windows programs that I like and that do exactly what I want them to.  In some ways I look forward to the adventure of trying out new programs, and possibly discovering something better than what I'm using now, but on the other hand their is all the time "and in some cases money" that I've spent refining and testing and getting used to the programs I have now.

In many ways, I'm going back to computing square 1.  Back to the first computer I got as a kid "486 25mhz 80 meg drive with a whopping 1 megs ram" that I had no clue how to use.  I'm not quite as excited anymore when I see that almost everything I know, years of often hard won experience, is no longer going to apply.

---

### Post by aysiu on 2006-06-23
Frankly, I don't think Ubuntu is the most technically superior or easiest-to-use distribution for ex-Windows users. Many here will disagree with me, but this is still how I feel.

I use Ubuntu because the support on these forums is unparalleled. That's the main reason I use Ubuntu and not Mepis, especially since Mepis' newest version (6, which is currently in release candidate 2) is based on Ubuntu.

Instead of going off recommendations, maybe you should take this quiz, which isn't the be-all and end-all of matching you up with a Linux distribution, but it'll give you a couple of good places to start, and those may not be Ubuntu: [http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

Mepis was my first real Linux distribution, and I'm glad it was. I'm also glad Ubuntu was my second. Mepis was just right to wean me off Windows--very point-and-click, and it includes a lot of popular restricted formats (proprietary drivers and codecs), so you don't have to do anything separate to install those.

Unfortunately, there are some barriers you're going to encounter regardless of what Linux distribution you use--installing software outside of the repositories and finding Linux applications that meet your needs.

I happen to find almost all of my needs met with repository software, and the few programs I do install that aren't in the repositories usually have a .deb, if not one especially made for Ubuntu.

Compiling from source can be a pain in the ***. I don't think I've ever done it successfully.

And if you have very specific Windows-only programs, you may need to run them through Wine, through Crossover Office, through Cedega, through VMWare... or through a dual boot.

---

### Post by strabes on 2006-11-24
For ext2/ext3 read/write support in Window$, you can use [this](http://fs-driver.org/) program. It works flawlessly for me.

My impression of KDE was that it was very windows-like.

---

