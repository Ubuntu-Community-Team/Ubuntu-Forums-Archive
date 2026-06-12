---
title: "Vista, compaq v6000 and partitions"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by blk03mitsues on 2007-05-04
let me start off with......i got a compaq presario v6000 laptop with vista home premium. its AMD Turion 64 mobile with 1 gig of ram, nvidia graphics. oh and vista is pre installed

from reading other threads i learned that the broadcom hardware the laptop uses gives problems if i ever want to connect wirelessly to the net. if i can fix this great if not i can always plug a cable directly to the router. I primarily use this laptop at work for things such as internet, music, dvd's, MS word, MS excel and sometimes i use photoshop/illustrators/flash/dreamweaver and other webdesign tools when i'm bored. 
i know websurfing, music, dvds, word and excel can easily be substituted in ubuntu. i recently installed Xubuntu on an old p3 900mhz 256mb ram and 60gig hd. it was flawlessly. like the desktop look, felt like it was a mac/xp hybrid but i know its not. problem is this pc is at home and i spend more time at work so i can really mess around with. i have another pc with a VIA c3 1 ghz that i will install ubuntu 7. but thats another story.

so the reason for my thread is. I want to install ubuntu on my laptop so that i can spend more time with it. so that i can learn. my first question.

should i attempt installing ubuntu on this laptop? problems that come to mind, are the errors other people have with installs on this series of presarios, other minor one would be the broadcom issues as far as wireless connection, and last but not least not having an install cd for vista. if you think i should just wait to have the VIA C3 system up and running and just bring it to the office then there's no point to keep going on this thread.

now if you think i should give it a try, then how do i partition my hard drive? i read that people partition when they're installing vista. but i cant do that as i dont have a vista cd, system comes with it preinstalled? if there's a way to partition the hdd, will i loose my exhisting files in vista?

how many partitions do i need? i've read that some people post like 3 or 4 different partitions. 2 are obvious 'cus they're for vista and ubuntu. one is a shared i guess for files. but there also got another couple. anybody want to explain this to me.

i really like how this community bonds. thanks in advance for anybody that reply

---

### Post by icechen1 on 2007-05-04
> **blk03mitsues said:**
> 
from reading other threads i learned that the broadcom hardware the laptop uses gives problems if i ever want to connect wirelessly to the net.
 You can  use ndiswrapper to make the wireless work.

---

### Post by blk03mitsues on 2007-05-04
so that takes care of wireless....how about the rest?

---

### Post by carrie.peary on 2007-05-04
Hey, finally someone else with a Compaq Presario! Anyways, I had the same questions you do when I first got it all, and yes, the Broadcom wireless chip is a piece of crap when it comes to Ubuntu usage, it's given me such headaches. But luckily, the new version of Ubuntu (Fiesty Fawn) came out recently. If you download that, you'll still have to do a couple steps probably to get your wireless to work but it's not what it use to be, since you now don't have to download any additional programs/drivers. We got mine to work in 5min this time around (accidentally deleted stuff when upgrading, so I had to start over). So you'll be fine there.

As for partitions, everyone seems to have the standard 4 partitions (/root, fat32 (for sharing), swap, and your windows) here is a great explanation/tutorial on partitions:  [http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning") hope that helps some. 

Good luck with it all!

---

### Post by blk03mitsues on 2007-05-04
that site was great. but i'm still confused about the swap partition. it said to make it double of the ram but whats the actual importance of the swap? ooh and windows is ntfs/ubuntu is ext3/shared fat32....so what kind is the swap?

on a side note.....for the VIA C3 system i'll end up getting two HDDs. One for ubuntu/ext3 and one fat32 for files. another hard drive partition the same way but i'll just this one to mess around with. that way i always have a drive with a perfectly working OS and anotherone that might end up screwing lol

---

### Post by fsSnowboard on 2007-05-04
I just got this laptop and am having trouble booting off of the live cd.  I also tried to boot into Knoppix and X would load, so I think there is some issue with X and the laptop, but am not sure.

---

