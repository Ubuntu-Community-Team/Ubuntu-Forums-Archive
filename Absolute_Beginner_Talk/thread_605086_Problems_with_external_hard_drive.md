---
title: "Problems with external hard drive"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by 01steven on 2007-11-06
I'm a total newbie. Have been with Windows all my life until a couple of days ago.
Very excited about Ubuntu but (as expected) getting the odd problem here and there.

Ubuntu had no problem recognising a 1GB USB memory stick when I plugged it in.
But now when I plug in my external hard drive it doesn't like it (see screenshot)!

Funny thing is, when I was testing Ubuntu in the Live CD environment it found this hard drive no problem.

Before anyone asks, yes I do need the files on it so am not prepared to format it!

I don't feel too comfortable with the command line yet, so keep it simple please if you can!

Many thanks...

---

### Post by taurus on 2007-11-06
You need to boot back into windows with that external harddrive connected.  Then, shut down your windows properly or cleanly.  Don't use the hibernation or stuff like that.  Then, boot back into Ubuntu and see if you can mount that external harddrive now.

```
sudo mount -t ntfs /dev/sdb1 /media/sdb1
df -h
```

---

### Post by 01steven on 2007-11-06
Windows has gone now that I've installed Ubuntu,
Also just discovered that it won't pick up my mobile phone (Nokia N95) when plugged in via USB.

And another weird thing:
I right-click on the top panel, select 'add to panel', drag or add the 'disk mounter' icon to the panel but nothing shows.
I did this a few times earlier, then can't remember what I did, but suddenly there were like 20 of these icons up there from when I'd added them before. Not adding to the panel again now. Trying it that way brought up the same message as in the screenshot, but thought I'd mention it.

---

### Post by taurus on 2007-11-06
You must have not shut down windows cleanly with that drive plugged in.  Do you have access to another machine that runs windows?  Maybe you want to run a scan disk on that external harddrive from windows first to see if there is a problem with that drive.

---

### Post by 01steven on 2007-11-06
I could try it on my neighbour's PC.
But then what about problems I'm having with my phone? In theory I should be able to just plug it in to the PC and it should detect it (and the memory card in it),
So I'm kind of wondering if it's more to do with Ubuntu than my external devices...

---

### Post by taurus on 2007-11-06
Why don't you unplug your external harddrive.  Reboot.  Then, plug in your phone and see if it will automate.

---

### Post by 01steven on 2007-11-06
Done that, still nothing from the phone and I get the same error message when I plug in the external hard drive (which has all my important docs and which is now beginning to worry me quite considerably!)

---

### Post by NT4usB on 2007-11-06
I've been dabbling with external drives*. I have a bunch of NTFS pata, connecting via USB adapters, a couple NTFS sata, and a couple new sata formatted ext3 that I connect via a PCI adapter card.
I've used the -f force option to mount and unmount a few times with no apparent problems... well, except for one of the ext3 drives ended up corrupt and wouldn't mount.
e2fsck -b(something), lots of 'y's, and a fsck -j got all the data back.
My impression is, it's pretty hard to fubar a drive except for actually breaking the hardware or disconnecting while writing...
Mind you, I've only been at this a couple months so the sample size is pretty small.

*most are actually internal drives that live in a bag, along with several  in various external enclosures...

---

### Post by 01steven on 2007-11-06
Hi NT4usB
Thanks for your post, but this is meant to be the Absolute Beginners section.
I'm a total newbie who knows nothing about command line prompts etc. and I have to say that my experience in this section of the forum so far hasn't been a positive one.
Surely the Linux/Ubuntu community appreciates that there are more and more people like myself who are coming over from Windows.
We're up for it, we really are, but we're nervous, very unfamiliar with everything, and need a lot of hand-holding.
Surely that's what this forum is all about?
Your post baffles me. Went completely over my head.
And no doubt over the head of anyone else who's new and having this issue.

I'm sorry- I really appreciate this is free support and people are posting out of the goodness of their hearts, but this is difficult for me.
Ubuntu is being marketed as Linux for Human Beings- seems like you still need to be a bit of a geek to get it working properly.

I'm not moaning- I did know there'd be teething problems and I don't mind that, but I did just want to make the point that overly technical responses in these forums are not helpful.

OK, I'll get off my soapbox. Thanks for listening.

And hey, if there is someone out there who gets what I'm saying- please pop by and help me out why don't ya?

---

### Post by NT4usB on 2007-11-06
Well, the point I was making is although the warning message is pretty cryptic, forcing a mount is not necessarily fatal.
You want to get the drive to read, then use the force option.

The problem is, people come over from Windows after having used it for a year, or ten, or twenty and want the same level of knowledge in Linux from one post.

I don't care if you just turned Windows on and off for a year to check your email, you learned stuff along the way. Not the first time you turned it on, not the next. But you learned stuff like how to make a shortcut. How to put a CD in and click _next_. (bet you don't even read all the warnings and stuff anymore. Just click next, next, finish...)

I hate typing. I don't do it well yet I find using a terminal quicker and easier than hunting for icons or shortcuts or links, to do many things. I even use the wannabe terminal in Windows to rename, copy, and delete files and things. Way easier than finding and installing some ap just to rename a bunch of vacation pics.

Crap. I didn't even have to know how to fix the corrupt drive or have to google the answer.
When I booted, Ubuntu told me the drive was borked, and told me the commands to try and fix it. It also told me it might trash the data. Got my 300 gigs back.

Yes. this is the beginners forum. 500 to 800 *beginners* viewing at any one time, day or night. 
Thousands and tens of thousands of questions posted. Nearly every question asked and answered hundreds, maybe thousands of times.

There really aren't that many **new** problems, just new visitors.
Your phone gets about a hundred hits on [this site alone]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+%22Nokia+N95%22&btnG=Google+Search")
A couple hundred thousand on all of [google](http://www.google.com/search?hl=en&q=%22Nokia+N95%22+%2Bubuntu+-%22for+sale%22&btnG=Search")

---

### Post by 01steven on 2007-11-07
All very well and good, but I still don't have the faintest clue how to solve my problem.
Any one care to help me please?

---

### Post by natehatewindows on 2007-11-07
ok ill tell you what i did in this situation, if you read the notice you got it tells you how,,,...here is step-by-step.

1. plug in  your hardrive
2. if you get that message again just click "OK"
3. open a terminal Applications>Accessories>Terminal
4. Copy and paste the folowing line in and hit enter on your key board.

mount -t ntfs-3g /dev/sdb1/media/disk/ -o force

I did this and i dodnt lose any data so i dont think you will either.....but if you do sorry. 
I should explain the reason your getting this message. Last time you had this hard drive plugged into windows you did not "eject" is safely. Chances are you just unplugged the cable from you usb port, you are never supposed to to that. In windows there is a option ( i think if you right click the hard drive) and is "safely remove hardware". becasue you didnt do this windows did not "finish" with the hard drive so in very simple term the hard drive still thinks its on windows (kinda but that super simple and just and big KINDA). So from now on when you unplug things (your hard drive, phone...anything you store data on) always eject, unmount or safely remove the device weather in ubuntu or windows. 

Also i have a question for you, when you said windows is gone do you mean you reformatted your whole HD or can you just not get it to boot? im not sure how much you really know about computers but i hope you know that its very easy to have both windows and ubuntu (or anyother linux) on the same machine. Since you are so new to ubuntu it might be a good idea so you can learn as you go.....but on the other hand you will learn much fast if you only have ubuntu. Chances are you will learn to love ubuntu...it really is much better that windows, faster, more stable and more apps (and they are free too ;) your just going to need to learn more. Also you will learn the command line is not very hard and very handy to use. :) good luck and remember to have fun!

---

### Post by 01steven on 2007-11-07
I tried the line you mentioned in the terminal, but all I got was this this:

steven@steven-laptop:~$ mount -t ntfs-3g /dev/sdb1/media/disk/ -o force
mount: only root can do that
steven@steven-laptop:~$

---

### Post by taurus on 2007-11-07
```
**sudo** mount -t ntfs-3g /dev/sdb1 /media/disk -o force
```

---

### Post by 01steven on 2007-11-07
Woohoo!!!!!

Taurus I love you! (my star sign actually).

My wife was starting to panic there- a few years of photos on there (baby growing up etc,)

Better go and back files up somewhere else to be on the safe side..


Thanks again- you're a life-saver!

---

### Post by taurus on 2007-11-07
> **01steven said:**
> Woohoo!!!!!

Taurus I love you! (my star sign actually).

Easy there, tiger.

> My wife was starting to panic there- a few years of photos on there (baby growing up etc,)

Better go and back files up somewhere else to be on the safe side..

Thanks again- you're a life-saver!

It's time to burn those onto a DVD or DVDs.  ;-)

---

