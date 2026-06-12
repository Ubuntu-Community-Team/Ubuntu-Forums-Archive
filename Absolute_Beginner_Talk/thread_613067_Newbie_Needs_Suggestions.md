---
title: "Newbie Needs Suggestions"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by jujubeez on 2007-11-14
Hello - I apologize in advance if the answers to this problem are in one of the "Read Here First" links.  I did read through them, and must admit that I am still a bit (alot) lost!

I have an old Toshiba 2105CDS, 400Mhz AMD K6-2, 128 Mb RAM, with a 2G HD and currently running Win98.  I would like to resurrect this machine for the sole purpose of surfing the web from my couch.

I have tried to run a LiveCD of two other distros (DSL, Puppy) but they only get as far as recognizing the hardware before all progress stops.

I'd like to try and install Xubuntu on this machine, but I am a little afraid to give it a try for the following reasons:

I realize that with the low ram on the machine, I will need to use the alternate install.  If I have been reading everything correctly, I will need to repartition the hard drive in order to install Xubuntu on it.  I am hesitant to do this because if I blitz out Windows, I don't know if I will be able to access the BIOS.  Toshiba says that it is possible to get into BIOS setup by hitting Esc/F1, but so far I've not had much luck.  My second concern is, since I'm no expert, I don't want to corrupt my hard drive by making a stupid mistake.

I would very much appreciate any suggestions on what I can/should do in this case.  If you could also point me to further reading or instruction on how to correctly partition/repartition the HD, I might feel more confident if I had a good guide to follow.  I really would like to be able to breathe new life into this machine, as well as learn at least the elementary principles of Linux.

Thanks in advance!

---

### Post by marco123 on 2007-11-14
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)  Loads of good info on this site.

I don't think Windows has anything to do with the BIOS.  With that sort of spec you would probably have to do a server install then install X and pure XFCE on top of it.

Edit: Or a "Window Manager" - I don't know much about them though.

---

### Post by Inxsible on 2007-11-14
Are you then planning to dual boot with Win 98 and Xubuntu?

you can also have a look at [fluxbuntu ]("http://fluxbuntu.org/js.html")which is a very light weight distro. This [link]("http://www.psychocats.net/ubuntu/partitioning") should help you with your partitioning questions and this will help you [install]("http://www.psychocats.net/ubuntu/installing")

---

### Post by overdrank on 2007-11-14
> **jujubeez said:**
> Hello - I apologize in advance if the answers to this problem are in one of the "Read Here First" links.  I did read through them, and must admit that I am still a bit (alot) lost!

I have an old Toshiba 2105CDS, 400Mhz AMD K6-2, 128 Mb RAM, with a 2G HD and currently running Win98.  I would like to resurrect this machine for the sole purpose of surfing the web from my couch.

I have tried to run a LiveCD of two other distros (DSL, Puppy) but they only get as far as recognizing the hardware before all progress stops.

I'd like to try and install Xubuntu on this machine, but I am a little afraid to give it a try for the following reasons:

I realize that with the low ram on the machine, I will need to use the alternate install.  If I have been reading everything correctly, I will need to repartition the hard drive in order to install Xubuntu on it.  I am hesitant to do this because if I blitz out Windows, I don't know if I will be able to access the BIOS.  Toshiba says that it is possible to get into BIOS setup by hitting Esc/F1, but so far I've not had much luck.  My second concern is, since I'm no expert, I don't want to corrupt my hard drive by making a stupid mistake.

I would very much appreciate any suggestions on what I can/should do in this case.  If you could also point me to further reading or instruction on how to correctly partition/repartition the HD, I might feel more confident if I had a good guide to follow.  I really would like to be able to breathe new life into this machine, as well as learn at least the elementary principles of Linux.

Thanks in advance!

HI and while xubuntu is great for low memory systems, then hard drive space you will need is at least 1.5gig of free space.

---

### Post by paul.matthijsse on 2007-11-14
Hello, are you sure you have a 2 GB disk? Or did you mean 20 GB? Never heard about that size. I'm not sure if you can install Xubu on 2 GB, on 20 GB you can without problems. Accessing the bios has nothing to do with the installed OS, you can even access the bios without any OS installed. Normally you have to press the Del or F1 key for that.

---

### Post by jujubeez on 2007-11-14
Thank you!  I will definitely check out those links as well as Fluxbuntu.

I wasn't necessarily planning on a dual boot, but my concern with losing Windows in its entirety is that the only way I have been able to change the BIOS settings is through a Toshiba Hardware setup program accesible only through Windows.

ETA: Nope, it really is only a 2G HD.  The machine was purchased late '99 or early 2000.  It origianlly had only 64 MB RAM but I just purchased the 128 upgrade.

---

### Post by peedeeramone on 2007-11-14
allright im no expert, but ive been doing stuff like this for a while and have a fairly decent idea of what im doing.

first off if you dont want the win98 on there at all anymore (ie formatting the entire drive) then you have a lot less to worry about. resizing the partition can get a little tricky but usually isnt too bad.

secondly accessing the BIOS really has nothing to do with the operating system installed. even with a DBANed hard disk you can access the bios.

the BIOS is accessed by pressing usually Del, F2, or some other F key when your computer first starts and probably says something like Toshiba. In your case i guess you would press F1 or Esc to enter BIOS

anyways I am not sure as to why you are having issues detecting hardware. if Xubuntu doesnt detect your hardware either then perhaps you could try Knoppix which is supposedly one of the best distros for hardware detection (also a live cd)

keep in mind that simply booting into a live cd will not affect your hard drive at all.

that being said lets move on.

if you want to keep windows then you will first have to resize the current windows partition. this is only possible if you have free space.  shrink the windows (fat32) partition first to allow you with enough room for linux.  if you dont want the windows install at all anymore then simply format the entire hard drive and create a swap partition (usually about double your ram size) and an ext3 for the actual files.

doing this should not corrupt the actual hard drive, but it is possible to corrupt the windows files.

anyways that should enable you to install the linux distro you want.


good luck with that and as a tip google and ubuntuforums are a lifesaver

---

### Post by Inxsible on 2007-11-14
> **jujubeez said:**
> Thank you!  I will definitely check out those links as well as Fluxbuntu.

I wasn't necessarily planning on a dual boot, but my concern with losing Windows in its entirety is that the only way I have been able to change the BIOS settings is through a Toshiba Hardware setup program accesible only through Windows.

ETA: Nope, it really is only a 2G HD.  The machine was purchased late '99 or early 2000.  It origianlly had only 64 MB RAM but I just purchased the 128 upgrade.

In that case, Damn Small Linux would be the best bet for you. I do not know how much memory Fluxbuntu requires. But Xubuntu definitely needs more than that.

Secondly, if you only have 2 GB then there is no way in hell that you can dual boot ;)

---

### Post by peedeeramone on 2007-11-14
wow got beaten to it...


oh whell good luck with all that

---

### Post by jujubeez on 2007-11-14
Thanks again.  I have tried to run DSL from a LiveCD, but after it gets through detecting the hardware it just stops and doesn't do anything else.  No prompts, no nothing.  I get a blinking cursor but I can't enter anything.  Even hitting Enter doesn't work.  That is what prompted looking into Xubuntu.

I guess I will try doing the partitioning and installing DSL to the hard drive instead of doing the LiveCD.

I don't really have anything to lose with this machine anyway as it's pretty much useless in the state it's in.  :)

---

### Post by Inxsible on 2007-11-14
> **jujubeez said:**
> Thanks again.  I have tried to run DSL from a LiveCD, but after it gets through detecting the hardware it just stops and doesn't do anything else.  No prompts, no nothing.  I get a blinking cursor but I can't enter anything.  Even hitting Enter doesn't work.  That is what prompted looking into Xubuntu.

I guess I will try doing the partitioning and installing DSL to the hard drive instead of doing the LiveCD.

I don't really have anything to lose with this machine anyway as it's pretty much useless in the state it's in.  :)Well Installing and finding out for yourself would be the best way to know something :)

And since you got nothing to lose ....... ;)

---

### Post by PointyWombat on 2007-11-14
Doing some reading on this, (becuase 2GB HD just doesn't sound right, even for 1999), this laptop came std with a 4.3GB disks. I bet the BIOS cant see above 2.1 GB or something dumb like that.

Can you throw in an ubuntu live cd and see if it sees a 2 GB or a 4.3GB disk? Can you physically get the model number of the drive itself?

Just a thought,

---

### Post by jujubeez on 2007-11-14
Pointy - I think you may be onto something.  On the back of the computer it does say 4.3!

If that is the case, is Xubuntu still a possibility or is it still too memory-poor to do any good?

---

### Post by overdrank on 2007-11-14
> **jujubeez said:**
> Pointy - I think you may be onto something.  On the back of the computer it does say 4.3!

If that is the case, is Xubuntu still a possibility or is it still too memory-poor to do any good?

If you do not want to dual boot then you could run xubuntu but it will not be speedy! :KS

---

### Post by sirscof on 2008-03-16
If you want to access the BIOS on a Toshiba 2105cds, press the "esc" key while booting.  This should work trouble free unless a password was activated during the initial installation of Windows.  Your hard drive should have 4.3 GB available.  If only 2 GB are available, the hard drive was likely partitioned during setup and possibly the remaining partition was never formated.

---

