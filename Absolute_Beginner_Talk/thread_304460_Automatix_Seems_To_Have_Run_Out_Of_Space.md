---
title: "Automatix Seems To Have Run Out Of Space"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2006-11-21
Okay . . .so I went ahead and started with Automatix, but midway through all the installs, it told me that there is no space left on the device . . .does this mean that my HD is out of space? Because I'm only using 2 gigs of the 40 on the partition that Ubuntu is on . . .but there are subs in that partition that are only 1.43 gigs large. One is called "Extended", and the other is called "Linux-Swap" . . .I'm so lost. ~LOL~

---

### Post by LLRNR on 2006-11-21
Ummm... I really hope I'm wrong... please open a terminal from Applications -> Accessories -> Terminal, then type in **df -h**, hit enter, then copy the output and paste it here. :-k

---

### Post by CheshireMac on 2006-11-21
Filesystem            Size  Used Avail Use% Mounted on
unionfs               875M  875M     0 100% /
varrun                252M   84K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  108K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M  8.8M  244M   4% /lib/modules/2.6.15-26-386/volatile
tmpfs                 252M   24K  252M   1% /tmp
/dev/hdd               77M   77M     0 100% /media/cdrecorder

---

### Post by LLRNR on 2006-11-21
Well it seems to me that you... well... did something wrong. Wait for someone else to confirm, but from the output you gave I see your filesystem only has 2 GB allocated, which is the install default... in which case it's not ok. It looks indeed filled up. (Don't take it too hard, it happened to me the first time too :D)

You used the LiveCD for installing? If so, at the partitioner phase, did you manually partition your drive? The default filesystem is ext3 and you use it as mount point for /, then you have to allocate a swap space = 2 * RAM (that you have), also it's a good idea to do a separate partition for /home - this is the "Home" directory for all your personal files (including other user accounts too) and it's better to keep it separate because at a later reinstall it might be useful to keep your existing settings and docs... 

I hope [this](http://www.psychocats.net/ubuntu/partitioning) might clarify some things for you.

LLRNR

---

### Post by CheshireMac on 2006-11-21
Okay . . .something that confuses the heck out of me is that I have two drives (I understand that part). One is my 80 gig drive, which holds XP, and I'm not going anywhere near that, because other people use it, and it contains files I don't want to mess with (Pics, music, etc.) The other drive is 40 gigs large, which is fine for me . . .and that's what I selected when I installed this OS . . .Now, what appears to have happened is that Ubuntu took that 40 gig drive and subed out 2 gigs of it for itself, but seperated itself from the larger remaining portion . . .does that seem right to you? If so . . .can I fix it in GParted without having to redo everything?

---

### Post by NiklasV on 2006-11-21
You should be able to resize you / filesystem with GParted.
Boot from the livecd, you can't resize while / is mounted.

---

### Post by LLRNR on 2006-11-21
If in the GParted utility you see a large amount (let's say 38 GB) of unallocated space, you should be able to do that, there are a lot of resizing queries using GParted here, it should work, although I didn't try it for myself.

The safe thing to do is to resize your partition while it's not mounted i.e. while you don't actually use it. You need for this the GParted LiveCD, which you can get from [here](http://gparted.sourceforge.net/livecd.php); you have to boot from it and then resize...

Still, better wait for suggestions since I'm not a guru :D I don't say "Go for it!" without hesitation if I didn't do it myself and didn't actually see how things go.

---

### Post by CheshireMac on 2006-11-21
Is "Unallocated space" different from "Unused space"? I imagine it is, from the terms . . .unallocated would mean that it's not even available without moving it somewhere, right? Also ...in GParted, there is no unallocated space. Only unused in the larger portion of the drive I installed the OS on.

---

### Post by LLRNR on 2006-11-21
By "unused" you mean a huge amount of your HDD, right? Unused = unallocated (I might not be using the appropriate terms) **IF** for the unused space that GParted shows you can't see a filesystem (something like ext3, ntfs, "swap" etc.) Otherwise (if the huge amount of GB would just be unused) I understand that they already belong to a partition, in which case you shouldn't have come across the 100% disk used thing. Also... 38 GB *would* have been visible in your "df -h" output ("df" stands for "disk free" and the -h switch stands for human readable).

LLRNR

---

### Post by CheshireMac on 2006-11-21
Okay  . . .this may help a little . . 
It's a screenshot of my GParted showing what's going on . . .from this, can you tell me what I can do to resize, because the last time I messed with partitions, I had a lot of people angry at me for losing their stuff. ~LOL~ I'm in LiveCD again, so I'm ready to go.

---

### Post by Buck2348 on 2006-11-21
LLRNR:

I read stuff online for two days before I repartitioned my disk and installed Ubuntu, and so far it has paid off.  I'd like to know more about what's in that file information that CheshireMac posted.  First, here is the same information on my machine:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb2             3.9G  2.2G  1.5G  60% /
varrun                252M  120K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  140K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  233M   8% /lib/modules/2.6.15-27-386/volatile
/dev/hdb4              23G  652M   21G   4% /home
/dev/hda1              40M  7.3M   32M  19% /media/hda1
/dev/hda2              33G   29G  4.9G  86% /media/hda2
/dev/hda3             4.3G  4.0G  259M  95% /media/hda3
/dev/hdb1              48G   36G   12G  76% /media/hdb1
```

What is all this varrun...devshm stuff?  I can see they are subfolders of root but why are they included in this listing of disk space usage?  What are you adding up to conclude that CheshireMac has 2 gigabytes allocated and used?  It appears to my unlearned mind that he has no partitions at all mounted.  All of mine except the Swap are listed as /dev/hdxx.  Are the items I mentioned (varrun, etc.) included in the 1.5G used in my root partition (hdb2)?

Thanks very much in advance.

Trying to learn,
Buck

---

### Post by CheshireMac on 2006-11-21
Hey Buck, thanks for making me feel less like a fool . . .not saying that you are a fool, but at least now I know I'm not alone. :) Appreciate the newbie-comradory. ~LOL~

---

### Post by mdsmedia on 2006-11-21
CheshireMac, I'm far from expert myself....I ALWAYS have problems when it comes to partitioning...I dive in and it doesn't work...I try something else...and eventually I stumble on a format that works.

It looks to me, the uneducated eye, that you've allocated most of your drive as the boot partition, so it may not be accessible for general file storing.

Edit: It looks like Meng has answered your question in the other thread and I was (as has been known to happen) wrong :)

---

### Post by CheshireMac on 2006-11-21
This, I have summized. ~LOL~ Any thoughts on how to adjust that problem? I'm in LiveCD so I'm ready to make changes.

---

### Post by mdsmedia on 2006-11-21
Have a look at Meng's response in your other thread. Looks like you're probably ok. Not sure why Automatix has run out of space in that case.

---

### Post by LLRNR on 2006-11-21
@ Buck2348: Your output seems ok, the hdx is a normal thing, it's the way that partitions are labeled. Your output is very close to mine although I can't literally compare it right now since I'm on an XP machine. The varrun, varlock, devshm stuff are generally needed things, I don't know their exact role... I also have a lot to learn, I've been around the Linux world for 3 weeks or so. :D (The thing I'm sure about is that /dev stands for certain types of devices...)

@ CheshireMac: I thought in the first place this is strange, since there only seems to be a /dev/hdd on your system, mounted in /media/cdrecorder. As far as I know, every partition you have should be something like hda1, hda2, ... , hdxy. This puzzles me indeed, it's the first time I see something like this. From the first line of your output (although I don't know what "unionfs" is, in my output it's something like /dev/hdax) I see your root partition 100% full.

About the screenshot... strange enough I have the slight feeling it looks alright although I can't verify my statement since I can't watch my own gparted display (I'm not at home and I only have an XP machine at my disposal...)

I'm sorry if I mislead you in any way, it was certainly not my intention, I asked for your df output just to check but it turns out I can't decipher what's going on... I don't have enough knowledge to judge if it's something fishy with your output and/or the screenshot taken from GParted. It totally confuses me.

I'm just learning, as you are, and I think it would be better that a more authorized person have a look at this...

First time I installed Ubuntu I did a stupid thing with my partitions, don't know exactly what, but the thing is I didn't have space and I simply wiped them off and reinstalled - the second time successfully. But since CheshireMac's HDD is not my own, I can't fool around with other people's partitions.

Again, please accept my apologies, by no means I don't want to pose as a guru or mislead people !

LLRNR

---

### Post by CheshireMac on 2006-11-21
On the contrary, LLRNR . . .you've been very gracious and helpful, and I thank you very much. In fact, to everyone who has given me input, helpful or not (Mostly helpful), I thank you very much. :) I'm yet to figure the problem out yet, so more input is appreciated, but still, I'm very thankful that Open Source is kinder than Evil Empire SoftWare INC. (That's Microsoft for the unaware. ~LOL~)

---

### Post by mdsmedia on 2006-11-21
> **LLRNR said:**
> 

@ CheshireMac: I thought in the first place this is strange, since there only seems to be a /dev/hdd on your system, mounted in /media/cdrecorder. As far as I know, every partition you have should be something like hda1, hda2, ... , hdxy. This puzzles me indeed, it's the first time I see something like this. From the first line of your output (although I don't know what "unionfs" is, in my output it's something like /dev/hdax) I see your root partition 100% full.

About the screenshot... strange enough I have the slight feeling it looks alright although I can't verify my statement since I can't watch my own gparted display (I'm not at home and I only have an XP machine at my disposal...)
LLRNRCould it be because he was running the command from LiveCd so it's giving him a readout from his Cd drive?

---

### Post by LLRNR on 2006-11-21
[quote="mdsmedia"]Could it be because he was running the command from LiveCd so it's giving him a readout from his Cd drive?[/quote]...Wow, I didn't think of that :-k I'm so pissed off and unconfortable on this XP box, I neeeeed my Ubuntu system to test myself the way things appear from a LiveCD, but I'm at work !!! ](*,) 

@ CheshireMac: I just love the way you think about the "Evil Empire Software inc." :lol:

LLRNR

---

### Post by CheshireMac on 2006-11-21
Okay . . .here's my readout in regular mode . . .
mac@mac-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              36G  1.9G   32G   6% /
varrun                252M   84K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  112K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-26-386/volatile
/dev/hdd               77M   77M     0 100% /media/cdrecorder

Does that look normal?

---

### Post by mdsmedia on 2006-11-21
> **LLRNR said:**
> ...Wow, I didn't think of that :-k I'm so pissed off and unconfortable on this XP box, I neeeeed my Ubuntu system to test myself the way things appear from a LiveCD, but I'm at work !!! ](*,) 

@ CheshireMac: I just love the way you think about the "Evil Empire Software inc." :lol:

LLRNRI know what you mean. I'm on an XP box myself. My Notebook with my Ubuntu :) Home :) is sitting in it's bag beside me but I don't have a net connection to it, and it wouldn't look like I was working if I was playing on my baby ;). 

That was just a guess on my part but it seemed to make sense since that was what the readout seemed to be saying.

Yep, CheshireMac, Open Source is much kinder than the EES Inc. :) I have no idea in Ubuntu, but at least I have a chance. In XP you really are at the mercy of the EES Inc.

---

### Post by LLRNR on 2006-11-21
Oh yeah, CheshireMac, of course, now my heart finally stopped pounding... I was so puzzled, I couldn't understand a thing, didn't even think your previous output was from the LiveCD.

```
Filesystem Size Used Avail Use% Mounted on
/dev/hdb1   36G 1.9G   32G   6% /
```

so you have a hdb1 after all, and you have 32 GB free.

Still, it's a strange thing with what Automatix told you (I never used it, I wanted to knock my head against the walls in doing "manual" stuff), but... who knows, either Automatix has gone mad, either now (after a reboot) it will run normally. :mrgreen:

LLRNR

---

### Post by CheshireMac on 2006-11-21
Okay, so Meng brought up a great point that I found some humour in. ~LOL~ He said that all is proper from appearances, and that Automatix is "A damned liar" ~LOL~ He suggested that I install stuff manually. The reason, however, that I found automatix to be tempting is that I'm of the impression that Linux doesn't offer a friendly install method . . .only the long way . . .am I wrong?

---

### Post by LLRNR on 2006-11-21
Well at a first glance you could be right, this is what I also thought for a day or so (but still didn't want to use Automatix or EasyUbuntu, just an ambition of mine), but there are some fast ways to install everything you need. From what I found out:

- a simple search in Synaptic did fine the first days ;
- after a few days I got sick at scrolling and clicking so I played a little with the command line ;
- now it's chronic, whenever I'm obliged to use an XP machine I wonder myself "but where did the konsole go?!" ;
- ubuntuforums + [this special thing](http://google.com/linux) (I didn't know about it before) + sourceforge.net became my best friends :D

Of course it's just a personal approach, but I love this more day by day. (Some of my colleagues warned me: "Beware! We're telling ya... if you go on like this, then you'll probably become some weird geek one day!!!" :lol:)

I'm glad your trouble is over... wow it was definetely something to learn from.

Cheers !

LLRNR

---

### Post by CheshireMac on 2006-11-22
TOO COOL!!!! There's a Linux Google?!?!?!?! Wicked!! ~LOL~ Buddy, you've been a huge help . . .essentially, the only thing I need to learn now, is how to write Linux code. Once I've got that down, there's no stopping me from ruling the world!! Or, at least a small island off the coast of Nova Scotia. ~LOL~ (It's called Sable Island. Look it up. You'll find it's worth taking over for it's resources.) ~LOL~ Thanks again.

---

### Post by mdsmedia on 2006-11-22
> **CheshireMac said:**
> TOO COOL!!!! There's a Linux Google?!?!?!?! Wicked!! ~LOL~ Buddy, you've been a huge help . . .essentially, the only thing I need to learn now, is how to write Linux code. Once I've got that down, there's no stopping me from ruling the world!! Or, at least a small island off the coast of Nova Scotia. ~LOL~ (It's called Sable Island. Look it up. You'll find it's worth taking over for it's resources.) ~LOL~ Thanks again.Ummmmm...that wouldn't have anything to do with sables?? LOL

---

### Post by LLRNR on 2006-11-22
> **CheshireMac said:**
> TOO COOL!!!! There's a Linux Google?!?!?!?! Wicked!! ~LOL~ Buddy, you've been a huge help . . .essentially, the only thing I need to learn now, is how to write Linux code. Once I've got that down, there's no stopping me from ruling the world!! Or, at least a small island off the coast of Nova Scotia. ~LOL~ (It's called Sable Island. Look it up. You'll find it's worth taking over for it's resources.) ~LOL~ Thanks again.

Yup, I'll certainly consider taking over your island for your resources, LOL.

Ok, since your installing things topic doesn't have such a great echo as this one, there are some things (I pointed them out in the first thread you started, but it doesn't hurt to put them down again) you should know:
- [(not-so-)quick intro](http://www.psychocats.net/ubuntu/) ;
- [media issues](https://help.ubuntu.com/community/RestrictedFormats) (music, video etc.) ;
- [different ways to install things](http://monkeyblog.org/ubuntu/installing) ;
- ok, since you mentioned it, [learning the shell and bash scripting tutorial](http://www.linuxcommand.org).

If it's not enough, please let me know :lol:

And, for "further reference", if you want to know what a specific command does (command that you run in a terminal/konsole), here are two ways to find out:
```
command --help | more
```and```
man command
```

Glad I could be of help!

Chhers ! 

LLRNR

---

### Post by CheshireMac on 2006-11-22
As in the pony? Yes, in fact. They were named for the island . . .other than that, I'm not sure what you would be implying. ~LOL~

---

### Post by Buck2348 on 2006-11-22
Well, cool--I'm glad to hear that it was Automatix that was screwed up and not your partitions.  [Here]("http://www.psychocats.net/ubuntu/partitioning") is a good place to read about partitioning--you can find quite a bit of other good stuff there--just click the link at the top to get back to his main page.  Everything I've read recommends making a big /home partition, where all your personal files and system settings would be stored.  That way, you can always reinstall your system on the root drive and not touch the other stuff.  I think that could still be done on your system just by shrinking the root partition and then creating the /home partition in the freed-up space.  But I suggest you not try that until you get some advice from someone who knows more than I do--I'm extremely new to Linux.  BTW, it's not really at all complicated to install things out of the repositories--just a couple of mouse clicks.  Anything else I've installed I did with the help of a step-by-step how-to, though it's beginning to come together.

Edit:  I just found [this how-to]("http://www.psychocats.net/ubuntu/separatehome") on the /home partition.  One other thing I meant to mention.  As I understand it, from looking at your screen shot of your partitions in GParted, your hdb2 and hdb5 are not really separate partitions.  An extended partition is made to house other (so-called logical) partitions so you can have more than four partitions on a single disk.  So your hdb5 (swap) partition is inside hdb2 (extended) partition.  But since they are the same size they are physically the same partition.  I wonder how the extended partition got made if you didn't do it deliberately?

Cheers,
Buck

---

