---
title: "Abslute Fan! Removing Windows tonight!"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Dcox on 2007-04-20
Guys,

I'm removing windows this evening, I'm wondering if my ATI 9800 will work out of the box ... with XGL offcourse. My work-PC works perfectly with an Intel based graphical card.

Wondering if you guys have some tips for me!

Cheers,
Dieter

---

### Post by Xarok on 2007-04-20
Why do you need to remove Windows when you can dual-boot?
Two OS's is always better than one...

---

### Post by Pobega on 2007-04-20
> **Xarok said:**
> Why do you need to remove Windows when you can dual-boot?
Two OS's is always better than one...

Unless you truly need Windows (Games, office, etc.) any GNU/Linux distribution is the way to go. Two operating systems isn't better than one for everyone, I know some people who use only FreeBSD and they're never touched Windows in their lifetime (Professors at a college).

---

### Post by Dcox on 2007-04-20
Mh, wanted to install Windows afterwards, but now you mention this, why not make it dual boot from start! Point taken mate!

Anyway, I'm repartitioning and reformatting 90% of the Harddisk to EXT3 so I thought my data would have been lost anyway.

---

### Post by Xarok on 2007-04-20
> **Pobega said:**
> Unless you truly need Windows (Games, office, etc.) any GNU/Linux distribution is the way to go. Two operating systems isn't better than one for everyone, I know some people who use only FreeBSD and they're never touched Windows in their lifetime (Professors at a college).

Well yes, if you aren't a web developer and don't need to check browser compatability, or your system does all the tasks you need then I guess your fine...

It's just that sometimes you run into a problem with a system and if you don't have time to fix it you can just jump over to the other system to finish your task. Plus, you never know what apps you'll need down the road that only run on Windows.

---

### Post by Xarok on 2007-04-20
> **Dcox said:**
> Mh, wanted to install Windows afterwards, but now you mention this, why not make it dual boot from start! Point taken mate!

Anyway, I'm repartitioning and reformatting 90% of the Harddisk to EXT3 so I thought my data would have been lost anyway.

Atually I would partition just enough space for the Linux OS and the Windows OS and leave the rest as a Shared FAT32 partition so you can access all your files from both OS's.

---

### Post by Pobega on 2007-04-20
> **Xarok said:**
> Well yes, if you aren't a web developer and don't need to check browser compatability, or your system does all the tasks you need then I guess your fine...

It's just that sometimes you run into a problem with a system and if you don't have time to fix it you can just jump over to the other system to finish your task. Plus, you never know what apps you'll need down the road that only run on Windows.

I'm a web developer and I personally don't test my stuff in IE, it's Microsoft's job to fix their flaws, not mine. But let's stop here before this becomes a dual boot vs. GNU/Linux thing.

---

### Post by jvc26 on 2007-04-20
> **Xarok said:**
> Atually I would partition just enough space for the Linux OS and the Windows OS and leave the rest as a Shared FAT32 partition so you can access all your files from both OS's.
I might suggest using ext2 and then putting the windows drivers for ext2 (I think its ext2 anyway) or put them as ntfs and then get the ntfs-3g drivers for read-write ubuntu access. Mainly this is due to the fragmentation issues which occur with FAT32.
Il

---

### Post by Xarok on 2007-04-20
> **Pobega said:**
> I'm a web developer and I personally don't test my stuff in IE, it's Microsoft's job to fix their flaws, not mine. But let's stop here before this becomes a dual boot vs. GNU/Linux thing.

What's the first thing most people think when they see a site that isn't working well? "THIS SITE SUCKS!" Not "My browser sucks, I better get a new one".  I *lot* of people don't even know what a browser is. Why do you think 70% of people are still using IE?

---

### Post by Nik_Doof on 2007-04-20
Sorry, have to pipe into this open flamewars thats starting here, no need to run Windows for IE, i dont. Use [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

[QUOTE=Xarok]What's the first thing most people think when they see a site that isn't working well? "THIS SITE SUCKS!" Not "My browser sucks, I better get a new one". I lot of people don't even know what a browser is. Why do you think 70% of people are still using IE?[/QUOTE]

How about staying on topic instead of discussing the intricies of internet browsing public :)

and p.s. even your site doesn't look nice in IE, its not as easy as it sounds maining a compatible all viewable site :D

---

### Post by Xarok on 2007-04-20
> **Nik_Doof said:**
> Sorry, have to pipe into this open flamewars thats starting here, no need to run Windows for IE, i dont. Use [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page")



How about staying on topic instead of discussing the intricies of internet browsing public :)

and p.s. even your site doesn't look nice in IE, its not as easy as it sounds maining a compatible all viewable site :D

IEs4Linux is only older versions arn't they? Besides, they don't even work properly sometimes.

PS. I haven't even tested my site in IE yet, but I plan to make it as compatible as I can. I just set up the new theme only a few hours ago, fyi >_>

What's wrong with side discussions?

---

### Post by kpel on 2007-04-20
> Unless you truly need Windows (Games, office, etc.) any GNU/Linux distribution is the way to go.

I've been playing with Ubuntu for a week now (my first time ever with Linux) and I'm pretty much here for life.  Sure I've had some head-banging moments trying to figure things out, but honestly, it's been fun.  Most of the programs I use in Windows are open-source or multi-OS and after the crap MS has pulled with Vista (especially the DRM) there's no way I'll use them primarily anymore.  Of course there's the simple fact that, as a power user, I just like Ubuntu better.

If only I wasn't such a hardcore gamer.  *sigh*  Maybe Xfire will get a Linux build for the chat system, at least.

> I might suggest using ext2 and then putting the windows drivers for ext2 (I think its ext2 anyway) or put them as ntfs and then get the ntfs-3g drivers for read-write ubuntu access. Mainly this is due to the fragmentation issues which occur with FAT32.

Not to get too far off-topic, but could you point me to a thread about this?  I plan on reformating my extra drive to store music on (and re-ripping to .ogg since the MP3 quality I originally ripped at is horrid).  I'd still like to be able to access the files from both OSes, not to mention it would be nice to have the ability to move files around if I manage to break one system.

Edit:  oooh, Thanks, Illuvatar.  Finally someone with a bunch of great newbie links in their sig.  *goes into bookmarking frenzy*

---

### Post by Dcox on 2007-04-20
So guys,

which filesystem to use in the extended Data-partition >160gb ?

FAT32 has fragmentation issue's
NTFS cannot be written safely from Linux ? (Would be the easiest as the disk is NTFS now, no data loss)
EXT2 
EXT3

?

---

### Post by lamalex on 2007-04-20
> **Dcox said:**
> So guys,

which filesystem to use in the extended Data-partition >160gb ?

FAT32 has fragmentation issue's
NTFS cannot be written safely from Linux ? (Would be the easiest as the disk is NTFS now, no data loss)
EXT2 
EXT3

?

don't use ext2, I don't why that guy told you that. The ext2 drivers for windows read ext3, if you're even planning on dual booting. IMO dual booting is a waste of time if you're loving Ubuntu and don't need any apps in windows (make sure you test for everything you'll need). NTFS can be written safely from Linux, that's not true anymore. Unless your power goes out while writing, then you might have some issues. FAT32 is a really bad filesystem, don't use it if you don't have to. It is however easily read from both linux and windows so there is the advantage. IMO just make it ext3 and ntfs and install the ext2 drivers in windows to read your files in windows; assuming you even want to dual boot.

---

### Post by greymongrey on 2007-04-20
> **Dcox said:**
> So guys,

which filesystem to use in the extended Data-partition >160gb ?

FAT32 has fragmentation issue's
NTFS cannot be written safely from Linux ? (Would be the easiest as the disk is NTFS now, no data loss)
EXT2 
EXT3

?

NTFS can be safely written to. I do it all the time with NTFS-3G. If you ever think you might need Windows one day, go NTFS. If not, use Ext3. I dual boot myself (yeah right, been in Windows 3 times since November of last year).

---

### Post by proalan on 2007-04-20
> If only I wasn't such a hardcore gamer. *sigh* Maybe Xfire will get a Linux build for the chat system, at least.

Theres a plugin for gaim called gfire which implements the chat protocol, don't know if they plan to fully implement 'in game' chat though

---

### Post by kpel on 2007-04-20
> **proalan said:**
> Theres a plugin for gaim called gfire which implements the chat protocol, don't know if they plan to fully implement 'in game' chat though

That's close.  I'd really like to know when my gaming buddies are in-game so that I can fire up Windows and jump in, but I guess that's just a dream for now.  Maybe I'll go scrounge around the Xfire forum and see if I can resurrect an old thread about that.

---

