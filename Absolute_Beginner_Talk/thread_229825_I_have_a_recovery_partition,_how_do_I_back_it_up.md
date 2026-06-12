---
title: "I have a recovery partition, how do I back it up?"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-08-05
Here's my story: So first I bought an HP desktop preinstalled with windows xp home sp1, I updated it to sp2, then, installed ubuntu 5.10 over windows, then installed ubuntu 6.06 over 5.10, then installed windows xp home sp1 over ubuntu from 6 cd's labeled "HP Recovery" (which I don't remember how I got them, because they don't look official - their names are written with a red sharpie marker), then updated that to sp2.  Just to note a fact, when I reinstalled windows from those recovery discs, a recovery partition was made in my hard drive (D:), with a size of 4.18 GB.

My first question is: did that recovery partition change at all after I updated to sp2?

Second question: how would I backup this new recovery partition, or is it the same as those recovery discs?

Also to note another fact, I also had a recovery partition when I first bought my computer, but I don't know if those six recovery discs were created from that recovery partition, I just found them the other day!

---

### Post by OU812 on 2006-08-05
It sounds like the manufacturer set up your hard drive - with a recovery partition - and ghosted the whole thing. The recovery discs are probably just the ghost image of the drive - fresh from the factory - spanned on several disks. So whenever you use those disks you are putting back the disk image created when your drive was first set up by the factory.

You may want to get win set up the way you want and ghost it. This way when you need to restore that image, everything is the way want it. That's what I did (I have an emachines that came with two recovery cds. One cd contains the drivers and the other cd contains everything else. They are really just a ghost image of the drive.)

john

P.S. Perhaps those homemade cds are backups that you made?

---

### Post by user1397 on 2006-08-05
> **OU812 said:**
> You may want to get win set up the way you want and ghost it. This way when you need to restore that image, everything is the way want it. ok, thanks for the reply, but I don't really know how to do that.  could you guide me through please?
> **OU812 said:**
> P.S. Perhaps those homemade cds are backups that you made?the thing is, i don't remember making them!  maybe somebody else did...oh well, at least they work!

---

### Post by OU812 on 2006-08-05
What I mean is this - I used the ghost cds to restore the drive to the factory installations (I did this a few times because of viruses and spyware). But the ghost image was so old it had sp1, not to mention a ton of software I din't need. So after the last time I restored the ghost image, I installed all of my favorite apps and drivers for the new hardware. Then I deleted all of the junk that came preinstalled (like aol and compuserve). I configured it with my favorite settings - such as turning off autoplay. I did all available updates. Installed antivirus, etc. Then I ran some programs to clean out temp files, the registry, etc; I did  defrag, scandisk, etc. Then I ghosted my updated drive to an image file on an external drive (I couldn't get the cd or dvd option working with ghost and I didn't want to create a partition on the win drive for the ghost image; so ghosting to the usb drive made the most sense to me). Now when I need to restore a disc image (for whatever reason), it is far more current than the one from the factory (But it does take a lot longer to reimage from the usb drive than it did from the cds).

john

P.S. If this is not clear, give me some specifics so I can be of more help.

---

### Post by user1397 on 2006-08-05
> **OU812 said:**
> What I mean is this - I used the ghost cds to restore the drive to the factory installations (I did this a few times because of viruses and spyware). But the ghost image was so old it had sp1, not to mention a ton of software I din't need. So after the last time I restored the ghost image, I installed all of my favorite apps and drivers for the new hardware. Then I deleted all of the junk that came preinstalled (like aol and compuserve). I configured it with my favorite settings - such as turning off autoplay. I did all available updates. Installed antivirus, etc. Then I ran some programs to clean out temp files, the registry, etc; I did  defrag, scandisk, etc. Then I ghosted my updated drive to an image file on an external drive (I couldn't get the cd or dvd option working with ghost and I didn't want to create a partition on the win drive for the ghost image; so ghosting to the usb drive made the most sense to me). Now when I need to restore a disc image (for whatever reason), it is far more current than the one from the factory (But it does take a lot longer to reimage from the usb drive than it did from the cds).

john

P.S. If this is not clear, give me some specifics so I can be of more help.thanks for your time man, actually, i would like to do exactly what you have done--ghost my new and improved windows.  so the only thing keeping me from doing this? ---i have no idea how to ghost a partition!!! (could you please help me on that???)

---

### Post by user1397 on 2006-08-05
bump

---

### Post by user1397 on 2006-08-05
i was tortured into doing this...bump

---

### Post by greenstar on 2006-08-05
I doubt that anyone is going to guide you through Norton Ghost step by step on these forums, as this is for Ubuntu support. 

Norton Ghost is commercial software. Ubuntu is open source as well as being community supported and developed. This works because Ubuntu gives to the community and the community gives back. Money needn't change hands in the Ubuntu scenario. With commercial software, the software companies get all of the money and generally do not give anything back to the community. Under this model, there is no incentive or benefit for other users to support commercial software without compensation. Norton/Symantec would be laughing all the way to the bank. This is basically why you won't get much help with commercial software here on the Ubuntu forums. There are many of us here on Ubuntu who make a living supporting Windows users & software. This is how we pay our bills. Many of these same people also support Ubuntu through the forums, mailing lists, etc. and do so for free. I imagine that a fair number of us also provide paid on-site support for Ubuntu users in our area, as do I.

That being said, I can help you with some links from [this google search]("http://www.ccs.neu.edu/home/donghui/howto/backup_restore_using_ghost.txt").

[This]("http://www.ccs.neu.edu/home/donghui/howto/backup_restore_using_ghost.txt") looks like a good place to start.

[This]("http://www.duxcw.com/digest/Howto/hd/cpyhd/index.html") one looks quite promising.

[This link]("http://www.softpanorama.org/Unixification/norton_ghost.shtml") might also help.


Good luck to you.

Greenstar

---

### Post by user1397 on 2006-08-05
> **greenstar said:**
> I doubt that anyone is going to guide you through Norton Ghost step by step on these forums, as this is for Ubuntu support. 

Norton Ghost is commercial software. Ubuntu is open source as well as being community supported and developed. This works because Ubuntu gives to the community and the community gives back. Money needn't change hands in the Ubuntu scenario. With commercial software, the software companies get all of the money and generally do not give anything back to the community. Under this model, there is no incentive or benefit for other users to support commercial software without compensation. Norton/Symantec would be laughing all the way to the bank. This is basically why you won't get much help with commercial software here on the Ubuntu forums. There are many of us here on Ubuntu who make a living supporting Windows users & software. This is how we pay our bills. Many of these same people also support Ubuntu through the forums, mailing lists, etc. and do so for free. I imagine that a fair number of us also provide paid on-site support for Ubuntu users in our area, as do I.

That being said, I can help you with some links from [this google search]("http://www.ccs.neu.edu/home/donghui/howto/backup_restore_using_ghost.txt").

[This]("http://www.ccs.neu.edu/home/donghui/howto/backup_restore_using_ghost.txt") looks like a good place to start.

[This]("http://www.duxcw.com/digest/Howto/hd/cpyhd/index.html") one looks quite promising.

[This link]("http://www.softpanorama.org/Unixification/norton_ghost.shtml") might also help.


Good luck to you.

Greenstarokay i thank you for your help, but i just want to clear some things up.  

first of all, i didn't even know norton ghost existed until you mentioned it, and i don't have it anyway, so I wasn't asking for support on that product, i thought i just needed some help with backing up my system.  

Anyway, this forum is made up mostly of ex-windows converts and dual-booters, so people can expect a lot of windows questions here.  Plus, a windowws question is almost always directly related to a linux question or object.  For example, i wanted to know how to backup my system, so that i could have a good backup of windows, and then i was going to repartition my hard drive and install edgy eft on the unallocated space.

---

### Post by greenstar on 2006-08-06
> **erik1397 said:**
> okay i thank you for your help
You're welcome. I try to do what I can.

> **erik1397 said:**
> first of all, i didn't even know norton ghost existed until you mentioned it, and i don't have it anyway, so I wasn't asking for support on that product, i thought i just needed some help with backing up my system. 

Using "first of all..." implies that you have both cause & authority to correct me, and that you have multiple reasons to do so. I disagree, as I didn't say anything that was incorrect. If I misinterpreted your words then let me apologize.

> **erik1397 said:**
> Anyway, this forum is made up mostly of ex-windows converts and dual-booters, so people can expect a lot of windows questions here. Plus, a windowws question is almost always directly related to a linux question or object. For example, i wanted to know how to backup my system, so that i could have a good backup of windows, and then i was going to repartition my hard drive and install edgy eft on the unallocated space.

Ex-Windows users or not, we don't expect lots of Windows questions here. Note that this thread has 66 views & only 8 posts by 3 people, yourself included. In less than 24 hours, 66 people have looked and only 2 stopped to help. That's probably because this isn't a Windows support forum. I'm sure that Canonical doesn't host the forums so that Windows users can get help with Windows. I'm equally sure they don't pay for bandwidth so that Windows users can get help with Windows. Do you see what I mean: your statement seems to imply that Canonical & Mark Shuttleworth should set aside some of their resources for Windows support issues.



Moving on...
---------------------------------------------------

Going back to the beginning of the thread, I see that OU812 introduced the term "ghost" into the thread. I *just* realized that you probably don't know the finer points of the differences between backup methods & such so I'll try to help.(sorry I was slow on the uptake here) "Ghosting" a partiton or disc is what you do with Norton's commercial product. Other methods & products call this imaging or dumping, depending on the software/method you use. The terms imaging and dumping are general terms and do not apply to any specific product the way that ghosting is used in conjunction with Norton/Symantec's disk imaging software.

I'm going to address your first post now, since I see that OU812 didn't really clear things up for you and, thus far, neither have I.

You have a set of discs which together contain an image of your entire hard disk in its factory condition. This image seems to include the Windows partition & the recovery partition.

> **erik1397 said:**
> My first question is: did that recovery partition change at all after I updated to sp2? 
Nope, it's just something to restore your disk to its factory condition. It doesn't change or update, HP figures that's on you.

> **erik1397 said:**
>  Second question: how would I backup this new recovery partition, or is it the same as those recovery discs?
Neither, it isn't the same as the recovery discs, but it is *part* of the contents of the disc set. Therefore, no need to back up the recovery partition.

However, when I was still using windows, I did backups in 2 stages:

  1. Back up personal data: burn pictures, documents, etc., onto CD or DVD, or you could use an external hard drive. Verify contents after burning... this is your data. If you ask me, this is what backup is for.

  2. Back up Windows. I rarely did this, preferring a clean, up-to-date installation periodically. However I did image the disc a few times so I'd have a copy of my Windows installation that I could get up & running in a short while. Each time I upgraded, changed or added new hardware the image became useless, so soon I quit doing it entirely. You might want to check out [nLite]("http://www.nliteos.com/"), [Autopatcher]("http://www.autopatcher.com/"), & [Autostreamer]("http://www.neowin.net/forum/index.php?showtopic=223562").

> **erik1397 said:**
> i was going to repartition my hard drive and install edgy eft on the unallocated space.
I would advise you to stick with dapper for now... edgy is going to be rough for some time to come. You'll sit down one day and something will be broken because the developers are swapping out packages which may have different dependencies, etc. I started using Dapper in April, 2 months before official release and sometimes things just broke. I was willing to take that chance because I've been a full-time Ubuntu user since Hoary, and I was familiar enough with it to manage the bumps. I wouldn't advise that for a first-timer. It might turn you off to Ubuntu. Wait until Edgy is officially released.
 

P.S. I saw your AVI to DVD how to, and I'm going to try it out in the next few days. It looks good.

---

### Post by user1397 on 2006-08-06
> **greenstar said:**
> Using "first of all..." implies that you have both cause & authority to correct me, and that you have multiple reasons to do so. I disagree, as I didn't say anything that was incorrect. If I misinterpreted your words then let me apologize.okay i admit i was kinda harsh, and i did mess up with the "first of all".  I was going to type "second of all" but it came out as "anyway".

> **greenstar said:**
> Ex-Windows users or not, we don't expect lots of Windows questions here. Note that this thread has 66 views & only 8 posts by 3 people, yourself included. In less than 24 hours, 66 people have looked and only 2 stopped to help. That's probably because this isn't a Windows support forum. I'm sure that Canonical doesn't host the forums so that Windows users can get help with Windows. I'm equally sure they don't pay for bandwidth so that Windows users can get help with Windows. Do you see what I mean: your statement seems to imply that Canonical & Mark Shuttleworth should set aside some of their resources for Windows support issues.well actually, i still disagree with you on this one.  since i use ubuntu, i am not a windows-only user, just to clear things up.  My title does not imply any windows relation, so views don't really matter, responses do.  And a lot of people here are fine with answering windows questions.  For example, aysiu himself has stated in one of his _[essays]("http://www.psychocats.net/essays/linuxdesktopmyth.php")_ :
> **aysiu]Ubuntuforums.org is an incredible mix of expert, intermediate, and novice users who subscribe to Ubuntu's philosophy of "Humanity Toward Others." They can answer all my Linux questions, and **they can usually answer my Windows and Mac OS X questions as well**.[/quote]And no I don't imply that Shuttleworth should set aside resources for windows support questions.  i just think its alright to have a helping hand when you need some help doing something on windows, since almost everybody here uses windows too, and therefore there are many windows experts who are willing to help.



[quote=greenstar said:**
>  Moving on...
---------------------------------------------------

Going back to the beginning of the thread, I see that OU812 introduced the term "ghost" into the thread. I *just* realized that you probably don't know the finer points of the differences between backup methods & such so I'll try to help.(sorry I was slow on the uptake here) "Ghosting" a partiton or disc is what you do with Norton's commercial product. Other methods & products call this imaging or dumping, depending on the software/method you use. The terms imaging and dumping are general terms and do not apply to any specific product the way that ghosting is used in conjunction with Norton/Symantec's disk imaging software.

I'm going to address your first post now, since I see that OU812 didn't really clear things up for you and, thus far, neither have I.

You have a set of discs which together contain an image of your entire hard disk in its factory condition. This image seems to include the Windows partition & the recovery partition.


Nope, it's just something to restore your disk to its factory condition. It doesn't change or update, HP figures that's on you.


Neither, it isn't the same as the recovery discs, but it is *part* of the contents of the disc set. Therefore, no need to back up the recovery partition.

However, when I was still using windows, I did backups in 2 stages:

  1. Back up personal data: burn pictures, documents, etc., onto CD or DVD, or you could use an external hard drive. Verify contents after burning... this is your data. If you ask me, this is what backup is for.

  2. Back up Windows. I rarely did this, preferring a clean, up-to-date installation periodically. However I did image the disc a few times so I'd have a copy of my Windows installation that I could get up & running in a short while. Each time I upgraded, changed or added new hardware the image became useless, so soon I quit doing it entirely. You might want to check out [nLite]("http://www.nliteos.com/"), [Autopatcher]("http://www.autopatcher.com/"), & [Autostreamer]("http://www.neowin.net/forum/index.php?showtopic=223562").Okay, thanks a lot for all that info and help, I really appreciate it.


> **greenstar said:**
>  I would advise you to stick with dapper for now... edgy is going to be rough for some time to come. You'll sit down one day and something will be broken because the developers are swapping out packages which may have different dependencies, etc. I started using Dapper in April, 2 months before official release and sometimes things just broke. I was willing to take that chance because I've been a full-time Ubuntu user since Hoary, and I was familiar enough with it to manage the bumps. I wouldn't advise that for a first-timer. It might turn you off to Ubuntu. Wait until Edgy is officially released.actually, i'm not a first timer, i have been using ubuntu since march 2006, and i have learned quite a few things over the last few months.  but, i have decided to install dapper afterall, partly because i thought i wanted a stable system and partly because i was too lazy to download and burn the edgy iso :cool:.
 

> **greenstar said:**
>  P.S. I saw your AVI to DVD how to, and I'm going to try it out in the next few days. It looks good.go ahead and try it!  it is quite a beginner-like tutorial, i have not mastered the commands of the tovid program yet, but it does the job.

---

### Post by greenstar on 2006-08-06
I'm glad this difference of viewpoints didn't degrade into a flame war. It's refreshing to be able to discuss such a thing in a reasonable manner, as we have.

> **erik1397 said:**
> well actually, i still disagree with you on this one. <break> And a lot of people here are fine with answering windows questions. And no I don't imply that Shuttleworth should set aside resources for windows support questions.  i just think its alright to have a helping hand when you need some help doing something on windows, since almost everybody here used it before, and therefore there are many experts who are willing to help.

Hmmm... hadn't quite thought about it like that... Something to think about. Ever since I embraced open source a couple of years ago, and then Ubuntu in spring of 2005, I've come to love the freedom it gives me. As a result, I've come to have a strong distaste for commercial software. I was just thinking, isn't there something ironic about helping with commercial OSes on the Ubuntu forum?:wink:

You're right about the community here, I learn something every time I'm on the forums. Sometimes the lesson has nothing to do with software, but rather dealing with others in a respectful, kind way that embodies the Ubuntu spirit. Usually I find that I can stand some improvement. :D Like tonight.

> **erik1397 said:**
> actually, i'm not a first timer, i have been using ubuntu since march 2006

Duh, of course not, or you wouldn't have a HOWTO, would you?:oops: *smacks forehead with palm*
  
> **erik1397 said:**
> go ahead and try it!  it is quite a beginner-like tutorial, i have not mastered the commands of the tovid program yet, but it does the job.

I'd never heard of tovid before. Just today one of my local customers was asking me about converting video from AVI to a format that can be used on blogs like myspace, so I was searching for info on that tonight when I found your HOWTO. Not exactly what my customer needs, but I'd like to check it out for myself, as I have some videos hanging around the hard disk that need to be burned.

Since "betterment of self = betterment of community" is part of or at least fitting with the concept of Ubuntu, I'll make the effort to better myself and therefore my community. To this end, if you have more questions, I'll do my best to help, and I'll do so more kindly.

Greenstar

---

### Post by user1397 on 2006-08-06
> **greenstar said:**
> I'm glad this difference of viewpoints didn't degrade into a flame war. It's refreshing to be able to discuss such a thing in a reasonable manner, as we have.it is indeed.



> **greenstar said:**
>  Since "betterment of self = betterment of community" is part of or at least fitting with the concept of Ubuntu, I'll make the effort to better myself and therefore my community. To this end, if you have more questions, I'll do my best to help, and I'll do so more kindly.

Greenstari thank you again for your help and your willingness to help, but i think you've hit the spot with those three links you gave me. ;)

---

### Post by djsroknrol on 2006-08-06
Erik1397...

It's clear you're dual booting..regardless of what OS it is (granted, it's mostly a win problem), and you are a senior staff member..help should always be there...'nuff said....

> My first question is: did that recovery partition change at all after I updated to sp2?

Second question: how would I backup this new recovery partition, or is it the same as those recovery discs?


#1) No, it shouldn't have changed, unless you changed it yourself

#2) The discs should load back the recovery partition that's already there. I also think, but could be wrong, that Partimage could be used on that recovery partition to revive your current partition. Chime in anyone if I'm wrong...

---

### Post by user1397 on 2006-08-06
> **djsroknrol said:**
> Erik1397...

It's clear you're dual booting..regardless of what OS it is (granted, it's mostly a win problem), and you are a senior staff member..help should always be there...'nuff said....thanks for your concern.  i am dual-booting windows xp home and ubuntu dapper.  i am not a senior staff member, however, i'm just part of the three-man green team, which cycles every 3 months or so, and who are devoted to helping out beginners the most.



> **greenstar said:**
>  #1) No, it shouldn't have changed, unless you changed it yourself
#2) The discs should load back the recovery partition that's already there. I also think, but could be wrong, that Partimage could be used on that recovery partition to revive your current partition. Chime in anyone if I'm wrong...i will look into Partimage, thanks for your suggestion

---

### Post by user1397 on 2006-09-04
okay i have been slacking on this subject for a while, so i got 2 new questions:

1) is it possible to copy my recovery partition onto a blank DVD? (DVD+R)

2) is there any other way of backing up a recovery partition without the use of some 3rd party software?

3) and as djsroknrol has mentioned, can PartImage be used for backing up my recovery partition? (i'm assuming that i would have to use that program inside ubuntu, right?)

---

### Post by user1397 on 2006-09-04
well w/e.  i used the HP live chat support system and asked if I could make a DVD recovery disc of my current recovery partition, and they said that it can only be made once.  since i already have the recovery cd's, i can't do this.  nuff said.  well w/e, im okay with those cd's i guess........

---

### Post by neogeo on 2006-09-04
Vendors such as Dell and Gateway are no longer required to to give you an original XP install disk !!!!
XP is installed on the hard drive along with a recovery program.
The first time the computer is turned on the recovery program starts up and guides you thru creating the backup cds. Someone must have done this for you as I'm sure you would have remembered doing it.Takes an hour or so. It also creates a hidden partition on your C: drive of about 5 gig on which another image of xp put. It is the same image as you have on the cds.
You can recover your original system from the hidden partition in about a 1/2 hour.
Or from the disks but it takes longer.
If your computer has usb 2 definitily try norton ghost. Get an external hard drive enclosure and a new drive and use ghost to do up to date images of your C: drive unlike the recovery system you have now.
I can recover about 30 gig in about 40 min.
Dont lose the disks or damage them. Make copies of them and test them. They are your OS!!!! The hard drive will problably pack up in a couple of years.
Hope this helps.

---

### Post by user1397 on 2006-09-09
> **neogeo said:**
> Dont lose the disks or damage them. Make copies of them and test them. They are your OS!!!! The hard drive will problably pack up in a couple of years.
Hope this helps.arite thanks for the advice.  do you think i would be able to copy those 6 discs into one dvd?

---

### Post by user1397 on 2006-09-16
umm im thinking about this whole backup thing again (yes, i am wishy-washy)

i read this guide by aysiu ([http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage))

and now that i think about it, couldn't i use that program to make dvd backup of my recovery partition?  (i wouldn't tell the HP guys...8-))

the thing is, i only have an ubuntu live dvd right now, so i couldn't do this with the live dvd, since i only have one dvd drive.

so then i thought, if my recovery partition weren't mounted, then i wouldn't even need the live cd, i could just do it from inside ubuntu, right?

---

### Post by user1397 on 2006-09-16
just curious about something....

in places > computer, i see my "HP_RECOVERY" partition, and its unmounted.  if i just popped in my blank dvd, and the nautilus CD?DVD creator came up, could i just right-click on recovery partition, copy, and paste it into the cd/dvd creator?

---

### Post by user1397 on 2006-09-16
bump

---

### Post by user1397 on 2006-09-16
bump :biggrin:

---

### Post by user1397 on 2006-09-17
sorry....bump

---

### Post by user1397 on 2006-09-18
well i noticed that i cannot do that simple copy/paste thing, but what about my previous idea?  the one about using partimage in ubuntu to backup my recovery partition to a blank dvd?

---

