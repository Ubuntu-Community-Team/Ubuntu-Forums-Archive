---
title: "How to format &amp; partition HDD? (I want to  move to Ubuntu7.10 complete)"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by MrQuangnd on 2007-11-15
I have two HDD (1 SATA 80GB and 1 ATA 20GB )...
The first SATA had installed WinXP and the second ATA had installed Ubuntu. I backed up all data.
now, I want to format two HDD and create new partitions to use Ubuntu (maybe I'll install a virtual machine to run some applications on Window)...

[B]I must format them how? (the way that best!)
[/B]
I want to install Ubuntu on SATA HDD and can contain more data with ATA HDD 20GB.
**How must I create new partitions ?** (I'll use Partition Magic on Hiren's Boot CD).

(if can, in the future, i'll remove ATA HDD 20GB, this work will effect to system or not? - i have which way to prevent this...)

please let me know...thanks so much ! :)

---

### Post by oneadvent on 2007-11-15
best way to partion and to format is with the liveCD. 

It has gparted on it already.

---

### Post by Inxsible on 2007-11-15
+ 1 for GParted. its the best partitioner I have come across :)

---

### Post by indytim on 2007-11-15
If you want to really "clean" those hard drives before adding partitions via GParted Live, I'd recommend doing a low level format of both drives.  That will get you back to a new state as far as the 0s & 1s are concerned :).

IndyTim

---

### Post by MrQuangnd on 2007-11-15
thanks for replies!

I have some ques:

1. what's low format? ... I don't know about it...how?
2. GParted have on Ubuntu 7.10 LiveCD? (ubuntu-7.10-desktop-i386.iso -- right?) - This is tool help us create partition automatically? (or manual...). But i have two HDD, it can work exactly for both of them ?

I'm newbie...Please explain something slowly...thanks a lot!

---

### Post by Inxsible on 2007-11-15
> **MrQuangnd said:**
> thanks for replies!

I have some ques:

1. what's low format? ... I don't know about it...how?
2. GParted have on Ubuntu 7.10 LiveCD? (ubuntu-7.10-desktop-i386.iso -- right?) - This is tool help us create partition automatically? (or manual...). But i have two HDD, it can work exactly for both of them ?

I'm newbie...Please explain something slowly...thanks a lot!1) Low level format is where you write you disk with a bunch of 0's and 1's to remove any trace of existing data on it.
2) Yes, yes and yes

---

### Post by eldragon on 2007-11-15
i would use the 20gb ata for the root partiton and OS, and use the 80gb for the home partition. this would give you home independance between OS formats :D

---

### Post by rsambuca on 2007-11-15
> **indytim said:**
> If you want to really "clean" those hard drives before adding partitions via GParted Live, I'd recommend doing a low level format of both drives.  That will get you back to a new state as far as the 0s & 1s are concerned :).

IndyTim

A low level format is completely unnecessary for installation of an OS.

---

### Post by Inxsible on 2007-11-15
> **rsambuca said:**
> A low level format is completely unnecessary for installation of an OS.
I agree. Unless you are giving/selling your hard drive to someone else ;)

---

### Post by MrQuangnd on 2007-11-15
So...I should:

1. Simple insert LiveCD Ubuntu into DVDROM
2. Run install then boot finish.
3. Use Gparted automatically (to format and create new partitions).
4. Step by step.

That's mean I don't need use software (ex: Fdisk in DOS to format or delete old partitions..) ????

that's right? :(

---

### Post by Inxsible on 2007-11-15
> **MrQuangnd said:**
> So...I should:

1. Simple insert LiveCD Ubuntu into DVDROM
2. Run install then boot finish.
3. Use Gparted automatically (to format and create new partitions).
4. Step by step.

That's mean I don't need use software (ex: Fdisk in DOS to format or delete old partitions..) ????

that's right? :(Correct.

---

### Post by Duck2006 on 2007-11-15
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by MrQuangnd on 2007-11-15
I read all replies...
**eldragon **adviced I should *use the 20gb ata for the root partiton and OS, and use the 80gb for the home partition* (with this work, i can have a fresh distro with uprade...)
but if i choose partition automatically (by Gparted) I can do as he said or not?

if i must partition manually, I should split two HDD into partitions how? somebody help me explain...where root partition?( format type, capacity, what's HDD)? where home partition (...) ???? Swap partition???
....or show me where have some tutorials about it.

pls let me know...thanks so much !!!

---

### Post by Inxsible on 2007-11-15
> **Duck2006 said:**
> [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
This is a great tutorial. Go through it. Its illustrated, so you cant go wrong.

---

### Post by buccaneere on 2007-11-15
> **Inxsible said:**
> 1) Low level format is where you write you disk with a bunch of 0's and 1's to remove any trace of existing data on it

Excellent description.

Good answer too, to the more important question that he asked... [SIZE="5"][COLOR="Red"]HOW[/COLOR][/SIZE]:confused:

---

### Post by buccaneere on 2007-11-15
> **MrQuangnd said:**
> So...I should:

1. Simple insert LiveCD Ubuntu into DVDROM
2. Run install then boot finish.
3. Use Gparted automatically (to format and create new partitions).
4. Step by step.

That's mean I don't need use software (ex: Fdisk in DOS to format or delete old partitions..) ????

that's right? :(


I'm with ya dude, on not gettin answers to yer questions. Just not too many answers here:confused:

BGates is LOL.

---

### Post by Inxsible on 2007-11-15
> **buccaneere said:**
> Excellent description.

Good answer too, to the more important question that he asked... [SIZE=5][COLOR=Red]HOW[/COLOR][/SIZE]:confused:
if you need an answer to your query, why don't you start your own thread rather than shouting in here. 

He wanted to know what low level format was and it isn't required for him since he only wants to change partition tables. Read all the posts please.

---

### Post by buccaneere on 2007-11-15
> **Inxsible said:**
> if you need an answer to your query, why don't you start your own thread rather than shouting in here. 
I did. With identical results. Lotta' wasted electrons. 
[http://ubuntuforums.org/showthread.php?t=610453](http://ubuntuforums.org/showthread.php?t=610453)
UNANSWERED.

> **Inxsible said:**
> He wanted to know what low level format was and it isn't required for him
Who's to say he can't have the knowledge he seeks? YOU?

I know someone else who says that - his initials are bill gates.

> **Inxsible said:**
>  Read all the posts please.
I did. 

I want the same knowledge - formatting low-level/write to access/partition deletion, whatever is necessary to get my solution.

I ain't got it. Lotsa' thread cloggin' responses like yours, but not the answer to the question.

And it looks like a common problem...

---

### Post by buccaneere on 2007-11-15
> **indytim said:**
> If you want to really "clean" those hard drives before adding partitions via GParted Live, I'd recommend doing a low level format of both drives.  That will get you back to a new state as far as the 0s & 1s are concerned :).

IndyTim

Great advice.

HOW???

---

### Post by buccaneere on 2007-11-15
> **eldragon said:**
> i would use the 20gb ata for the root partiton and OS, and use the 80gb for the home partition. this would give you home independance between OS formats :D

More great advice.

And the OP's question is unanswered.

Surprise, surprise.

---

### Post by Inxsible on 2007-11-15
> **buccaneere said:**
> I did. With identical results. Lotta' wasted electrons. 
[http://ubuntuforums.org/showthread.php?t=610453](http://ubuntuforums.org/showthread.php?t=610453)
UNANSWERED.


Who's to say he can't have the knowledge he seeks? YOU?

I know someone else who says that - his initials are bill gates.


I did. 

I want the same knowledge - formatting low-level/write to access/partition deletion, whatever is necessary to get my solution.

I ain't got it. Lotsa' thread cloggin' responses like yours, but not the answer to the question.

And it looks like a common problem...

> **buccaneere said:**
> Great advice.

HOW???

> **buccaneere said:**
> More great advice.

And the OP's question is unanswered.

Surprise, surprise.With that attitude, you will surely not get responses. People here are not obligated to give you answers. They are not paid for it. They do so out of their own free will.

So please, Request, don't Demand !!!

If you want, you can always pay for support. There are lots of companies that do provide support for Linux. But of course, you wouldn't wanna do that, now would you?
The other way could be taking the pain to search through the forum or better yet, Google. It can do wonders !!

In any case, I think you are only here to start flaming wars, so I shall end it right here.

Also, most importantly, please do not misquote me.

I said>  He wanted to know what low level format was and it isn't required for him since he only wants to change partition tables It was not required for him because he only wanted to partition his drive not nuke it. There was no point in going into that in this thread.

---

### Post by MrQuangnd on 2007-11-16
I installed Ubuntu on HDD 80GB SATA (auto partition with Gparted in LiveCD) while 20GB ATA still contain Ubuntu that installed from first.

Then install finish, I take a message: "Missing operating system" :( 
I used fdisk to delete all partition Linux on 20GB ATA but still take old message.

Conti, I logged into BIOS and choose boot from 20GB ATA. Fortunatly, I looked a list OS...
3 item at first for Ubuntu that I have just installed.
3 item at last for Ubuntu that I deleted :( (I don't understand why? about sector or MBR ? :( )

And now, I want to configure GRUB again to only boot from 80GB SATA and menu list with 6 items replaced by 3 items...How must i do?
and I also want to repartition 20GB ATA how to I can use this HDD store data...

pls let me know...thanks a lot!

---

### Post by Inxsible on 2007-11-16
you would be better off with a fresh install at this point.

Follow this [guide]("http://www.psychocats.net/ubuntu/installing") to help you out

---

### Post by MrQuangnd on 2007-11-16
i don't want to install again...!
I need configure GRUB ... 
Should I post new topic?

---

