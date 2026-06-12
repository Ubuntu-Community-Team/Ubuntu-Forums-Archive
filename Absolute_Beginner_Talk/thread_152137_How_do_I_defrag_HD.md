---
title: "How do I defrag HD?"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-03-29
I'velooked for a defrag program but can't find one. Does Ubuntu have one or do I need to install one?

---

### Post by Sef on 2006-03-29
Linux does not need to be defragged.

---

### Post by meborc on 2006-03-29
why do you need one? ... as far as i know - the linux filesystem is built to automatically 'defrag' the system as new files are written to the HD... at least thats the image in my mind :) 

-under 'defrag' here i mean the way the files are written to the HD

---

### Post by stoeptegel on 2006-03-29
As far as using ext3 (and i believe also reiserfs), you don't need one. Somewhere linux or a program is so smart with the files on the disk that it just doesn't fragment much.

---

### Post by meborc on 2006-03-29
defragmentation, virus and ad-aware scans are not known in linux world... :-k

---

### Post by wolfee on 2006-03-29
Wow !!!! The more I find out about linux the cooooooler it gets!!!
Thanx!!!!!!

---

### Post by Cirrocco on 2006-03-29
Is there any documentation on this "ext3fx doesn't need to be defragged" thing?  I'd like to read it.  everytime somone brings it up: all of the responses have a certain air about them...heresy, bias, personal opinion, etc...

no one ever gives this response: "it doesn't need to be defragmented because of _________, further more you can read up on the process here __________, and if you feel you can contribute to the theory behind it, here's the source ____________."

the reason I look for the above response is because there is never any shortage of information on a lot of linux questions.  this question's answers are lacking.

/has anyone else noticed this?

---

### Post by tribaal on 2006-03-29
/agree

I'd like to figure out exactly *why* you don't need to defrag ext3...

I'll try googling for it, I'll post whatever revelant I can find in this thread...

Cheers!

- Trib'

---

### Post by tribaal on 2006-03-29
Ok, without in-depth reading of most of the articles and references google returned, [Wikipedia]("http://en.wikipedia.org/wiki/Ext3") gave me a good enough answer (good enough for me, at least): 

> There is no ext3 defragmentation tool. [...] However, defragmentation has long been considered a non-issue for ext2/ext3, since they are much better at placing files on the disk versus old FAT-based filesystems.

Granted, I'd love to see some numbers here (just *how better* is it?), but it lets you get the idea: ext3 writes to disk in a "more intelligent" fashion, so there is no need to defrag. 
One apparent drawback is that it's slower that other filesystems, according to the same source.

Anyone with a more... hum... *quatified* answer?
I'll escalate this to one of my teachers here at school, as this topic spiked my curiosity. I'll try to share the answer.

- Trib'

---

### Post by Perfect Storm on 2006-03-29
I found an acticle some months ago...I'll see if I can find it. But it's true that you don't need to defrag and I have never experience performance issues on linux regarding defragging subject.

---

### Post by tribaal on 2006-03-29
Wikipedia also has [this]("http://en.wikipedia.org/wiki/Comparison_of_file_systems") good (although lenghty) article.

Might help.

- Trib'

---

### Post by steve.horsley on 2006-03-29
[QUOTE=Cirrocco]Is there any documentation on this "ext3fx doesn't need to be defragged" thing?  I'd like to read it.  everytime somone brings it up: all of the responses have a certain air about them...heresy, bias, personal opinion, etc...
[/QUOTE]
You're still wearing your Windows head, aren't you. How would you answer if someone came up to you and demanded to know why you don't need crutches, or glasses, or something like that (that you don't need)? It's not an issue of "Why not?", but "Why should I?".

Yes it does sound pompous, but that's the way it is.

BTW, I asked the question "What if you have a FAT partition, because FAT does need defragging?", and no-one could answer. I guess the answer there must be to defrag with windows, or to backup, erase and re-write occasionally, because Linux has no defrag tools at all. Not even for FAT partitions.

---

### Post by NeghVar on 2006-03-29
The whole no defrag thing comes from the journalling nature. If im not mistaken it works like ntfs, youll notice when you defrag an ntfs partition in windows that it doesnt REALLY do anything. Defraging stopped being comon once people stopped using fat.

---

### Post by Cirrocco on 2006-03-29
> You're still wearing your Windows head, aren't you
<rant>
yes, of course I am.  I grew up on it, it's the basis of all I know.  I use my experience to understand and adapt.  If I don't, I will be trapped, facing a corner somewhere wondering why when I walk forward I bump into something.
</rant>

allow me to retaliate with another question:
If I asked: "how does sources.list work?  where can I get documentation on it?  why should I change it?"  

do you think I'd get better/more sophisticated/more reasonable responses?  would the responses be based on what someone *thinks it should be* or *knows exactly what it is*?
would you have gone off on your little rant?

---

### Post by tribaal on 2006-03-30
I have the feeling that you did post a valid question Cirrocco. 
I would like to learn more about how ext3 deals with my files, too, and I can't seem to find any decent documentation online, which seems to be a very uncomon thing in the linux community. 

Of course, I might not be searching in the right place. Hence the question: "*Why* don't you need to defrag ext3 filesystems?"
I understand the concept of "I don't need to defrag", but I'd like to know *why* or *how* it is that I don't need to... 

Could anyone explain the algorithm behind it in a few words? Maybe comparing it to FAT in a few words, too, since I also feel more confident learning stuff keeping my "windows head" in place?

Thanks a lot for you help.

- Trib'

---

### Post by pommattski on 2006-03-30
(I don't know too much about the subject, but) the question this raises in my head is this:

Before resizing a Windows partition, the advice is to defrag the partition first. I'd assumed that this was more to move all files to the beginning of the partition than anything else... is that correct? (... or does the resizing, using gparted, or whatever, move files as necessary anyway?)

So... does ext3 automatically move files from the end of the partition to the start of the partition after files in the middle have been deleted?...

---

### Post by xyz on 2006-03-30
I cannot remember where I read this but, as a noob, it helped me understand a few things.

The guy compared the need to defrag to a totally messed-up kitchen...where fragmented elements in your OS are, in this case, forks,pans,durty dishes,what is in the fridge,rags and so on.

This kitchen here needs cleaning-up (defrag the kitchen)!

He said Windows is a messy person who will clean up his kitchen rearranging his stuff wherever he finds space for it! For instance, you would find your forks in the oven!

Linux is a clean,organised person who will nor only put stuff back where there is space for it but in the RIGHT place IMMEDIATELY.

It made sense to me. Of course, he explained it much better than I did.

---

### Post by Princey on 2006-03-30
For those interested in following up on file systems and reading why you don't need to defrag linux file systems, here's something worth reading:

[http://linux.org.mt/article/filesystems]("http://linux.org.mt/article/filesystems")

Should help clear the air.

---

### Post by steve.horsley on 2006-03-30
[QUOTE=Cirrocco]<rant>
yes, of course I am.  I grew up on it, it's the basis of all I know.  I use my experience to understand and adapt.  If I don't, I will be trapped, facing a corner somewhere wondering why when I walk forward I bump into something.
</rant>

allow me to retaliate with another question:
If I asked: "how does sources.list work?  where can I get documentation on it?  why should I change it?"  

do you think I'd get better/more sophisticated/more reasonable responses?  would the responses be based on what someone *thinks it should be* or *knows exactly what it is*?
would you have gone off on your little rant?[/QUOTE]
Sorry, I meant no offence. And I wasn't having a rant. Maybe a misguided little joke. I was thinking of a childrens program called Worzel Gummage, where a talking scaecrow put different heads on depending on how he wanted to think. But the short answer to "Why doesn't it need fixing" is "Because it's not broken." Our differences in expectations are due to our different backgrounds. It not needing fixing sounds odd to you, but you must admit that the expectation that it **must be** broken will look odd to someone who is used to file systems that are not broken. It's a difference in world views. 

As for the technical details of why it doesn't need defragging, I don't know of any detailed articles on the subject, in the same way as there is not any detailed explanation published as to why the Ford Focus (or any other car) doesn't stop and need restarting every 50 miles. You will probably have to read some fairly detailed descriptions of how the file systems work before you can work out the significant difference.

As for sources.list, I really don't know. It should be fairly easy to work out what the format means, judging by extracts I have seen posted. You should change it if you want to add oher software repositories for easy installation.

---

### Post by tech9 on 2007-09-14
> **xyz said:**
> I cannot remember where I read this but, as a noob, it helped me understand a few things.

The guy compared the need to defrag to a totally messed-up kitchen...where fragmented elements in your OS are, in this case, forks,pans,durty dishes,what is in the fridge,rags and so on.

This kitchen here needs cleaning-up (defrag the kitchen)!

He said Windows is a messy person who will clean up his kitchen rearranging his stuff wherever he finds space for it! For instance, you would find your forks in the oven!

Linux is a clean,organised person who will nor only put stuff back where there is space for it but in the RIGHT place IMMEDIATELY.

It made sense to me. Of course, he explained it much better than I did.

Nice analogy :)

---

### Post by echo $USER on 2007-09-14
After every 30 mounts of the file system, the OS will run fscheck (file system) check on the next boot.  That is pretty much all you need.

---

### Post by marco123 on 2007-09-14
> **echo $USER said:**
> After every 30 mounts of the file system, the OS will run fscheck (file system) check on the next boot.  That is pretty much all you need.

Been using Feisty since release on an ext3 filesystem.  Finally scheduled a disk check with Bonager and it said I had 0.5% non-contiguous files in / , and /home which has been abused for months had 3.5%!!!:) - There's your figures.:)

---

### Post by skyjacker on 2007-09-14
Have a look at this page. It helped me understand why (in my opinion)a defrag utility is not needed

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by mikewhatever on 2007-09-14
Hi Cirrocco,

I am sorry you got such dumb replies. People revel in their ignorance, perpetuate it, and actually seem to enjoy this state of affairs. There is no reliable evidence I've seen to back up the myth that ext3 does not require defragmentation. A lot of linux users circulate the idea, but as evident from this thread, they do not know what the h**l they are talking about. Try reading the following article for an attempt at explanation [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

Another common misconception is that fsck tool defragments ext3 every number of reboots. There is actually a tool for it, not sure it works though.
[http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551) Perhaps we can get some intelligent input from jdong.

---

### Post by mysticmatrix on 2007-09-14
> **Cirrocco said:**
> Is there any documentation on this "ext3fx doesn't need to be defragged" thing?  I'd like to read it.  everytime somone brings it up: all of the responses have a certain air about them...heresy, bias, personal opinion, etc...

no one ever gives this response: "it doesn't need to be defragmented because of _________, further more you can read up on the process here __________, and if you feel you can contribute to the theory behind it, here's the source ____________."

the reason I look for the above response is because there is never any shortage of information on a lot of linux questions.  this question's answers are lacking.

/has anyone else noticed this?

Ok for the more technical and sophisticated....
This is the article you would definitely want to see.

[http://duggmirror.com/linux_unix/Why_Linux_doesn_t_need_regular_defragging/](http://duggmirror.com/linux_unix/Why_Linux_doesn_t_need_regular_defragging/)

Technically, (and you will know what I mean if you had been a Computer Science student), fragmentation of FAT/NTFS increases O(n) and that of Ext3 increases O(log n).
Moreover, fsck defragments your drive automatically after 30 or so mounts, so no need to fear.

Only thing you would miss is if you have a NTFS partition, which Linux can't defragment, and you must use Windows if you still maintain one. This is again a classical example why we use a bad format(like MP3), even if better formats(like OGG) are availible :lolflag:

EDIT: Didn't noticed that people have already given link to article :)

---

### Post by swoll1980 on 2007-09-14
> **Cirrocco said:**
> <rant>
yes, of course I am.  I grew up on it, it's the basis of all I know.  I use my experience to understand and adapt.  If I don't, I will be trapped, facing a corner somewhere wondering why when I walk forward I bump into something.
</rant>

allow me to retaliate with another question:
If I asked: "how does sources.list work?  where can I get documentation on it?  why should I change it?"  

do you think I'd get better/more sophisticated/more reasonable responses?  would the responses be based on what someone *thinks it should be* or *knows exactly what it is*?
would you have gone off on your little rant?

fat32 and ntfs file systems save data in the first available space. Which works fine until you delete something, This leaves a gap between files. The next time you you try to save something it still saves it in the first available space even if it doesn't fit in the gap that you created the data will be split into sections some being put into the gap you created the rest into the next available space which (if you have deleted several files) will be the gap that you created when you deleted those files and so on and so on. This is fragmentation you now have a single file split into sections and saved in different locations on the hard drive. ext3 avoids this by leaving large gaps between individual files, and then using the laws of averages to decide which files will be placed in those gaps to best maximize the available hard drive space. If a file is to large to fit in a gap it will be placed at the end. The reason a ext3 file system doesn't need to be defraged is because it doesn't get fragmented in the first place. Now a linux fan boy would tell you this doesn't decrease the amount of available hard drive space but I don't  see how thats possible if there no way to eliminate the small gaps that would be left in between file that are to small to save thing in. But hey thats what hard drive upgrades are for

---

### Post by jb5 on 2007-09-15
> **marco123 said:**
> Been using Feisty since release on an ext3 filesystem.  Finally scheduled a disk check with Bonager and it said I had 0.5% non-contiguous files in / , and /home which has been abused for months had 3.5%!!!:) - There's your figures.:)

Well funnily enough came across this article when trying to find info on something else.

I tend to switch off my PC a lot and so see a lot of disk checks. Just this morning an automatic check on one of my partitions showed it had 6.3% non-contiguous files! 
(Using a fresh install of Feisty for ca. 3/4 months on this machine, ext3).

But here is my confusion, isn't the disk check just that, a check and not a means to reduce the number of non-contiguous files?

I guess what I am asking is, if the check is just a check then what is the point of checking something if there is nothing to do about it, or as some would argue, nothing needs to be done about it?

---

### Post by psusi on 2007-09-15
> **mysticmatrix said:**
> 
Technically, (and you will know what I mean if you had been a Computer Science student), fragmentation of FAT/NTFS increases O(n) and that of Ext3 increases O(log n).
Moreover, fsck defragments your drive automatically after 30 or so mounts, so no need to fear.


No, fsck does NOT defrag, it is the file system CHECKER; it only checks for errors and fixes them if you tell it to.  

> **bloor75 said:**
> fat32 and ntfs file systems save data in the first available space. Which works fine until you delete something, This leaves a gap between files.

It is not the filesystem, but the filesystem driver that chooses where to place data.  Windows chooses very poorly, leading to files with thousands of fragments.  Linux is a bit smarter about it, so when you do get fragments, they are few and large, causing no significant performance loss.  

> **mysticmatrix said:**
> The reason a ext3 file system doesn't need to be defraged is because it doesn't get fragmented in the first place. Now a linux fan boy would tell you this doesn't decrease the amount of available hard drive space but I don't  see how thats possible if there no way to eliminate the small gaps that would be left in between file that are to small to save thing in. But hey thats what hard drive upgrades are for

No, like any read-write filesystem, ext3 does become fragmented, but because linux is careful about choosing where to store files, it it tends to not fragment them to such a degree as to cause a large performance loss.  

You can install the defrag package and use it to defrag an unmounted ext2/3 partition if you really want, but you will be hard pressed to notice any performance change.

---

### Post by FUbuf on 2007-09-15
> **mikewhatever said:**
> I am sorry you got such dumb replies. People revel in their ignorance, perpetuate it, and actually seem to enjoy this state of affairs. There is no reliable evidence I've seen to back up the myth that ext3 does not require defragmentation. A lot of linux users circulate the idea, but as evident from this thread, they do not know what the h**l they are talking about. Try reading the following article for an attempt at explanation [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

Another common misconception is that fsck tool defragments ext3 every number of reboots. There is actually a tool for it, not sure it works though.
[http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551) Perhaps we can get some intelligent input from jdong.

I totally agree. I'm so annoyed when I get very dump responses to my questions. Here is what I wrote and I would like to hear how ext3 takes care of this situation. Other than I already explained, which needs defragmentation.

Some lengthy samples. That why doesnt linux need defragmentation article was excellent. But they got way too much free space and not so many files. If we take that approach bit further we'll get situation what I describe here.

[http://ubuntuforums.org/showpost.php?p=3368381&postcount=12](http://ubuntuforums.org/showpost.php?p=3368381&postcount=12)

Very short version: Ext2/3 Needs defrag to maintain performance.

---

### Post by misfitpierce on 2007-09-15
Basically I would not worry about defragging a sysem on linux. I got same copy of mandriva on old machine and never reformatted or restarted it for years. Runs fine and same as first day basically. I use reiserFS filesystem too.

---

### Post by vanadium on 2007-09-15
There is indeed a lot of mist spawn up in this thread. psusi gave a nice and concise summary with which I totally agree. The conclusion is that for practical purposes, there is no strong need for a defragmenter if your disk is not quite full. Near full disks eventually might become strongly fragmented. A defragmentation tool would seem to be be useful, but in this case we have a contradiction: defragmentation tools cannot anymore work properly on a near full disk...

Bottom line:
- on a disk that usually is below 70% of usage, fragmentation will be limited and not lead to any noticeable loss in performance.
- the only way to cope with an almost full and fragmented disk is to delete all and copy all files back (you have this backup anyway, don you?).

---

### Post by marco123 on 2007-09-15
> **misfitpierce said:**
> Basically I would not worry about defragging a sysem on linux. I got same copy of mandriva on old machine and never reformatted or restarted it for years. Runs fine and same as first day basically. I use reiserFS filesystem too.

That's right.  I didn't trust most Linux ways of doing things when I first switched, but time will prove you wrong.  I now trust Linux completely.

I think it's just hard to come from a system like Windows that needs vast amounts of work to maintain to a system that just works once it's set up properly.:)

My home partition that was at 3.5% non-contiguous files was over 80% full BTW.:)

---

### Post by suupaabaka on 2007-09-15
A bit off topic, but as a newcomer to the world of Linux, I am constantly amazed at how things work in the OS. Here is an OS that caters to different levels of experience, is customisable to the extreme (Slackware, anyone?) and simply *works*.

Then you have Windows... and it seems to me entire industries thrive on Microsoft's inability to fashion a decent operating system. Defraggers, anti-virus, anti-spyware... at least they're providing jobs.

---

### Post by marco123 on 2007-09-15
> **suupaabaka said:**
> A bit off topic, but as a newcomer to the world of Linux, I am constantly amazed at how things work in the OS. Here is an OS that caters to different levels of experience, is customisable to the extreme (Slackware, anyone?) and simply *works*.

Then you have Windows... and it seems to me entire industries thrive on Microsoft's inability to fashion a decent operating system. Defraggers, anti-virus, anti-spyware... at least they're providing jobs.

It's a shame that someone who doesn't know what spyware, viruses or fragmentation is buys a PC and it comes with Windows.:confused:  It would be much better for them to have an OS where they don't need to know what any of those things are.  Oh well, maybe with Dell jumping onboard one day they'll be able to just buy a pre-configured Linux PC from anywhere.

---

### Post by swoll1980 on 2007-09-29
> **FUbuf said:**
> I totally agree. I'm so annoyed when I get very dump responses to my questions. Here is what I wrote and I would like to hear how ext3 takes care of this situation. Other than I already explained, which needs defragmentation.

Some lengthy samples. That why doesnt linux need defragmentation article was excellent. But they got way too much free space and not so many files. If we take that approach bit further we'll get situation what I describe here.

[http://ubuntuforums.org/showpost.php?p=3368381&postcount=12](http://ubuntuforums.org/showpost.php?p=3368381&postcount=12)

Very short version: Ext2/3 Needs defrag to maintain performance.

I thought my explanation was pretty good

---

### Post by atlfalcons866 on 2007-10-01
my jfs /home is 4.6% fragmented with 8000 files

---

