---
title: "I feel hopeless."
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by deloreanz1 on 2007-10-09
I have been a savvy Mac and *shudder* Windows user for quite some time, but I recently switched to Linux, and I find myself baffled. I try to follow instructions to do various things, and the Lappy randomly reboots or does not do what it was supposed to do. I feel hopeless. Is there any way to learn Linux from the ground up?

I am prepared for the flaming that is to come.

---

### Post by perce on 2007-10-09
> **deloreanz1 said:**
> I have been a savvy Mac and *shudder* Windows user for quite some time, but I recently switched to Linux, and I find myself baffled. I try to follow instructions to do various things, and the Lappy randomly reboots or does not do what it was supposed to do. I feel hopeless. Is there any way to learn Linux from the ground up?

I am prepared for the flaming that is to come.

Here are some tutorials: 
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

You should be able to find more with google. Also trying to figure out things yourself and searching Ubuntu's wiki or asking in the forum is a good way to learn. No reason to be flamed.

---

### Post by masingerz on 2007-10-09
sometimes going into irc helps

(type in terminal)

sudo apt-get irssi

irssi

(and once irssi is open)

/server chat.freenode.net 

/join #ubuntuforums

(and ask your question there)

---

### Post by HermanAB on 2007-10-09
If you have serious hardware/driver trouble, then you should try another distribution.  Once you know Linux well, you may be able to sort it out, but as a new user, another distro is the best option.  The reason being that every distribution has a different install system, so when you shop around a bit, you are likely to find one that works perfectly on your hardware.

That being said, Mandriva 2008 is out now, so why don't you head over there and join the download fun? ([http://www.mandriva.com/](http://www.mandriva.com/))

Cheers,

H.

---

### Post by tgalati4 on 2007-10-10
When you get to a terminal, post the output of:

>lspci -vv

and

>lsmod

Look for errors and post them from:

>dmesg

---

### Post by rubbsdecvik on 2007-10-10
coming from a similar background, all I can say is to not lose hope and keep trying.  Soon it will be worth it.

I had some problems in the beginning, and still do every once and a while, however, it is becoming much easier.  I even can help other people now.  

The point is that sometimes asking the "stupid" questions every day can help you learn and even later help those people who ask questions and feel helpless.  

I'm not sure what your specific problem is in this situation, however I know if you tackle one problem at a time, soon you will have a beautifully working system and you will love it.

Don't be afraid to ask questions, I noticed most people here are patient (with a few exceptions) and willing to go as detailed as you need to help you out.

Many tutorials will have you use the command line.  don't be too afraid of this.  The reason they do this, is because the commands are more or less universal.  They can give their info over a wider audience.  Just do exactly what they say and if it doesn't work ask.  

The best way to learn is to keep trying.  We're all here for you.

---

### Post by deloreanz1 on 2007-10-10
Oooh, fun.

My first task was running MupeN64, which went beautifully. Then I tried FCEUltra, which didn't work out quite as well. :(

The biggest problem with this Linux Lappy is the lack of audio. I read in various places across the internets that that is a common problem with this particular model of Laptop (Toshiba Satellite A75-S213.) I first came here in an attempt to solve that, and found myself increasingly despaired.

The other main problem is the random reboots of this machine. It was apparently designed by a monkey on crack, because the only cooling vents are on the Underside, and when it gets too hot, it automatically shuts down. Stupid, stupid, stupid.

Also, the system can handle itself just fine for standard Web surfing and instant messaging, amongst a few other things. it's when I try to do other stuff (installing WINE, getting the audio working) that I start to have that sinking feeling of "Why am I here?" :)

So, anyway.

---

### Post by rubbsdecvik on 2007-10-10
both of those problems seem fairly common. I can't seem to help you with either(no experience with them myself), but others here might be able to.

The heat/random restarts thing might be fixed soon.  It probably has to do with an overheating hardware, probably the processor.  Linux is supposed to be getting some really neat updates that help reduce the power needed by the processors, therefore effectively reducing the heat.  That *might* reduce the restart problems.

Audio... I understand that... I've seen the post enough times to know it's a problem, but I also know that some people have gotten it to work.  Just keep trying.

---

### Post by deloreanz1 on 2007-10-10
Yeah. I'm thoroughly enamored with the concept of using Linux, as I hate Windows with the fiery passion of a thousand suns. Macs are my real heart, but until I can afford one, I'm happy with Linux. Now if I can only figure out how to use it...

Also, I suppose that the improved power consumption would mean longer battery life? Maybe it's just this particular model (wouldn't be the first time,) but the battery life on this thing blows. Less than an hour, on simply reading documents, with the brightness ALL THE WAY down.

---

### Post by rubbsdecvik on 2007-10-10
Thats what I hear... I don't know how long it will take for it to roll out on your laptop (or if it already has) I just remember hearing it.  But yeah, that should help with battery consumption.

---

### Post by Martje_001 on 2007-10-10
For the sound: look if it's not muted. And for your linux: why don't use ubuntu? It has very good hardware support.

---

### Post by deloreanz1 on 2007-10-10
It's not muted; no amount of checking and rechecking all the stops will fix the problem.

Secondly, I may well be running Ubuntu. Honestly, I have absolutely no idea what I'm running. Here's the thing:

I quietly repossessed my brother's disused laptop for my own uses, until I discovered the reason for its disuse: in the short time that he had had it, it had been riddled with viruses, to the point that it would not boot At All.

My friend gave me a hard drive with Linux on it, and that's what I'm on right now. I know he had been running Ubuntu at one point, but it appears to be PCLinuxOS2007 right now.

I know, I know - I'm this forum's worst nightmare. Or at least I feel that way.

---

### Post by Colro on 2007-10-10
[http://linuxcommand.org/index.php](http://linuxcommand.org/index.php) is a great read that I'd recommend. While it's perfectly possible to use Ubuntu without knowing most of it, it's good knowledge to have and will possibly help you troubleshoot future problems on your own.

---

### Post by tact on 2007-10-10
> **deloreanz1 said:**
> It's not muted; no amount of checking and rechecking all the stops will fix the problem.

Secondly, I may well be running Ubuntu. Honestly, I have absolutely no idea what I'm running. Here's the thing:

I quietly repossessed my brother's disused laptop for my own uses, until I discovered the reason for its disuse: in the short time that he had had it, it had been riddled with viruses, to the point that it would not boot At All.

My friend gave me a hard drive with Linux on it, and that's what I'm on right now. I know he had been running Ubuntu at one point, but it appears to be PCLinuxOS2007 right now.

I know, I know - I'm this forum's worst nightmare. Or at least I feel that way.

If I might be so bold as to make a suggestion - before you customise too much, or have too much data on that laptop that needs backing up - think about downloading ubuntu v7.10 (Gutsy Gibbon) when it is released in a week or so.

If you are very impatient then maybe download the beta.  Its pretty good even pre-release.

I guess the i386 desktop live cd is the thing you should download (the beta is here [http://www.ubuntu.com/testing/gutsybeta](http://www.ubuntu.com/testing/gutsybeta)).
(edit:  since writing the above the "Release Candidate" has been made available.  Don't go for the beta.  Go for the RC.  Its here:
[http://www.ubuntu.com/testing/710rc](http://www.ubuntu.com/testing/710rc)  )

The good thing is that you can download and burn the ISO to a CD and then boot directly from the CD.   Doing this changes nothing on your laptop at all.  It gives you a chance to see that all your hardware is properly supported.  If everything works (and it will be slow because you are running from a CD not the hard disk) ...and assuming there is nothing on the laptop you want to back up or save - then you can double click the "install to HDD" icon and start fresh with a new copy of ubuntu.

ubuntu 7.10 has the power saving mods another writer mentions so perhaps that will easy your laptop overheating issues.

---

### Post by deloreanz1 on 2007-10-10
Ooooh, sounds like a good time.

I have nothing particularly difficult to back up on here. About 100 photos, 20 documents, and around 10 videos. I can reinstall the emulators later, if the desire so strikes me.

I do believe that this feeling of hopelessness has been broken by a ray of bright light, and nary a Linux freight train in sight.

---

### Post by bliffle on 2007-10-10
What 'tact' said.

To save your stuff just copy your '/home' directory to a thumb drive. 

I ran from the 7.04 liveCD for about a week about 4 months ago and it went so well that I had a very easy transition to installing and using 7.04 Feisty.

---

### Post by deloreanz1 on 2007-10-10
Well, this is turning out very well. Prehaps I will grasp the concepts after all! Cue the music! (Kidding.)

Seriously though, this is pretty awesome. I didn't know how many replies I might get, and I was expecting the majority of them to be flames. You guys are pretty helpful people. \\:D/

---

### Post by wolfen69 on 2007-10-10
some other distros you could try are: mepis, pclinuxos, granular, sabayon, dreamlinux. although with the distros i just mentioned, you wont learn alot because they do everything for you "out of the box". im sure one of those will work perfectly on your computer.

---

### Post by dptxp on 2007-10-10
> **deloreanz1 said:**
> Well, this is turning out very well. Prehaps I will grasp the concepts after all! Cue the music! (Kidding.)

Seriously though, this is pretty awesome. I didn't know how many replies I might get, and I was expecting the majority of them to be flames. You guys are pretty helpful people. \\:D/

One of the prime reasons of success of Ubuntu is excellent Forum support. 
You get help and you give help.

---

### Post by pjkoczan on 2007-10-10
> **deloreanz1 said:**
> Well, this is turning out very well. Prehaps I will grasp the concepts after all! Cue the music! (Kidding.)

Seriously though, this is pretty awesome. I didn't know how many replies I might get, and I was expecting the majority of them to be flames. You guys are pretty helpful people. \\:D/

You came in asking for, not demanding, help. You show a willingness to learn and a basic level of cluefulness. You're not bashing Ubuntu, Linux, these forums, or anyone else for that matter. Of course you're not going to get flamed.

We're here to help if you're willing to learn.

Anyway, if you're worried about hardware compatibility, you can always look at online compatibility lists. I found these without much trouble, and I'm sure there are many more.
[http://www.linux.org/docs/beginner/platforms.html](http://www.linux.org/docs/beginner/platforms.html)
[http://tuxmobil.org/laptop_manufacturer.html](http://tuxmobil.org/laptop_manufacturer.html)

As mentioned before, but it bears repeating, LiveCDs will help suss out problems before installation.

Good luck, and don't be afraid to ask questions.

---

### Post by lespaul_rentals on 2007-10-10
Oh mate, no wonder you're having problems with your Linux!  Who knows what's on that hard drive?  It's possible it got corrupted, the version is old or unpatched...I say it's time to download a distro so you can get started.  :)  I also have a Toshiba Satellite (same series as you) and I have never had a problem with the sound, Wi-Fi, or anything.

First off, I'd try Ubuntu 7.04 (or Ubuntu 7.10 when it comes out).  You can burn the .iso file to a CD and give it a "test-drive" before you install!  If you don't like what you see, try Kubuntu 7.04.  It has the same underlying system, but Kubuntu uses KDE as its desktop interface while Ubuntu uses Gnome.  KDE is more sleek and attractive, but not everyone likes it.

If you still experience problems with the Ubuntu family, you might try Fedora 7.  I found it had slightly better software support for my system, but it was bloated compared to the Ubuntu family.  Fedora uses KDE as its desktop interface.

If you need help finding, burning, or installing a distro, I'll be happy to help.

---

### Post by Paqman on 2007-10-10
> **rubbsdecvik said:**
> 
The heat/random restarts thing might be fixed soon.  It probably has to do with an overheating hardware, probably the processor.  Linux is supposed to be getting some really neat updates that help reduce the power needed by the processors, therefore effectively reducing the heat.  That *might* reduce the restart problems.


In the meantime try cleaning out the inside of your computer. Over time they suck dust inside and that reduces the airflow, and thus the cooling.

You've got a laptop right? If so, just give the air vents a good suck out with the vacuum cleaner. Don't open it up unless you're really confidant about what you're doing.

Can't hurt, anyway!

---

### Post by tgalati4 on 2007-10-10
If you still want to get flamed.  Post *I LOVE VISTA* in the Backyard forum.

---

### Post by twiceasworn on 2007-10-10
All I can say is that the command line is your bestfriend.  If it isn't right now, it will be down the line.  Trust me.  I highly suggest taking a look at some of the CLI tutorials.

---

### Post by bliffle on 2007-10-10
Just be careful with that vacuum cleaner: I ripped some keycaps off with my shop-vac!

And learn the CLI! It'll be your best friend when you have big projects or big problems.

---

### Post by deloreanz1 on 2007-10-11
This is pretty awesome.

I think I'm gonna wait until the full release of Gutsy Gibbon comes out before I install it, as I'm not particularly impatient, and have no immediate need of this Lappy.

For those of you who have been using the beta version - scale of 1-10?

---

### Post by Martje_001 on 2007-10-11
> **deloreanz1 said:**
> For those of you who have been using the beta version - scale of 1-10?
9!. There are some rough ends, but that will come in 8.04 :D

---

### Post by rubbsdecvik on 2007-10-11
I would give it an 8ish.  It's good, but has some wrinkles to smooth out before I give it a 9 or a ten.  It's still very good though.  Those wrinkles could just be my system too.

---

### Post by Shazaam on 2007-10-11
deloreanz1...
have you tried this to fix your sound issue?
```
alsamixer
```
in terminal. Along the bottom (scroll right/left with your right/left arrows) you will see what looks like an "MM" or "00". The ones marked with the MM mean they are muted. For some reason they will show muted here but NOT when you right click the volume icon. Use the arrow keys to get to the ones that have MM, hit your "m" key on your keyboard to un-mute what you need. Be sure to keep scrolling as there are quite a few you can tweak. Oh, and you can use your up/down arrow keys to change volume levels there too.

---

### Post by tact on 2007-10-11
> **deloreanz1 said:**
> This is pretty awesome.

I think I'm gonna wait until the full release of Gutsy Gibbon comes out before I install it, as I'm not particularly impatient, and have no immediate need of this Lappy.

For those of you who have been using the beta version - scale of 1-10?

The beta, as is the nature of betas, has its good days and better days.    (Not good and bad days).  :)

Every day there are heaps of updates as it gets closer to release.  Majority of the updates are improvements but some of the updates have been a step backwards in some small areas (like a few days ago the update broke laptop sleep/hibernate modes if initiated by the lid switch).  I gotta say tho that was fixed very fast.  It was less than a day!

Such is the nature of beta's.  :)

Overall (and this may be because i have very compatible hardware) I give the beta (now Release Candidate) ...  a clean 9/10

---

### Post by deloreanz1 on 2007-10-12
> **Shazaam said:**
> deloreanz1...
have you tried this to fix your sound issue?
```
alsamixer
```
in terminal. Along the bottom (scroll right/left with your right/left arrows) you will see what looks like an "MM" or "00". The ones marked with the MM mean they are muted. For some reason they will show muted here but NOT when you right click the volume icon. Use the arrow keys to get to the ones that have MM, hit your "m" key on your keyboard to un-mute what you need. Be sure to keep scrolling as there are quite a few you can tweak. Oh, and you can use your up/down arrow keys to change volume levels there too.

It didn't work. It said:


"alsamixer: function snd_ctl_open failed for default: No such device"

I'm confused. Perhaps this distro simply has horrible hardware support?

I have no idea. Personally, I don't understand much of what that line up there means.

---

