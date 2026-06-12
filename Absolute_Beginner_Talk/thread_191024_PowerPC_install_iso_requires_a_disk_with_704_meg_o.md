---
title: "PowerPC install iso requires a disk with ?704? meg of free space?"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by n00bWillingToLearn on 2006-06-07
I downloaded the PPC install cd iso (701 meg) and when I try to burn it ubuntu complains that I need a cd with 704 meg of free space, yes seven hundred and FOUR. And since the iso is 701 meg, already larger than all of my 700 meg CDRWs, I think it is not just an error in Ubuntu ( though I may be wrong ). But it is late and this seems to strange to be anything other than my mistake. what is happening?:confused:

---

### Post by manicka on 2006-06-07
How are you trying to burn the iso image?

---

### Post by n00bWillingToLearn on 2006-06-07
[QUOTE=manicka]How are you trying to burn the iso image?[/QUOTE]
right click -> write to disk...

---

### Post by manicka on 2006-06-07
hmm, that should do it for you. Very strange

---

### Post by n00bWillingToLearn on 2006-06-07
Could you confirm that this iso is 701 meg? just start the download, you don't need to finish it, I just want to know because if this is not my problem, it should be fixed. [http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-powerpc.iso](http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-powerpc.iso)

---

### Post by rcarring on 2006-06-07
If you use a Mac it will add some extra files to the root of the burnt disk. One of which is the index which it needs to list all the files. It's what's called a Table of Contents I believe.

---

### Post by n00bWillingToLearn on 2006-06-07
[QUOTE=rcarring]If you use a Mac it will add some extra files to the root of the burnt disk. One of which is the index which it needs to list all the files. It's what's called a Table of Contents I believe.[/QUOTE]

I'm sorry, I am a little tired, what does that mean I do to burn it?

---

### Post by rcarring on 2006-06-07
Sorry, its slang. Burn means to write out the image to cdr media.

---

### Post by n00bWillingToLearn on 2006-06-07
[QUOTE=rcarring]Sorry, its slang. Burn means to write out the image to cdr media.[/QUOTE]

I know that, but the image is larger than 700 meg?
[edit] and to be more clear, my CDs are all only 700 meg.

---

### Post by rubliwdrahcir on 2006-06-07
I'm new enough on this forum that this is my second post.  Oddly, my first post seems very related to the tale you tell of the woes of trying to burn ubuntu 6.06 powerpc desktop image to CD.  Since I am so new, I don't know how to combine threads.  That would seem to be the propitious thing to do at this point, though.

My other post is in the path:
Ubuntu Forums > Support & Resources  > Other Support Options  > Breezy Badger 5.10 Release  > Ubuntu 5.10 Support (GNOME) > Ubuntu Macintosh/Apple/PPC Users

The thread is named:
"dapper desktop powerpc ISO bigger than breezy can burn CD"

I am also deeply interested in the answers to this question.

Thanks,

r

---

### Post by n00bWillingToLearn on 2006-06-07
Can I do something to make the iso smaller, like delete the intro video?

---

### Post by nalmeth on 2006-06-07
This is very weird
Can you find a Breezy Badger PowerPC image? Maybe you could install that, and then immediately upgrade to Dapper.
Just an idea

---

### Post by jason.b.c on 2006-06-07
What i don't understand is how you think your going to burn 704 mb's worth of stuff onto a 700 mb's max disk..:confused:    It's not going to fit unless it's like compressed or something..:confused:

---

### Post by rubliwdrahcir on 2006-06-07
Since I have no idea of how to combine threads, here is a copy of my post creating the other thread I mentioned above.

Subject:  dapper desktop powerpc ISO bigger than breezy can burn CD

I am running Breezy on an iBook 14" 1.4GHz G4 PPC 1.5GB RAM 100GB HD with the SuperDrive (CD-R/DVD-R) made by Matsushita (UJ845-E).  I downloaded the Dapper Drake Ubuntu 6.06  desktop powerpc release ISO from the local bit torrent and attempted to write it to a 700MB CD-R as I have done with half a dozen previous ISO images.  This time it refused to work in Nautilus(2.12.1):CD/DVD Creator claiming that it needed a 702MB disk for the 701.1MB image.  I turned to GnomeBaker version 0.5.0-3~breezy1 which also refused to write the image.  While perusing the GnomeBaker project home at [http://gnomebaker.sourceforge.net/v2/](http://gnomebaker.sourceforge.net/v2/)
I noticed that the most recent version of GnomeBaker 0.5.1 was released February 4th, 2006 and includes the following line in its change log:
* Fix Bug #1270524 Won&#8217;t allow burning of 700mb files

I am currently configured to see the Ubuntu Breezy Universe repository which provides GnomeBaker.  Synaptic lists the latest version available from that repository as 0.5.0-3~breezy1.  This is what I have installed.  I checked the file sizes of the most recent images I have been burning and the Ubuntu 6.06 Dapper PowerPC desktop is the largest and closest to the maximum size:
 680540160 2006-06-06 09:09 xubuntu-6.06-desktop-i386.iso
 701743104 2006-05-29 17:51 ubuntu-6.06-rc-desktop-powerpc.iso
 707751936 2006-06-06 13:50 xubuntu-6.06-alternate-i386.iso
 720015360 2006-04-01 15:54 dapper-live-flight6-powerpc.iso
 729980928 2006-04-30 20:31 dapper-live-daily20060430-powerpc.iso
 730804224 2006-05-05 14:01 dapper-live-powerpc.iso
 735117312 2006-06-06 07:40 ubuntu-6.06-desktop-powerpc.iso

I am using Sony  700MB 80min CD-R media which should approximate the Optical Storage Technology Association's listing of 737,280,000 bytes available in mode 1 with 2KB blocks, 75 blocks/second for 80 minutes.
[http://www.osta.org/technology/cdqa7.htm](http://www.osta.org/technology/cdqa7.htm)

A short calculation in bc -l
700MB = 700 * 2^20 = 734003200 Bytes
maximum available on 80 min CD-R = 737280000 / 2^20 = 703.125000MB
file in question = 735117312 / 2^20 = 701.062500MB
This makes it look like the file should fit since it is after all an image of the filesystem and thus shouldn't gain (too much?) size when written to disk.

This brings me to a triple of questions:
1.  When will the new GnomeBaker 0.5.1 arrive in the Breezy Universe repository?  I'd like to try Dapper out with the live CD before upgrading since this is my production machine right now.
2.  Does anyone else have some insight into this problem that I am missing?  If so, please share it and remedy my ignorance.  (I noticed that with the BurnFree option checked in the GnomeBaker setup dialog it could not set its scheduler priority when running non-privileged so I tried it with sudo gnomebaker and then it said it couldn't find the device.  I also tried invoking gnomebaker with the -ignsize and -overburn options, to no avail.)
3.  Has the Dapper powerpc desktop CD outgrown 700MB media so that we now need 800MB media to hold 701.1MB?

Thanks,
r

---

### Post by linear on 2006-06-07
For what it's worth, Apple's Disk Utility was able to burn that 701MB image to a 700MB CD without any problem. It boots just fine.
 
I haven't had much luck with GnomeBaker or Burn to Disk in general. K3B (which you can install in Gnome) works much better.

---

### Post by avtolle on 2006-06-07
I have the same problem. What I did was give up burning the ISO, and installed from update. I have a Mac G4 Cube, and the update/upgrade install over a very simple but working Breezy install went very well. Sorry I can't give any more assistance than to suggest an update install over a Breezy install.

---

### Post by rubliwdrahcir on 2006-06-08
linear,

Thanks for the tip.  I already had K3B installed but hadn't tried it, yet.  K3B worked like a charm!

Thanks again,
r

---

