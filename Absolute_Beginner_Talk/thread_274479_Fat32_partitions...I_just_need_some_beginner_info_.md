---
title: "Fat32 partitions...I just need some beginner info please..."
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-09
Hello, I am installing xubuntu 6.0.6 LTS onto my HP pc with Xp.

I will be installing it as a dual booted pc with a 10gb Fat32 partition.

My question is about the Fat32 usage. Could someone explain to me about the way the Fat32 is used. I know it's for sharing files between my Xp OS and my xubuntu OS, but how do I actually use it and open and save files for it. 

When I installed xubuntu 6.10(which I'm changing right now to a 6.0.6 since I'm so new to ubuntu/xubuntu), I noticed that in my xubuntu thunar file manager, that I saw media 1(xp), and media 3(Fat32). On my Xp, my Fat32 was E: Local Disk.

So am I able to open anything from my Xp in media 1 on xubuntu, and only open xubuntu files saved in media 3, in my Xp's E: Local Disk? Or do I have it wrong?

---

### Post by aysiu on 2006-10-09
You probably need to mount it properly, but otherwise it should appear as a regular folder where you can open/save/delete files...

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by crimesaucer on 2006-10-09
I mounted it properly. My question is about the correct usage of a Fat32 partition, and whether I can open any Xp media 1 file on my xubuntu os, and if the way to save something on the xubuntu os that I want to access on Xp, is it by saving it in media 3 in xubutu so it shows up in the Fat32 partition in Windows as a xubuntu file in E: Local Disk.

And about mounting, I found these instructions far more informative and easier to follow for a beginner, even though psychocatz is really good for the ISO and md5summer info: [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

thanks,
-c.

---

### Post by aysiu on 2006-10-09
I've often linked to Herman's tutorial, but that's helpful only when installing Ubuntu (and from the Alternate CD). Once you've installed Ubuntu, you need a different method to get a partition mounted.

In any case, I don't know if I understand your question. You save files on the FAT32 partition that you want both Windows and Ubuntu to access (that includes saving, renaming, deleting, copying).

---

### Post by crimesaucer on 2006-10-09
So, I save the files in media 3 on xubuntu to be able to use them in Xp from my E: Local Disk, right.

So can I still open media 1 files (the original Xp partiton) on xubuntu, like say My Pictures on my C: drive of Xp?

or do I have to transfer them into my E: drive to be able to access them in xubuntu.

that was my question, sorry if I was confusing.

---

### Post by lemonsCC on 2006-10-09
You seem to be asking what you CAN do and can't do.

The FAT32 partition is used for transfering files from Ubuntu to Windows.  Both Ubuntu and Windows can READ and WRITE to this partition.

The NTFS (media1) is where XP is installed.  Ubuntu can read from this partition but CANNOT WRITE to it, and obviously windows can read and write to it.

**EDIT**  If you want full access to files such as your pictures, you would be "better" off leaving them on the FAT32 partition, else they will be taking up twice the space and this is a little unnecessary.  This also depends on how large your drive is and personal opinion

---

### Post by crimesaucer on 2006-10-09
oops...I read your post again and realized you had already answered this question...please read this and tell me if I have understood.


But I read somewhere that ubuntu can read a ntfs file from windows, but you need the Fat32 so windows can read an ubuntu file. Am I wrong. 

Because that was why I was asking about accessing My Pictures through the media 1 file on ubuntu, or was I wrong and the only way to transfer and use files on both machines is the Fat32 media 3.

For example, if ubuntu/xubuntu can read both ntfs and Fat32 files, could I leave my media 1 files, or Xp NTFS files the way they are, and then make the media 3 a place for only files saved on xubuntu/ubuntu.

I don't mean to confuse the situation, but simply, can the ubuntu OS access and open a file from the media 1 ntfs file.

EDIT*** so after reading your post a third time and thinking a bit...I figured that putting all files that I need to work on with both Xp and ubuntu, such as images that I create with GIMP or other files that I use for my web page like html files and css and php radio blog files, that it would be best to put those on to the FAT32 so I can work on both operating systems.

And then files that I don't need to "change" or "work on" on ubunut, such as mp3 files and MPEG AVI video files that I only need to view or listen to, it would be best to just leave them on the NTFS media 1 since xubuntu/ubuntu can still read them and play them, right?

---

### Post by lemonsCC on 2006-10-09
Yes Ubuntu can open, read, etc your pictures and other files on media1.

---

### Post by CatKiller on 2006-10-09
You are correct in your assertions.

Xubuntu can read all of the files on an NTFS partition (Media 1 in this case). Any files that you don't wish to change from Xubuntu can remain on this partition.

Anything that you wish to change in Xubuntu, or have created in Xubuntu but wish to access from Windows, should go on your Media 3.

---

### Post by crimesaucer on 2006-10-09
Thanks for the info. I actually edited my thread while you were posting the last posts.

Anyway, I'm starting to think that 10gb is maybe too much space for a Fat32 partition since most of the files that I would maybe work on  with both operating systems are usually not too big. My little web page is only 100mb total. And the image files and jpegs are only about 1-2gb total.

The Fat32 partition can be adjusted into different sizes, right?

And Fat32 file quality is the same as NTFS for music and video, am I correct?

---

### Post by lemonsCC on 2006-10-09
The FAT32 partition can be adjusted, but this may leave you with HD space that can't be used.  I believe depending on where it is would determine this.

We wouldn't want to see you with this problem. [http://ubuntuforums.org/showthread.php?t=272819]("http://ubuntuforums.org/showthread.php?t=272819") :p

---

### Post by crimesaucer on 2006-10-10
Thanks, I just read that post while you were writing your last comment...lol. In fact, ubuntu beginner posts are funny like that, it seems we all have a lot of the same questions at the same time, it most be difficult for the monitors to always have to repeat everything.

So, my newest and last question is this: would it be better to under-size the partition, then to oversize it, because if I needed more gb's for the Fat32, then I could always "re-size it", right?

Thanks again for the help,
-c.

---

### Post by lemonsCC on 2006-10-10
Well it depends.. what are you planning on doing with this space?  Do you want to increase another partion size?  Do you plan on leaving it as unused (unallocated) space?  Chop it up and feed it to the birds?

---

### Post by crimesaucer on 2006-10-10
I basically plan on having my jpg images and gifs that I work on with gimp, accessible between thee two systems, I also would like my simple files like my word document resumes and of course all of my html and css for my few web pages. Also whatever files I need to use for my web pages like my radio blogs php sound files. Besides that, I was thinking about being able to easily access my mp3 files so I could use the mp3 mixer packages for dj quality mixing, sampling, and looping of my music.

Other than that, I don't really know what I would need to have in file transfer. I think 5gb might be all I need, and 10gb for xubuntu(is that enough?), and the rest for xp, since that is where all of my movies and music are stored. I only have 55gb available maximum.

I was just burning the iso to disk and am now ready to start, so what do you think 5GB for Fat32, 10GB for xubuntu, the rest for Xp, or should I make more room for xubuntu's packages, say like 15gb for xubuntu?

thanks,
-c.

---

### Post by lemonsCC on 2006-10-10
Ubuntu is only ~3gigs.  And i think Xubuntu may be a little smaller.  My Ubuntu is on a 9gig partition and couldn't be happier.  But my home folder is on its onw partition.

---

### Post by crimesaucer on 2006-10-10
Well, how much space do the packages offered in synaptic take up? I know I have about 1.5gb of downloaded software on my Windows, and those programs are mostly codecs,a tcp,a ftp, a patch for utorrent, various media players and music players, gimp, things like ccleaner and other spyware/malware, utorrent, and a bunch of msnmsg, yahoo and google talk...ect...and so on. Basically, my programs file looks like the Filehippo page of the best programs they offer.

I know there are a lot of games and useful freeware and open source programs offered through the many repositories, so that is one of the reasons I want to learn xubuntu/ubuntu linux so I can access so many more free and useful programs, also because I'm so over my Xp (vista shell) freezing on me and getting malware issues.

I'm also really interested in learning to use terminal for everything, and learning the inner workings of my computer. 

So is 10gbs enough?

**edit**Don't bother with a reply, I'm just going to install it as 10gb and learn from there, thanks for the help,
-c.

---

