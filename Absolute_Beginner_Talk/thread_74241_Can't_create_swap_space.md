---
title: "Can't create swap space"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by editrix on 2005-10-11
I installed Ubuntu 5.04 on a pre-partitioned HD. The 2nd partition was unformatted, and when I got to the partitioner, it didn't create a swap space. So I tried reinstalling, figuring when I got to the "format" part, it would go through the correct hoops this time. It didn't.

Here's what the screen says now:

You are editing partition #2 of IDE1 mster (hda) ... All data will be destroyed ...

Partition settings:

Use as:	                   Ext3
Format partition: 	Yes, format it
Mount point:	         /
Mount options:	       defaults
Label:	                   /
Reserved blocks:      5%
Typical usage:	       standard
Bootable flag:	        on
Size: 	                  4.6GB

4.6GB is the entire partition. No option to create swap space.

I'm wondering, should I delete this second partition, or somehow "erase" the Ubuntu I have there now, to create free space, or what?

---

### Post by wishyjr on 2005-10-11
you have to create another partition (quite small - try one double the size of your RAM) and tell that to be the swap partition.

your ubuntu is gonig onto partition 2? does that mean you have a first partition with something else on it? (i.e. windows?)

if so then you need that third partition for a swap space.

---

### Post by editrix on 2005-10-11
[QUOTE=wishyjr]you have to create another partition (quite small - try one double the size of your RAM) and tell that to be the swap partition.

your ubuntu is gonig onto partition 2? does that mean you have a first partition with something else on it? (i.e. windows?)

if so then you need that third partition for a swap space.[/QUOTE]

Yes, I know what I have to do, I just don't know how to do it. The partitioner never gives me the option to create swap space. IOW, there's no free space detected by the partitioner, so it never asks me how I want to split that space.

I don't even know if the above makes sense to anyone but me.

And, yes, the 1st partition is Win98. Sorry, should have said.

I guess what I want to do is split the 2nd, existing partition into / and swap space, during the Ubuntu 5.04 install process.

---

### Post by wishyjr on 2005-10-11
sorry to be vauge but i am sure that if you edit the partition table manually then the options are there somewhere to 'cut' a chunk out of the 2nd partition then you set the 'use as' parameter to 'swap file' ..or something.

---

### Post by editrix on 2005-10-11
[QUOTE=wishyjr]sorry to be vauge but i am sure that if you edit the partition table manually then the options are there somewhere to 'cut' a chunk out of the 2nd partition then you set the 'use as' parameter to 'swap file' ..or something.[/QUOTE]

wishyjr, I wish someone could tell me where. I've been searching this website, and no one seems to have quite my problem. It's as if the partitioner sees no free space, and can only split free space. 

Thanks for trying. Part of my problem is, despite the screenshots I've seen elsewhere on the web, I really don't know what's supposed to happen. It just seems to me there should be an option, if a partition is already formatted, to repartition/split it. Or the partitioner ask me if I want to make a swap, while it's formatting for me.

---

### Post by wishyjr on 2005-10-11
ok. dunno if this will help steer you into the right place but check this out:

step 7

[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo) 

maybe that'll help? if you run from that step on your 2nd partition?

---

### Post by editrix on 2005-10-11
[QUOTE=wishyjr]ok. dunno if this will help steer you into the right place but check this out:

step 7

[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo) 

maybe that'll help? if you run from that step on your 2nd partition?[/QUOTE]

My problem is, I can't get to step 7. But thanks for bringing this up. I read it, ages ago, but who remembers?

Also from the wiki: (later: spent ages making nice indents on this post, and none of them show up in the preview!)

The installer will then detect your hard drives and load the disk partitioner.

   1.  Choose "Manually edit partition table"
          

I did.
       
        Listed will be your current partitions

They were.
   
   2.   Select the partition you want to resize and press Enter.

I did.

    3. Select "Size:", press Enter.

Okay, here's where I stumble. Of course, I can't see it now, but I don't recall seeing anything for size.

     4. Select Yes, press Enter.

No idea what this is referring to.

      5. Type in a new size in Gigabytes for your the partition,

Well, I don't want a new size. I want the partition to be the size it is. 

      6. Create a swap partition of around 500mb.

I'm never given the opportunity to.

Time for one of those banging-the-head-against-the-wall thingies.

---

### Post by wishyjr on 2005-10-11
[B]5. Type in a new size in Gigabytes for your the partition,

Well, I don't want a new size. I want the partition to be the size it is. [/B]

-you have to make that partition smaller so that you can use some of it to create another partition (the swap partition). Try making your second partition 500MB smaller than it is now then create a new (third) partition and set it as a swap. You wont get the option to make a swap if theres no space to do it with mate.

---

### Post by aragorn2909 on 2005-10-11
[QUOTE=editrix]My problem is, I can't get to step 7. But thanks for bringing this up. I read it, ages ago, but who remembers?

Also from the wiki: (later: spent ages making nice indents on this post, and none of them show up in the preview!)

The installer will then detect your hard drives and load the disk partitioner.

   1.  Choose "Manually edit partition table"
          

I did.
       
        Listed will be your current partitions

They were.
   
   2.   Select the partition you want to resize and press Enter.

I did.

    3. Select "Size:", press Enter.

Okay, here's where I stumble. Of course, I can't see it now, but I don't recall seeing anything for size.

     4. Select Yes, press Enter.

No idea what this is referring to.

      5. Type in a new size in Gigabytes for your the partition,

Well, I don't want a new size. I want the partition to be the size it is. 

      6. Create a swap partition of around 500mb.

I'm never given the opportunity to.

Time for one of those banging-the-head-against-the-wall thingies.[/QUOTE]


In terms of step 5, you DO want a new size.  Enter in the size of your partition, minus say 500 megs.  This will resize your / partition and allow you to create a 500 meg swap space

* you beat me to the punch wishyjr, quick fingers.

---

### Post by editrix on 2005-10-11
Hi wishyjr and aragorn2909:

Guess what! I'm here, posting through Ubuntu--and I'd have been here 15 minutes earlier but for some reason my dialup connection is slo-o-o-w. Hope it's just Firefox, which I don't like anyway.

Thanks for all your help. I guess I just didn't understand partitioning the way I thought I did. The screenshots I saw on the web led me to believe the partitioner would jump to the swap configurer automatically.

Anyway, I bit the bullet and just kept pressing enter and other buttons until I managed it, but somehow, you make it much clearer. II feel kind of stupid for not figuring it out myself before.

And, please stay tuned, because I know I'll have a lot more questions. :D

---

### Post by Ishmael on 2005-10-11
Since I have the same problem I hardly beleive that you do not understand the problem even if the other newbee explains you his problem four or five times. The problem is not the space for paritition or the fifth pot of istructions. The problem is where to find command wich will start the proces which will create swap partition, or how to start this process.In other words what one must do to triger this event which will bring desired goal which is swap partition. Or the installation procese wil do this automaticaly only if this space will yust lay ther on the dard disk.

LIFE IS BEAUTIFUL

---

### Post by wishyjr on 2005-10-12
glad you go it sorted matey!! oooh i feel all warm and fuzzy.. but i think thats just my hangover. :)

---

### Post by editrix on 2005-10-12
Ishmael wrote:
>The problem is where to find command wich will start the proces 

Yes, that is the problem. Also fear, because if you have the guts to just keep pushing buttons, eventually (usually) the right one appears. But the fear is well founded, and probably not common enough. I think if I ever recommend Linux of any flavour to a newbie, I'll recommend they buy a cheap used computer to eliminate the fear factor.

---

### Post by wishyjr on 2005-10-12
lol i agree, ive binned many a computer starting out on linux! but got there eventually. :)

---

