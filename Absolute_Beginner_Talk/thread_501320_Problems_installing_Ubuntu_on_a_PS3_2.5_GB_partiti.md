---
title: "Problems installing Ubuntu on a PS3 2.5 GB partition"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by mattinthematrix on 2007-07-15
One installs Ubuntu from live CD, providing 2.5GB for the root partition.
One fires up the network connect for the fresh new Ubuntu, and finds that there are 97 updates. OK. Go.
With three updates remaining, the update process fails. Not enough disk space.
OK, one will just reboot live CD and extend the root partition to make more room.
Nope, can't do that. OK, back to hard disk installation to see about making a partition image.
Nope. Can't log-in to Ubuntu at all because of lack of disk space.

Can't log-in! It filled up the disk without warning, then is incapable of even logging in to do something about it!

I'm starting to understand why linux can't break in as a desktop OS.

I've tried numerous distros, and always end up back on Windows, as crappy as it is, and as much as I hate proprietary software. Why?

Because it works. Because it doesn't require one to have written machine code to be able to anticipate the bizarre assumptions of the OS.

Lack of disk space should not lock one out of the system. This is a pretty serious bug.

---

### Post by Game_boy on 2007-07-15
I believe one of the goals of the next release of Ubuntu is to make it more manageable with a full disk.

2.5GB? Who can't spare 10GB these days?

Redo the partition, larger and reinstall.

---

### Post by apoth on 2007-07-15
Did you try CTRL-ALT-F1 for a text login? I filled my hard disk up in the past week when my girlfriend left kaffeine recording TV indefinitely and it didn't keep me out.

Why couldn't you resize the partition? Did you get any errors? What else is on the disk?

How well do you think Windows would play with a 2.5GB partition?

The thing I like most about Linux is that when things go wrong, it's because I've done something wrong and not just because Windows has had a fit. Calling the tool that so many of us use without problem stupid is not the best way of getting help.

---

### Post by corney91 on 2007-07-15
Have you tried Windows with only 2.5GB disk space?

---

### Post by dptxp on 2007-07-15
You should read some basic instructions before you install.
Feisty needs minimum 4 GB for /.
And If you install any software months after its release, you are bound to have updates.
But who is forcing you to do so?
And do not compare Ubuntu with XP for resources, XP is old. Compare with Vista.

---

### Post by mthakur2006 on 2007-07-15
> **mattinthematrix said:**
> Main Entry: 1stu·pid
Pronunciation: 'stü-p&d, 'styü-
Function: adjective
Etymology: Middle French stupide, from Latin stupidus, from stupEre to be numb, be astonished -- more at TYPE
1 a : slow of mind : OBTUSE b : given to unintelligent decisions or acts : acting in an unintelligent or careless manner c : lacking intelligence or reason : BRUTISH


One installs Ubuntu from live CD, providing 2.5GB for the root partition.
One fires up the network connect for the fresh new Ubuntu, and finds that there are 97 updates. OK. Go.
With three updates remaining, the update process fails. Not enough disk space.
OK, one will just reboot live CD and extend the root partition to make more room.
Nope, can't do that. OK, back to hard disk installation to see about making a partition image.
Nope. Can't log-in to Ubuntu at all because of lack of disk space.

Can't log-in! It filled up the disk without warning, then is incapable of even logging in to do something about it!

This is absolutely absurd. No wonder linux can't break in as a desktop OS.

I've tried numerous distros, and always end up back on Windows, as crappy as it is, and as much as I hate proprietary software. Why?

Because it works. Because it doesn't require one to have written machine code to be able to anticipate the bizarre assumptions of the OS.

Lack of disk space should not lock one out of the system. It's idiotic.
</rant>

i agree, this is annoying.
but this bug is being fixed for future releases, probably even gutsy :D

---

### Post by darrenm on 2007-07-15
You should have been able to log in as root using the recovery boot option. You could then have done lots of things to rectify the situation. Good job only people who know what they are doing will  attempt to do something like only use 2.5GB for an install ;)

---

### Post by insane_alien on 2007-07-15
just because you are stingy with discspace does not mean that ubuntu itself is stupid. it sort of implies that you are.

i'd also like to see XP or vista function with that little.

my root partition is 5GiB full just now (i'l go clean it out next week or something). i gave it 10GiB for a reason.

to fix this in the long run you will ned to reinstall as the extents filesystem doesn't resize well. either use a single partition for the entire filesystem and one for swap or make sure the root partition has at least 6GiB.

---

### Post by mattinthematrix on 2007-07-15
I read more than basic instructions. They told me 2.5GB would be sufficient. And most reasonably intelligent people can operates Windows or MacOS without reading any documentation, at least for basic tasks like generic installation, logging in, and installing updates.

The point is not how much space it takes, the point is that it becomes completely unusable when full. You can still login to windows when it's full, even at 2.5GB and less.

I don't have 10GB to spare because I'm installing on a PS3.

Obviously the solution is to make new partitions and reinstall. And I maintain that it's absurd that I must resort to that.

It takes a much bigger problem than a full disk to require a reinstall of windows.

I'm also not complaining about the fact that there were so many updates. I'm complaining about the fact that I was not warned that installing them would fill my filesystem and break my OS.

parted gave a "File system has an incompatible feature" error, even after removing the journal to turn my ext3 into a ext2.

I didn't know about the CTL-ALT-F1, but thats just a  real life example of my joking reference to needing to know machine code. If that's a solution, why couldn't there be a 'switch to text log-in' on the reboot menu?

I hate that you guys are making me sound like an apologist for MS. There are few companies I dislike more. I guess I'm just pissed off because I was really hoping that Ubuntu would finally be a usable desktop linux for the mass market, and I was quite disappointed to find otherwise.

---

### Post by jingo811 on 2007-07-15
Make your partition size right from the beginning around 5-10 Gb when doing your full install.  I've experienced a bunch of hang-ups and freezes when partitioning too much in Live CD.
That's why I prefer installing in Ubuntu's "DOS-mode" that you install with with the **Ubuntu Alternate Install CD** not the default Live CD that Ubuntu.com tricks you into downloading.
Besides not even Windows XP can function with less than 5 Gb let alone 2,5 Gb.

Ubuntu has been using "DOS-mode" install since it started.  Tricking ppl into using the Live CD for installation for the sake of testing the OS before installing is the most Stupidest move Ubuntu.com has made.  So in that sense your opinion is probably right but the OS Ubuntu beeing stupid is as wrong as you can be.

Computers and Programs only do what they're told to.  When the user is smart the computer/program behaves in a smart manner, when the user is ignorant the computer/program behaves Stupid and dumb #-o
It's a looking in the mirror thing!

---

### Post by Vague on 2007-07-15
> **insane_alien said:**
> i'd also like to see XP or vista function with that little.

Heh.  Doesn't Vista want something like 15 GB free for its installation?

---

### Post by mattinthematrix on 2007-07-15
No, there's a difference between ignorance and stupidity. 

I was ignorant of the fact that the installation utility's minimum root size of 2GB was wrong.

The fact that this ignorance results in me being locked out of my system is STUPID.

I'd also like to note that I didn't come here saying the developers were stupid, or the programmers, or Linus Torvald, or anybody. I said the OS was stupid, because a non-stupid OS would have a means to warn of potential problems of this magnitude.

But unfortunately, I'm not the least bit shocked that i've become the target of personal attacks.

Oh well, I asked for it. I was kind of an ***. It's 3:30 am here. I should be sleeping...

...but I'm busy reinstalling my Ubuntu...

---

### Post by J11Gyro on 2007-07-15
Uh Uh nope not going to say anything but just sit back and watch Forrest Gump again on my Ubuntu Linux computer:guitar:

---

### Post by kalmah on 2007-07-15
Windows Vista recommended system requirements:

# 1 GHz 32-bit (x86) or 64-bit (x64) processor
# 1 GB of system memory
# 40 GB hard drive with at least 15 GB of available space

---

### Post by primski on 2007-07-15
> **mattinthematrix said:**
> ...It takes a much bigger problem than a full disk to require a reinstall of windows....

yea, like anyone of 10 brazillion  spywares out there,  or stupid system file corruption or .... i can name like 100 things when win brake and ubuntu doenst ;)

---

### Post by lisati on 2007-07-15
> **corney91 said:**
> Have you tried Windows with only 2.5GB disk space?
My old Windoze 98SE machine came with a 1Gb hard drive....it currently has a 3Gb hard drive, & one of my current projects is t\o get it working on a network in co-operation with my current desktop & laptop....it's a bit tired but we're getting there!

---

### Post by J11Gyro on 2007-07-15
Ok now you are talking, the only hold up most of family and friends have had with Ubuntu is the language it uses, the names of files and such. The install is almost bullet proof if system is prepared and will normally pick up all hardware already installed on the system. I have built pc's for 15 years and not but just a few times did I get windoze to load with all hardware in system without a glitch. It used to be so bad I built them with cover off and 1 card at a time after basic drivers were loaded. Ubuntu has loaded every time bar none except when I messed up and used wrong drive. This community will help you with 99.99% of your problems even if it has been asked 1000 times, so give the OS a chance and take time to learn it abit and I think you will like it.:guitar:

---

### Post by Tomosaur on 2007-07-15
> **mattinthematrix said:**
> I read more than basic instructions. They told me 2.5GB would be sufficient. And most reasonably intelligent people can operates Windows or MacOS without reading any documentation, at least for basic tasks like generic installation, logging in, and installing updates.

The point is not how much space it takes, the point is that it becomes completely unusable when full. You can still login to windows when it's full, even at 2.5GB and less.

I don't have 10GB to spare because I'm installing on a PS3.

Obviously the solution is to make new partitions and reinstall. And I maintain that it's absurd that I must resort to that.

It takes a much bigger problem than a full disk to require a reinstall of windows.

I'm also not complaining about the fact that there were so many updates. I'm complaining about the fact that I was not warned that installing them would fill my filesystem and break my OS.

parted gave a "File system has an incompatible feature" error, even after removing the journal to turn my ext3 into a ext2.

I didn't know about the CTL-ALT-F1, but thats just a  real life example of my joking reference to needing to know machine code. If that's a solution, why couldn't there be a 'switch to text log-in' on the reboot menu?

I hate that you guys are making me sound like an apologist for MS. There are few companies I dislike more. I guess I'm just pissed off because I was really hoping that Ubuntu would finally be a usable desktop linux for the mass market, and I was quite disappointed to find otherwise.

Except that you're absolutely wrong. As much as you'd like to disagree, **most** computer users are incapable of doing anything other than opening a web browser or running MS Office. Nobody ever really installs Windows, it comes pre-loaded on their computer. The **only** reason Windows is so 'easy' to install, aside from the fact that most people never do it, is because the default Windows installer behaviour completely wipes your hard disk and removes your MBR. Ubuntu tries to be friendly, and allows you to keep Windows and install Ubuntu in a dual boot. In this case, you simply should give Ubuntu more disk space. 2.5GB is an incredibly small amount of space for a modern OS. Yes, Linux **can** run perfectly well in 2.5GB of space, but in anything other than special cases, it shouldn't be forced to. The default installation of Ubuntu requires 2.5GB of space for root **only** if you also create a seperate partition for some other directories, such as /home. If you can't spare more than 2.5GB in total, then Ubuntu isn't really for you. You could try a lighter distribution of Linux, but if you're that willing to give up, then I would, frankly, advise you to stick with Windows.

As for your inability to log in, this is kind of annoying, but I'm fairly sure it is being fixed. You can always use the Ubuntu recovery mode, which gives you a root shell, so you'll be working from the command line. You can probably start the GUI manually from there, but in all honesty, your problem WILL be easier to fix from the command line, since all you really need to is resize your partitions. If you're reinstalling Ubuntu, then just give Ubuntu more space.

---

### Post by Lenz_Kappov on 2007-07-15
> **mattinthematrix said:**
> Main Entry: 1stu·pid
Pronunciation: 'stü-p&d, 'styü-
Function: adjective
Etymology: Middle French stupide, from Latin stupidus, from stupEre to be numb, be astonished -- more at TYPE
1 a : slow of mind : OBTUSE b : given to unintelligent decisions or acts : acting in an unintelligent or careless manner c : lacking intelligence or reason : BRUTISH


One installs Ubuntu from live CD, providing 2.5GB for the root partition.
One fires up the network connect for the fresh new Ubuntu, and finds that there are 97 updates. OK. Go.
With three updates remaining, the update process fails. Not enough disk space.
OK, one will just reboot live CD and extend the root partition to make more room.
Nope, can't do that. OK, back to hard disk installation to see about making a partition image.
Nope. Can't log-in to Ubuntu at all because of lack of disk space.

Can't log-in! It filled up the disk without warning, then is incapable of even logging in to do something about it!

This is absolutely absurd. No wonder linux can't break in as a desktop OS.

I've tried numerous distros, and always end up back on Windows, as crappy as it is, and as much as I hate proprietary software. Why?

Because it works. Because it doesn't require one to have written machine code to be able to anticipate the bizarre assumptions of the OS.

Lack of disk space should not lock one out of the system. It's idiotic.
</rant>

Getting used to a new OS can be a challenge, fraught with many frustrations, and as a newbie to Ubuntu myself I have great sympathy with all of that, but may I suggest chilling a degree or two.  There's oodles of help available.  Fair enough, not all of it is well written or easy to find, and much of it requires a Linux glossary window for the beginner to make sense of it, but the bottom line is that Linux IS being taken seriously by a lot of big players now, and HAS matured into something users can cope with, as long as the techies supporting it have the perseverence and cool professionalism to work through the problems.  I'm coming at this after 15 years of solid MS Windows experience, and I don't expect it to be all plain sailing, but so far it doesn't seem significantly more insane.

---

### Post by OoooMatron on 2007-07-15
there should be no reason the livecd won't run just because the disk is full. as far as i knew, it doesn't use the harddisc.

why can't you resize the partition on the fly from the livecd?

---

### Post by darrenm on 2007-07-15
There are various ways to get around this and TBH the kind of people who are manually partitioning to 2.5GB should know these ways. Also I would probably go as far as to say that if you are knowing that you need to partition specifically to 2.5GB then you would also know to check how much space you have before doing updates. This isn't a personal attack (can't find any in this thread anyway) but I think you are being slightly unfair.

---

### Post by dptxp on 2007-07-15
If you think that Ubuntu is Stupid and does not care about your ignorance on HDD space, then use Puppy Linux. No need to install. But you need to know that it needs 128 MB of RAM to run.
Microsoft has a huge team to write error messages. Ubuntu team has no such luxury to take care of all sorts of User ignorance. It is for the user to know the hardware (and disk space) requirements.
By your logic most flavors of Linux are stupid, Ubuntu is no exception.

---

### Post by eentonig on 2007-07-15
Never heard the mass market running Windows on a PS3. But that's just me.

What the hell, rants like yours are just a waste of my time. You choose to abuse a system and then blame it for not functioning for the masses.


And I guess your reading skills are not up to par.

> Recommended minimum requirements
 500 MHz x86 processor 
 192 MB of system memory (RAM) 
[COLOR="Red"]** 8 GB of disk space **[/COLOR]
 Graphics card capable of 1024x768 resolution 
Sound card 
A network or Internet connection

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by Dennis the Menace on 2007-07-15
When you talk about stupid systems, XP wouldn't let me turn off my ext hd, said it was busy.
I found out after that it had moved the paging file on to it.
Is that stupid or what?.
My windows system uses about 5gb of space just with the basics.
I'm pretty new to computing but I've managed to install several distos with no problems at all.
I read the basics about installing it from the website and off I went, so I should think anyone with a bit of intelligence could do it quite the same.
The live cd is good because you can check all your hardware is compatable & sort out any problems before you install it.
I hardly ever use windows except to use Aconis true image to back-up my Kubuntu partitions.
Another good thing about it is that it's free and I don't have to authenticate it before every update.

---

### Post by jingo811 on 2007-07-15
To quote Forrest Gump > "Now that I know your name and you know my name, we aren't strangers anymore"  [SIZE="4"]So less talkey and more doey:[/SIZE]
[http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot](http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot)
Even though it's a Dual OS setup I think that you get more than enogh info to make a Single OS install by yourself.  But then installing on a PS3 must be harder than installing on some PC hardware I would think.  PC's been around for some decades PS3 just been around for 1-3 years the tested hardware support shouldn't be as highly expected as for the PC hardware support.

---

### Post by AlexenderReez on 2007-07-15
> **mattinthematrix said:**
> Main Entry: 1stu·pid
Pronunciation: 'stü-p&d, 'styü-
Function: adjective
Etymology: Middle French stupide, from Latin stupidus, from stupEre to be numb, be astonished -- more at TYPE
1 a : slow of mind : OBTUSE b : given to unintelligent decisions or acts : acting in an unintelligent or careless manner c : lacking intelligence or reason : BRUTISH


One installs Ubuntu from live CD, providing 2.5GB for the root partition.
One fires up the network connect for the fresh new Ubuntu, and finds that there are 97 updates. OK. Go.
With three updates remaining, the update process fails. Not enough disk space.
OK, one will just reboot live CD and extend the root partition to make more room.
Nope, can't do that. OK, back to hard disk installation to see about making a partition image.
Nope. Can't log-in to Ubuntu at all because of lack of disk space.

Can't log-in! It filled up the disk without warning, then is incapable of even logging in to do something about it!

This is absolutely absurd. No wonder linux can't break in as a desktop OS.

I've tried numerous distros, and always end up back on Windows, as crappy as it is, and as much as I hate proprietary software. Why?

Because it works. Because it doesn't require one to have written machine code to be able to anticipate the bizarre assumptions of the OS.

Lack of disk space should not lock one out of the system. It's idiotic.
</rant>

i think you are bill gates son....or one of microsoft employee member...

---

### Post by alex_anthony on 2007-07-15
although I doubt Bill Gates' son would have a PS3...
who told you that 2.5gb would be enough?

---

### Post by AlexenderReez on 2007-07-15
> **alex_anthony said:**
> although I doubt Bill Gates' son would have a PS3...
who told you that 2.5gb would be enough?

i don't think mattinthematrix has install operating system to any computer before....i don't about dos,but surely this guy never install windows...windows xp need average 5 gb....i=vista ultimate need atlease 8gb for clean installation not including any softwares.....

---

### Post by Wim Sturkenboom on 2007-07-15
If you have limited diskspace, only create two partitions (swap and /). Creating more partitions is a waste of space (one will be full while others still have plenty space).

With regards the question of a few why you can not resize:
As far as I know you can not move the beginning of a partition without data loss.

---

### Post by coffeecat on 2007-07-15
Has anyone else noticed the OP's nickname? If matt is still in the matrix how can he be sure that what he is experiencing as real is really real?  :-? :wink:

---

### Post by argie on 2007-07-15
How did that happen? I've had my Dapper desktop show 99% of the root drive full and it still lets me log in. Atleast it's getting fixed.

---

### Post by steevols on 2007-07-15
I haven't read all 4 pages of this thread, but this sounds like someone who didn't really think through. I'm fairly sure that Ubuntu recommends at least 2 GB for install... but that's like reading that "Vista" takes 256 RAM minimum.

When you install updates, there's this cute little "Total Size of Updates" thing in plain site. Try reading next time :P

---

### Post by jw5801 on 2007-07-15
Lol. That openning post was almost as bad as posting on any major political party's forum with the topic "Democracy is the stupidest politcal system ever."

If you have a problem, post it here and ask what you can do to fix it. Saying the OS is stupid because you filled the partition isn't exactly helpful, and (as has been demonstrated quite obviously here) is only going to get you flamed. Linux is extremely different to Windows, it's like learning a new language, but the good thing about it is that once something breaks you can almost always fix it without resorting to a fresh install, provided you know how. And the good thing about Ubuntu is this forum! Where there is pretty much guaranteed to be someone who "know's how." All you need to do is say "This happened, how do I fix it?" and chances are someone will try to help, usually within a few hours!

As for the problem, you should be able to log in in the command line, and clear some things from there, then I'm sure someone can point you in the direction of a good command-line based partition resizer, if that's where you want to go. They'll probably even tell you exactly what you need to type in so all you need to do is copy and paste.

---

### Post by benton on 2007-07-15
> **mattinthematrix said:**
> I was really hoping that Ubuntu would finally be a usable desktop linux for the mass market, and I was quite disappointed to find otherwise.

I hope your problem is gone by now. But I also hope you realize the people who wants to install Ubuntu on a PS3 or on a 2.5GB HD (or with that much free space) is not "mass market".

---

### Post by notwen on 2007-07-15
> I've tried numerous distros, and always end up back on Windows, as crappy as it is, and as much as I hate proprietary software. Why?

Try running Windows on a 2.5GB partition.  =]

---

### Post by techno-mole on 2007-07-15
this is directed at the original post (the first one in this thread) 2.5gig whats the point of a partition that size ? my photo's folder is 3 times the size of that and i have some files that are bigger again.
i also disagree that ubuntu is not ready for the mass market, i think it is, maybe not this release but the next, and from what ive been reading lately ubuntu is being used by more and more people, as are other distros, windows is ok if you want to use it, but windows vista hasnt done alot to keep people using wndows, that fact that its probably not as stable as ubuntu, in some cases its alot worse, more and more people will change, and who wants to pay a couple of hundred for an unstable os, when you can download one that works for nothing.
cheers.

---

### Post by vexorian on 2007-07-15
I was unable to install it! It must fail for everyone!

---

### Post by M$LOL on 2007-07-15
> **jw5801 said:**
> Lol. That openning post was almost as bad as posting on any major political party's forum with the topic "Democracy is the stupidest politcal system ever."

If you have a problem, post it here and ask what you can do to fix it. Saying the OS is stupid because you filled the partition isn't exactly helpful, and (as has been demonstrated quite obviously here) is only going to get you flamed. Linux is extremely different to Windows, it's like learning a new language, but the good thing about it is that once something breaks you can almost always fix it without resorting to a fresh install, provided you know how. And the good thing about Ubuntu is this forum! Where there is pretty much guaranteed to be someone who "know's how." All you need to do is say "This happened, how do I fix it?" and chances are someone will try to help, usually within a few hours!

As for the problem, you should be able to log in in the command line, and clear some things from there, then I'm sure someone can point you in the direction of a good command-line based partition resizer, if that's where you want to go. They'll probably even tell you exactly what you need to type in so all you need to do is copy and paste.

Exactly. If you want to whine about it, don't bother posting. If you want to get help fixing your problem, and are open to learning new things, post, but don't say things like "it's stupid because it won't work on my partition because it's full". You have no reason to say it's stupid, if you can write an OS better than it, go ahead.

---

### Post by JesterDev on 2007-07-15
I think that the issue is not whether or not ubuntu is "stupid" but more that one needs to research things more closely before attempting to install it. Linux is not for everyone, and I think that most of us already know that. It's way more complex then an everyday windows user is used too, and it takes time to learn. Life is full of challenges and learning something as complex as a new OS is no different - failing and having to reinstall is just one of these challenges that we all have faced at one point or another. 

Aggravation is one of the top most things that cause people to head back to windows. Community I believe is where ubuntu stands as one of the most noteworthy distributions around. Believe me I've used many distro's over the years and ubuntu happens to have one of the best and most helpful community's I have ever seen. 

The point? Ask and you shall receive (with great abundance in most cases) the assistance that you desire. 

To drop ubuntu just because of one simple error is in itself an ignorant act. Linux takes time and patience to learn. It will not happen over night, and will not just fall into your lap. My personal suggestion to you is to stick with it - in time you will learn the many benefits of having complete control over your OS - the tools are there, if you can't  find them, that's why we are here. :)

One last thing. If you have a PC try installing it there first (or run the live version). Get to know it, and then try it on your PS3. 

Good luck,
JesterDev

---

### Post by arashiko28 on 2007-07-15
Man, you really shouldn't be talking like that. Have you ever calculated disk space for windows? I have, sure, it does install in 3-4 GB, now, install all the updates, the good old 280MB antivirus yo need to install unless you're the only windows user virus free, the office, more updates... gee i've alredady filled 8 GB! Yikes!
It's even worse! I have a 26GB music folder. So, who on earth thinks that 2.5 GB will work for an etire OS???? Oh, and I almost forgot! The CD PACKAGE DOES INDICATES THAT NEEDS AT LEAST 4GB HDD SPACE.... Did you even read the system recquirements????

UBUNTU ROCKS!!!! 60 Days windows and virus free!!!!

---

### Post by angryfirelord on 2007-07-15
I really don't see what all the fuss is about. Just give Ubuntu more breathing room (20GB) and you'll be fine. You do need room to install applications anyway.

Now, if you don't have a bigger HDD for some reason, you can use something like Damn Small Linux, Puppy Linux, Slackware, or Debian, but they're not as noob friendly.

---

### Post by bapoumba on 2007-07-15
To the OP: I changed the thread title.

---

### Post by angryfirelord on 2007-07-15
Oh yea, it's a PS3. Whoops.

If you want to do that, I'd recommend installing Yellow Dog Linux, as it was designed with the PS3 in mind.

---

### Post by M$LOL on 2007-07-15
> **arashiko28 said:**
> Have you ever calculated disk space for windows? I have, sure, it does install in 3-4 GB,

Actually, a Vista Ultimate base install is 8GB :P

---

### Post by Jimmyfj on 2007-07-15
> **mattinthematrix said:**
> Main Entry: 1stu·pid
Pronunciation: 'stü-p&d, 'styü-
Function: adjective
Etymology: Middle French stupide, from Latin stupidus, from stupEre to be numb, be astonished -- more at TYPE
1 a : slow of mind : OBTUSE b : given to unintelligent decisions or acts : acting in an unintelligent or careless manner c : lacking intelligence or reason : BRUTISH


One installs Ubuntu from live CD, providing 2.5GB for the root partition.
One fires up the network connect for the fresh new Ubuntu, and finds that there are 97 updates. OK. Go.
With three updates remaining, the update process fails. Not enough disk space.
OK, one will just reboot live CD and extend the root partition to make more room.
Nope, can't do that. OK, back to hard disk installation to see about making a partition image.
Nope. Can't log-in to Ubuntu at all because of lack of disk space.

Can't log-in! It filled up the disk without warning, then is incapable of even logging in to do something about it!

This is absolutely absurd. No wonder linux can't break in as a desktop OS.

I've tried numerous distros, and always end up back on Windows, as crappy as it is, and as much as I hate proprietary software. Why?

Because it works. Because it doesn't require one to have written machine code to be able to anticipate the bizarre assumptions of the OS.

Lack of disk space should not lock one out of the system. It's idiotic.
</rant>

I've seen this kind of threads many times, and not just in this community, about how skilled Windows users seem to assume that Linux is just like Windows - Thank God it's not. 

"Oh - I'll just partition the disk this way. That ought to do the trick. It usually does so in Windows!"

To quote you even further:

"I've tried numerous distros, and always end up back on Windows, as crappy as it is, and as much as I hate proprietary software. Why?"

Just exactly WHAT is it in Windows that "Just works"? The amount of drivers and service packs? Anti this and that? Just exactly what is it?

I'll prefer GNU/Linux over any Windows version ever written / ever to release.

---

### Post by mattinthematrix on 2007-07-15
1.) I very intentionally used the original provocative thread title, and I accomplished my purpose. I've drawn a lot of attention to a very major error (which I do not believe is exclusive to the PS3 platform), and hopefully inspired a bunch of people to work a little harder at making a pretty good distro into a great distro that can be used in the mass market.

2.) I'm passionate about this becuase I love linux. I've administered LAMP servers for years. I will never ever serve a web page or a database from a MS box. I have installed many OS's many times, including at least 7 by MS, at least 6 linux distros, and 2 BSDs. I really want desktop linux, and I really want it to be for everyone.

3.) Most of you aren't getting the fact that this has nothing to do with the partition size being so smalll. It has to do with the partition being FULL. If I had made the partition 200GB and filled it, it seems I would have had the same problem -- being locked out of the system. If I can, I'm going to rename the thread to "Can't log-in when root filesystem is full"

4.) The comparison to Windows installation requirements, and especially vista (which I do not yet endorse), is completely irrelevant. I don't care if Windows requires 600GB to install. The installer will tell you this, and it will actually work when you give it that much. And when you fill that 600GB, you will still be able to log in so that you can delete unnessary files or take other actions to make your system usable again.

---

### Post by bapoumba on 2007-07-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/gdm/+bug/35217](https://bugs.launchpad.net/gdm/+bug/35217) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **mattinthematrix said:**
> 
3.) Most of you aren't getting the fact that this has nothing to do with the partition size being so smalll. It has to do with the partition being FULL. If I had made the partition 200GB and filled it, it seems I would have had the same problem -- being locked out of the system. If I can, I'm going to rename the thread to "Can't log-in when root filesystem is full"

I'm not sure members have access to the main thread title. Please let me know.

The login problem when a partition is full is known.
Please check the bug report. It's also been reported upstream and looks its going to be implemented for gutsy.
[https://wiki.ubuntu.com/BootLoginWithFullFilesystem]("https://wiki.ubuntu.com/BootLoginWithFullFilesystem")
[http://ubuntuforums.org/showthread.php?t=409822]("http://ubuntuforums.org/showthread.php?t=409822")

---

### Post by darrenm on 2007-07-15
> **mattinthematrix said:**
> 3.) Most of you aren't getting the fact that this has nothing to do with the partition size being so smalll. It has to do with the partition being FULL. If I had made the partition 200GB and filled it, it seems I would have had the same problem -- being locked out of the system. If I can, I'm going to rename the thread to "Can't log-in when root filesystem is full"

I got it. And this will be the third time that I have posted it didnt lock you out of the system. The GUI wouldnt let you log in because you had filled up the hard disk. You could have booted into the command line and made some space. I don't get the complication?

---

### Post by angryfirelord on 2007-07-15
> **mattinthematrix said:**
> 1.) I very intentionally used the original provocative thread title, and I accomplished my purpose. I've drawn a lot of attention to a very major error (which I do not believe is exclusive to the PS3 platform), and hopefully inspired a bunch of people to work a little harder at making a pretty good distro into a great distro that can be used in the mass market.

2.) I'm passionate about this becuase I love linux. I've administered LAMP servers for years. I will never ever serve a web page or a database from a MS box. I have installed many OS's many times, including at least 7 by MS, at least 6 linux distros, and 2 BSDs. I really want desktop linux, and I really want it to be for everyone.

3.) Most of you aren't getting the fact that this has nothing to do with the partition size being so smalll. It has to do with the partition being FULL. If I had made the partition 200GB and filled it, it seems I would have had the same problem -- being locked out of the system. If I can, I'm going to rename the thread to "Can't log-in when root filesystem is full"

4.) The comparison to Windows installation requirements, and especially vista (which I do not yet endorse), is completely irrelevant. I don't care if Windows requires 600GB to install. The installer will tell you this, and it will actually work when you give it that much. And when you fill that 600GB, you will still be able to log in so that you can delete unnessary files or take other actions to make your system usable again.

1) You used the original title as flame bait. Of course it's going to draw users.
2) It's not really that linux isn't "desktop ready", rather it's trying to get linux as an alternative to windows. Dell has done that somewhat, but I can assure you, linux has made great strides into easy usage (like ubuntu and pclinuxos).
3) It's full BECAUSE it's small. Most people install an OS onto a much larger partiton. Just expand it and that'll fix your problem. Or get Yellow Dog, as I stated before.
4) How do you know if it'll work? Did you try it? The reason for bringing that up was to show you that Windows Vista has an insane amount of disk space requirement, whereas Ubuntu doesn't even need that much.

Also, did you try hitting Ctrl+Alt+F1? I think the problem here is you're giving up too easily.

---

### Post by insane_alien on 2007-07-15
> 
4.) The comparison to Windows installation requirements, and especially vista (which I do not yet endorse), is completely irrelevant. I don't care if Windows requires 600GB to install. The installer will tell you this, and it will actually work when you give it that much. And when you fill that 600GB, you will still be able to log in so that you can delete unnessary files or take other actions to make your system usable again.

well, you see, it did actually install and function didn't it. it was only when you downloaded files to the partition and filled that things started to go wrong. the login thing was known long before you showed up and a fix is on its way. besides, the average user probably has a bigger drive.80GB is very very common nowadays.

---

### Post by dptxp on 2007-07-16
> mattinthematrix;3024612
> 1.) I very intentionally used the original provocative thread title, and I accomplished my purpose. I've drawn a lot of attention to a very major error (which I do not believe is exclusive to the PS3 platform), and hopefully inspired a bunch of people to work a little harder at making a pretty good distro into a great distro that can be used in the mass market.

END OF QUOTE.

I do not think that anyone in the forums should help such persons who try to be too smart. The help provided in the forums here are done in full sincerity. I find this method very improper.
And I do not think that crying WOLF is a great idea.

---

### Post by M$LOL on 2007-07-16
> **mattinthematrix said:**
> 1.) I very intentionally used the original provocative thread title, and I accomplished my purpose. I've drawn a lot of attention to a very major error
That's not a major error.
> **mattinthematrix said:**
> 
4.) The comparison to Windows installation requirements, and especially vista (which I do not yet endorse), is completely irrelevant. I don't care if Windows requires 600GB to install. The installer will tell you this, and it will actually work when you give it that much. And when you fill that 600GB, you will still be able to log in so that you can delete unnessary files or take other actions to make your system usable again.

Go use Windows then if it's so much better.

---

### Post by arashiko28 on 2007-07-16
Well now that you insist in doing it on a 2.5GB partition even if the CD cover says it needs, 4, i recommend you Xubuntu, it has all the characteristics of Ubuntu, and needs as little as 1.5. I Installed it my self, and after al the updates and adding the most of the programs I really need, took only 2.2GB. It is a much simpler version, but, goes with little HDD space and low ram, only needs 128mb, 197 for install.
Good Luck

---

### Post by mattinthematrix on 2007-07-19
> **M$LOL said:**
> That's not a major error.


Not being able to log into an operating system at all is minor?

Have you read your own sig? Talk about being killed by the common cold, this is more like being killed by the common sandwich.  A cold is a bug, managing disk space is one of the primary functions of an operating system.

And for the hundredth time, I don't think Windows is the best OS. Neither is Mac OS, and neither is Ubuntu.

But Ubuntu is getting pretty darn close, were it not for issues like these.

---

### Post by angryfirelord on 2007-07-19
> **mattinthematrix said:**
> Not being able to log into an operating system at all is minor?

Have you read your own sig? Talk about being killed by the common cold, this is more like being killed by the common sandwich.  A cold is a bug, managing disk space is one of the primary functions of an operating system.

And for the hundredth time, I don't think Windows is the best OS. Neither is Mac OS, and neither is Ubuntu.

But Ubuntu is getting pretty darn close, were it not for issues like these.
So are you going to put Ubuntu onto a larger partition?

---

### Post by jw5801 on 2007-07-19
> **mattinthematrix said:**
> Not being able to log into an operating system at all is minor?

Have you read your own sig? Talk about being killed by the common cold, this is more like being killed by the common sandwich.  A cold is a bug, managing disk space is one of the primary functions of an operating system.

And for the hundredth time, I don't think Windows is the best OS. Neither is Mac OS, and neither is Ubuntu.

But Ubuntu is getting pretty darn close, were it not for issues like these.

But you probably can log into the operating system... just not through a graphical interface, which by the way you still haven't told us if you tried, all you continue to do is complain about how fundamentally flawed Ubuntu is. You've already been told that this is a known issue that is being worked on and has been fixed for the next release. Seriously, if you have something constructive to contribute then go ahead, but this isn't constructive and as much as you may thing you're "motivating" the developers, you're not. They don't get paid to do this, they do it in their own free time, and they've already fixed the bug you're complaining about! If it's that big an issue then reinstall using the gutsy beta! If you really want to play around graphically then chuck in the liveCD and you should be able to mount the partition using that, and then delete some things so that you can get back on.

---

### Post by darrenm on 2007-07-20
I've deleted the /usr directory and now I can't log in. Ubuntu is fatally flawed and should still work if the /usr directory is deleted.

---

### Post by jw5801 on 2007-07-20
^^ not helping :p

---

### Post by darrenm on 2007-07-20
Sorry. I really shouldn't.

---

### Post by jw5801 on 2007-07-20
haha 'sall good, I laughed.

---

### Post by M$LOL on 2007-07-22
> **mattinthematrix said:**
> Not being able to log into an operating system at all is minor?

It's minor when you do the exact opposite of what both common sense and the requirements tell you, that 2.5 gigs isn't enough.
> **mattinthematrix said:**
> 
Have you read your own sig? Talk about being killed by the common cold, this is more like being killed by the common sandwich.  A cold is a bug, managing disk space is one of the primary functions of an operating system.

No, I haven't read it at all, I just typed randomly while blindfolded and hoped something came out that I wouldn't get arrested for.
> **mattinthematrix said:**
> 
And for the hundredth time, I don't think Windows is the best OS. Neither is Mac OS, and neither is Ubuntu.


So, what then, BSD or something?

---

