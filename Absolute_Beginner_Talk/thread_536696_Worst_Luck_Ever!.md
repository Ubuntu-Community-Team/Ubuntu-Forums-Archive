---
title: "Worst Luck Ever!"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by c3genesis on 2007-08-28
Okay, its official.  I am the most UN-lucky person on the planet.  First, I buy a toshiba sat. with the sole intentions of creating a dual boot with vista and ubuntu fiesty.  One problem after another happens, after fixing something other things go wrong and then to top it off, i had some error partitioning the hd and damaged some sectors, so I took it back pretending that the computer was fine and i just didnt like vista, which is the truth.  I have now bought an hp pavilion dv2000 special edition(verve), not much different just a bigger battery and a prettier lid.  Anyways, the first thing I do is put in the live cd.  I get the error: .

So I get on here and read a few threads, and it seems to be an error that shows up alot for alot of different problems.  So before I actually ASK for help I figure I should try the alt text boot cd.  I put it in and it runs fine til the partitioning comes up.  Easy fix right,  I just use my windows partitioner and shrink the ntfs drive and boot with the alt text boot cd again and i get to the partitioner, create a 70 gb primary ext3 partition(with boot flagging turned on) at the beginning of the hd, a 2gb primary swap space partition at the beginning after ext 3, sounds right so far?  i finish it and its all successful then i get to the select and install software and it stops at 6% of course theres an error saying to try again or skip it, so i looked up some threads and decided to skip it, installed the grub boot thingy and finished, rebooted, and tried some commands, including "apt-get install ubuntu-desktop" i did switch to root first btw.  and it says, media change please insert the disc labeled "ubuntu 7.04 Feisty Fawn - Release i386 in the drive /cdrom/ and press enter"

I try entering my alternate cd and my live cd, nothing works, im completely lost, can anyone give me anything to go on?

---

### Post by HermanAB on 2007-08-28
If you get many errors when you try to install Linux, then you really should go and try a different distribution.  The main reason why distributions are different, is the different ways in which they do their configuration systems and wizards.

Yes, it is possible for a seasoned Linux administrator to make any version of Linux work on anything, but an ordinary mortal is much better off by shopping around a bit.  So please go and download Fedora, Suse, Mandriva (or PCLinuxOS) and Mepix and try them all.  One of those will probably install with only one, or no errors.

"If at first you don't succeed, try and try again, then give up.  It is no use being a damn fool about it." :)

Hope that helps!

Herman

---

### Post by wormser on 2007-08-28
I found a [thread]("http://ubuntuforums.org/showthread.php?t=512059&highlight=dv2000") that is a howto on your model.  It might answer some of your questions.

---

### Post by phyrewall on 2007-08-28
> **c3genesis said:**
>  <snip>....  I get the error: .

<snip> ....


Maybe it's just my end (I'm at work, there's a web filter in between Ubuntu forums and me), but is the error you're getting just " . " ?  :confused:

---

