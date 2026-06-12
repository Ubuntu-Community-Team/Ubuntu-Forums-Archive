---
title: "Everything's working, but I've a few concerns..."
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by littleoracle on 2008-04-09
Okay, I know this is wordy, but I wanted to be thorough with my information. And yes, I did do some extensive searching, but failed to find an answer to my sort of unique situation.

First a bit of info:
After a bit of struggling, I've got Feisty Fawn Xubuntu running on my old clamshell ibook. (Gutsy was a no-go) And I've got all the software I need up and running. 

I also know that support for Feisty will run out and I'm concerned about the repositories disappearing soon after that (as proved by staying on breezy for too long).

As this is my secondary machine and I'm not keeping anything vital on here, I'd really love to find a way to back up the software I've installed. I don't need to backup my home folder (or can do so separately) and I have a working OS disc (not a live cd, though. just for installing as far as I can tell, I burned it myself from the iso).

FYI I'm also limited to a CD-ROM drive, USB drives and my home network (to a Vista machine) for external storage and file transfer. No DVD and no burner.

And now the questions:
Is there an easy way to back up just the software I've installed? I installed some of it through add/remove, some through Synaptic and a few through sudo apt-get. Obviously I'd want to include any codecs and drivers and things as well.

I don't mind reinstalling the OS and the software. So would I be better off downloading the debs for each piece of software I've installed and saving those? If so, what about OS updates?

Is there a way to simply back up the files (minor OS updates, etc.) from the repositories and make my own repository? I don't need the WHOLE repository system. Just the files I've installed.

And lastly, is there any other way that would be simpler to do this kind of backup? I know my system is old, but I love that little machine and want to keep it running as long as humanly possible. 

The simpler the method, the better, though I'm not afraid of getting my hands a little dirty in the terminal.

Any help with this would be great. Thanks!

---

### Post by swoll1980 on 2008-04-09
apt on cd it's in the repos

---

### Post by kleo skywalker on 2008-04-09
[http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/) - check this out, it might be useful.
And instead of worrying about Feisty support running out, you could just install Hardy when it comes out.

---

### Post by swoll1980 on 2008-04-09
upgrades are easy to do and can be done from system to system like windows

---

### Post by Crafty Kisses on 2008-04-09
> **swoll1980 said:**
> upgrades are easy to do and can be done from system to system like windows

Yep, I think it's easier then Windows, and it really doesn't "Force" the update on you.

---

### Post by littleoracle on 2008-04-09
hmmm. i guess apt on cd is going to be my horse then. though i'm concerned about getting it back on the drive as we're talking a couple gigs of info and i have to have it on cd or external hard drive.

would i reinstall the operating system, create a partition, install apt on cd and then copy the backup over to that partition? sorry, it's not the backup process that's confusing me, it's the restore process.

also, can i back it up to an external drive or do i have to burn it to disc? looks like i can create iso files, could i just save those and restore from there?

as for hoary, i understand upgrades are supposed to be easy, but my particular hardware configuration does not like the upgrade system much. i need to use the alternate ppc install and my hardware utterly rejected gutsy whereas feisty installed with no problems whatsoever. 

thanks so much for the input, though! this is very helpful!

---

