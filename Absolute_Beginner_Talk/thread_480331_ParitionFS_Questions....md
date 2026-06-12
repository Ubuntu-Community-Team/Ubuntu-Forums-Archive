---
title: "Parition/FS Questions..."
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by starcraft.man on 2007-06-21
Hey there folks. Been away for a bit over a day now. Had a good reason though, got my brand new computer (you would not believe the amount of wires in my room and how many had to move) :D. Now I have to do some serious work because of course it is not set up how I want it to be... no shock there.

So, I'm taking this opportunity while reinstalling my triple boot to move to 64 bit (I hope its not too painful). I have a few questions though that I'd like answered before.

1) First thing on my mind is file systems, I have just been using plain Ext3 for a long time and am now considering changing that (to get best performance out of my new comp). I was looking at the options and they seem to me to be XFS, JFS and ReiserFS. I was reading up on Wikipedia (and other sites) about them but I can't say I really understand the subtle differences. Can someone explain what each of the 3 does so differently from Ext3 (especially in terms of reliability, performance and features)? Does one work better with 64 bit than rest? Then if not in the explanation, which is best for large chunks of data? I ask that because I work extensively with VMs (they of course are giant blobs) and large media files, and I move them a lot... 

On a similar vein of thought, is a mixed FS the best solution for optimal performance? Say one for the root and a different one for home (maybe even sub divisions of home with different FS')? If so, whats your recommendation?

I hope I don't sound too nooby, I'm just not very familiar with them and there is lots of choice as opposed to another OS we know :p.

2) Second and rather simple question after the first one is just to be sure... Ubuntu (and other Linux) can be installed and booted from Logical/Extended partitions right? Where as Win XP (I know it has to be C and first) and Vista  have to be primary to be booted? Just checking.

3) One last thing, any warning/problems about 64 bit I should know about? Other than the flash plug in, that it?

Thats it, I know its quite a few questions I hope someone has all the answers for me. :)

I'll be around for most of the morning, setting up my p4 with a fresh install of Ubuntu (its gonna be my spare, plus its the only machine my printer attaches to, the new PC has no serial ports >.>). See ya around.

---

### Post by Inxsible on 2007-06-21
1) I know Reiserf is more suited to smaller file sizes. I read it somewhere. Let me see if I can fish out the link for you.
 
2) Yes you can definitely use a Logical/Extended partition to boot Linux from. Infact, I do that currently. I think you can also boot Windows from an extended partition, but it is cumbersome to do so.
 
3) Wouldn't know too much about the 64-bit. If you have no problems with it, please let us know. I am thinking of biting the 64-bit bullet too. I hear that its become a breeze now and I might as well utilize both my processors which I have paid for :)

---

### Post by Inxsible on 2007-06-21
Reiser trivia :
 
>  
ReiserFS was the default file system in [_[COLOR=#0000ff]Novell[/COLOR]_]("http://en.wikipedia.org/wiki/Novell")'s SUSE Linux Enterprise until Novell decided to move to [_[COLOR=#0000ff]ext3[/COLOR]_]("http://en.wikipedia.org/wiki/Ext3") on [_[COLOR=#0000ff]October 12[/COLOR]_]("http://en.wikipedia.org/wiki/October_12"), [_[COLOR=#0000ff]2006[/COLOR]_]("http://en.wikipedia.org/wiki/2006")[_[COLOR=#0000ff][1][/COLOR]_]("http://en.wikipedia.org/wiki/ReiserFS#_note-0"), two days after principal author Hans Reiser was charged with the murder of his wife.

 
Also check this link on Wikipedia which lists the performance and criticisms of [Reiser]("http://en.wikipedia.org/wiki/ReiserFS")
 
As for [EXT3]("http://en.wikipedia.org/wiki/Ext3")
>  
Although its performance (speed) and scalability is less attractive than competitors such as [_[COLOR=#0000ff]JFS2[/COLOR]_]("http://en.wikipedia.org/wiki/IBM_Journaled_File_System_2_%28JFS2%29"), [_[COLOR=#810081]ReiserFS[/COLOR]_]("http://en.wikipedia.org/wiki/ReiserFS") and [_[COLOR=#0000ff]XFS[/COLOR]_]("http://en.wikipedia.org/wiki/XFS"), it does have the significant advantage in that it allows in-place upgrades from the popular [_[COLOR=#0000ff]ext2[/COLOR]_]("http://en.wikipedia.org/wiki/Ext2") file system without having to [_[COLOR=#0000ff]backup[/COLOR]_]("http://en.wikipedia.org/wiki/Backup") and restore data as well as requiring lower CPU consumption[_[COLOR=#0000ff][1][/COLOR]_]("http://linuxgazette.net/122/TWDT.html#piszcz") than [_[COLOR=#810081]ReiserFS[/COLOR]_]("http://en.wikipedia.org/wiki/ReiserFS") and [_[COLOR=#0000ff]XFS[/COLOR]_]("http://en.wikipedia.org/wiki/XFS").

 


---

### Post by starcraft.man on 2007-06-21
> **Inxsible said:**
> 1) I know Reiserf is more suited to smaller file sizes. I read it somewhere. Let me see if I can fish out the link for you.


Right I also read that... I guess thats not exactly what I'm looking for since I deal with large media.
> 
2) Yes you can definitely use a Logical/Extended partition to boot Linux from. Infact, I do that currently. I think you can also boot Windows from an extended partition, but it is cumbersome to do so.
 
Right, thats what I thought. I guess its probably simplest to make my two windows OS' Primary and extend for everything else.

Thanks for the reply, anyone else to weigh in on the File System issue?

I was reading up a bit of JFS and it seems interesting, it seems to offer great performance overall and supports newly implemented extents, what exactly are those though?

---

