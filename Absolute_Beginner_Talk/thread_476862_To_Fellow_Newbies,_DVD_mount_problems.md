---
title: "To Fellow Newbies, DVD mount problems"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Roadrunner777 on 2007-06-17
I recently began having DVD mounting problems, and I ended up spending something like 20 hours trying to solve them.  There are dozens of threads here about DVD mounting problems, and I read every one of them, tried every solution given. None of them solved my problem.  There are a couple of threads that relate DVD mounting problems to the latest kernel release, and I decided that was the problem, since I could find no other cause.

But, in the end, I fixed it, and this thread is an attempt to keep others from straying as far down the wrong path as I have.  Are your symptoms something like this?

- Can read and burn CD-R perfectly
- Plays DVD movies
- Will not mount a data DVD, automatically or manually
- fstab file looks correct

Sounds like software, right?  Nope.  The drive was bad.  In order to prove this to myself, I loaded SUSE and then Windows 2000 on a spare drive and got similar results.  Then, I bought a new drive and everything is fine now.  How can this be?

I knew this all along, but I allowed other people's similar problems to lead me away from my own knowledge.  A   DVD drive is really 2 drives in one chassis, sharing some electronics.  It is actually very common for CD's to work where DVD's do not, and visa-versa because of hardware failure.  Movie DVD's must use some other route as well, though I did not realize this before, and I am not certain of it now.  I offer two pieces of advice:

1. If you are having DVD mount problems but CD's work, it could still be the drive.  Try it in another system if you can.  My drive was 1-1/2 years old, and  an expensive name brand (NEC).  I would never have guessed it had gone bad, but it did.

2. Just because others are having similar symptoms doesn't mean you have the same problem.  These forums are GREAT, but do not let them take the place of your own brain.

Sorry for the length of this post, but having killed 20 hours on this, I had to tell someone.

- Phil

---

### Post by twice on 2007-07-26
Thank you for posting this.  I had similar symptoms (though in my case dvd video stopped working too), but since cds still worked fine, I was convinced that something had spontaneously gone wrong in Ubuntu.  Fortunately, I'd only wasted an hour before I found this post and tested my drive in another OS/machine.

---

### Post by minhtrietle on 2007-07-31
Sorry but I don't agree that it's the hardware problem. Just like you, I wasted my entire 2 weeks to work on this but no help. I only found out that after the fresh install, Ubuntu 7.04 should be running ok and be able to mount DVD-ROM as well as CD-ROM. After I clicked on update or ran "sudo apt-get update" things f*@ked me up from the bottom of my butts to the top of my head.

I just re-installed Feisty and didn't run no updates. I'll wait until Oct 18 which is the release day of Gusty and see how it's like.

---

### Post by snake444 on 2007-07-31
same problem here [http://ubuntuforums.org/showthread.php?t=511769](http://ubuntuforums.org/showthread.php?t=511769)
the dvd is new from the shop and its very annoying because my hd is full and i need to get rid from files by burning them to dvd's but the ubuntu have problems with mounting them:mad::mad::mad::mad::mad::mad::mad:

---

### Post by jdwinfodesign on 2007-11-25
Thanks, Roadrunner777, for making a very good point. 

I had installed a used DVD+-RW to replace a CD-ROM drive in a little desktop box I had bought quite a while back. I had successfully run Dapper and have been running Feisty with no problems since it first came out.

A week or two ago, I purchased a video card so I could use my television to watch video stored on the hard drive. 

I had installed vlc and k9copy, and had successfully copied and played a couple of DVDs, too. But then, all of a sudden, the machine would not mount DVDs, even though it would autoplay music CDs and mount data CDs, as well. 

I figured that, being a "stupid n00b", I had managed to fsck up my installation somehow.

So, two days of reading posts, removing and installing packages through the graphical package manager and on the command line, reading many (often contradictory) posts, overwriting packages with older packages, overwriting packages with newer ones, and general newbie package hell.

Then, I read the post by Roadrunner777 and decided to try playing a DVD I had burned (on my desktop box) in my dual-boot laptop. It ran perfectly. 

So, on the ailing desktop box, I booted into Windows XP (which I keep for a couple of games) and Windows would not mount the DVD...even though, as I said, it would autoplay CDs just fine.

Still, it would not play a movie, whether the movie was on a pressed commercial DVD or on a burned copy.

So, I got a new DVD drive (saving the receipt, of course, and opening the box carefully to preserve the original packaging) and it worked perfectly.

Thanks, Roadrunner777 for reminding me to trust my instincts.

---

